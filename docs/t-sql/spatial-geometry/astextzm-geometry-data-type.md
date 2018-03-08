---
title: AsTextZM (tipo di dati geometry) | Documenti Microsoft
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AsTextZM_TSQL
- AsTextZM
- AsTextZM (geometry Data Type)
- AsTextZM_(geometry_Data_Type)_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- AsTextZM (geometry Data Type)
ms.assetid: 08ac8aa0-aff7-4b22-87e0-1a1d55dcbc04
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 88403972b53bbefecabde04606f9211c3160ab32
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="astextzm-geometry-data-type"></a>AsTextZM (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce la rappresentazione di Open Geospatial Consortium (OGC) Well-Known Text (WKT) di un'istanza di geometria integrata con qualsiasi **Z** (innalzamento) e **M** valori (misura) appartenente all'istanza.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.AsTextZM ()  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **nvarchar (max)**  
  
 Tipo CLR restituito: **SqlChars**  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creato un `Point` istanza contenente **Z** (innalzamento) e **M** valori (misura). `STAsText()`Seleziona i valori WKT, (1 2); `AsTextZM()` seleziona gli stessi valori WKT e restituisce i valori per **Z** e **M**, generando (1 2 3 4).  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(1 2 3 4)', 0);  
SELECT @g.STAsText();  
SELECT @g.AsTextZM();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geometria](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [M &#40; tipo di dati geometry &#41;](../../t-sql/spatial-geometry/m-geometry-data-type.md)   
 [Z &#40; tipo di dati geometry &#41;](../../t-sql/spatial-geometry/z-geometry-data-type.md)  
  
  

