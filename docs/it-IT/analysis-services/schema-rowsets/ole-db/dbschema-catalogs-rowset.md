---
title: Set di righe DBSCHEMA_CATALOGS | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBSCHEMA_CATALOGS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DBSCHEMA_CATALOGS rowset
ms.assetid: f02dc75d-5442-4eea-b33a-567dc816be7a
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fe0b9bd6fa59114d95720b4c0b5b631ea88c2748
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="dbschemacatalogs-rowset"></a>Set di righe DBSCHEMA_CATALOGS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Identifica gli attributi fisici associati a cataloghi accessibili dal sistema di gestione di database (DBMS).  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DBSCHEMA_CATALOGS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|255|Nome del catalogo. Non può essere null.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Descrizione leggibile della tabella.|  
|**RUOLI**|**DBTYPE_WSTR**||Elenco di ruoli delimitato da virgole a cui appartiene l'utente corrente.<br /><br /> Un asterisco (\*) è incluso come ruolo se l'utente corrente è un server o amministratore del database.<br /><br /> **Nome utente** viene aggiunto alla **ruoli** se uno dei ruoli utilizza la sicurezza dinamica.|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**||Data dell'ultima modifica apportata al catalogo.|  
  
 Il set di righe viene ordinato in base **CATALOG_NAME**.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DBSCHEMA_CATALOGS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Facoltativo|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello Schema OLE DB](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  