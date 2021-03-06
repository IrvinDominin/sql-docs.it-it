---
title: SQLColAttribute | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLColAttribute function
ms.assetid: a5387d9e-a243-4cfe-b786-7fad5842b1d6
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 80e78d486ff0b87a2cf187a134beb029774f9171
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773149"
---
# <a name="sqlcolattribute"></a>SQLColAttribute
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  È possibile usare **SQLColAttribute** per recuperare un attributo di una colonna del set di risultati per le istruzioni ODBC preparate o eseguite. La chiamata **SQLColAttribute** su istruzioni preparate provoca un round trip al [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client riceve i dati di colonna del set di risultati come parte dell'esecuzione dell'istruzione, quindi la chiamata **SQLColAttribute** dopo il completamento della **SQLExecute** o  **SQLExecDirect** non comporta un round trip del server.  
  
> [!NOTE]  
>  Gli attributi di identificazione di colonna ODBC non sono disponibili in tutti i set di risultati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Identificatore del campo|Description|  
|----------------------|-----------------|  
|SQL_COLUMN_TABLE_NAME|Disponibile nei set di risultati recuperati da istruzioni che generano cursori server o in istruzioni SELECT eseguite contenenti una clausola FOR BROWSE.|  
|SQL_DESC_BASE_COLUMN_NAME|Disponibile nei set di risultati recuperati da istruzioni che generano cursori server o in istruzioni SELECT eseguite contenenti una clausola FOR BROWSE.|  
|SQL_DESC_BASE_TABLE_NAME|Disponibile nei set di risultati recuperati da istruzioni che generano cursori server o in istruzioni SELECT eseguite contenenti una clausola FOR BROWSE.|  
|SQL_DESC_CATALOG_NAME|Nome del database. Disponibile nei set di risultati recuperati da istruzioni che generano cursori server o in istruzioni SELECT eseguite contenenti una clausola FOR BROWSE.|  
|SQL_DESC_LABEL|Disponibile in tutti i set di risultati. Il valore è identico al valore del campo SQL_DESC_NAME.<br /><br /> Il campo è di lunghezza zero solo se una colonna è il risultato di un'espressione e l'espressione non contiene un'assegnazione di etichetta.|  
|SQL_DESC_NAME|Disponibile in tutti i set di risultati. Il valore è identico al valore del campo SQL_DESC_LABEL.<br /><br /> Il campo è di lunghezza zero solo se una colonna è il risultato di un'espressione e l'espressione non contiene un'assegnazione di etichetta.|  
|SQL_DESC_SCHEMA_NAME|Nome del proprietario. Disponibile nei set di risultati recuperati da istruzioni che generano cursori server o in istruzioni SELECT eseguite contenenti una clausola FOR BROWSE.<br /><br /> Disponibile solo se viene specificato il nome del proprietario per la colonna nell'istruzione SELECT.|  
|SQL_DESC_TABLE_NAME|Disponibile nei set di risultati recuperati da istruzioni che generano cursori server o in istruzioni SELECT eseguite contenenti una clausola FOR BROWSE.|  
|SQL_DESC_UNNAMED|SQL_NAMED per tutte le colonne in un set di risultati, a meno che una colonna non sia il risultato di un'espressione che non contiene un'assegnazione di etichetta come parte dell'espressione. Quando SQL_DESC_UNNAMED restituisce SQL_UNNAMED, tutti gli attributi di identificazione di colonna ODBC contengono stringhe di lunghezza zero per la colonna.|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver utilizza l'istruzione SET FMTONLY per ridurre il sovraccarico del server quando **SQLColAttribute** viene chiamato per ma non eseguite le istruzioni preparate.  
  
 Per i tipi di valori di grandi dimensioni, **SQLColAttribute** restituirà i valori seguenti:  
  
|Identificatore del campo|Descrizione della modifica|  
|----------------------|---------------------------|  
|SQL_DESC_DISPLAY_SIZE|Si tratta del numero massimo di caratteri necessari per visualizzare dati dalla colonna. Per le colonne con tipo di dati per valori di grandi dimensioni, il valore restituito è SQL_SS_LENGTH_UNLIMITED.|  
|SQL_DESC_LENGTH|Restituisce la lunghezza effettiva della colonna nel set di risultati. Per le colonne con tipo di dati per valori di grandi dimensioni, il valore restituito è SQL_SS_LENGTH_UNLIMITED.|  
|SQL_DESC_OCTET_LENGTH|Restituisce la lunghezza massima di una colonna con tipo di dati per valori di grandi dimensioni. SQL_SS_LENGTH_UNLIMITED viene utilizzato per indicare dimensioni illimitate.|  
|SQL_DESC_PRECISION|Restituisce il valore SQL_SS_LENGTH_UNLIMITED per colonne con tipo di dati per valori di grandi dimensioni.|  
|SQL_DESC_TYPE|Restituisce SQL_VARCHAR, SQL_WVARCHAR e SQL_VARBINARY per tipi di dati per valori di grandi dimensioni.|  
|SQL_DESC_TYPE_NAME|Restituisce "varchar", "varbinary" e "nvarchar" per tipi di dati per valori di grandi dimensioni.|  
  
 Per tutte le versioni, gli attributi di colonna vengono indicati solo per il primo set di risultati quando più set di risultati vengono generati da un batch preparato di istruzioni SQL.  
  
 Gli attributi di colonna seguenti sono estensioni esposte dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client restituisce tutti i valori di *NumericAttrPtr* parametro. I valori vengono restituiti come SDWORD (signed long) ad eccezione di SQL_CA_SS_COMPUTE_BYLIST, che è un puntatore a una matrice di WORD.  
  
|Identificatore del campo|Valore restituito|  
|----------------------|--------------------|  
|SQL_CA_SS_COLUMN_HIDDEN*|TRUE se la colonna a cui si fa riferimento fa parte di una chiave primaria nascosta creata per supportare un'istruzione Transact-SQL SELECT che contiene la clausola FOR BROWSE.|  
|SQL_CA_SS_COLUMN_ID|Posizione ordinale di una colonna di risultati della clausola COMPUTE all'interno dell'istruzione Transact-SQL SELECT corrente.|  
|SQL_CA_SS_COLUMN_KEY*|TRUE se la colonna a cui si fa riferimento è parte di una chiave primaria per la riga e se l'istruzione Transact-SQL SELECT contiene la clausola FOR BROWSE.|  
|SQL_CA_SS_COLUMN_OP|Numero intero che specifica l'operatore di aggregazione responsabile del valore in una colonna della clausola COMPUTE. Le definizioni dei valori integer sono incluse in sqlncli.h.|  
|SQL_CA_SS_COLUMN_ORDER|Posizione ordinale della colonna all'interno di una clausola ORDER BY di un'istruzione ODBC o Transact-SQL SELECT.|  
|SQL_CA_SS_COLUMN_SIZE|Lunghezza massima, in byte, necessaria per associare un valore di dati recuperato dalla colonna a una variabile SQL_C_BINARY.|  
|SQL_CA_SS_COLUMN_SSTYPE|Tipo di dati nativo dei dati archiviati nella colonna di SQL Server. Le definizioni dei valori dei tipi sono incluse in sqlncli.h.|  
|SQL_CA_SS_COLUMN_UTYPE|Tipo di dati di base del tipo di dati definito dall'utente della colonna di SQL Server. Le definizioni dei valori dei tipi sono incluse in sqlncli.h.|  
|SQL_CA_SS_COLUMN_VARYLEN|TRUE se i dati della colonna possono variare in lunghezza; in caso contrario, FALSE.|  
|SQL_CA_SS_COMPUTE_BYLIST|Puntatore a una matrice di WORD (unsigned short) che specifica le colonne utilizzate nella frase BY di una clausola COMPUTE. Se la clausola COMPUTE non specifica una frase BY, viene restituito un puntatore NULL.<br /><br /> Il primo elemento della matrice contiene il conteggio di colonne dell'elenco BY. I numeri ordinali di colonna sono elementi aggiuntivi.|  
|SQL_CA_SS_COMPUTE_ID|*computeid* di una riga che rappresenta il risultato di una clausola COMPUTE nell'istruzione Transact-SQL SELECT corrente.|  
|SQL_CA_SS_NUM_COMPUTES|Numero di clausole COMPUTE specificate nell'istruzione Transact-SQL SELECT corrente.|  
|SQL_CA_SS_NUM_ORDERS|Numero di colonne specificate in una clausola ORDER BY di un'istruzione ODBC o Transact-SQL SELECT.|  
  
 \*   È disponibile se l'attributo dell'istruzione SQL_SOPT_SS_HIDDEN_COLUMNS è impostato su SQL_HC_ON.  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ha introdotto i campi di descrizione specifici del driver per fornire informazioni aggiuntive per indicare rispettivamente il nome della raccolta XML schema, il nome dello schema e il nome del catalogo. Tali proprietà non richiedono virgolette o un carattere di escape se contengono caratteri non alfanumerici. Nella tabella seguente sono inclusi i nuovi campi di descrizione:  
  
|Nome colonna|Tipo|Description|  
|-----------------|----------|-----------------|  
|SQL_CA_SS_XML_SCHEMACOLLECTION_CATALOG_NAME|CharacterAttributePtr|Nome del catalogo in cui viene definito il nome di una raccolta di XML Schema. Se non è possibile trovare il nome del catalogo, questa variabile contiene una stringa vuota.<br /><br /> Queste informazioni vengono restituite dal campo del record SQL_DESC_SS_XML_SCHEMACOLLECTION_CATALOG_NAME del descrittore delle righe di implementazione, che è un campo di lettura/scrittura.|  
|SQL_CA_SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|CharacterAttributePtr|Nome dello schema in cui viene definito il nome di una raccolta di XML Schema. Se non è possibile trovare il nome dello schema, questa variabile contiene una stringa vuota.<br /><br /> Queste informazioni vengono restituite dal campo del record SQL_DESC_SS_XML_SCHEMACOLLECTION_SCHEMA_NAME del descrittore delle righe di implementazione, che è un campo di lettura/scrittura.|  
|SQL_CA_SS_XML_SCHEMACOLLECTION_NAME|CharacterAttributePtr|Nome di una raccolta di XML Schema. Se non è possibile trovare il nome, questa variabile contiene una stringa vuota.<br /><br /> Queste informazioni vengono restituite dal campo del record SQL_DESC_SS_XML_SCHEMACOLLECTION_NAME del descrittore delle righe di implementazione, che è un campo di lettura/scrittura.|  
  
 In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] sono stati inoltre introdotti nuovi campi di descrizione specifici del driver per fornire informazioni aggiuntive per una colonna con tipo definito dall'utente di un set di risultati o un parametro con tipo definito dall'utente di una stored procedure o di una query con parametri. Tali proprietà non richiedono virgolette o un carattere di escape se contengono caratteri non alfanumerici. Nella tabella seguente sono inclusi i nuovi campi di descrizione:  
  
|Nome colonna|Tipo|Description|  
|-----------------|----------|-----------------|  
|SQL_CA_SS_UDT_CATALOG_NAME|CharacterAttributePtr|Nome del catalogo contenente il tipo definito dall'utente.|  
|SQL_CA_SS_UDT_SCHEMA_NAME|CharacterAttributePtr|Nome dello schema contenente il tipo definito dall'utente.|  
|SQL_CA_SS_UDT_TYPE_NAME|CharacterAttributePtr|Nome del tipo definito dall'utente.|  
|SQL_CA_SS_UDT_ASSEMBLY_TYPE_NAME|CharacterAttributePtr|Nome completo dell'assembly del tipo definito dall'utente.|  
  
 L'identificatore SQL_DESC_TYPE_NAME del campo di descrizione esistente viene utilizzato per indicare il nome del tipo definito dall'utente. Il campo SQL_DESC_TYPE per una colonna con tipo definito dall'utente è SQL_SS_UDT.  
  
## <a name="sqlcolattribute-support-for-enhanced-date-and-time-features"></a>Supporto di SQLColAttribute per le caratteristiche avanzate di data e ora  
 Per i valori restituiti per i tipi data/ora, vedere la sezione "Informazioni restituite nei campi IRD" in [Parameter and Result Metadata](../../relational-databases/native-client-odbc-date-time/metadata-parameter-and-result.md).  
  
 Per altre informazioni, vedere [data e miglioramenti per la fase &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlcolattribute-support-for-large-clr-udts"></a>Supporto di SQLColAttribute per tipi CLR definiti dall'utente di grandi dimensioni  
 **SQLColAttribute** supporta grandi CLR tipi definiti dall'utente (UDT). Per altre informazioni, vedere [Large CLR User-Defined tipi &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlcolattribute-support-for-sparse-columns"></a>Supporto di SQLColAttribute per colonne di tipo sparse  
 SQLColAttribute esegue una query il nuovo campo implementazione riga IRD (descrittore), SQL_CA_SS_IS_COLUMN_SET, per determinare se una colonna è una **column_set** colonna.  
  
 Per altre informazioni, vedere [supporto per colonne di tipo Sparse &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLColAttribute](http://go.microsoft.com/fwlink/?LinkId=59334)   
 [Dettagli di implementazione di API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)  
  
  
