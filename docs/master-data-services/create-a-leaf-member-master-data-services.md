---
title: "Creare un membro foglia (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "membri foglia [Master Data Services], creazione"
  - "creazione di membri foglia [Master Data Services]"
  - "membri [Master Data Services], creazione di membri foglia"
ms.assetid: 0499d3b3-d508-4d43-a740-19cf53ade9f1
caps.latest.revision: 14
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 14
---
# Creare un membro foglia (Master Data Services)
  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] creare un membro foglia per aggiungere dati master al sistema. Per aggiungere i dati in blocco, usare invece le tabelle di gestione temporanea. Per altre informazioni, vedere [Importare dati dalle tabelle &#40;Master Data Services&#41;](../master-data-services/import-data-from-tables-master-data-services.md)  
  
 È anche possibile usare [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] per importare i dati.  
  
## Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'autorizzazione per accedere all'area funzionale **Esplora** .  
  
-   È necessario avere almeno l'autorizzazione **Create** o **Update** per l'oggetto modello foglia per l'entità a cui si vuole aggiungere un membro. L'autorizzazione Create consente di creare un membro e modificarne solo l'attributo Code. L'autorizzazione Update consente di aggiornare altri attributi.  
  
     Per altre informazioni, vedere [Sicurezza &#40;Master Data Services&#41;](../master-data-services/security-master-data-services.md).  
  
### Per creare un membro foglia  
  
1.  Nella home page di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] selezionare un modello nell'elenco **Modello** .  
  
2.  Se si è un utente, selezionare una versione aperta nell'elenco **Versione**. Se si è un amministratore, selezionare una versione con stato aperto o bloccato nell'elenco **Versione**.  
  
3.  Fare clic su **Esplora**.  
  
4.  Dalla barra dei menu scegliere **Entità**, quindi fare clic sul nome dell'entità alla quale si desidera aggiungere un membro.  
  
5.  Fare clic su **Aggiungi membro**.  
  
6.  Nel riquadro **Dettagli** completare i campi.  
  
     Se è stato applicato un filtro all'attributo che è basato su dominio, l'elenco dei valori di attributo sarà vincolato dall'attributo padre del filtro.  
  
     Per altre informazioni sugli attributi padre del filtro e gli attributi basati su dominio, vedere [Creare un attributo basato su dominio &#40;Master Data Services&#41;](../master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
7.  Facoltativa. Nella casella **Annotazioni** , digitare un commento indicando il perché è stato aggiunto il membro. Tutti gli utenti che dispongono di accesso al membro possono visualizzare l'annotazione.  
  
8.  Scegliere **OK**.  
  
## Vedere anche  
 [Creare membri consolidati &#40;Master Data Services&#41;](../master-data-services/create-a-consolidated-member-master-data-services.md)   
 [Membri &#40;Master Data Services&#41;](../master-data-services/members-master-data-services.md)  
  
  