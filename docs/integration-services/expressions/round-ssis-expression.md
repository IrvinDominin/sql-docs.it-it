---
title: ROUND (espressione SSIS) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rounding expressions
- ROUND function [SSIS]
ms.assetid: 376f1947-4fc5-4611-ad86-823e4db1b468
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bc531db140527e9ec2bfd73adffb2a81f2bcfcf4
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="round-ssis-expression"></a>ROUND (espressione SSIS)
  Restituisce un'espressione numerica arrotondata alla lunghezza o alla precisione specificata. Il parametro length deve restituire un valore integer.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ROUND(numeric_expression,length)  
```  
  
## <a name="arguments"></a>Argomenti  
 *numeric_expression*  
 Espressione di tipo numeric valido. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
 *lunghezza*  
 Espressione integer. Precisione per l'arrotondamento di *numeric_expression* .  
  
## <a name="result-types"></a>Tipi restituiti  
 Tipo identico a *numeric*_*expression*.  
  
## <a name="remarks"></a>Remarks  
 Tramite l'argomento *length* deve essere restituito un numero intero positivo oppure zero.  
  
 Se l'argomento è Null, ROUND restituirà Null.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questi esempi alcuni valori letterali numerici vengono arrotondati con lunghezza tre. Il primo risultato restituito è 137,1570, il secondo 137,1580.  
  
```  
ROUND(137.1574,3)  
ROUND(137.1575,3)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
