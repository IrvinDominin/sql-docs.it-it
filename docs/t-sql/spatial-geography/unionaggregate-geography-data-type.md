---
title: UnionAggregate (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 07/30/2017
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
- UnionAggregate
- UnionAggregate_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- UnionAggregate method (geography)
ms.assetid: 1a3aeef1-5b0e-4ae8-aeb7-c4aab22f42ab
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 63299cfd3847f236f5908085b824b7b271dafc7a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="unionaggregate-geography-data-type"></a>UnionAggregate (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Esegue un'operazione di unione in un set di oggetti geografia.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
UnionAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>Argomenti  
 *geography_operand*  
 È un **geography** colonna della tabella che contiene il set di tipo **geography** oggetti su cui eseguire un'operazione di unione.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
## <a name="remarks"></a>Osservazioni  
 Metodo **null** se l'input dispone di SRID diversi. Vedere [identificatori SRID &#40; Identificatori SRID &#41; ](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
 Metodo ignora **null** input.  
  
> [!NOTE]  
>  Metodo **null** se tutti i valori immessi sono **null**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene eseguito un `UnionAggregate` su un set di **geography** punti percorso all'interno di una città.  
  
 ```
 USE AdventureWorks2012  
 GO  
 SELECT City,  
 geography::UnionAggregate(SpatialLocation) AS SpatialLocation  
 FROM Person.Address  
 WHERE PostalCode LIKE('981%')  
 GROUP BY City;
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi geography statici estesi](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
