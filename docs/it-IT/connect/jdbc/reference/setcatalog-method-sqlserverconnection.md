---
title: Metodo setCatalog (SQLServerConnection) | Documenti Microsoft
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
ms.topic: conceptual
apiname:
- SQLServerConnection.setCatalog
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 553c0603-c07d-436a-86eb-3ba6b51bd696
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c500a74ee2b87487e9596ac372deb2ed5021b325
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="setcatalog-method-sqlserverconnection"></a>Metodo setCatalog (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il nome di catalogo specificato per selezionare uno spazio secondario di questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) database dell'oggetto da utilizzare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setCatalog(java.lang.String catalog)  
```  
  
#### <a name="parameters"></a>Parametri  
 *catalog*  
  
 Oggetto **stringa** che contiene il nome del catalogo.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setCatalog viene specificato dal metodo setCatalog nell'interfaccia Java.SQL. Connection.  
  
 Il *catalogo* argomento di escape per il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] automaticamente. Questo metodo imposta la proprietà di catalogo per l'oggetto connessione. Tale proprietà non viene impostata in modo implicito in altro modo.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
