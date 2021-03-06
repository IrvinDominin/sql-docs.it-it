---
title: Viste di compatibilità di sistema (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- compatibility views [SQL Server]
- system tables [SQL Server], compatibility views
- type IDs [SQL Server]
- system views [SQL Server], compatibility
- metadata [SQL Server], views
- backward compatibility [SQL Server], compatibility views
- compatibility [SQL Server], compatibility views
- backward compatibility [SQL Server], system tables
- compatibility [SQL Server], system tables
- user IDs [SQL Server]
ms.assetid: 8e4624f5-9d36-4ce7-9c9e-1fe010fa2122
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: dbc4f4f1fb55603a6918357e4c6aa16e4a819f3d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47805479"
---
# <a name="system-compatibility-views-transact-sql"></a>Viste di compatibilità di sistema (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Molte delle tabelle di sistema incluse nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono implementate come set di viste. Queste viste sono note come viste di compatibilità e sono disponibili solo per compatibilità con le versioni precedenti. Le viste di compatibilità espongono gli stessi metadati disponibili in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], ma non espongono i metadati correlati a funzionalità introdotte in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. Quando si utilizzano nuove funzionalità, ad esempio [!INCLUDE[ssSB](../../includes/sssb-md.md)] o il partizionamento, è pertanto necessario passare all'utilizzo delle viste del catalogo.  
  
 Un altro motivo per eseguire l'aggiornamento alle viste del catalogo è rappresentato dal fatto che le colonne delle viste di compatibilità in cui sono archiviati ID utente e ID di tipo possono restituire NULL o attivare overflow aritmetici, dal momento che è possibile creare oltre 32.767 utenti, gruppi e ruoli e 32.767 tipi di dati. Se ad esempio è necessario creare 32.768 utenti e quindi eseguire la query `SELECT * FROM sys.sysusers`, in caso di impostazione di ARITHABORT su ON la query ha esito negativo e viene generato un errore di overflow aritmetico. Se ARITHABORT è impostata su OFF, la **uid** colonna viene restituito NULL.  
  
 Per evitare questi problemi, è consigliabile usare le nuove viste del catalogo in grado di gestire un numero più elevato di ID utente e ID di tipo. Nella tabella seguente sono elencate le colonne soggette a questo tipo di overflow.  
  
|Nome colonna|Vista di compatibilità|Vista di SQL Server 2005|  
|-----------------|------------------------|--------------------------|  
|**xusertype**|**syscolumns**|**sys.columns**|  
|**usertype**|**syscolumns**|**sys.columns**|  
|**memberuid**|**sysmembers**|**sys.database_role_members**|  
|**groupuid**|**sysmembers**|**sys.database_role_members**|  
|**uid**|**sysobjects**|**sys.objects**|  
|**uid**|**sysprotects**|**sys.database_permissions**<br /><br /> **sys.server_permissions**|  
|**Utente che concede**|**sysprotects**|**sys.database_permissions**<br /><br /> **sys.server_permissions**|  
|**xusertype**|**systypes**|**sys.types**|  
|**uid**|**systypes**|**sys.types**|  
|**uid**|**sysusers**|**sys.database_principals**|  
|**altuid**|**sysusers**|**sys.database_principals**|  
|**gid**|**sysusers**|**sys.database_principals**|  
|**uid**|**syscacheobjects**|**sys.dm_exec_plan_attributes**|  
|**uid**|**sysprocesses**|**sys.dm_exec_requests**|  
  
 Quando viene fatto riferimento in un database utente, sistema di tabelle che sono state annunciate come deprecate in SQL Server 2000 (ad esempio **syslanguages** o **syscacheobjects**), sono ora associate alla visualizzazione compatibilità retroattiva nel **sys** dello schema. Poiché le tabelle di sistema di SQL Server 2000 sono state deprecate per più versioni, tale modifica non viene considerata una modifica di rilievo.  
  
 Esempio: Se un utente crea una tabella utente denominata **syslanguages** in un database di utente, in SQL Server 2008, l'istruzione `SELECT * from dbo.syslanguages;` in tale database restituisce i valori dalla tabella utente. A partire da SQL Server 2012, questa procedura restituisce i dati dalla vista di sistema **Sys. syslanguages**.  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Mapping di tabelle di sistema a viste di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)  
  
  
