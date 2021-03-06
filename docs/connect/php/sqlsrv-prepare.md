---
title: sqlsrv_prepare | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_prepare
apitype: NA
helpviewer_keywords:
- executing queries
- API Reference, sqlsrv_prepare
- sqlsrv_prepare
ms.assetid: 8c74c697-3296-4f5d-8fb9-e361f53f19a6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9a293ff4bd2eae7f1e54914c805e4e180ce17fb2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47669519"
---
# <a name="sqlsrvprepare"></a>sqlsrv_prepare
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Crea una risorsa di istruzione associata alla connessione specificata. Questa funzione è utile per l'esecuzione di più query.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sqlsrv_prepare(resource $conn, string $tsql [, array $params [, array $options]])  
```  
  
#### <a name="parameters"></a>Parametri  
*$conn*: risorsa di connessione associata all'istruzione creata.  
  
*$tsql*: espressione Transact-SQL corrispondente all'istruzione creata.  
  
*$params* [facoltativo]: **matrice** di valori corrispondenti ai parametri di una query con parametri. Ogni elemento della matrice può corrispondere a uno dei seguenti:
  
-   Valore letterale.  
  
-   Riferimento a una variabile PHP.  
  
-   **Matrice** con la struttura seguente:  
  
    ```  
    array(&$value [, $direction [, $phpType [, $sqlType]]])  
    ```  
  
    > [!NOTE]  
    > Le variabili passate come parametri di query devono essere passate per riferimento e non per valore. Ad esempio, passare `&$myVariable` anziché `$myVariable`. Se viene eseguita una query con parametri per valore, viene generato un avviso PHP.  
  
    Nella tabella riportata di seguito vengono descritti gli elementi di matrice seguenti:  
  
    |Elemento|Descrizione|  
    |-----------|---------------|  
    |*&$value*|Valore letterale o riferimento a una variabile PHP.|  
    |*$direction*[facoltativo]|Una delle costanti **SQLSRV_PARAM_\*** seguenti usate per indicare la direzione del parametro: **SQLSRV_PARAM_IN**, **SQLSRV_PARAM_OUT**, **SQLSRV_PARAM_INOUT**. Il valore predefinito è **SQLSRV_PARAM_IN**.<br /><br />Per altre informazioni sulle costanti PHP, vedere [Costanti &#40;driver Microsoft per PHP per SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
    |*$phpType*[facoltativo]|Costante **SQLSRV_PHPTYPE_\*** che specifica il tipo di dati PHP del valore restituito.|  
    |*$sqlType*[facoltativo]|Costante **SQLSRV_SQLTYPE_\*** che specifica il tipo di dati SQL Server del valore di input.|  
  
*$options* [facoltativo]: matrice associativa che imposta le proprietà delle query. Nella tabella seguente sono elencate le chiavi supportate e i valori corrispondenti:  
  
|Key|Valori supportati|Descrizione|  
|-------|--------------------|---------------|  
|QueryTimeout|Valore integer positivo.|Imposta il timeout in secondi della query. Per impostazione predefinita il driver attende i risultati per un periodo illimitato.|  
|SendStreamParamsAtExec|**true** o **false**<br /><br />Il valore predefinito è **true**.|Configura il driver per l'invio di tutti i flussi di dati in fase di esecuzione (**true**) o in blocchi (**false**). Per impostazione predefinita, il valore è impostato su **true**. Per altre informazioni, vedere [sqlsrv_send_stream_data](../../connect/php/sqlsrv-send-stream-data.md).|  
|Scorrimento|SQLSRV_CURSOR_FORWARD<br /><br />SQLSRV_CURSOR_STATIC<br /><br />SQLSRV_CURSOR_DYNAMIC<br /><br />SQLSRV_CURSOR_KEYSET<br /><br />SQLSRV_CURSOR_CLIENT_BUFFERED|Per altre informazioni su questi valori, vedere [Specifica di un tipo di cursore e selezione di righe](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md).|  
  
## <a name="return-value"></a>Valore restituito  
Risorsa di istruzione. Se non è possibile creare la risorsa di istruzione, viene restituito **false** .  
  
## <a name="remarks"></a>Remarks  
Quando si prepara un'istruzione che usa variabili come parametri, le variabili vengono associate all'istruzione. Ciò significa che se si aggiornano i valori delle variabili, alla successiva esecuzione l'istruzione verrà eseguita con i valori aggiornati dei parametri.  
  
La combinazione di **sqlsrv_prepare** e **sqlsrv_execute** , che separa la preparazione e l'esecuzione dell'istruzione in due chiamate di funzione, può essere usata per eseguire query con parametri. Questa funzione è ideale per eseguire un'istruzione più volte con valori di parametro diversi per ciascuna esecuzione.  
  
Per strategie alternative per la scrittura e la lettura di grandi quantità di informazioni, vedere la pagina relativa ai [batch di istruzioni SQL](../../odbc/reference/develop-app/batches-of-sql-statements.md) e la pagina [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md).  
  
Per altre informazioni, vedere [How to: Retrieve Output Parameters Using the SQLSRV Driver](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md).  
  
## <a name="example"></a>Esempio  
Nell'esempio seguente viene preparata ed eseguita un'istruzione. Quando viene eseguita (vedere [sqlsrv_execute](../../connect/php/sqlsrv-execute.md)), l'istruzione aggiorna un campo nella tabella *Sales.SalesOrderDetail* del database AdventureWorks. Nell'esempio si presuppone che SQL Server e il database [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) siano installati nel computer locale. Quando si esegue l'esempio dalla riga di comando, tutto l'output viene scritto nel browser.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
    echo "Could not connect.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Set up Transact-SQL query. */  
$tsql = "UPDATE Sales.SalesOrderDetail   
         SET OrderQty = ?   
         WHERE SalesOrderDetailID = ?";  
  
/* Assign parameter values. */  
$param1 = 5;  
$param2 = 10;  
$params = array(&$param1, &$param2);  
  
/* Prepare the statement. */  
if ($stmt = sqlsrv_prepare($conn, $tsql, $params)) {
    echo "Statement prepared.\n";  
} else {  
    echo "Statement could not be prepared.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Execute the statement. */  
if (sqlsrv_execute($stmt)) {  
    echo "Statement executed.\n";  
} else {  
    echo "Statement could not be executed.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  
?>  
```  
  
## <a name="example"></a>Esempio  
Nell'esempio seguente viene illustrato come preparare un'istruzione ed eseguirla nuovamente con valori diversi per i parametri. L'esempio aggiorna la colonna *OrderQty* della tabella *Sales.SalesOrderDetail* nel database AdventureWorks. Dopo gli aggiornamenti, viene eseguita una query nel database per verificare che gli aggiornamenti siano stati completati correttamente. Nell'esempio si presuppone che SQL Server e il database [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) siano installati nel computer locale. Quando si esegue l'esempio dalla riga di comando, tutto l'output viene scritto nel browser.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
     echo "Could not connect.\n";  
     die(print_r(sqlsrv_errors(), true));  
}  
  
/* Define the parameterized query. */  
$tsql = "UPDATE Sales.SalesOrderDetail  
         SET OrderQty = ?  
         WHERE SalesOrderDetailID = ?";  
  
/* Initialize parameters and prepare the statement. Variables $qty  
and $id are bound to the statement, $stmt1. */  
$qty = 0; $id = 0;  
$stmt1 = sqlsrv_prepare($conn, $tsql, array(&$qty, &$id));  
if ($stmt1) {  
    echo "Statement 1 prepared.\n";  
} else {  
    echo "Error in statement preparation.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Set up the SalesOrderDetailID and OrderQty information. This array  
maps the order ID to order quantity in key=>value pairs. */  
$orders = array(1=>10, 2=>20, 3=>30);  
  
/* Execute the statement for each order. */  
foreach ($orders as $id => $qty) {  
    // Because $id and $qty are bound to $stmt1, their updated  
    // values are used with each execution of the statement.   
    if (sqlsrv_execute($stmt1) === false) {  
        echo "Error in statement execution.\n";  
        die(print_r(sqlsrv_errors(), true));  
    }  
}  
echo "Orders updated.\n";  
  
/* Free $stmt1 resources.  This allows $id and $qty to be bound to a different statement.*/  
sqlsrv_free_stmt($stmt1);  
  
/* Now verify that the results were successfully written by selecting   
the newly inserted rows. */  
$tsql = "SELECT OrderQty   
         FROM Sales.SalesOrderDetail   
         WHERE SalesOrderDetailID = ?";  
  
/* Prepare the statement. Variable $id is bound to $stmt2. */  
$stmt2 = sqlsrv_prepare($conn, $tsql, array(&$id));  
if ($stmt2) {  
    echo "Statement 2 prepared.\n";  
} else {  
    echo "Error in statement preparation.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Execute the statement for each order. */  
foreach (array_keys($orders) as $id)  
{  
    /* Because $id is bound to $stmt2, its updated value   
    is used with each execution of the statement. */  
    if (sqlsrv_execute($stmt2)) {  
        sqlsrv_fetch($stmt2);  
        $quantity = sqlsrv_get_field($stmt2, 0);  
        echo "Order $id is for $quantity units.\n";  
    } else {  
        echo "Error in statement execution.\n";  
        die(print_r(sqlsrv_errors(), true));  
    }  
}  
  
/* Free $stmt2 and connection resources. */  
sqlsrv_free_stmt($stmt2);  
sqlsrv_close($conn);  
?>  
```  
  
> [!NOTE]
> È consigliabile usare le stringhe come input durante l'associazione di valori da un [colonna decimal o numeric](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) per garantire precisione e accuratezza come PHP ha limitato la precisione per [numeri a virgola mobile](http://php.net/manual/en/language.types.float.php). Lo stesso vale per le colonne di tipo bigint, soprattutto quando i valori sono di fuori dell'intervallo di un' [integer](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md).

## <a name="example"></a>Esempio  
Questo esempio di codice viene illustrato come associare un valore decimale come parametro di input.  

```
<?php
$serverName = "(local)";
$connectionInfo = array("Database"=>"YourTestDB");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
    echo "Could not connect.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  

// Assume TestTable exists with a decimal field 
$input = "9223372036854.80000";
$params = array($input);
$stmt = sqlsrv_prepare($conn, "INSERT INTO TestTable (DecimalCol) VALUES (?)", $params);
sqlsrv_execute($stmt);

sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  

?>
```

## <a name="see-also"></a>Vedere anche  
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Procedura: Eseguire query con parametri](../../connect/php/how-to-perform-parameterized-queries.md)

[Informazioni sugli esempi di codice nella documentazione](../../connect/php/about-code-examples-in-the-documentation.md)

[Procedura: Inviare dati come flusso](../../connect/php/how-to-send-data-as-a-stream.md)

[Uso dei parametri direzionali](../../connect/php/using-directional-parameters.md)

[Recupero di dati](../../connect/php/retrieving-data.md)

[Aggiornamento dei dati &#40;Driver Microsoft per PHP per SQL Server&#41;](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)

