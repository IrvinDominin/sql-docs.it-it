---
title: "Modifiche di rilievo apportate alle funzionalità del Motore di database in SQL Server 2016 | Microsoft Docs"
ms.custom: 
ms.date: 11/15/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: database-engine
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Database Engine [SQL Server], what's new
- breaking changes [SQL Server]
ms.assetid: 47edefbd-a09b-4087-937a-453cd5c6e061
caps.latest.revision: "144"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: cf25b27d53102931857454cf6bfd7c4a7a53f29f
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="breaking-changes-to-database-engine-features-in-sql-server-2016"></a>Modifiche di rilievo apportate alle funzionalità del Motore di database in SQL Server 2016
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Questo argomento descrive le modifiche di rilievo nel [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)] e versioni precedenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Tali modifiche potrebbero interrompere il funzionamento di applicazioni, funzionalità o script basati su versioni precedenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. È possibile che questi problemi si verifichino quando viene effettuato un aggiornamento.  
  
##  <a name="SQL15"></a> Modifiche di rilievo in [!INCLUDE[ssSQL15](../includes/sssql15-md.md)]  
  
-   La colonna sample_ms di sys.dm_io_virtual_file_stats è stata ampliata passando da un tipo di dati **int** a un tipo di dati **bigint** .  
  
-   La colonna TimeStamp di sys.fn_virtualfilestats è stata ampliata passando da un tipo di dati **int** a **bigint** .  

-   Se si usano gli algoritmi di hash MD2, MD4, MD5, SHA o SHA1 (scelta non consigliata), è necessario impostare il livello di compatibilità del database su un valore inferiore a 130.  

-   Nel livello di compatibilità del database 130, le conversioni implicite dai tipi di dati **datetime** a **datetime2** mostrano una maggiore precisione prevedendo i millisecondi frazionari, risultanti in diversi valori convertiti. Usare il cast esplicito per il tipo di dati datetime2 ogni volta che si presenta uno scenario di confronto misto tra tipi di dati datetime e datetime2. Per altre informazioni, fare riferimento a questo [articolo del supporto tecnico Microsoft](http://support.microsoft.com/help/4010261).
  
## <a name="previous-versions"></a>Versioni precedenti  
  
-   [Modifiche di rilievo apportate alle funzionalità del motore di database in SQL Server 2014](https://msdn.microsoft.com/library/ms143179\(v=sql.120\))  
  
-   [Modifiche di rilievo apportate alle funzionalità del motore di database in SQL Server 2012](https://msdn.microsoft.com/library/ms143179\(v=sql.110\))  
  
-   [Modifiche di rilievo apportate alle funzionalità del motore di database in SQL Server 2008](https://msdn.microsoft.com/library/ms143179\(v=sql.100\))  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità del motore di database deprecate in SQL Server 2016](../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [Funzionalità del motore di database non più usate in SQL Server 2016](../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)   
 [Compatibilità con le versioni precedenti del motore di database di SQL Server](../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [Livello di compatibilità ALTER DATABASE &#40;Transact-SQL&#41;](../t-sql/statements/alter-database-transact-sql-compatibility-level.md)   
 [Miglioramenti di SQL Server 2016 o SQL Server 2017 in Windows relativi alla gestione di alcuni tipi di dati e operazioni non comuni](http://support.microsoft.com/help/4010261)
  
  
