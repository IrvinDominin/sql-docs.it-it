---
title: Metodo getUnicodeStream (int) | Documenti Microsoft
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
- SQLServerResultSet.getUnicodeStream (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0de79b65-a25e-4028-9cc2-7ac02340115b
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8034a89bde03c3994dc660ed7cfde390ff970357
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32838956"
---
# <a name="getunicodestream-method-int"></a>Metodo getUnicodeStream (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore di indice della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come flusso di caratteri Unicode.  
  
> [!NOTE]  
>  Questo metodo è stato deprecato dalla specifica JDBC e, chiamandolo, verrà generata un'eccezione relativa a una mancata implementazione. Utilizzare invece il [getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md) metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.io.InputStream getUnicodeStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnIndex*  
  
 Un **int** che indica l'indice di colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto InputStream.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getUnicodeString viene specificato dal metodo getUnicodeString nell'interfaccia Java.SQL. ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getUnicodeStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getunicodestream-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
