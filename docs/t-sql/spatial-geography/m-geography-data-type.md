---
title: M (tipo di dati geography) | Documenti Microsoft
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
- M (geography Data Type)
- M_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- M method
ms.assetid: cdba04f0-4e17-48f6-bafb-b1f918c5a501
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5db0fc032ce961d7c7b45f2a7542c6afb7747284
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="m-geography-data-type"></a>M (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Il **M** (misura) valore di **geography** istanza. La semantica del valore della misura viene definita dall'utente, ma generalmente descrive la distanza lungo un valore linestring. Il valore della misura, ad esempio, potrebbe essere utilizzato per tenere traccia di pietre miliari lungo una strada.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.M  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo: **float**  
  
 Tipo CLR: **SqlDouble**  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questa proprietà è null se il **geography** istanza non è un **punto**, nonché per qualsiasi **punto** istanza per cui non è impostata.  
  
 Questa proprietà è di sola lettura.  
  
 I valori M non vengono utilizzati in alcun calcolo eseguito dalla libreria e non saranno ad alcun calcolo della libreria.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `Point` con valori Z (innalzamento) e M (misura) valuta e viene utilizzato `M` per recuperare il valore M`M` dell'istanza.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100 10.3 12)', 4326);  
SELECT @g.M;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geografia](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [Z &#40; tipo di dati geography &#41;](../../t-sql/spatial-geography/z-geography-data-type.md)  
  
  
