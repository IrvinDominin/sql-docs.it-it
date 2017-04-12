---
title: "Eliminare utenti o gruppi (Master Data Services) | Microsoft Docs"
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
  - "eliminazione di gruppi [Master Data Services]"
  - "gruppi [Master Data Services], eliminazione"
  - "utenti [Master Data Services], eliminazione"
  - "eliminazione di utenti [Master Data Services]"
ms.assetid: 0bbf9d2c-b826-48bb-8aa9-9905db6e717f
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Eliminare utenti o gruppi (Master Data Services)
  Eliminare utenti o gruppi se non si desidera più che accedano a [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
 Prestare attenzione al seguente comportamento quando si eliminano utenti e gruppi:  
  
-   Se si elimina un utente membro di un gruppo che ha accesso a [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], l'utente potrà continuare ad accedere a [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] finché non verrà rimosso dal gruppo Active Directory o locale.  
  
-   Se si elimina un gruppo, tutti gli utenti del gruppo che hanno effettuato l'accesso a [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] verranno visualizzati nell'elenco **Utenti** finché non verranno eliminati.  
  
-   Le modifiche alla sicurezza non vengono propagate a MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] per 20 minuti.  
  
## Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Autorizzazioni utenti e gruppi** .  
  
### Per eliminare utenti o gruppi  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Autorizzazioni utenti e gruppi**.  
  
2.  Per eliminare un utente, rimanere nella pagina **Utenti**. Per eliminare un gruppo, dalla barra dei menu fare clic su **Gestisci gruppi**.  
  
3.  Nella griglia selezionare la riga relativa all'utente o al gruppo che si vuole eliminare.  
  
4.  Fare clic su **Elimina utente selezionato** o **Elimina gruppo selezionato**.  
  
5.  Nella finestra di dialogo di conferma fare clic su **OK**.  
  
## Vedere anche  
 [Sicurezza &#40;Master Data Services&#41;](../master-data-services/security-master-data-services.md)  
  
  