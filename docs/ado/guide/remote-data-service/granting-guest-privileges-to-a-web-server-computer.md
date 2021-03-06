---
title: Concessione dei privilegi Guest a un Computer Server Web | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- guest privileges in RDS [ADO]
ms.assetid: e851a22d-01bc-4eb0-bc42-92b8f65d1c63
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f0ebb888b223cab81d01817ec4c10f96813d3f3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678479"
---
# <a name="granting-guest-privileges-to-a-web-server-computer"></a>Concessione dei privilegi Guest a un computer server Web
L'account anonimo di server Web (IUSR_*ComputerName*) deve essere aggiunto al gruppo locale utenti guest nel computer del server Web per usare servizi desktop remoto.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più incluse nel sistema operativo Windows (vedere Windows 8 e [indicazioni sulla compatibilità di Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). I componenti client di servizi desktop remoto verranno rimosso in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che usano servizi desktop remoto devono eseguire la migrazione a [di WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
### <a name="to-grant-guest-privileges-to-a-web-server-computer"></a>Per concedere privilegi guest a un computer server Web  
  
1.  Nel computer Microsoft Windows 2000 Server, fare clic su **avviare**, scegliere **programmi**, scegliere **strumenti di amministrazione**, quindi fare clic su **Computer Gestione**.  
  
2.  Nell'albero della console, in **utenti e gruppi locali**, fare clic su **gruppi**.  
  
3.  Selezionare il **guest** gruppo locale. Dal **azione** menu, scegliere **proprietà**.  
  
4.  Nel **proprietà gli utenti guest** finestra di dialogo, fare clic su **Add**.  
  
5.  Se l'account anonimo di server Web non vengono visualizzati nell'elenco il **Seleziona utenti o gruppi** finestra di dialogo, digitare il nome (IUSR_*ComputerName*) nella parte inferiore della casella vuota e quindi fare clic su **Add** .  
  
6.  Fare clic su **OK**.


