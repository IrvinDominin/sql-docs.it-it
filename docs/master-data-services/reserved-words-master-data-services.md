---
title: "Parole riservate (Master Data Services) | Microsoft Docs"
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
  - "parole riservate [Master Data Services]"
  - "Master Data Services, parole riservate"
ms.assetid: 88afd0d0-4362-4394-8357-4e65388fc0fc
caps.latest.revision: 11
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 11
---
# Parole riservate (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], quando si creano oggetti modello o membri, alcune parole non possono essere utilizzate. È possibile che l'utilizzo di queste parole provochi errori.  
  
> [!NOTE]  
>  Inoltre, è necessario limitare l'utilizzo di caratteri speciali (simboli, sillabazione e così via).  
  
-   [Modelli](../master-data-services/reserved-words-master-data-services.md#models)  
  
-   [Entità](../master-data-services/reserved-words-master-data-services.md#entities)  
  
-   [Gerarchie esplicite](../master-data-services/reserved-words-master-data-services.md#exhierarchies)  
  
-   [Attributi](../master-data-services/reserved-words-master-data-services.md#attributes)  
  
-   [Membri](../master-data-services/reserved-words-master-data-services.md#members)  
  
##  <a name="models"></a> Modelli  
 Se si crea un modello con il nome impostato su **Name** o **Code**, non selezionare **Crea entità con lo stesso nome del modello** poiché non è possibile usare **Name** o **Code** per il nome di un'entità.  
  
##  <a name="entities"></a> Entità  
 Per i nomi dell'entità, non è possibile utilizzare **Name** o **Code**.  
  
##  <a name="exhierarchies"></a> Gerarchie esplicite  
 Per i nomi della gerarchia espliciti, non è possibile utilizzare **Name** o **Code**.  
  
##  <a name="attributes"></a> Attributi  
  
-   **ID**  
  
-   **Codice**  
  
-   **EnterUserName**  
  
-   **LastChgUserName**  
  
-   **Nome**  
  
-   **EnterDTM**  
  
-   **EnterUserID**  
  
-   **EnterUserName**  
  
-   **LastChgDTM**  
  
-   **LastChgUserID**  
  
-   **Status_ID**  
  
-   **ValidationStatus_ID**  
  
-   **Version_ID**  
  
##  <a name="members"></a> Membri  
 Per i membri, non è possibile usare **MDMMemberStatus**, **MDMUnused** o **ROOT** per il valore di attributo **Code**.  
  
## Vedere anche  
 [Panoramica di Master Data Services (MDS)](../master-data-services/master-data-services-overview-mds.md)  
  
  