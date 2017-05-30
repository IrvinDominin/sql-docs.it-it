---
title: "Eseguire i set di raccolta dell&quot;utilità e non appartenenti all&quot;utilità nella stessa istanza di SQL | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca7ee9b3-ef9a-4ba4-83d0-9ee9f80dab27
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d6f1a687472d2ee83f48fe273008a0d60f51bc58
ms.lasthandoff: 04/11/2017

---
# <a name="run-utility-and-non-utility-collection-sets-on-same-sql-instance"></a>Eseguire i set di raccolta dell'utilità e non appartenenti all'utilità nella stessa istanza di SQL
  L'esecuzione side-by-side del set di raccolta di Utilità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e dei set di raccolta non appartenenti a Utilità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è supportata. Ciò significa che un'istanza gestita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può essere monitorata da altri set di raccolta anche se l'istanza è membro di un'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . È tuttavia necessario disabilitare la funzionalità della raccolta dati non appartenente all'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mentre l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene registrata nell'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Dopo la registrazione dell'istanza con il punto di controllo dell'utilità, è possibile riavviare i set di raccolta non appartenenti dell'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Tuttavia, tutti i set di raccolta sull'istanza gestita caricheranno i propri dati nel data warehouse di gestione dell'utilità (UMDW); il nome del file UMDW è sysutility_mdw.  
  
 Per eseguire side-by-side i set di raccolta dell'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e i set di raccolta non appartenenti all'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , tenere presente quanto segue:  
  
-   L'esecuzione side-by-side dei set di raccolta è supportata.  
  
-   È necessario disabilitare gli agenti di raccolta dati esistenti mentre si registrano le istanze nell'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Per soddisfare i requisiti della convalida, è necessario eseguire le stored procedure seguenti sull'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prima di creare un punto di controllo dell'utilità e su un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prima di registrarla nell'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
    ```  
    exec msdb.dbo.sp_syscollector_set_warehouse_database_name NULL  
    exec msdb.dbo.sp_syscollector_set_warehouse_instance_name NULL  
    ```  
  
     Se non si eseguono queste stored procedure prima di avviare la procedura guidata Crea punto di controllo dell'utilità o Aggiungi istanza gestita, l'operazione non riuscirà.  
  
-   È necessario utilizzare il data warehouse di gestione (sysutility_mdw) dell'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per tutti i set di raccolta su un'istanza gestita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e funzionalità di Utilità SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Configurare il data warehouse del punto di controllo dell'utilità &#40;Utilità SQL Server&#41;](../../relational-databases/manage/configure-your-utility-control-point-data-warehouse-sql-server-utility.md)  
  
  