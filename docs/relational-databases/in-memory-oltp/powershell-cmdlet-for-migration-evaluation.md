---
title: Cmdlet di PowerShell per la valutazione della migrazione | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 117250d3-9982-47fe-94fd-6f29f6159940
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 63f5604c01bba64b75c51908840b8b9650ed03d2
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="powershell-cmdlet-for-migration-evaluation"></a>Cmdlet di PowerShell per la valutazione della migrazione
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Il cmdlet Save-SqlMigrationReport è uno strumento che valuta l'idoneità per la migrazione di più oggetti in un database di SQL Server. Attualmente è limitato alla valutazione di OLTP in memoria. Il cmdlet può essere eseguito sia in un ambiente Windows PowerShell con privilegi elevati che in sqlps.  
  
## <a name="syntax"></a>Sintassi  
  
```powershell  
Save-SqlMigrationReport [ -MigrationType OLTP ] [ -Server server -Database database [ -Object object_name ] ]  |  [ -InputObject smo_object ] -FolderPath path  
```  
  
#### <a name="parameters"></a>Parametri  
 I parametri sono descritti nella tabella riportata di seguito.  
  
|Parametri|Description|  
|----------------|-----------------|  
|MigrationType|Tipo di scenario di migrazione specificato come destinazione dal cmdlet. Attualmente l'unico valore è il valore predefinito OLTP. Facoltativo.|  
|Server|Nome dell'istanza di SQL Server di destinazione. Obbligatorio nell'ambiente Windows Powershell se non viene specificato il parametro -InputObject. Facoltativo in SQLPS.|  
|Database|Nome del database di SQL Server di destinazione. Obbligatorio nell'ambiente Windows Powershell se non viene specificato il parametro -InputObject. Facoltativo in SQLPS.|  
|Object|Nome dell'oggetto di database di destinazione. Può essere una tabella o una stored procedure.|  
|InputObject|Oggetto SMO a cui il cmdlet deve fare riferimento. Obbligatorio nell'ambiente Windows Powershell se non vengono specificati -Server e -Database. Facoltativo in SQLPS.|  
|FolderPath|Cartella in cui il cmdlet deve depositare i report generati. Obbligatorio.|  
  
## <a name="results"></a>Risultati  
 La cartella specificata nel parametro -FolderPath conterrà due nomi di cartella: Tables e Stored procedures. Se l'oggetto di destinazione è una tabella, il report sarà all'interno della cartella Tables. In caso contrario, sarà all'interno della cartella Stored procedures.  
  
  
