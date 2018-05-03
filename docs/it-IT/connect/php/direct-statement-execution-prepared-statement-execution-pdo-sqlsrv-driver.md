---
title: Indirizzare informativa - Driver PDO_SQLSRV esecuzione di istruzione preparata | Documenti Microsoft
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 05544ca6-1e07-486c-bf03-e8c2c25b3024
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aaa67ec16086dcfac895422c58c8cdddc50ef243
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="direct-statement-execution-and-prepared-statement-execution-in-the-pdosqlsrv-driver"></a>Esecuzione di istruzioni diretta e preparata nel driver PDO_SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In questo argomento viene illustrato l'utilizzo dell'attributo PDO:: sqlsrv_attr_direct_query per specificare l'esecuzione diretta delle istruzioni anziché l'impostazione predefinita, che viene preparata l'esecuzione dell'istruzione. Utilizzo di un'istruzione preparata può comportare prestazioni migliori se l'istruzione viene eseguita più volte utilizzando l'associazione di parametri.  
  
## <a name="remarks"></a>Osservazioni  
Se si desidera inviare un [!INCLUDE[tsql](../../includes/tsql_md.md)] istruzione direttamente al server senza la preparazione dell'istruzione dal driver, è possibile impostare l'attributo PDO:: sqlsrv_attr_direct_query con [PDO:: SetAttribute](../../connect/php/pdo-setattribute.md) (o come un driver (opzione) passato a [PDO::__construct](../../connect/php/pdo-construct.md)) o quando si chiama [PDO:: Prepare](../../connect/php/pdo-prepare.md). Per impostazione predefinita, il valore di PDO:: sqlsrv_attr_direct_query è False (utilizzare l'esecuzione dell'istruzione preparata).  
  
Se si utilizza [PDO:: query](../../connect/php/pdo-query.md), è possibile l'esecuzione diretta. Prima di chiamare [PDO:: query](../../connect/php/pdo-query.md), chiamare [PDO:: SetAttribute](../../connect/php/pdo-setattribute.md) e PDO:: sqlsrv_attr_direct_query su True.  Ogni chiamata a [PDO:: query](../../connect/php/pdo-query.md) possono essere eseguite con un'impostazione diversa per PDO:: sqlsrv_attr_direct_query.  
  
Se si utilizza [PDO:: Prepare](../../connect/php/pdo-prepare.md) e [pdostatement:: Execute](../../connect/php/pdostatement-execute.md) per eseguire una query più volte con parametri associati, l'esecuzione di istruzione preparata consente di ottimizzare l'esecuzione della query ripetute.  In questo caso, chiamare [PDO:: Prepare](../../connect/php/pdo-prepare.md) con PDO:: sqlsrv_attr_direct_query impostato su False il parametro di matrice opzioni driver. Se necessario, è possibile eseguire le istruzioni preparate con PDO:: sqlsrv_attr_direct_query impostato su False.  
  
Dopo aver chiamato [PDO:: Prepare](../../connect/php/pdo-prepare.md), non è possibile modificare il valore di PDO:: sqlsrv_attr_direct_query durante l'esecuzione di query preparata.  
  
Se una query richiede il contesto che è stato impostato in una query precedente, quindi eseguire le query con PDO:: sqlsrv_attr_direct_query impostato su True. Ad esempio, se si utilizzano tabelle temporanee nelle query, PDO:: sqlsrv_attr_direct_query deve essere impostata su True.  
  
L'esempio seguente viene illustrato quando è necessario contesto da un'istruzione precedente, è necessario impostare PDO:: sqlsrv_attr_direct_query su True.  Questo esempio utilizza le tabelle temporanee, sono disponibili solo per le istruzioni successive del programma quando si eseguono query direttamente.  
  
```  
<?php  
   $conn = new PDO('sqlsrv:Server=(local)', '', '');  
   $conn->setAttribute(constant('PDO::SQLSRV_ATTR_DIRECT_QUERY'), true);  
  
   $stmt1 = $conn->query("DROP TABLE #php_test_table");  
  
   $stmt2 = $conn->query("CREATE TABLE #php_test_table ([c1_int] int, [c2_int] int)");  
  
   $v1 = 1;  
   $v2 = 2;  
  
   $stmt3 = $conn->prepare("INSERT INTO #php_test_table (c1_int, c2_int) VALUES (:var1, :var2)");  
  
   if ($stmt3) {  
      $stmt3->bindValue(1, $v1);  
      $stmt3->bindValue(2, $v2);  
  
      if ($stmt3->execute())  
         echo "Execution succeeded\n";       
      else  
         echo "Execution failed\n";  
   }  
   else  
      var_dump($conn->errorInfo());  
  
   $stmt4 = $conn->query("DROP TABLE #php_test_table");  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Guida di programmazione per i driver Microsoft per PHP per SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)
  
