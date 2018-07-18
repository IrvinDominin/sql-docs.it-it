---
title: Gestione dei risultati set con il Driver JDBC | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9ed5ad41-22e0-4e4a-8a79-10512db60d50
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6e428a66a506005cdbde4fbc58b724e8b22972ab
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32829886"
---
# <a name="managing-result-sets-with-the-jdbc-driver"></a>Gestione dei set di risultati con il driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il set di risultati è un oggetto che rappresenta un set di dati restituito da un'origine dati, in genere come risultato di una query. Il set di risultati contiene righe e colonne con gli elementi di dati richiesti e per spostarsi al suo interno viene utilizzato un cursore. Un set di risultati può essere aggiornabile, ovvero può essere modificato e le modifiche inserite nell'origine dati originale. Il set di risultati può inoltre disporre di vari livelli di sensibilità alle modifiche nell'origine dati sottostante.  
  
 Il tipo di set di risultati viene determinato quando viene creata un'istruzione, ovvero quando una chiamata al [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) metodo il [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) viene effettuata. La finalità del set di risultati è di fornire alle applicazioni Java una rappresentazione utilizzabile dei dati del database, in genere con i metodi digitati per il richiamo e l'impostazione degli elementi di dati del set di risultati.  
  
 Nell'esempio seguente, che si basa sul [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio, un set di risultati viene creato chiamando il [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) metodo il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) classe. I dati dal set di risultati viene quindi visualizzati utilizzando il [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md) metodo il [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) classe.  
  
 [!code[JDBC#ManagingResultSets1](../../connect/jdbc/codesnippet/Java/managing-result-sets-with-t_1.java)]  
  
 Negli argomenti di questa sezione vengono descritti i diversi aspetti dell'utilizzo del set di risultati, compresi tipi di cursore, concorrenza e blocchi a livello di riga.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Informazioni sui tipi di cursore](../../connect/jdbc/understanding-cursor-types.md)|Vengono descritti i diversi tipi di cursore di [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] supporta.|  
|[Informazioni sul controllo della concorrenza](../../connect/jdbc/understanding-concurrency-control.md)|Viene descritto il supporto fornito dal driver JDBC per il controllo della concorrenza.|  
|[Informazioni sul blocco delle righe](../../connect/jdbc/understanding-row-locking.md)|Viene descritto in che modo il driver JDBC supporta i blocchi a livello di riga.|  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
