---
title: La registrazione degli oggetti Business sul Client per l'uso con DCOM | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- business objects in RDS [ADO]
ms.assetid: 75a21910-607f-463a-ae18-a17130dafb7e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4094d147e47bd39298b6dd94b4819eaa3d650eb6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47691009"
---
# <a name="registering-business-objects-on-the-client-for-use-with-dcom"></a>Registrazione degli oggetti business sul client per l'uso con DCOM
Gli oggetti business personalizzati devono assicurarsi che sul lato client può eseguire il mapping il nome del programma (ProgId) a un identificatore di classe (CLSID) che può essere usato su DCOM. Per questo motivo, il ProgID dell'oggetto DCOM deve essere nel Registro di sistema lato client e il mapping all'ID di classe dell'oggetto business sul lato server. Per altri protocolli supportati (HTTP, HTTPS e in-process), ciò non è necessario.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più incluse nel sistema operativo Windows (vedere Windows 8 e [indicazioni sulla compatibilità di Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). I componenti client di servizi desktop remoto verranno rimosso in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che usano servizi desktop remoto devono eseguire la migrazione a [di WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Ad esempio, se si espone un oggetto business sul lato server chiamato MyBObj con un ID di classe specifica, ad esempio, quale "{00112233-4455-6677-8899-00AABBCCDDEE}", assicurarsi che le voci seguenti vengano aggiunti al Registro di sistema lato client:  
  
```  
[HKEY_CLASSES_ROOT]  
\MyBObj\Clsid\(Default) "{00112233-4455-6677-8899-00AABBCCDDEE}"  
```


