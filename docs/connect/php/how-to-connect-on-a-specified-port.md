---
title: 'Procedura: connettersi a una porta specifica | Microsoft Docs'
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connecting to the server, specifying a port
ms.assetid: 65a154d1-375c-439b-a653-7815c9d70ff3
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6dd90c68aa47f21c35c2f566a2a8206ba421ace6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38033026"
---
# <a name="how-to-connect-on-a-specified-port"></a>Procedura: Connessione a una porta specifica
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In questo argomento viene descritto come connettersi a SQL Server mediante una porta specifica con i [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
### <a name="to-connect-on-a-specified-port"></a>Per connettersi a una porta specifica  
  
1.  Verificare la porta del server configurata per accettare le connessioni. Per informazioni su come configurare un server per accettare le connessioni su una porta specifica, vedere [Configurazione di un server per l'attesa su una porta TCP specifica ](../../database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md)Gestione configurazione SQL Server.  
  
2.  Aggiungere la porta desiderata al parametro *$serverName* della funzione [sqlsrv](../../connect/php/sqlsrv-connect.md)connect. Separare il nome del server e la porta con una virgola. Ad esempio, le righe di codice seguente usano il driver SQLSRV per illustrare come connettersi a un server denominato *myServer* sulla porta 1521:  
  
    ```  
    $serverName = "myServer, 1521";  
    sqlsrv_connect( $serverName );  
    ```  
  
    Le righe di codice seguente usano il driver PDO*SQLSRV per illustrare come connettersi a un server denominato* myServer sulla porta 1521:  
  
    ```  
    $serverName = "(local), 1521";  
    $database = "AdventureWorks";  
    $conn = new PDO( "sqlsrv:server=$serverName;Database=$database", "", "");  
    ```  
  
## <a name="see-also"></a>Vedere anche  
[Connessione al server](../../connect/php/connecting-to-the-server.md)

[Guida di programmazione per i driver Microsoft per PHP per SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Introduzione a Microsoft Drivers per PHP per SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Guida di riferimento del driver PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
