---
title: '- (Negativo) (MDX) | Documenti Microsoft'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1406eee16ed2ec0349aa4405a4f59b478048dcdf
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742350"
---
# <a name="--negative-mdx"></a>- (negativo) (MDX)


  Esegue un'operazione unaria che restituisce l'opposto del valore di un'espressione numerica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
- Numeric_Expression  
```  
  
#### <a name="parameters"></a>Parametri  
 *Numeric_expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un valore numerico.  
  
## <a name="return-value"></a>Valore restituito  
 Valore negativo con tipo di dati del parametro specificato.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato l'utilizzo di questo operatore.  
  
```  
-- This member creates a negative version of the  
-- Reseller Freight Cost.  
WITH MEMBER   
   Measures.[Resell Cost as Negative]   
   AS -Measures.[Reseller Freight Cost]  
SELECT   
   [Date].[Calendar Month of Year].Children ON COLUMNS,  
   [Product].[Product Categories].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    {[Measures].[Resell Cost as Negative]}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento agli operatori MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
