---
title: sys.external_libraries (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 10/05/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- external_libraries
- external_libraries_TSQL
- sys.external_libraries
- sys.external_libraries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_libraries catalog view
author: jeannt
ms.author: jeannt
manager: craigg
ms.openlocfilehash: c1e65db4ccb43dde92188e462b6e99414ee05f52
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysexternallibraries-transact-sql"></a>sys.external_libraries (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]


Supporta la gestione delle librerie di pacchetto correlati a runtime esterni, ad esempio R o Python.

## <a name="sysexternallibraries"></a>sys.external_libraries

Il sys.external_libraries di vista del catalogo elenca una riga per ogni libreria esterna che è stato caricato nel database.

|Nome colonna |Tipo di dati | Description|
|------|------|------|
|external_library_id |int | ID dell'oggetto libreria esterna. |
|name |sysname |Nome della libreria esterna. È univoco all'interno del database per proprietario.|
|principal_id |int |ID dell'entità a cui appartiene questa libreria esterna. |
|language | sysname | Nome della lingua o runtime che supporta la libreria esterna. I valori validi sono 'R'. I runtime aggiuntivi potrebbero essere aggiunti in futuro.|
|ambito |int |0 per ambito pubblico. 1 per l'ambito privato |  
|scope_desc |varchar(7) |Indica se il pacchetto è pubblica o privata|


## <a name="see-also"></a>Vedere anche  
[sys.external_library_files](sys-external-library-files-transact-sql.md)  
[CREARE UNA LIBRERIA ESTERNA](../../t-sql/statements/create-external-library-transact-sql.md)  
[Gestione dei pacchetti per SQL Server R Services](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
