---
title: Metodo getBytes (SQLServerBlob) | Documenti Microsoft
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
- SQLServerBlob.getBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bea1b810-b5c1-466d-bdc4-561468214632
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7a872d042c0a96123cccffac5c5a6f8e2b686c4d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32830873"
---
# <a name="getbytes-method-sqlserverblob"></a>Metodo getBytes (SQLServerBlob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ottiene i dati BLOB come matrice di byte.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public byte[] getBytes(long pos,  
                       int length)  
```  
  
#### <a name="parameters"></a>Parametri  
 *POS*  
  
 Posizione di inizio, a partire da 1 (non 0).  
  
 *lunghezza*  
  
 Lunghezza dei dati da ottenere.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **byte** matrice contenente i dati richiesti.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getBytes viene specificato dal metodo getBytes nell'interfaccia Java.SQL. BLOB.  
  
 Se si dispone di un valore null o BLOB di lunghezza zero e si tenta di ottenere esattamente zero byte in posizione 1, un oggetto vuoto **byte** matrice viene restituita (matrice di byte di lunghezza 0).  
  
 Se si dispone di una lunghezza BLOB Null o zero e si tenta di ottenere una qualsiasi lunghezza di byte in una posizione diversa da 1, verrà generata un'eccezione di posizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Membri di SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Classe SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
