---
title: STArea (tipo di dati geometry) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- STArea (geometry Data Type)
- STArea_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STArea (geometry Data Type)
ms.assetid: a7dd6083-c649-4ac3-885d-1234e0db62f1
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 87325f0124b52f6b77c9b62d67b1eec6915afbbb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="starea-geometry-data-type"></a>STArea (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Restituisce l'area della superficie totale di un **geometry** istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STArea ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **float**  
  
 Tipo CLR restituito: **SqlDouble**  
  
## <a name="remarks"></a>Osservazioni  
 `STArea()`Restituisce 0 se un **geometry** istanza contiene solo figure 0 e 1-dimensioni o se è vuota. `STArea()`Restituisce **NULL** se il **geometry** istanza non inizializzata.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-computing-the-area-of-a-polygon-instance"></a>A. Calcolo dell'area di un'istanza Polygon  
 Nell'esempio seguente viene creato un `Polygon``geometry` istanza e viene calcolata l'area del poligono.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STArea();  
```  
  
### <a name="b-computing-the-area-of-a-curvepolygon-instance"></a>B. Calcolo dell'area di un'istanza CurvePolygon  
 Nell'esempio seguente viene calcolata l'area di un'istanza `CurvePolygon`:  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(0 2, 2 0, 4 2, 4 2, 0 2))');  
 SELECT @g.STArea() AS Area;
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
