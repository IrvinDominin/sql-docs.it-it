---
title: getSchemas (metodo) (String, String) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 672171ac-976f-4605-9bee-2a5e141d92cb
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff8790ad1d8d24b548835be4013998bda782596b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getschemas-method-string-string"></a>Metodo getSchemas (String, String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera i nomi di schema disponibili nel database corrente tramite il nome di catalogo specificato e il nome dello schema.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public ResultSet getSchemas(java.lang.String catalog,  
                       java.lang.String schemaPattern)  
```  
  
#### <a name="parameters"></a>Parametri  
 *catalog*  
  
 Nome di un catalogo del database. Se è una stringa vuota (""), il risultato include gli schemi senza un catalogo. Se è **null**, il nome del catalogo non viene utilizzato per la ricerca.  
  
 *schemaPattern*  
  
 Nome di uno schema. Se è **null**, il nome dello schema non viene utilizzato per la ricerca.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getSchemas viene specificato dal metodo getSchemas nell'interfaccia DatabaseMetaData.  
  
 Il set di risultati restituito dal metodo getSchemas contiene le informazioni seguenti:  
  
|Nome|Tipo|Description|  
|----------|----------|-----------------|  
|TABLE_SCHEM|**String**|Nome dello schema.|  
|TABLE_CATALOG|**String**|Nome di catalogo per lo schema.|  
  
 I risultati vengono ordinati in base a TABLE_CATALOG e quindi in base a TABLE_SCHEM. La prima colonna di ogni riga è TABLE_SCHEM, mentre la seconda è TABLE_CATALOG.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
