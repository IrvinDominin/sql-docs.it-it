---
title: CollectionAggregate (tipo di dati geography) | Documenti Microsoft
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
dev_langs:
- TSQL
helpviewer_keywords:
- CollectionAggregate method (geography)
ms.assetid: e49a644a-dbf2-46c3-98f5-4b3ec197e2ad
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4c697a43ac6b79fd137da968ce5f01e49e60c105
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="collectionaggregate-geography-data-type"></a>CollectionAggregate (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Crea un **GeometryCollection** istanza da un set di **geography** oggetti.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ConvexHullAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>Argomenti  
 *geography_operand*  
 È un **geography** colonna di tabella di tipo che rappresenta un set di **geography** oggetti da includere nel **GeometryCollection** istanza.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
## <a name="exception"></a>Eccezione  
 Genera un'eccezione `FormatException` in presenza di valori di input non validi. Vedere [STIsValid &#40; tipo di dati geography &#41;](../../t-sql/spatial-geography/stisvalid-geography-data-type.md)  
  
## <a name="remarks"></a>Osservazioni  
 Metodo **null** quando l'input è vuoto o l'input dispone di SRID diversi. Vedere [identificatori SRID &#40; Identificatori SRID &#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
 Metodo ignora **null** input.  
  
> [!NOTE]  
>  Metodo **null** se tutti i valori immessi sono **null**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito un `GeometryCollection` istanza che contiene un set di **geography** oggetti.  
  
 ```
 USE AdventureWorks2012  
 GO  
 SELECT geography::CollectionAggregate(SpatialLocation).ToString() AS SpatialLocation  
 FROM Person.Address  
 WHERE City LIKE ('Bothell')
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi geography statici estesi](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
