---
title: EnvelopeAngle (tipo di dati geography) | Documenti Microsoft
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
- EnvelopeAngle
- EnvelopeAngle_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- EnvelopeAngle method
ms.assetid: 14a7ba15-168c-4b08-ba3d-951d73092ac7
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 692287aee372bf349cfa795e3b52c6e84c8e4f42
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="envelopeangle-geography-data-type"></a>EnvelopeAngle (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce l'angolo massimo tra il punto restituito da `EnvelopeCenter()` e un punto di **geography** istanza in gradi.  
  
 Questo **geography** metodo supportata dal tipo di dati **FullGlobe** istanze o le istanze spaziali con dimensioni maggiori di un emisfero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
EnvelopeAngle( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **float**  
  
 Tipo CLR restituito: **SqlDouble**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo restituisce un punto di **geography** istanza in gradi. Se usato con EnvelopeCenter(), `EnvelopeAngle()` restituisce un cerchio di delimitazione di un **geography** istanza.  
  
 In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], questo metodo è stato esteso alle **FullGlobe** istanze.  
  
 La limitazione di emisfero applicata a `EnvelopeAngle()` in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] è stato rimosso. Tuttavia, per le istanze con angoli più ampi di 90 gradi, verrà restituito 180 gradi. `EnvelopeAngle()`non è preciso per **geography** istanze che si estendono su più di un emisfero.  
  
## <a name="examples"></a>Esempi  
  
```  
DECLARE @g geography = 'LINESTRING(-120 45, -120 0, -90 0)';   
SELECT @g.EnvelopeAngle();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geografia](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [EnvelopeCenter &#40; tipo di dati geography &#41;](../../t-sql/spatial-geography/envelopecenter-geography-data-type.md)  
  
  
