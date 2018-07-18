---
title: 'Errore del Server Internet: Accesso negato | Documenti Microsoft'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- access denied error in RDS [ADO]
ms.assetid: e5b43cfa-da8d-430d-a2ab-5443dda47a16
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 28e175b244c538fb0bab9d7adfdc1fcf6c2a48bf
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273990"
---
# <a name="internet-server-error-access-denied"></a>Errore del Server Internet: Accesso negato
Se questo errore si verifica in genere significa che Microsoft Internet Information Services (IIS) ha restituito il seguente stato:  
  
 HTTP_STATUS_DENIED 401  
  
 Verificare che le directory a cui accede IIS dispongano delle autorizzazioni appropriate. Servizi Desktop remoto può comunicare con un server Web IIS in esecuzione in una delle tre modalità di autenticazione di Password: anonima, Basic o NT Challenge/Response (denominato autenticazione integrata di Windows in Windows 2000). Il server Web deve disporre delle autorizzazioni per il computer di origine dati se si tratta di un computer Windows NT o Windows 2000.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali su RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)




