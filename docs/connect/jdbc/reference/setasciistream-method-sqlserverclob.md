---
title: Metodo setAsciiStream (SQLServerClob) | Documenti Microsoft
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
- SQLServerClob.setAsciiStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6e1779df-3b2a-41d1-8dca-99692cc9da14
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6e5d609145246cad254ba7242a0dd5717588d276
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setasciistream-method-sqlserverclob"></a>Metodo setAsciiStream (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce un flusso da utilizzare per scrivere caratteri ASCII nell'oggetto CLOB a partire dalla posizione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.io.OutputStream setAsciiStream(long pos)  
```  
  
#### <a name="parameters"></a>Parametri  
 *POS*  
  
 Posizione in corrispondenza della quale iniziare la scrittura nell'oggetto CLOB.  
  
## <a name="return-value"></a>Valore restituito  
 Flusso in cui possono essere scritti i caratteri ASCII.  
  
## <a name="exceptions"></a>Eccezioni  
 java.sql.SQLException  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setAsciiStream viene specificato dal metodo setAsciiStream nell'interfaccia Java.SQL. Clob.  
  
 I dati di tipo carattere nell'oggetto CLOB vengono sovrascritti dal flusso di output a partire dalla posizione specificata e possono superare la lunghezza iniziale di tale oggetto. Se si specifica un valore posizione+1, verranno aggiunti caratteri ASCII. Se si specifica un valore posizione+2 o superiore (o zero o inferiore) verrà generato un errore di posizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Membri di SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Classe SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  