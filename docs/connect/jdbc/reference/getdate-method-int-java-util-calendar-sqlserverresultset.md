---
title: Metodo getDate (int, java.util.Calendar) (SQLServerResultSet) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.getDate (int, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 150411f7-2a73-4380-b921-9698acd5d1f9
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ad49f68c86068907fc0324fc13c6adbe926398f8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32834586"
---
# <a name="getdate-method-int-javautilcalendar-sqlserverresultset"></a>Metodo getDate (int, java.util.Calendar) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore di indice della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come oggetto java.SQL. date nel linguaggio linguaggio di programmazione, utilizzando l'oggetto di calendario specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.Date getDate(int columnIndex,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnIndex*  
  
 Un **int** che indica l'indice di colonna.  
  
 *licenza CAL*  
  
 Un oggetto di calendario.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto Date.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getDate è specificato dal metodo getDate nell'interfaccia Java.SQL. ResultSet.  
  
 Questo metodo restituisce una parte della data valida di un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipo di dati datetime o smalldatetime, con la parte dell'ora impostata sull'ora di base Java di 00:00 (mezzanotte) nel fuso orario del calendario.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getDate &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdate-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
