---
title: Metodo supportsConvert () | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsConvert ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 45c83c4f-649a-4cd6-9d44-d38524758bb8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b2d3b80a0fadb6d08ef5c24dfef0c96191127892
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47841249"
---
# <a name="supportsconvert-method-"></a>Metodo supportsConvert ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un valore che indica se il database supporta la funzione CONVERT tra i tipi SQL.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean supportsConvert()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se supportata. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo supportsConvert viene specificato dal metodo supportsConvert nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo supportsConvert &#40;SQLServerDatabaseMetaData&#41;](../../../connect/jdbc/reference/supportsconvert-method-sqlserverdatabasemetadata.md)   
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
