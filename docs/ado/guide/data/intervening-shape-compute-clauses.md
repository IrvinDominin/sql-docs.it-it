---
title: Le clausole di calcolo forma coinvolti | Documenti Microsoft
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
- shape commands [ADO]
- COMPUTE clause [ADO]
- data shaping [ADO], COMPUTE clause
ms.assetid: a576bf81-8f3c-4ba1-817b-87e89a8da684
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9604b599bb7ce50bb0160553a38f0c002f5e611b
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="intervening-shape-compute-clauses"></a>Clausole di calcolo forma intermedi
È possibile incorporare uno o più clausole COMPUTE tra padre e figlio in un comando shape con parametri, come nell'esempio seguente:  
  
```  
SHAPE {select au_lname, state from authors} APPEND   
   ((SHAPE   
      (SHAPE   
         {select * from authors where state = ?} rs   
      COMPUTE rs, ANY(rs.state) state, ANY(rs.au_lname) au_lname   
      BY au_id) rs2   
   COMPUTE rs2, ANY(rs2.state) BY au_lname)   
RELATE state TO PARAMETER 0)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Data Shaping di esempio](../../../ado/guide/data/data-shaping-example.md)   
 [Grammatica formale forma](../../../ado/guide/data/formal-shape-grammar.md)   
 [Comandi Shape in generale](../../../ado/guide/data/shape-commands-in-general.md)
