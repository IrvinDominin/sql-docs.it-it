---
title: Modificare le applicazioni per prevedere valori bigint da sysperfinfo. cntr_value | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- sysperfinfo
- bigint values [SQL Server]
ms.assetid: b0345303-6e9a-4078-8148-6e1bce207b8c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e4f7945a5657cefb43af402523a6aee3e12eb63a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48137532"
---
# <a name="modify-applications-to-expect-bigint-values-from-sysperfinfocntrvalue"></a>Modificare le applicazioni in modo da prevedere valori bigint da sysperfinfo.cntr_value
  sysperfinfo restituisce un `bigint` valore per la colonna cntr_value.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Azione correttiva  
 Modificare le applicazioni che utilizzano sysperfinfo per assicurarsi che siano in grado di gestire i valori `bigint` della colonna cntr_value.  
  
> [!NOTE]  
>  sysperfinfo è una vista di compatibilità. È consigliabile utilizzare la vista a gestione dinamica sys.dm_os_performance_counter.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Preparazione aggiornamento a SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
