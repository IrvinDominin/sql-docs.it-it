---
title: Argomenti delle funzioni di catalogo in | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- arguments in catalog functions [ODBC]
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], about arguments
- functions [ODBC], catalog functions
ms.assetid: f5e0abec-8f24-42e0-b94f-16dd1f2004fd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1df1c7701b3e6c64e2acb103ad2b38fc4cbb99d6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911496"
---
# <a name="arguments-in-catalog-functions"></a>Argomenti nelle funzioni di catalogo
Tutte le funzioni di catalogo accettano gli argomenti con cui un'applicazione può limitare l'ambito dei dati restituiti. Ad esempio, le chiamate a primo e seconda **SQLTables** nel codice seguente restituisce un set di risultati contenente informazioni su tutte le tabelle, mentre la terza chiamata restituisce informazioni sulla tabella Ordini:  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, NULL, 0, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "%", SQL_NTS, NULL, 0);  
SQLTables(hstmt3, NULL, 0, NULL, 0, "Orders", SQL_NTS, NULL, 0);  
```  
  
 Gli argomenti di stringa di funzione di catalogo rientrano in quattro tipi diversi: argomento normale (OA), argomento valore di pattern (PV), argomento dell'identificatore (ID) e argomento valore di elenco (contratto Multilicenza). La maggior parte degli argomenti di stringa possono essere di uno dei due tipi diversi, a seconda del valore dell'attributo di istruzione SQL_ATTR_METADATA_ID. Nella tabella seguente sono elencati gli argomenti per ogni funzione di catalogo e descrive il tipo dell'argomento per valore SQL_TRUE o SQL_FALSE SQL_ATTR_METADATA_ID.  
  
|Funzione|Argomento|Digitare quando SQL _<br /><br /> ATTR_METADATA_<br /><br /> ID = SQL_FALSE|Digitare quando SQL _<br /><br /> ATTR_METADATA_<br /><br /> ID = SQL_TRUE|  
|--------------|--------------|---------------------------------------------------------------|--------------------------------------------------------------|  
|**SQLColumnPrivileges**|*CatalogName* *SchemaName* *TableName* *ColumnName*|OA OA OA PV|ID ID ID ID|  
|**SQLColumns**|*CatalogName* *SchemaName* *TableName* *ColumnName*|OA PV PV PV|ID ID ID ID|  
|**SQLForeignKeys**|*PKCatalogName* *PKSchemaName* *PKTableName* *FKCatalogName* *FKSchemaName*  *FKTableName*|OA OA OA OA OA OA|ID ID ID ID ID ID|  
|**SQLPrimaryKeys**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ID ID ID|  
|**SQLProcedureColumns**|*CatalogName* *SchemaName* *ProcName* *ColumnName*|OA PV PV PV|ID ID ID ID|  
|**SQLProcedures**|*CatalogName* *SchemaName* *ProcName*|PV PV OA|ID ID ID|  
|**SQLSpecialColumns**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ID ID ID|  
|**SQLStatistics**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ID ID ID|  
|**SQLTablePrivileges**|*CatalogName* *SchemaName* *TableName*|PV PV OA|ID ID ID|  
|**SQLTables**|*CatalogName* *SchemaName* *TableName* *TableType*|CONTRATTO MULTILICENZA DI PV PV PV|ID CONTRATTO MULTILICENZA ID DI ID|  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Argomenti ordinari](../../../odbc/reference/develop-app/ordinary-arguments.md)  
  
-   [Argomenti del valore criterio](../../../odbc/reference/develop-app/pattern-value-arguments.md)  
  
-   [Argomenti di tipo identificatore](../../../odbc/reference/develop-app/identifier-arguments.md)  
  
-   [Argomenti dell'elenco di valori](../../../odbc/reference/develop-app/value-list-arguments.md)
