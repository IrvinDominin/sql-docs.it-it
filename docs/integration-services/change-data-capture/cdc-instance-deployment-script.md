---
title: CDC Instance Deployment Script | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: change-data-capture
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8fa82822-ac99-48ef-a18d-f4f3a77105b4
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eaa5e76954f4ad9f694128d72fb647ee72395610
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="cdc-instance-deployment-script"></a>CDC Instance Deployment Script
  Nella finestra di dialogo CDC Instance Deployment Script viene visualizzato lo script di distribuzione dell'istanza di CDC. Questo script può essere usato per ricreare il database CDC con tutti i relativi elementi in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] diversa.  
  
 Al completamento dello script di distribuzione, è necessario accertare le condizioni seguenti:  
  
-   Lo script di distribuzione presuppone che l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di destinazione sia stata preparata per Oracle CDC, tramite Oracle CDC Service Configuration Console o lo **script di preparazione** creato dal programma.  
  
-   La parte dello script utilizzata per abilitare il database per CDC deve essere eseguita con il ruolo `sysadmin`.  
  
-   Nello script non viene memorizzata la password di log mining di Oracle. Questa operazione deve essere eseguita manualmente dopo l'esecuzione dello script e l'avvio del servizio CDC.  
  
 Selezionare le opzioni seguenti nella finestra di dialogo **CDC Instance Deployment Script** .  
  
 **Save As**  
 Tramite questa opzione è possibile salvare lo script in un file di testo nel percorso desiderato. È possibile copiare il file con lo script in qualsiasi altro server si desideri eseguirlo.  
  
 **Copia**  
 Tramite questa opzione è possibile copiare lo script negli Appunti. Sarà quindi possibile incollare lo script in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o in qualsiasi editor di testo per eseguirlo in un momento successivo.  
  
## <a name="see-also"></a>Vedere anche  
 [Preparare SQL Server per CDC](../../integration-services/change-data-capture/prepare-sql-server-for-cdc.md)  
  
  
