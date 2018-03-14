---
title: Database di pubblicazione | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newpubwizard.publicationdatabase.f1
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 23969b740711c3c3184438d984953a1535820f34
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="publication-database"></a>Database di pubblicazione
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Il database di pubblicazione è il database del server di pubblicazione che funge da origine dei dati e degli oggetti di database da replicare. Tutti i database utilizzati nella replica devono essere abilitati. Il database viene abilitato quando un membro del ruolo predefinito del server **sysadmin** :  
  
-   Crea una pubblicazione nel database tramite la Creazione guidata nuova pubblicazione.  
  
-   Seleziona il database nella finestra di dialogo **Proprietà server di pubblicazione** .  
  
-   Esegue **sp_replicationdboption** e imposta su **True** l'opzione per la **pubblicazione** relativa a snapshot e pubblicazioni transazionali o l'opzione per la **pubblicazione di tipo merge**relativa a pubblicazioni di tipo merge.  
  
## <a name="options"></a>Opzioni  
 **Database**  
 Consente di selezionare il nome del database contenente i dati e gli oggetti di database che si desidera pubblicare.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicare dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Visualizzare e modificare le proprietà del server di pubblicazione e del database di distribuzione](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_replicationdboption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)  
  
  
