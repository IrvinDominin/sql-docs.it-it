---
title: Set di righe MDSCHEMA_KPIS | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: be7d4519be7f113a3ddfd058f9e890ba71409b9d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34028892"
---
# <a name="mdschemakpis-rowset"></a>Set di righe MDSCHEMA_KPIS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Descrive gli indicatori di prestazioni chiave (KPI) all'interno di un database.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **MDSCHEMA_KPIS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Database di origine.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Non supportato.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Cubo padre per l'indicatore di prestazioni chiave (KPI).|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**|Gruppo di misure associato per l'indicatore di prestazioni chiave (KPI).<br /><br /> È possibile utilizzare questa colonna per determinare la dimensionalità dell'indicatore di prestazioni chiave (KPI). Se "**\<NULL >**", l'indicatore KPI verrà dimensionato in base a tutti i gruppi di misure.<br /><br /> Il valore predefinito è "**\<NULL >**".|  
|**NOME_KPI**|**DBTYPE_WSTR**|Nome dell'indicatore di prestazioni chiave (KPI).|  
|**KPI_CAPTION**|**DBTYPE_WSTR**|Etichetta o didascalia associata all'indicatore di prestazioni chiave (KPI). Utilizzata principalmente a scopo di visualizzazione. Se non esiste una didascalia, **nome_kpi** viene restituito.|  
|**KPI_DESCRIPTION**|**DBTYPE_WSTR**|Descrizione leggibile dell'indicatore di prestazioni chiave (KPI).|  
|**KPI_DISPLAY_FOLDER**|**DBTYPE_WSTR**|Una stringa che identifica il percorso della cartella di visualizzazione che l'applicazione client utilizza per mostrarla al membro. Il separatore di livello delle cartelle è definito dall'applicazione client. Per gli strumenti e i client forniti da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], la barra rovesciata (\\) è il separatore di livello. Per fornire più cartelle di visualizzazione, utilizzare un punto e virgola (;) per separare le cartelle.|  
|**KPI_VALUE**|**DBTYPE_WSTR**|Nome univoco del membro nella dimensione di tipo misura per il valore dell'indicatore di prestazioni chiave (KPI).|  
|**KPI_GOAL**|**DBTYPE_WSTR**|Nome univoco del membro nella dimensione di tipo misura per l'obiettivo dell'indicatore di prestazioni chiave (KPI).<br /><br /> Restituisce **NULL** se non vi è alcun obiettivo definito.|  
|**KPI_STATUS**|**DBTYPE_WSTR**|Nome univoco del membro nella dimensione di tipo misura per lo stato dell'indicatore di prestazioni chiave (KPI).<br /><br /> Restituisce **NULL** se non vi sono stati definiti.|  
|**KPI_TREND**|**DBTYPE_WSTR**|Nome univoco del membro nella dimensione di tipo misura per la tendenza dell'indicatore di prestazioni chiave (KPI).<br /><br /> Restituisce **NULL** se non vi è alcuna tendenza definita.|  
|**KPI_STATUS_GRAPHIC**|**DBTYPE_WSTR**|Rappresentazione grafica predefinita dell'indicatore di prestazioni chiave (KPI).|  
|**KPI_TREND_GRAPHIC**|**DBTYPE_WSTR**|Rappresentazione grafica predefinita dell'indicatore di prestazioni chiave (KPI).|  
|**KPI_WEIGHT**|**DBTYPE_WSTR**|Nome univoco del membro nella dimensione di tipo misura per il peso dell'indicatore di prestazioni chiave (KPI).|  
|**KPI_CURRENT_TIME_MEMBER**|**DBTYPE_WSTR**|Nome univoco del membro nella dimensione temporale che definisce il contesto temporale dell'indicatore di prestazioni chiave (KPI).<br /><br /> Restituisce **NULL** se non è presente alcun membro temporale definito.|  
|**KPI_PARENT_KPI_NAME**|**DBTYPE_WSTR**|Nome dell'indicatore di prestazioni chiave (KPI) padre.|  
|**AMBITO**|**DBTYPE_I4**|Ambito dell'indicatore di prestazioni chiave (KPI). L'indicatore di prestazioni chiave (KPI) può corrispondere a un indicatore di prestazioni chiave di sessione o globale.<br /><br /> I possibili valori della colonna sono i seguenti:<br /><br /> MDKPI_SCOPE_GLOBAL=1<br /><br /> MDKPI_SCOPE_SESSION=2|  
|**ANNOTAZIONI**|**DBTYPE_WSTR**|(Facoltativo) Set di note, in formato XML.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **MDSCHEMA_KPIS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**NOME_KPI**|**DBTYPE_WSTR**|Facoltativa.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Facoltativo) Restrizione predefinita è un valore di **1**. Una bitmap con uno dei valori validi seguenti:<br /><br /> **1** CUBO<br /><br /> **2** DIMENSIONE|  
  
## <a name="see-also"></a>Vedere anche  
 [OLE DB per OLAP i rowset dello Schema](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
