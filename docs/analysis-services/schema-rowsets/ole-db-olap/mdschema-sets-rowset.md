---
title: Set di righe MDSCHEMA_SETS | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MDSCHEMA_SETS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: MDSCHEMA_SETS rowset
ms.assetid: abb00dc0-2b83-48d6-b2ba-6615c1488d06
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d861c23e40464535fbde4b666c2e1429f65c772c
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="mdschemasets-rowset"></a>Set di righe MDSCHEMA_SETS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Descrive i set attualmente definiti in un database, compresi i set con ambito sessione.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **MDSCHEMA_SETS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Nome del database.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Non supportato.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Nome del cubo.|  
|**SET_NAME**|**DBTYPE_WSTR**|Il nome del set, come specificato nella **CREATE SET** istruzione.|  
|**AMBITO**|**DBTYPE_I4**|Ambito del set.<br /><br /> **MDSET_SCOPE_GLOBAL** (**1**)<br /><br /> **MDSET_SCOPE_SESSION** (**2**)|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Non supportato.|  
|**ESPRESSIONE**|**DBTYPE_WSTR**|Espressione per il set.|  
|**DIMENSIONI**|**DBTYPE_WSTR**|Elenco delimitato da virgole delle gerarchie incluse nel set.|  
|**SET_CAPTION**|**DBTYPE_WSTR**|Etichetta o didascalia associata al set. L'etichetta o la didascalia viene utilizzata principalmente per scopi di visualizzazione.|  
|**SET_DISPLAY_FOLDER**|**DBTYPE_WSTR**|Una stringa che identifica il percorso della cartella di visualizzazione che l'applicazione client utilizza per mostrare il set. Il separatore di livello delle cartelle è definito dall'applicazione client. Per gli strumenti e i client forniti da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], la barra rovesciata (\\) è il separatore di livello. Per fornire più cartelle di visualizzazione, utilizzare un punto e virgola (;) per separare le cartelle.|  
|**SET_EVALUATION_CONTEXT**|**DBTYPE_I4**|Contesto del set. Il set può essere statico o dinamico. I possibili valori della colonna sono i seguenti:<br /><br /> MDSET_RESOLUTION_STATIC=1<br /><br /> MDSET_RESOLUTION_DYNAMIC=2|  
  
 Il set di righe viene ordinato in base **CATALOG_NAME**, **SCHEMA_NAME**, **CUBE_NAME**.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **MDSCHEMA_SETS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**SET_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**AMBITO**|**DBTYPE_I4**|Facoltativo.|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|Facoltativo.<br /><br /> Nota: Solo una gerarchia può essere inclusa e le cui gerarchie corrispondono esattamente alla restrizione vengono restituiti solo i set denominati.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
