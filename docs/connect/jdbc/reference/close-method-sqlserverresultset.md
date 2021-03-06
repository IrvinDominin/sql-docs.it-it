---
title: Close (metodo) (SQLServerResultSet) | Documenti Microsoft
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
- SQLServerResultSet.close
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8f3adf5b-874e-4cf2-b4ef-672dda42d77a
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: deea90b13bb4bb99c504f5eaa344babdf4a1c680
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32830736"
---
# <a name="close-method-sqlserverresultset"></a>Metodo close (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rilascia questa [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) dell'oggetto database e le risorse JDBC immediatamente anziché attendere che ciò si verifica quando viene chiuso automaticamente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void close()  
```  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo di chiuso viene specificato dal metodo di chiusura nell'interfaccia Java.SQL. ResultSet.  
  
 Un oggetto SQLServerResultSet è chiuso automaticamente dal [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto che lo ha generato quando l'oggetto SQLServerStatement è chiuso, Esegui nuovamente o utilizzato per recuperare il risultato successivo da una sequenza di più risultati . Un oggetto SQLServerResultSet è chiuso automaticamente quando è sottoposto a garbage collection.  
  
 Quando si esegue un'istruzione che genera un solo set di risultati forward-only di sola lettura di grandi dimensioni, si potrebbe essere interessati solo a qualche set di righe iniziale nel set di risultati restituito. In questo caso, l'applicazione potrebbe chiamare il [Annulla](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md) metodo dell'oggetto istruzione associato prima di chiudere il risultato è impostato per ridurre al minimo il tempo di elaborazione richiesto per rimuovere le rimanenti righe non necessarie. Al momento di decidere se utilizzare o meno questa tecnica, si consiglia di tenere conto della necessità di mantenere un equilibrio tra il tempo di elaborazione salvato e il tempo e il round trip al server aggiuntivo necessari per annullare l'esecuzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
