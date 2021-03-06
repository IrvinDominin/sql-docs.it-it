---
title: ADCPROP_AUTORECALC_ENUM | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_AUTORECALC_ENUM
helpviewer_keywords:
- ADCPROP_AUTORECALC_ENUM [ADO]
ms.assetid: ded4f087-87b9-4efa-8026-bde53d3e9e8a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bb10b3f4fb563275a8f27a92e41c265336c3cb55
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47815719"
---
# <a name="adcpropautorecalcenum"></a>ADCPROP_AUTORECALC_ENUM
Specifica quando il [MSDataShape](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) provider nuovamente Calcola aggregazione e le colonne calcolate in un Recordset gerarchico.  
  
 Queste costanti vengono utilizzate solo con il **MSDataShape** provider e il **Recordset** "**ricalcolo automatico**" proprietà dinamiche, che fa riferimento il [ADO Indice delle proprietà dinamiche](../../../ado/reference/ado-api/ado-dynamic-property-index.md) e documentato nel [Microsoft Cursor Service per OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) o [Microsoft Data shaping per OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) documentazione.  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adRecalcAlways**|1|Valore predefinito. Vengono ricalcolati ogni volta che il **MSDataShape** provider determina i valori che le colonne calcolate dipendono sono stati modificati.|  
|**adRecalcUpFront**|0|Calcola solo quando viene creato inizialmente il gerarchica **Recordset**.|  
  
## <a name="adowfc-equivalent"></a>Equivalente di ADO o WFC  
 Queste costanti non dispongono di equivalenti di ADO o WFC.
