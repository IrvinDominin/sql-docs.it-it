---
title: Metodo (long, byte) setBytes | Documenti Microsoft
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
- SQLServerBlob.setBytes (long.byte[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ffb8f107-0f9d-4410-957f-62b718e1e872
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cdb1b7185d60f474d180143fe6d78dc9fd2fa42b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="setbytes-method-long-byte"></a>setBytes (long, byte) (metodo)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Scrive la matrice di byte specificata nell'oggetto BLOB a partire dalla posizione specificata, quindi restituisce il numero di byte scritti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int setBytes(long pos,  
                    byte[] bytes)  
```  
  
#### <a name="parameters"></a>Parametri  
 *POS*  
  
 Posizione (in base 1) nell'oggetto BLOB in corrispondenza della quale iniziare la scrittura dei dati.  
  
 *Byte*  
  
 Matrice di byte da scrivere nell'oggetto BLOB.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **lungo** valore che specifica il numero di byte scritti.  
  
## <a name="exceptions"></a>Eccezioni  
 java.sql.SQLException  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setBytes viene specificato dal metodo setBytes nell'interfaccia Java.SQL. BLOB.  
  
 I dati vengono sovrascritti a partire dalla posizione specificata e possono superare la lunghezza iniziale dell'oggetto BLOB. Se si specifica un valore posizione+1, verranno aggiunti byte. Se si passa un valore posizione+2 o superiore (o zero o inferiore) verrà generato un errore di posizione. Il passaggio di lunghezza zero **byte** matrice restituirà zero perché è stato scritto alcun byte.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setBytes &#40;SQLServerBlob&#41;](../../../connect/jdbc/reference/setbytes-method-sqlserverblob.md)   
 [Metodi di SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Membri di SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Classe SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
