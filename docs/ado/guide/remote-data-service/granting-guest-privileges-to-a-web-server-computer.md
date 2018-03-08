---
title: Concessione dei privilegi Guest in un Computer Server Web | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- guest privileges in RDS [ADO]
ms.assetid: e851a22d-01bc-4eb0-bc42-92b8f65d1c63
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4c9e1f3dace4916b7d8044a5b21f480bacb04238
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="granting-guest-privileges-to-a-web-server-computer"></a>Concessione dei privilegi Guest in un Computer Server Web
L'account del server Web anonimo (IUSR_*ComputerName*) deve essere aggiunto al gruppo locale utenti guest nel computer server Web per l'utilizzo di RDS.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
### <a name="to-grant-guest-privileges-to-a-web-server-computer"></a>Per concedere privilegi guest a un computer server Web  
  
1.  Nel computer Microsoft Windows 2000 Server, fare clic su **avviare**, scegliere **programmi**, scegliere **strumenti di amministrazione**, quindi fare clic su **Computer Gestione**.  
  
2.  Nell'albero della console, in **utenti e gruppi locali**, fare clic su **gruppi**.  
  
3.  Selezionare il **guest** gruppo locale. Dal **azione** menu, scegliere **proprietà**.  
  
4.  Nel **Guests Properties** la finestra di dialogo, fare clic su **Aggiungi**.  
  
5.  Se l'account del server Web anonimo non vengono visualizzati nell'elenco di **Seleziona utenti o gruppi** finestra di dialogo digitare il nome (IUSR_*ComputerName*) nella casella vuota nella parte inferiore e quindi fare clic su **Aggiungi** .  
  
6.  Scegliere **OK**.


