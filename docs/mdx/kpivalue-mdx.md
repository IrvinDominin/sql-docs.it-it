---
title: KPIValue (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- KPIValue function
ms.assetid: c4f8532c-4c24-4ad5-8847-4522511e0039
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 705b549d3204439bfccf0c5ba1b79243dc6db953
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="kpivalue-mdx"></a>KPIValue (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il membro da cui viene calcolato il valore dell'indicatore di prestazioni chiave (KPI) specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
KPIValue(KPI_Name)  
```  
  
## <a name="arguments"></a>Argomenti  
 *Nome_kpi*  
 Espressione stringa valida che specifica il nome dell'indicatore di prestazioni chiave (KPI).  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono restituiti valore, obiettivo, stato e tendenza dell'indicatore di prestazioni chiave (KPI) relativo alla misura del ricavo del canale per i discendenti di tre membri della gerarchia dell'attributo Fiscal Year.  
  
```  
SELECT  
   { KPIValue("Channel Revenue"),   
     KPIGoal("Channel Revenue"),  
     KPIStatus("Channel Revenue"),   
     KPITrend("Channel Revenue")  
   } ON Columns,  
Descendants  
   ( { [Date].[Fiscal].[Fiscal Year].&[2002],  
       [Date].[Fiscal].[Fiscal Year].&[2003],  
       [Date].[Fiscal].[Fiscal Year].&[2004]   
     }, [Date].[Fiscal].[Fiscal Quarter]  
   ) ON Rows  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
