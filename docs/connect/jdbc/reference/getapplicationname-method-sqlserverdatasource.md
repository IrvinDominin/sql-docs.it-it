---
title: Metodo getApplicationName (SQLServerDataSource) | Documenti Microsoft
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
- SQLServerDataSource.getApplicationName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f71e501c-ccd7-4a1e-b6ea-4d47a81c18c6
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0239d7d251b4104000646a8f98a3cae0be656853
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getapplicationname-method-sqlserverdatasource"></a>Metodo getApplicationName (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce il nome dell'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getApplicationName()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** che contiene il nome dell'applicazione o "[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]" se è impostato alcun valore.  
  
## <a name="remarks"></a>Osservazioni  
 Il nome dell'applicazione viene utilizzato per identificare l'applicazione specifica nei diversi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] strumenti di registrazione e analisi. Se il nome dell'applicazione non è impostato, il metodo getApplicationName restituisce la stringa non localizzata "[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]".  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
