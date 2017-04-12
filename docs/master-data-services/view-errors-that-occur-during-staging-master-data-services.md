---
title: "Visualizzare gli errori che si verificano durante il processo di gestione temporanea (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "processo di gestione temporanea [Master Data Services], visualizzazione degli errori"
ms.assetid: 6d2bff84-624b-47fc-a4a5-d9ea01d13412
caps.latest.revision: 8
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 8
---
# Visualizzare gli errori che si verificano durante il processo di gestione temporanea (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], è possibile visualizzare errori che si verificano durante il processo di gestione temporanea. Nel database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , sono disponibili due viste che mostrano errori:  
  
-   stg.viw_name_MemberErrorDetails per foglia o aggiornamenti dei membri consolidati.  
  
-   stg.viw_name_RelationshipErrorDetails per aggiornamenti delle relazioni di gerarchia.  
  
## Prerequisiti  
 Per eseguire questa procedura:  
  
-   Nel database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], è necessario disporre delle autorizzazioni SELECT per la vista stg.viw_name_MemberErrorDetails o stg.viw_name_RelationshipErrorDetails.  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### Per visualizzare gli errori di gestione temporanea  
  
1.  Aprire [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] e connettersi all'istanza [!INCLUDE[ssDE](../includes/ssde-md.md)] per il database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Aprire una nuova query.  
  
3.  Digitare il testo seguente, sostituendo il nome con quello della tabella di gestione temporanea, ad esempio, viw_Product_MemberErrorDetails.  
  
     `SELECT * FROM stg.viw_name_MemberErrorDetails`  
  
4.  Eseguire la query. I dettagli dell'errore vengono visualizzati nel campo **ErrorDescription** .  
  
## Passaggi successivi  
 Per informazioni dettagliate sui messaggi di errore, vedere [Errori del processo di gestione temporanea &#40;Master Data Services&#41;](../master-data-services/staging-process-errors-master-data-services.md).  
  
## Vedere anche  
 [Panoramica: Importazione di dati da tabelle &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)   
 [Risoluzione dei problemi relativi al processo di gestione temporanea (Master Data Services)](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)  
  
  