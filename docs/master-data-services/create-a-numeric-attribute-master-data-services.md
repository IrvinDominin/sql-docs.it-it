---
title: "Creare un attributo numerico (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "attributi [Master Data Services], creazione di attributi per numeri"
  - "creazione di attributi per numeri [Master Data Services]"
ms.assetid: c0dbb6d8-ba78-485a-a40d-6d5cb7e75d0a
caps.latest.revision: 9
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# Creare un attributo numerico (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] creare un attributo numerico quando si vuole che gli utenti immettano un numero come valore di attributo.  
  
> [!NOTE]  
>  Gli attributi numerici presentano limitazioni. Per altre informazioni, vedere [Attributi &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md).  
  
## Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   È necessario che sia presente un'entità perché ne venga creato l'attributo. Per altre informazioni, vedere [Creare un'entità &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
## Informazioni sugli attributi  
 Per ogni indice creato, viene aggiunta alla griglia una riga con sette colonne. La tabella seguente descrive le colonne.  
  
|Colonna|Description|  
|------------|-----------------|  
|Stato|Stato dell'attributo.<br /><br /> Quando si fa clic su Salva viene visualizzata l'immagine ![Icon for updating status](../master-data-services/media/mds-statusicon-updating.png "Icon for updating status") che indica che l'attributo è in fase di aggiornamento.<br /><br /> Se si verificano errori durante la creazione o la modifica di un attributo, viene visualizzata l'immagine ![Icon for error status](../master-data-services/media/mds-statusicon-error.png "Icon for error status").<br /><br /> In caso contrario, lo stato è OK e viene visualizzata l'immagine ![Icon for OK status](../master-data-services/media/mds-statusicon-ok.png "Icon for OK status").|  
|Nome|Nome dell'attributo.|  
|Nome visualizzato|Nome visualizzato dell'attributo.|  
|Description|Descrizione dell'attributo.|  
|Larghezza in pixel visualizzazione|Larghezza dell'attributo.|  
|Tipo e proprietà|Informazioni sul tipo e sul tipo di dati dell'attributo.|  
|Abilita rilevamento modifiche|Specifica se l'attributo è abilitato per il rilevamento delle modifiche e visualizza tra parentesi il numero del gruppo.|  
  
 Quando si fa clic su un attributo vengono visualizzate le informazioni seguenti.  
  
-   **Creato da**: nome dell'utente che ha creato l'attributo.  
  
-   **Il**: data e ora di creazione dell'attributo.  
  
-   **Aggiornato da**: nome dell'ultimo utente che ha aggiornato l'attributo.  
  
-   **Il**: data e ora dell'ultimo aggiornamento dell'attributo.  
  
### Per creare un attributo numerico  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Nella pagina **Gestisci modelli** selezionare un modello dalla griglia, quindi fare clic su **Entità**.  
  
3.  Nella pagina **Gestisci entità** selezionare la riga dell'entità per la quale si vuole creare un attributo.  
  
4.  Fare clic su **Attributi**.  
  
5.  Nella pagina **Gestisci attributi** eseguire una di queste operazioni, quindi fare clic su **Aggiungi**.  
  
    -   Se l'attributo è per i membri foglia, selezionare **Foglia** nella casella di riepilogo **Tipo di membro** .  
  
    -   Se l'attributo è per i membri consolidati, selezionare **Consolidato** nella casella di riepilogo **Tipo di membro** .  
  
    -   Se l'attributo è per le raccolte, selezionare **Raccolta** nella casella di riepilogo **Tipo di membro** .  
  
6.  Nella casella **Nome** digitare un nome per l'attributo. Per un elenco di parole che non vanno usate come nomi di attributo, vedere [Parole riservate &#40;Master Data Services&#41;](../master-data-services/reserved-words-master-data-services.md).  
  
7.  Facoltativamente, digitare un nome visualizzato e specificare una descrizione per l'attributo nella casella **Descrizione**.  
  
8.  Nella casella **Larghezza in pixel visualizzazione** digitare la larghezza della colonna attributo da visualizzare nella griglia **Esplora** .  
  
9. Nell'elenco **Tipo di attributo** selezionare **Formato libero**.  
  
10. Nell'elenco **Tipo di dati** selezionare **Numero**.  
  
11. Nella casella **Decimali** digitare il numero di cifre che è possibile immettere dopo un separatore decimale.  
  
12. Nella casella di riepilogo **Maschera di input** selezionare un formato per i numeri negativi.  
  
13. Facoltativamente, selezionare **Abilita rilevamento modifiche** per tenere traccia delle modifiche a gruppi di attributi. Per altre informazioni, vedere [Aggiungere attributi ad un gruppo rilevamento modifiche &#40;Master Data Services&#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).  
  
14. Fare clic su **Salva**.  
  
## Vedere anche  
 [Attributi &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)   
 [Modificare il nome e il tipo di dati di un attributo &#40;Master Data Services&#41;](../master-data-services/change-an-attribute-name-and-data-type-master-data-services.md)   
 [Creare un attributo basato su dominio &#40;Master Data Services&#41;](../master-data-services/create-a-domain-based-attribute-master-data-services.md)   
 [Creare un attributo di file &#40;Master Data Services&#41;](../master-data-services/create-a-file-attribute-master-data-services.md)  
  
  