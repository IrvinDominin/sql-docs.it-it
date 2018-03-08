---
title: + (addizione) (SSIS) | Microsoft Docs
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
- + (add)
- add operator (+)
- adding expressions
ms.assetid: 44df4154-fed5-4e7f-9995-e703a0164f6a
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2ec27e30b38c0f373024e0dd473b3dd2696270cf
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="-add-ssis"></a>+ (addizione) (SSIS)
  Vengono aggiunte due espressioni numeriche.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
numeric_expression1 + numeric_expression2  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *numeric_expression1, numeric_expression2*  
 Espressione valida con tipo di dati numeric.  
  
## <a name="result-types"></a>Tipi restituiti  
 Dipendenti dai tipi di dati dei due argomenti. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="remarks"></a>Remarks  
 Se uno degli operandi è Null, il risultato sarà Null.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio vengono sommati alcuni valori letterali numerici.  
  
```  
5 + 6.09 + 7.0  
```  
  
 In questo esempio vengono sommati i valori nelle colonne **VacationHours** e **SickLeaveHours** .  
  
```  
VacationHours + SickLeaveHours  
```  
  
 In questo esempio un valore calcolato viene sommato alla colonna **StandardCost** . Poiché il nome include il carattere %, la variabile **Profit%** deve essere racchiusa tra parentesi. Per altre informazioni, vedere [Identificatori &#40;SSIS&#41;](../../integration-services/expressions/identifiers-ssis.md).  
  
```  
StandardCost + (StandardCost * @[Profit%])  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Precedenza e associatività degli operatori](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operatori &#40;espressione SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
