---
title: sys.fulltext_document_types (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fulltext_document_types_TSQL
- fulltext_document_types
- fulltext_document_types_TSQL
- sys.fulltext_document_types
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_document_types catalog view
ms.assetid: 156fcfa4-7304-4a5c-b96f-1c3e061e5df0
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0995b501bd1032cdbc067fcef6c8f59693ef9abf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47812929"
---
# <a name="sysfulltextdocumenttypes-transact-sql"></a>sys.fulltext_document_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni tipo di documento disponibile per operazioni di indicizzazione full-text. Ogni riga rappresenta l'interfaccia IFilter registrata nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**document_type**|**sysname**|Estensione di file del tipo di documento supportato.<br /><br /> Questo valore può essere utilizzato per identificare il filtro che verrà usato durante l'indicizzazione full-text di colonne di tipo **varbinary (max)** oppure **immagine**.|  
|**class_id**|**uniqueidentifier**|GUID della classe IFilter che supporta l'estensione di file.|  
|**path**|**nvarchar(260)**|Percorso della DLL dell'interfaccia IFilter. Il percorso è visibile ai membri del solo il **serveradmin** ruolo predefinito del server.|  
|**version**|**sysname**|Versione della DLL dell'interfaccia IFilter.|  
|**Produttore**|**sysname**|Nome del produttore dell'interfaccia IFilter.<br /><br /> Nota: Solo documenti il cui il produttore [!INCLUDE[msCoName](../../includes/msconame-md.md)] sono supportati in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
