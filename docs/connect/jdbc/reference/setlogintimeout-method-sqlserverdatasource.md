---
title: Metodo setLoginTimeout (SQLServerDataSource) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.setLoginTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b63d1cf4-dc1b-4e35-9a56-50436642eaaf
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6e95a0377de7fe9a901f33b5913e70399b298aba
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setlogintimeout-method-sqlserverdatasource"></a>Metodo setLoginTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il numero di secondi che questo [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) oggetto attesa durante il tentativo di stabilire una connessione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setLoginTimeout(int loginTimeout)  
```  
  
#### <a name="parameters"></a>Parametri  
 *loginTimeout*  
  
 Un **int** valore che rappresenta il numero di secondi di attesa. Un valore pari a zero indica che il timeout è quello predefinito di sistema, impostato su 15 secondi.  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setLoginTimeout viene specificato dal metodo setLoginTimeout nell'interfaccia javax.SQL.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  