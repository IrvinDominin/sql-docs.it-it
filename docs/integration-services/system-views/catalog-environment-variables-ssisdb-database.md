---
title: catalog.environment_variables (database SSISDB) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 45f5aacd-505a-443b-8fc2-c7929e78cff8
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cb3d2a6db5f17bb8c180e590426cec34b6dbc359
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="catalogenvironmentvariables-ssisdb-database"></a>catalog.environment_variables (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Vengono visualizzati i dettagli delle variabili di ambiente di tutti gli ambienti nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|variable_id|**bigint**|Identificatore (ID) univoco della variabile di ambiente.|  
|environment_id|**bigint**|ID univoco dell'ambiente a cui è associata la variabile.|  
|NAME|**sysname**|Nome della variabile di ambiente.|  
|description|**nvarchar(1024)**|Descrizione della variabile di ambiente.|  
|Tipo|**nvarchar(128)**|Tipo di dati della variabile di ambiente.|  
|sensitive|**bit**|Quando il valore è `1`, la variabile è importante e viene crittografata quando viene archiviata. Quando il valore è `0`, la variabile non è importante e il valore viene archiviato non crittografato.|  
|Valore|**sql_variant**|Valore della variabile di ambiente. Quando sensitive è `0`, viene visualizzato il valore non crittografato. Quando sensitive è `1`, viene visualizzato il valore **NULL**.|  
  
## <a name="remarks"></a>Remarks  
 In questa vista viene visualizzata una riga per ogni variabile di ambiente nel catalogo.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per questa vista è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazione READ sull'ambiente corrispondente  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**  
  
> [!NOTE]  
>  Quando si dispone delle autorizzazioni per eseguire un'operazione nel server, si dispone anche delle autorizzazioni per visualizzare le informazioni sull'operazione. È applicata la sicurezza a livello di riga, pertanto vengono visualizzate solo le righe per le quali si dispone delle autorizzazioni per la visualizzazione.  
  
  
