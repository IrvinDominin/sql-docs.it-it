---
title: moveToInsertRow (metodo) (SQLServerResultSet) | Documenti Microsoft
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
- SQLServerResultSet.moveToInsertRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f3c54bfe-d5b7-4f6e-ae6c-3e8954e5b1c9
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e3a53a13c1352f33033a9507b66a4b257265acc3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32839736"
---
# <a name="movetoinsertrow-method-sqlserverresultset"></a>moveToInsertRow (metodo) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Sposta il cursore nella riga di inserimento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void moveToInsertRow()  
```  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo moveToInsertRow viene specificato dal metodo moveToInsertRow nell'interfaccia Java.SQL. ResultSet.  
  
 La posizione corrente del cursore viene memorizzata mentre il cursore viene posizionato sulla riga di inserimento. La riga di inserimento è una riga speciale associata a un set di risultati aggiornabile. Si tratta essenzialmente di un buffer in cui è possibile costruire una nuova riga chiamando i metodi di aggiornamento prima di aggiungere la riga al set di risultati.  
  
 Solo l'aggiornamento, richiamo e [insertRow](../../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md) metodi possono essere chiamati quando il cursore si trova sulla riga di inserimento. Tutte le colonne in un set di risultati devono essere specificato un valore ogni volta che questo metodo viene chiamato e prima di chiamare insertRow. Un metodo di aggiornamento deve essere chiamato prima che uno di richiamo possa essere chiamato su un valore della colonna.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
