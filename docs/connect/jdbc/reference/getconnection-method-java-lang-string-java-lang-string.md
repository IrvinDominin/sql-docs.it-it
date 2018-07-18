---
title: Metodo (lang. String, lang) getConnection | Documenti Microsoft
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
- SQLServerDataSource.getConnection (java.lang.String, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 78db89d6-a8a0-4116-8885-548e627220ed
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fb33640c75d98fa065c6388458aaffc3067c3126
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32832296"
---
# <a name="getconnection-method-javalangstring-javalangstring"></a>Metodo getConnection (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Tenta di stabilire una connessione con i dati di origine da questo [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) oggetto rappresenta utilizzando il nome utente e la password.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.Connection getConnection(java.lang.String username,  
                                         java.lang.String password)  
```  
  
#### <a name="parameters"></a>Parametri  
 *username*  
  
 Oggetto **stringa** che contiene il nome utente.  
  
 *password*  
  
 Oggetto **stringa** che contiene la password.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 java.sql.SQLException  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getConnection viene specificato dal metodo getConnection nell'interfaccia javax.SQL.  
  
 La chiamata di getConnection metodo con un nome utente diverso da null o una password sostituirà le proprietà di nome e una password utente impostate per la classe SQLServerDataSource durante l'inizializzazione dell'oggetto SQLServerConnection. Ad esempio, se il chiamante ha chiamato [setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md) e [setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md) l'origine dati e quindi chiama getConnection e fornisce un valore non null nome utente o password non null, il nome utente e la password impostata setUser e setPassword verrà sostituiti dal nome utente e password passati in getConnection.  
  
> [!NOTE]  
>  Il nome utente e la password che vengono impostati nell'URL tramite una chiamata al [setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md) (metodo) non verrà modificata in questo caso.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getConnection &#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)   
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
