---
title: Informazioni sull'errore relative al campo | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- field-related errors [ADO]
- errors [ADO], field-related
ms.assetid: 5e7b1af4-996b-47c5-9161-c5575ad4fec9
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6513328c3d26d794e3881f8a29fb3ecf51feee15
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="field-related-error-information"></a>Informazioni sugli errori di campo
Se l'errore è direttamente correlato a un campo, ad esempio, se mancano i dati o se è il tipo non corretto per il campo: è possibile recuperare ulteriori informazioni sulla causa del problema esaminando il **campo** dell'oggetto **stato**  proprietà. Questa proprietà è stata migliorata per fornire informazioni specifiche sul problema. In questo caso, ad esempio, quando una chiamata a **UpdateBatch** ha esito negativo, la causa del problema può essere determinata esaminando il **stato** proprietà del **campi** in ognuna dell'interessati record. La proprietà conterrà uno dei valori di **FieldStatusEnum** costante. Nella tabella seguente include i valori che sono di particolare interesse quando si verifica un errore.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adFieldCantConvertValue**|2|Indica che il campo non può essere recuperato o archiviato senza perdita di dati.|  
|**adFieldDataOverflow**|6|Indica che i dati restituiti dal provider di overflow rispetto al tipo di dati del campo.|  
|**adFieldDefault**|13|Indica che il valore predefinito per il campo è stato utilizzato durante l'impostazione di dati.|  
|**adFieldIgnore**|15|Indica che questo campo è stato ignorato durante l'impostazione dati dei valori nell'origine. È stato impostato alcun valore dal provider.|  
|**adFieldIntegrityViolation**|10|Indica che il campo non può essere modificato perché è un'entità calcolata o derivata.|  
|**adFieldIsNull**|3|Indica che il provider ha restituito un valore null.|  
|**adFieldOutOfSpace**|22|Indica che il provider non riesce a ottenere spazio di archiviazione sufficiente per completare un'operazione di spostamento o l'operazione di copia.|
