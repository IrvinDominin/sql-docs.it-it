---
title: Utilizzo di transazioni | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, transactions
- transactions [SMO]
- SMO [SQL Server], transactions
ms.assetid: 399aded8-bee3-4cfb-a671-1877c7d0de9f
caps.latest.revision: 37
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 31e80049a084a167d356e282b212dcde4418c0a6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-transactions"></a>Utilizzo di transazioni
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), l'elaborazione delle transazioni viene eseguita mediante la connessione all'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzando l'oggetto <xref:Microsoft.SqlServer.Management.Common.ServerConnection>. Il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> oggetto fa riferimento il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà del <xref:Microsoft.SqlServer.Management.Smo.Server> dell'oggetto quando viene stabilita la connessione. Metodi come <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>, <xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A> e <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A> appartengono alla proprietà dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di programmi SMO](../../../relational-databases/server-management-objects-smo/create-program/creating-smo-programs.md)  
  
  
