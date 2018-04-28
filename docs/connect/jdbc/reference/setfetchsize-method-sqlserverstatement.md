---
title: Metodo setFetchSize (SQLServerStatement) | Documenti Microsoft
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
apiname:
- SQLServerStatement.setFetchSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 760e555e-9667-4b40-b0ba-778026ff2923
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e56a7578bae0911f4fde9e279d725460ffec2708
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="setfetchsize-method-sqlserverstatement"></a>Metodo setFetchSize (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Fornisce il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] un hint per il numero di righe che devono essere recuperate dal database quando sono necessarie più righe.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setFetchSize(int rows)  
```  
  
#### <a name="parameters"></a>Parametri  
 *rows*  
  
 Un **int** che indica il numero di righe da recuperare.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setFetchSize viene specificato dal metodo setFetchSize nell'interfaccia Java.SQL. Statement.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
