---
title: Utilizzando i metadati del parametro | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db2c1957-91c6-4989-a07b-9f8be6d2033a
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 812e8af3f3b08cf7cd25de64b157cb76657a6b6f
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2018
---
# <a name="using-parameter-metadata"></a>Utilizzo dei metadati dei parametri
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Per eseguire query un [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) o [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) oggetto sui parametri in esso contenuti, il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] implementa il [ SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md) classe. Questa classe contiene numerosi campi e metodi che restituiscono informazioni in forma di singolo valore.  
  
 Per creare un oggetto SQLServerParameterMetaData, è possibile utilizzare il [getParameterMetaData](../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md) metodi delle classi SQLServerPreparedStatement e SQLServerCallableStatement.  
  
 Nell'esempio seguente, una connessione aperta per la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio viene passato alla funzione, il metodo getParameterMetaData della classe SQLServerCallableStatement viene utilizzato per restituire un oggetto SQLServerParameterMetaData e quindi vari Per visualizzare informazioni sul tipo e la modalità dei parametri contenuti all'interno della routine Uspupdateemployeehireinfo archiviati vengono utilizzati i metodi dell'oggetto SQLServerParameterMetaData.  
  
 [!code[JDBC#UsingParamMetaData1](../../connect/jdbc/codesnippet/Java/using-parameter-metadata_1.java)]  
    
> [!NOTE]  
Esistono alcune limitazioni quando si utilizza la classe SQLServerParameterMetaData con le istruzioni preparate. 
**Con Microsoft JDBC Driver 6.0 (o versione successiva) per SQL Server**: quando si utilizza SQL Server 2008 o 2008 R2, il driver JDBC supporta istruzioni SELECT, DELETE, INSERT e UPDATE purché queste istruzioni non contengano sottoquery e/o join.  

UNIONE query anche non sono supportate per la classe SQLServerParameterMetaData quando si utilizza SQL Server 2008 o 2008 R2. Sono supportati per SQL Server 2012 e versioni successive i metadati del parametro con query complesse.  

Recupero dei metadati di parametro per le colonne crittografate non sono supportati. **Con Microsoft JDBC Driver 4.1 o 4.2 per SQL Server**: JDBC il driver supporta istruzioni SELECT, DELETE, INSERT e UPDATE purché queste istruzioni non contengano sottoquery e/o join. MERGE di query non è inoltre supportati per la classe SQLServerParameterMetaData.  
  
  
