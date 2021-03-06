---
title: Metodo jdbcCompliant (SQLServerDriver) | Documenti Microsoft
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
- SQLServerDriver.jdbcCompliant
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b299b20d-d1cd-45b3-91dc-dcf579498570
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 357024153bb862ff369278096018dd544ead4ca8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32840346"
---
# <a name="jdbccompliant-method-sqlserverdriver"></a>Metodo jdbcCompliant (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Verifica che il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] è conforme alla specifica JDBC.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean jdbcCompliant()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se il driver JDBC soddisfa i requisiti minimi. In caso contrario, **false**.  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo jdbcCompliant viene specificato dal metodo jdbcCompliant nell'interfaccia Java.SQL. driver.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [Membri di SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [Classe SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
