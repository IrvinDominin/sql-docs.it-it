---
title: STConvexHull (tipo di dati geography) | Documenti Microsoft
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
dev_langs:
- TSQL
helpviewer_keywords:
- STConvexHull method (geography)
ms.assetid: fb435db7-31bb-4243-9d8b-35379184cfb4
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d797c6e2b0e4f7163aae0e1b6ecb37af95051942
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="stconvexhull-geography-data-type"></a>STConvexHull (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce un oggetto che rappresenta la struttura convessa di una **geography** istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STConvexHull ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="remarks"></a>Osservazioni  
 Restituisce un `FullGlobe` oggetto **geography** istanza con un angolo della busta maggiore di 90 gradi.  
  
 Restituisce un oggetto vuoto **geography** raccolta per un oggetto vuoto **geography** istanza.  
  
 Restituisce **null** per oggetto non inizializzato **geography** istanza.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-stconvexhull-on-an-uninitialized-geography-instance"></a>A. Utilizzo di STConvexHull() in un'istanza geografica non inizializzata  
 L'esempio seguente usa `STConvexHull()` su un valore non inizializzato **geography** istanza.  
  
```
 DECLARE @g geography;  
 SELECT @g.STConvexHull();
 ```  
  
### <a name="b-using-stconvexhull-on-an-empty-geography-instance"></a>B. Utilizzo di STConvexHull in un'istanza geografica vuota  
 Nell'esempio seguente viene utilizzato `STConvexHull()` in un'istanza `Polygon` vuota.  
  
```
 DECLARE @g geography = 'POLYGON EMPTY';  
 SELECT @g.STConvexHull().ToString();
 ```  
  
### <a name="c-finding-the-convex-hull-of-a-non-convex-polygon-instance"></a>C. Ricerca della struttura convessa di un'istanza Polygon non convessa  
 Nell'esempio seguente viene utilizzato `STConvexHull()` per trovare la struttura convessa di un'istanza `Polygon` non convessa.  
  
```  
 DECLARE @g geography;  
 SET @g = geography::Parse('POLYGON((-120.533 46.566, -118.283 46.1, -122.3 47.45, -120.533 46.566))');  
 SELECT @g.STConvexHull().ToString();  
```  
  
### <a name="d-finding-the-convex-hull-on-a-geography-instance-with-an-envelope-angle-larger-than-90-degrees"></a>D. Ricerca della struttura convessa in un'istanza geografica con un angolo della busta maggiore di 90 gradi  
 L'esempio seguente usa `STConvexHull()` su un **geography** istanza con un angolo della busta maggiore di 90 gradi.  
  
```
 DECLARE @g geography = 'POLYGON((20.533 46.566, -18.283 46.1, -22.3 47.45, 20.533 46.566))';  
 SELECT @g.STConvexHull().ToString();
 ```  
  
  
