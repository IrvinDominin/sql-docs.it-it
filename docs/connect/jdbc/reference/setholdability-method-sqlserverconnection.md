---
title: Metodo (SQLServerConnection) setHoldability | Documenti Microsoft
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
- SQLServerConnection.setHoldability
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 552eebd0-4c38-43f0-961f-35244f99109b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 266030ab3db448b3d70909370e81aeefd21ca332
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="setholdability-method-sqlserverconnection"></a>setHoldability (metodo) (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta sul valore [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) gli oggetti creati tramite questo [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) oggetto per la trattenibilità specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setHoldability(int nNewHold)  
```  
  
#### <a name="parameters"></a>Parametri  
 *nNewHold*  
  
 Un **int** valore contenente uno dei livelli di trattenibilità seguenti:  
  
 HOLD_CURSORS_OVER_COMMIT  
  
 CLOSE_CURSORS_AT_COMMIT  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setHoldability viene specificato dal metodo setHoldability nell'interfaccia Java.SQL. Connection.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
