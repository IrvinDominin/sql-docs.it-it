---
title: Metodo setTrustServerCertificate (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- setTrustServerCertificate Method (SQLServerDataSource)
apilocation:
- setTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 6c37b518-147e-4cd9-9eff-b48a3f5888c6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 313e763fd82b1bf8515fcb5f7a850d84da260de9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47793738"
---
# <a name="settrustservercertificate-method-sqlserverdatasource"></a>Metodo setTrustServerCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta un valore **Boolean** che indica se la proprietà trustServerCertificate è abilitata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setTrustServerCertificate(boolean trustServerCertificate)  
```  
  
#### <a name="parameters"></a>Parametri  
 *trustServerCertificate*  
  
 **true** se il certificato Secure Sockets Layer (SSL) del server deve essere automaticamente considerato attendibile quando il livello di comunicazione è crittografato tramite SSL. In caso contrario, **false**.  
  
## <a name="remarks"></a>Remarks  
 Se la proprietà trustServerCertificate è impostata su **true**, il certificato SSL di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene automaticamente considerato attendibile quando il livello di comunicazione è crittografato tramite SSL. In altri termini, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] non convalida il certificato SSL di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il valore predefinito è **false**.  
  
 Se la proprietà trustServerCertificate è impostata su **false**, il certificato SSL del server viene convalidato da [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
