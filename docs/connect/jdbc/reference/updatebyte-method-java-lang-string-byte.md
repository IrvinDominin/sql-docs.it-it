---
title: Metodo updateByte (lang, byte) | Documenti Microsoft
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
- SQLServerResultSet.updateByte (java.lang.String, byte)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5416aed2-a5b6-4e3b-9750-90db8cda8cec
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8be753415e11a62849bfdfdf68f15f5d2d4613ef
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="updatebyte-method-javalangstring-byte"></a>Metodo updateByte (java.lang.String, byte)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un **byte** valore in base al nome della colonna.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateByte(java.lang.String columnName,  
                       byte x)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnName*  
  
 Oggetto **stringa** che contiene il nome della colonna.  
  
 *x*  
  
 Oggetto **byte** valore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateByte viene specificato dal metodo updateByte nell'interfaccia Java.SQL. ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateByte &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebyte-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
