---
title: Metodo registerOutParameter al tipo e nome | Documenti Microsoft
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
apiname:
- SQLServerCallableStatement.registerOutParameter
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f962c912-2475-4e1f-a384-579be2d17f37
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6f08c9c62b59a01755859938c6b2734dc33c8d09
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="registeroutparameter-method-javalangstring-int-javalangstring"></a>Metodo registerOutParameter (java.lang.String, int, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Registra il parametro OUT con il nome specificato nel tipo e nel nome del tipo JDBC forniti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void registerOutParameter(java.lang.String s,  
                                 int n,  
                                 java.lang.String s1)  
```  
  
#### <a name="parameters"></a>Parametri  
 *S*  
  
 Oggetto **stringa** che contiene il nome del parametro.  
  
 *n*  
  
 Codice di tipo JDBC come definito in java.sql.Types.  
  
 *S1*  
  
 Oggetto **stringa** che contiene il nome completo del tipo SQL.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo registerOutParameter viene specificato dal metodo registerOutParameter nell'interfaccia Java.SQL. CallableStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo registerOutParameter &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
