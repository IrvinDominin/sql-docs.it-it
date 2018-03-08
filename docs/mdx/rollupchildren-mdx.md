---
title: RollupChildren (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ROLLUPCHILDREN
dev_langs: kbMDX
helpviewer_keywords: RollupChildren function
ms.assetid: 6f092540-067d-443f-b631-8523836a0d86
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: e3553458eecb094ec76ecb6bf7f65691aaa1c4bd
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="rollupchildren-mdx"></a>RollupChildren (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce un valore generato tramite il rollup dei valori degli elementi figlio del membro indicato, utilizzando l'operatore unario specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RollupChildren(Member_Expression, Unary_Operator)   
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
 *Unary_Operator*  
 Espressione stringa valida che specifica un operatore unario.  
  
## <a name="remarks"></a>Osservazioni  
 Il **RollupChildren** funzione rollup i valori degli elementi figlio del membro specificato utilizzando l'operatore unario specificato.  
  
 Nella tabella seguente vengono descritti gli operatori unari validi per questa funzione.  
  
|Operatore|Risultato|  
|--------------|------------|  
|**+**|totale = totale + membro figlio corrente|  
|**-**|totale = totale - membro figlio corrente|  
|**\***|totale = totale * membro figlio corrente|  
|**/**|totale = totale / membro figlio corrente|  
|**%**|totale = (totale / membro figlio corrente) * 100|  
|**~**|Il membro figlio non viene utilizzato nel rollup e il valore corrispondente viene ignorato.|  
  
 Se l'operatore nella proprietà del membro non è elencato nella tabella precedente, viene generato un errore. L'ordine di valutazione è determinato dall'ordine degli elementi di pari livello, non dalla precedenza degli operatori.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene utilizzata una proprietà di membro denominata "Alternate Rollup Operator" contenente valori alternativi per gli operatori unari per eseguire il rollup degli elementi figlio della gerarchia Net Profit nella dimensione Account in un modo alternativo. Questa proprietà non esiste nel cubo Adventure Works, ma potrebbe essere creata. Questo utilizzo del **RollupChildren** funzione potrebbe essere utilizzata in un'applicazione di elaborazione di budget per l'analisi di simulazione.  
  
```  
RollupChildren  
   ( [Account].[Net Profit]  
   , [Account].CurrentMember.Properties ('Alternate Rollup Operator') )  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
