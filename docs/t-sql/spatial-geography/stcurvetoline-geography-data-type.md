---
title: STCurveToLine (tipo di dati geography) | Documenti Microsoft
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
- STCurveToLine_TSQL
- STCurveToLine
dev_langs:
- TSQL
helpviewer_keywords:
- STCurveToLine method (geography)
ms.assetid: 2f863a85-6168-465a-b32f-bb5e3de58dee
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d503d7c7ad67e56ddfd38495f40e8960daa13561
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="stcurvetoline-geography-data-type"></a>STCurveToLine (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce un'approssimazione poligonale di un' **geography** istanza contenente i segmenti di arco circolare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STCurveToLine()  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="remarks"></a>Osservazioni  
 Restituisce un **LineString** istanza per un **CircularString** o **CompoundCurve** istanza.  
  
 Restituisce un **poligono** istanza per un **CurvePolygon** istanza.  
  
 Restituire una copia di **geography** istanze che non contengono **CircularString**, **CompoundCurve**, o **CurvePolygon** istanze.  
  
 A differenza della specifica SQL MM, questo metodo non utilizza i valori di coordinata z nel calcolo dell'approssimazione poligonale. Coordinata z tutti i valori presentano nel chiamante **geography** istanza vengono ignorati.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituita un'istanza `LineString` che rappresenta un'approssimazione poligonale di un'istanza `CircularString`.  
  
```
 DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @g2 geography;  
 SET @g2 = @g1.STCurveToLine();  
 SELECT @g1.STNumPoints() AS G1, @g2.STNumPoints() AS G2;
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [STLength &#40; tipo di dati geography &#41;](../../t-sql/spatial-geography/stlength-geography-data-type.md)   
 [STNumPoints &#40; tipo di dati geography &#41;](../../t-sql/spatial-geography/stnumpoints-geography-data-type.md)   
 [Panoramica dei tipi di dati spaziali](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  
