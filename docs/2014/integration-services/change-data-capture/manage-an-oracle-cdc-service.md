---
title: Gestire un servizio Oracle CDC | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- createSrv
ms.assetid: 5972cee3-b1a9-4c56-aed6-bdddf84af283
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8fb328c6fb7418ad1aa239e63eb537e0857e345c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48073461"
---
# <a name="manage-an-oracle-cdc-service"></a>Gestire un servizio Oracle CDC
  È possibile utilizzare CDC Service Configuration Console per gestire un servizio CDC specifico.  
  
 **Per selezionare il servizio CDC che si desidera utilizzare**  
  
1.  Dal riquadro sinistro di CDC Service Configuration Console, espandere **Local CDC Services**.  
  
2.  Selezionare il servizio CDC che si desidera utilizzare.  
  
     È inoltre possibile fare clic con il pulsante destro del mouse sul servizio CDC da utilizzare e selezionare l'azione desiderata. Vedere [What can you do with a CDC Service](manage-an-oracle-cdc-service.md#bkmk_whatcandowithcdcservice).  
  
 **O**  
  
1.  Selezionare **Local CDC Services** nel riquadro sinistro in CDC Service Configuration Console.  
  
2.  Dalla sezione centrale di CDC Service Configuration Console selezionare il servizio che si desidera utilizzare.  
  
     È inoltre possibile fare clic con il pulsante destro del mouse sul servizio CDC da utilizzare e selezionare l'azione desiderata. Vedere [What can you do with a CDC Service](manage-an-oracle-cdc-service.md#bkmk_whatcandowithcdcservice).  
  
##  <a name="BKMK_WhatcandowithCDCService"></a> What can you do with a CDC Service  
 Quando si utilizza un servizio CDC è possibile eseguire le azioni seguenti:  
  
### <a name="delete-the-service"></a>Eliminare il servizio  
 Dal riquadro **Actions** sul lato destro di CDC Service Configuration Console, fare clic su **Delete** per eliminare il servizio.  
  
 È inoltre possibile fare clic con il pulsante destro del mouse sul servizio CDC da eliminare e scegliere **Delete**.  
  
 **Nota**: se il servizio è in esecuzione al momento dell'eliminazione, il servizio viene arrestato prima di essere eliminato.  
  
 Per eliminare la definizione del servizio Windows di Oracle CDC, è necessario aggiornare l'accesso al database MSXDBCDC nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associata. Quando si fa clic su OK per eliminare il servizio, viene effettuato un tentativo di eliminare la registrazione del servizio Oracle CDC nel database MSXDBCDC. Se non è possibile eliminare la registrazione del servizio Oracle CDC tramite il programma perché non sono disponibili le autorizzazioni appropriate, viene richiesto all'utente di immettere un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con autorizzazioni di aggiornamento per il database MSXDBCDC.  
  
 Per informazioni sui dati da immettere nella finestra di dialogo Connect to SQL Server, vedere [Connection to SQL Server for Delete](connection-to-sql-server-for-delete.md).  
  
### <a name="edit-the-cdc-service-properties"></a>Modificare le proprietà del servizio CDC  
 Dal riquadro **Actions** sul lato destro di CDC Service Configuration Console, fare clic su **Properties**.  
  
 È inoltre possibile fare clic con il pulsante destro del mouse sul servizio CDC in cui si desidera modificare le proprietà e scegliere **Properties**.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura di gestione di un servizio CDC locale](how-to-manage-a-local-cdc-service.md)  
  
  
