---
title: Metodo (lang) (SQLServerResultSet) getNString | Documenti Microsoft
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
ms.assetid: 546d77e2-723a-42ac-ba3f-fabf2395d376
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 38e3391d16fed59fbb0de1efd8052e8eb9260f90
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getnstring-method-javalangstring-sqlserverresultset"></a>Metodo getNString (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore della colonna designata nella riga corrente del [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come oggetto lang.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getNString(java.lang.String columnLabel)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnLabel*  
  
 Stringa che contiene l'etichetta di colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto stringa.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getNString viene specificato dal metodo nell'interfaccia java.sql.SQLServerResultSet getNString.  
  
 Questo metodo può essere utilizzato per recuperare il valore di un **nvarchar**, **nchar**, **nvarchar (max)**, **ntext**, o **xml** colonna nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto. Se si tenta di utilizzare questo metodo per recuperare valori di altri tipi di dati, verrà generata un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getNString &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getnstring-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)  
  
  
