---
title: Metodo setTrustStore (SQLServerDataSource) | Documenti Microsoft
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
- setTrustStore Method (SQLServerDataSource)
apilocation:
- setTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: bab5485d-4547-426c-adbe-44e2b5702d1d
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cf5d6034fbf2e9ce9d1c1b58909146dbcf56f0c6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32846736"
---
# <a name="settruststore-method-sqlserverdatasource"></a>Metodo setTrustStore (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il percorso (incluso il nome file) del file trustStore del certificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setTrustStore(java.lang.String trustStore)  
```  
  
#### <a name="parameters"></a>Parametri  
 *trustStore*  
  
 Oggetto **stringa** che contiene il percorso (incluso il nome di file) del file trustStore del certificato.  
  
## <a name="remarks"></a>Osservazioni  
 Se la proprietà trustStore non specificato o impostato su null, il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] si basano le regole per determinare l'archivio certificati da utilizzare ricerca della factory del manager di attendibilità. Tramite l'istanza predefinita di TrustManagerFactory SunX509 viene eseguito un tentativo di individuare il materiale attendibile nelle posizioni seguenti in base all'ordine indicato:  
  
-   1. Un file specificato dalla proprietà di sistema JVM (Java Virtual Machine) "javax.net.ssl.trustStore".  
  
-   2. "\<java-home >/lib/security/jssecacerts" file.  
  
-   3. "\<java-home >/lib/security/cacerts" file.  
  
 Per ulteriori informazioni, vedere la documentazione relativa all'interfaccia TrustManager SunX509 nel sito Web Sun Microsystems.  
  
 Se la proprietà trustStore è impostata su una stringa o una stringa vuota "", tale valore verrà utilizzato dal driver per trovare il file trustStore e convalidare il certificato SSL del server.  
  
 È possibile specificare la proprietà trustStorePassword insieme alla proprietà trustStore in modo da utilizzarne il valore per aprire il file trustStore. Per ulteriori informazioni, vedere [setTrustStorePassword](../../../connect/jdbc/reference/settruststorepassword-method-sqlserverdatasource.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
