---
title: Metodo getFunctions (SQLServerDatabaseMetaData) | Documenti Microsoft
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
ms.topic: article
ms.assetid: 44335cbd-c84d-4ef3-a6a1-fca7eb7ec768
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7cafae4dcdbe9102da3ef4e27ee20b41b231667e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="getfunctions-method-sqlserverdatabasemetadata"></a>Metodo getFunctions (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una descrizione delle funzioni utente e di sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public ResultSet getFunctions(java.lang.String catalog,  
                       java.lang.String schemaPattern,  
                       java.lang.String functionNamePattern)  
```  
  
#### <a name="parameters"></a>Parametri  
 *catalog*  
  
 Nome di un catalogo del database. Se è una stringa vuota (""), il risultato include le funzioni senza un catalogo. Se è **null**, il nome del catalogo non viene utilizzato per la ricerca.  
  
 *schemaPattern*  
  
 Nome di uno schema. Se è una stringa vuota (""), il risultato include le funzioni senza uno schema. Se è **null**, il nome dello schema non viene utilizzato per la ricerca.  
  
 *functionNamePattern*  
  
 Nome di una funzione.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getFunctions viene specificato dal metodo getFunctions nell'interfaccia DatabaseMetaData.  
  
 Restituisce solo le funzioni utente e di sistema che corrispondono ai nomi di schema e funzione specificati.  
  
> [!IMPORTANT]  
>  Il set di risultati restituito può contenere funzioni per le quali l'utente chiamante non dispone delle autorizzazioni di esecuzione.  
  
 La descrizione di ogni funzione include le colonne seguenti:  
  
|Nome|Tipo|Description|  
|----------|----------|-----------------|  
|FUNCTION_CAT|**String**|Nome del database contenente la funzione.|  
|FUNCTION_SCHEM|**String**|Nome dello schema contenente la funzione.|  
|FUNCTION_NAME|**String**|Nome della funzione.|  
|NUM_INPUT_PARAMS|**int**|Riservato per utilizzi futuri, attualmente restituisce un valore pari a -1.|  
|NUM_OUTPUT_PARAMS|**int**|Riservato per utilizzi futuri, attualmente restituisce un valore pari a -1.|  
|NUM_RESULT_SETS|**int**|Riservato per utilizzi futuri, attualmente restituisce un valore pari a -1.|  
|REMARKS|**String**|Commenti sulla funzione.|  
|FUNCTION_TYPE|**short**|Tipo della funzione. Può essere uno dei valori seguenti:<br /><br /> SQL_PT_UNKNOWN (0)<br /><br /> SQL_PT_PROCEDURE (1)<br /><br /> SQL_PT_FUNCTION (2)|  
  
 Tutte le descrizioni del set di risultati restituito sono ordinate in base a FUNCTION_CAT, FUNCTION_SCHEM, FUNCTION_NAME e SPECIFIC_NAME.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
