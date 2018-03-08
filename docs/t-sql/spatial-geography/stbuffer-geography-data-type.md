---
title: STBuffer (tipo di dati geography) | Documenti Microsoft
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
- STBuffer (geography Data Type)
- STBuffer_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STBuffer (geography Data Type)
ms.assetid: cb4deab8-642b-44d9-b3d9-85114d64021e
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e6bd49bb41c8db0fa702e97e5ad8316961e7af15
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="stbuffer-geography-data-type"></a>STBuffer (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Restituisce un oggetto geografico che rappresenta l'unione di tutti i punti la cui distanza da un **geography** istanza è minore o uguale a un valore specificato.  
  
 Metodo supportata dal tipo di dati geography **FullGlobe** istanze o le istanze spaziali con dimensioni maggiori di un emisfero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STBuffer ( distance )  
```  
  
## <a name="arguments"></a>Argomenti  
 *distance*  
 È un valore di tipo **float** (**doppie** in .NET Framework) che specifica la distanza tra il **geography** istanza intorno alla quale calcolare il buffer.  
  
 La distanza massima del buffer non può superare 0,999 \* *π* * minorAxis \* minorAxis / majorAxis (~0.999 \* della circonferenza della terra di 1/2) o l'intero globo.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="remarks"></a>Osservazioni  
 Stbuffer () calcola un buffer in modo analogo [BufferWithTolerance](../../t-sql/spatial-geography/bufferwithtolerance-geography-data-type.md), specificando *tolleranza* = Abs (distanza) \* .001 e *relativo*  =  **false**.  
  
 Un buffer negativo rimuove tutti i punti all'interno della distanza specificata del limite del **geography** istanza.  
  
 `STBuffer()`verrà restituito un **FullGlobe** istanza in determinati casi; ad esempio, `STBuffer()` restituisce un **FullGlobe** istanza quando la distanza del buffer è maggiore della distanza dall'equatore ai poli. Un buffer non può superare l'intero globo.  
  
 Questo metodo genererà un' **ArgumentException** in **FullGlobe** istanze in cui la distanza del buffer eccede il limite seguente:  
  
 0,999 \* *π* * minorAxis \* minorAxis / majorAxis (~0.999 \* della circonferenza della terra di 1/2)  
  
 Il limite massimo della distanza consente la massima flessibilità per la costruzione del buffer.  
  
 L'errore tra il buffer calcolato e quello teorico è max (tolleranza, extent * all'1. e-7) in cui tolleranza = distanza \* .001. Per ulteriori informazioni sulle estensioni, vedere [metodo riferimento al tipo di dati geography](http://msdn.microsoft.com/library/028e6137-7128-4c74-90a7-f7bdd2d79f5e).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creato un `LineString``geography` istanza. e viene utilizzato `STBuffer()` per restituire l'area all'interno di 1 metro dell'istanza.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STBuffer(1).ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [BufferWithTolerance &#40; tipo di dati geography &#41;](../../t-sql/spatial-geography/bufferwithtolerance-geography-data-type.md)   
 [Metodi OGC sulle istanze geografiche](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
