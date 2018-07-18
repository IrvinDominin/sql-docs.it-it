---
title: Metodo getSubString (SQLServerNClob) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1d91c930-1bac-4da9-b9a5-ac2cfd31541b
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8740faa9070f785b8610c847f0b5871f0e21dbd4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getsubstring-method-sqlservernclob"></a>Metodo getSubString (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una copia della sottostringa specificata nel **NCLOB** in base a una posizione iniziale specificata e il numero di caratteri da copiare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getSubString(long pos,  
                                  int length)  
```  
  
#### <a name="parameters"></a>Parametri  
 *POS*  
  
 Primo carattere della sottostringa da estrarre. Il primo carattere si trova nella posizione 1.  
  
 *lunghezza*  
  
 Numero di caratteri consecutivi da copiare.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** che rappresenta la sottostringa specificata nel **NCLOB**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getSubString viene specificato dal metodo getSubString nell'interfaccia Java.SQL. NClob.  
  
 Se si tenta di ottenere zero caratteri da un oggetto NCLOB Null o di lunghezza zero, viene restituita una stringa vuota. Se si tenta di ottenere un numero qualsiasi di caratteri in qualsiasi posizione diversa dalla posizione 1 in un oggetto NCLOB di lunghezza zero, verrà generata un'eccezione di posizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Membri di SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Classe SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
