---
title: Utilizzo di tipi definiti dall'utente | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|features
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_DATASOURCEINFO property set
- UDTs [SQL Server Native Client]
- user-defined types [SQL Server], SQL Server Native Client
- SQL Server Native Client OLE DB provider, user-defined types
- DBPROPSET_SQLSERVERPARAMETER property set
- IColumnsRowset interface
- SQLNCLI, user-defined types
- SQL Server Native Client, user-defined types
- data access [SQL Server Native Client], user-defined types
- ISSCommandWithParameters interface
ms.assetid: e15d8169-3517-4323-9c9e-0f5c34aff7df
caps.latest.revision: "45"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8092282c18758860ee76f9e61108aa6db1551bc8
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="using-user-defined-types"></a>Utilizzo dei tipi definiti dall'utente (UDT)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] sono stati introdotti i tipi definiti dall'utente (UDT). Tipi definiti dall'utente estendono il sistema di tipi SQL consentendo di archiviare oggetti e strutture di dati personalizzati in un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database. I tipi definiti dall'utente possono contenere più tipi di dati e possono assumere comportamenti, differenziandoli dai tipi di dati alias tradizionali costituiti da un singolo tipo di dati di sistema [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. I tipi definiti dall'utente vengono definiti utilizzando uno dei linguaggi supportati da .NET Common Language Runtime (CLR) che generano codice verificabile, Sono inclusi Microsoft Visual c#<sup>®</sup> e Visual Basic<sup>®</sup> .NET. I dati vengono esposti come campi e proprietà di una classe o struttura .NET mentre i comportamenti vengono definiti dai metodi della classe o della struttura.  
  
 Un tipo definito dall'utente può essere utilizzato come definizione di colonna di una tabella, come una variabile in un [!INCLUDE[tsql](../../../includes/tsql-md.md)] batch, o come un argomento di un [!INCLUDE[tsql](../../../includes/tsql-md.md)] stored procedure o funzione.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>Provider OLE DB di SQL Server Native Client  
 Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta i tipi definiti dall'utente come tipi binari con le informazioni sui metadati, che consente di gestire i tipi definiti dall'utente come oggetti. Le colonne di tipo definito dall'utente vengono esposte come DBTYPE_UDT e i relativi metadati vengono esposti tramite l'interfaccia OLE DB principale **IColumnRowset**e il nuovo [ISSCommandWithParameters](../../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md) interfaccia.  
  
> [!NOTE]  
>  Il **irowsetfind:: FindNextRow** metodo non funziona con il tipo di dati definito dall'utente. Se il tipo definito dall'utente viene utilizzato come tipo di colonna di ricerca, viene restituito DB_E_BADCOMPAREOP.  
  
### <a name="data-bindings-and-coercions"></a>Associazione dati e coercizioni  
 Nella tabella seguente vengono descritte l'associazione e la coercizione che si verificano quando si utilizzano i tipi di dati elencati con un tipo definito dall'utente [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le colonne di tipo definito dall'utente vengono esposte tramite il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client come DBTYPE_UDT. È possibile ottenere i metadati tramite i set di righe dello schema appropriati in modo da potere gestire i tipi definiti personalizzati come oggetti.  
  
|Tipo di dati|Al server<br /><br /> **UDT**|Al server<br /><br /> **non-UDT**|Dal server<br /><br /> **UDT**|Dal server<br /><br /> **non-UDT**|  
|---------------|---------------------------|--------------------------------|-----------------------------|----------------------------------|  
|DBTYPE_UDT|Supportato<sup>6</sup>|Errore<sup>1</sup>|Supportato<sup>6</sup>|Errore<sup>5</sup>|  
|DBTYPE_BYTES|Supportato<sup>6</sup>|N/A<sup>2</sup>|Supportato<sup>6</sup>|N/A<sup>2</sup>|  
|DBTYPE_WSTR|Supportato<sup>3,6</sup>|N/A<sup>2</sup>|Supportato<sup>4, 6</sup>|N/A<sup>2</sup>|  
|DBTYPE_BSTR|Supportato<sup>3,6</sup>|N/A<sup>2</sup>|Supportato<sup>4</sup>|N/A<sup>2</sup>|  
|DBTYPE_STR|Supportato<sup>3,6</sup>|N/A<sup>2</sup>|Supportato<sup>4, 6</sup>|N/A<sup>2</sup>|  
|DBTYPE_IUNKNOWN|Non supportato|N/A<sup>2</sup>|Non supportato|N/A<sup>2</sup>|  
|DBTYPE_VARIANT (VT_UI1 &#124; VT_ARRAY)|Supportato<sup>6</sup>|N/A<sup>2</sup>|Supportato<sup>4</sup>|N/A<sup>2</sup>|  
|DBTYPE_VARIANT (VT_BSTR)|Supportato<sup>3,6</sup>|N/A<sup>2</sup>|N/D|N/A<sup>2</sup>|  
  
 <sup>1</sup>se un server di tipo diverso da DBTYPE_UDT è specificato con **ICommandWithParameters:: SetParameterInfo** e il tipo di funzione di accesso è DBTYPE_UDT, si verifica un errore quando viene eseguita l'istruzione (DB_E_ERRORSOCCURRED; stato del parametro è DBSTATUS_E_BADACCESSOR). In caso contrario, i dati vengono inviati al server, ma il server restituisce un errore indicando che non è possibile eseguire una conversione implicita dal tipo definito dall'utente al tipo di dati del parametro.  
  
 <sup>2</sup>esula dall'ambito di questo argomento.  
  
 <sup>3</sup> si verifica la conversione di dati da stringa esadecimale in dati binari.  
  
 <sup>4</sup> si verifica la conversione dei dati dai dati binari a stringa esadecimale.  
  
 <sup>5</sup>convalida può verificarsi nella creazione della funzione di accesso o in fase di recupero, l'errore è DB_E_ERRORSOCCURRED, lo stato impostato su DBBINDSTATUS_UNSUPPORTEDCONVERSION dell'associazione.  
  
 <sup>6</sup>può essere utilizzato BY_REF.  
  
 DBTYPE_NULL e DBTYPE_EMPTY possono essere associati per i parametri di input ma non per i parametri di output o per i risultati. Se vengono associati per i parametri di input, lo stato deve essere impostato su DBSTATUS_S_ISNULL o DBSTATUS_S_DEFAULT.  
  
 DBTYPE_UDT può essere convertito anche in DBTYPE_EMPTY e DBTYPE_NULL, ma DBTYPE_NULL e DBTYPE_EMPTY non possono essere convertiti in DBTYPE_UDT. È coerente con DBTYPE_BYTES.  
  
> [!NOTE]  
>  Una nuova interfaccia viene utilizzata per la gestione di tipi definiti dall'utente come parametri, **ISSCommandWithParameters**, che eredita da **ICommandWithParameters**. Le applicazioni devono utilizzare questa interfaccia per impostare almeno SSPROP_PARAM_UDT_NAME del set di proprietà DBPROPSET_SQLSERVERPARAMETER per i parametri UDT. Se questa non operazione viene eseguita, **ICommand:: Execute** restituirà DB_E_ERRORSOCCURRED. Questo set di proprietà e questa interfaccia vengono descritti più avanti in questo argomento.  
  
 Se un tipo definito dall'utente viene inserito in una colonna che non è sufficientemente grande da contenere tutti i relativi dati, **ICommand:: Execute** restituirà S_OK con lo stato DB_E_ERRORSOCCURRED.  
  
 Le conversioni di dati fornite dai servizi principali OLE DB (**IDataConvert**) non sono applicabili a DBTYPE_UDT. Non sono supportate altre associazioni.  
  
### <a name="ole-db-rowset-additions-and-changes"></a>Aggiunte e modifiche ai set di righe OLE DB  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client aggiunge nuovi valori o modifiche a molti dei set di righe dello schema OLE DB principali.  
  
#### <a name="the-procedureparameters-schema-rowset"></a>Set di righe dello schema PROCEDURE_PARAMETERS  
 Al set di righe dello schema PROCEDURE_PARAMETERS sono state effettuate le seguenti aggiunte.  
  
|Nome colonna|Tipo|Description|  
|-----------------|----------|-----------------|  
|SS_UDT_CATALOGNAME|DBTYPE_WSTR|Identificatore del nome in tre parti.|  
|SS_UDT_SCHEMANAME|DBTYPE_WSTR|Identificatore del nome in tre parti.|  
|SS_UDT_NAME|DBTYPE_WSTR|Identificatore del nome in tre parti.|  
|SS_UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Nome completo dell'assembly che include il nome del tipo e l'identificazione dell'assembly necessaria a cui deve fare riferimento CLR.|  
  
#### <a name="the-sqlassemblies-schema-rowset"></a>Set di righe dello schema SQL_ASSEMBLIES  
 Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client espone un nuovo provider dello schema specifico set di righe che descrive i tipi definiti dall'utente registrato. Il server ASSEMBLY può essere specificato come DBTYPE_WSTR, ma non è presente nel set di righe. Se non viene specificato, il set di righe imposterà come valore predefinito il server corrente. Il set di righe dello schema SQL_ASSEMBLIES viene definito nella tabella seguente.  
  
|Nome colonna|Tipo|Description|  
|-----------------|----------|-----------------|  
|ASSEMBLY_CATALOG|DBTYPE_WSTR|Nome del catalogo dell'assembly contenente il tipo.|  
|ASSEMBLY_SCHEMA|DBTYPE_WSTR|Nome dello schema o nome del proprietario dell'assembly contenente il tipo. Sebbene l'ambito degli assembly sia il database e non lo schema, gli assembly dispongono di un proprietario qui rappresentato.|  
|ASSEMBLY_NAME|DBTYPE_WSTR|Nome dell'assembly contenente il tipo.|  
|ASSEMBLY_ID|DBTYPE_UI4|ID oggetto dell'assembly contenente il tipo.|  
|PERMISSION_SET|DBTYPE_WSTR|Valore che indica l'ambito di accesso per l'assembly. I valori includono "SAFE", "EXTERNAL_ACCESS" e "UNSAFE".|  
|ASSEMBLY_BINARY|DBTYPE_BYTES|Rappresentazione binaria dell'assembly.|  
  
#### <a name="the-sqlassemblies-dependencies-schema-rowset"></a>Set di righe dello schema SQL_ASSEMBLIES_ DEPENDENCIES  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB provider espone un nuovo set di righe dello schema specifico del provider che descrive le dipendenze dell'assembly per un server specificato. ASSEMBLY_SERVER può essere specificato dal chiamante come DBTYPE_WSTR, ma non è presente nel set di righe. Se non viene specificato, il set di righe imposterà come valore predefinito il server corrente. Il set di righe dello schema SQL_ASSEMBLY_DEPENDENCIES viene definito nella tabella seguente.  
  
|Nome colonna|Tipo|Description|  
|-----------------|----------|-----------------|  
|ASSEMBLY_CATALOG|DBTYPE_WSTR|Nome del catalogo dell'assembly contenente il tipo.|  
|ASSEMBLY_SCHEMA|DBTYPE_WSTR|Nome dello schema o nome del proprietario dell'assembly contenente il tipo. Sebbene l'ambito degli assembly sia il database e non lo schema, gli assembly dispongono di un proprietario qui rappresentato.|  
|ASSEMBLY_ID|DBTYPE_UI4|ID oggetto dell'assembly.|  
|REFERENCED_ASSEMBLY_ID|DBTYPE_UI4|ID oggetto dell'assembly a cui viene fatto riferimento.|  
  
#### <a name="the-sqlusertypes-schema-rowset"></a>Set di righe dello schema SQL_USER_TYPES  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB provider espone nuovi rowset dello schema, SQL_USER_TYPES, che descrive quando viene aggiunto i tipi definiti dall'utente registrati per un server specificato. UDT_SERVER deve essere specificato dal chiamante come DBTYPE_WSTR, ma non è presente nel set di righe. Il set di righe dello schema SQL_USER_TYPES viene definito nella tabella seguente.  
  
|Nome colonna|Tipo|Description|  
|-----------------|----------|-----------------|  
|UDT_CATALOGNAME|DBTYPE_WSTR|Per le colonne con tipo definito dall'utente questa proprietà è una stringa che specifica il nome del catalogo in cui viene definito il tipo definito dall'utente.|  
|UDT_SCHEMANAME|DBTYPE_WSTR|Per le colonne con tipo definito dall'utente questa proprietà è una stringa che specifica il nome dello schema in cui viene definito il tipo definito dall'utente.|  
|UDT_NAME|DBTYPE_WSTR|Nome dell'assembly contenente la classe UDT.|  
|UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Il nome completo del tipo (AQN) include il nome del tipo preceduto dallo spazio dei nomi se applicabile.|  
  
#### <a name="the-columns-schema-rowset"></a>Set di righe dello schema COLUMNS  
 Le aggiunte al set di righe dello schema COLUMNS includono le colonne seguenti.  
  
|Nome colonna|Tipo|Description|  
|-----------------|----------|-----------------|  
|SS_UDT_CATALOGNAME|DBTYPE_WSTR|Per le colonne con tipo definito dall'utente questa proprietà è una stringa che specifica il nome del catalogo in cui viene definito il tipo definito dall'utente.|  
|SS_UDT_SCHEMANAME|DBTYPE_WSTR|Per le colonne con tipo definito dall'utente questa proprietà è una stringa che specifica il nome dello schema in cui viene definito il tipo definito dall'utente.|  
|SS_UDT_NAME|DBTYPE_WSTR|Nome del tipo definito dall'utente.|  
|SS_UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Il nome completo del tipo (AQN) include il nome del tipo preceduto dallo spazio dei nomi se applicabile.|  
  
### <a name="ole-db-property-set-additions-and-changes"></a>Aggiunte e modifiche ai set di proprietà OLE DB  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client aggiunge nuovi valori o modifiche a molti dei componenti di base proprietà OLE DB set.  
  
#### <a name="the-dbpropsetsqlserverparameter-property-set"></a>Set di proprietà DBPROPSET_SQLSERVERPARAMETER  
 Per supportare i tipi definiti dall'utente tramite OLE DB, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client implementa il nuovo set di proprietà DBPROPSET_SQLSERVERPARAMETER contenente i valori seguenti.  
  
|Nome|Tipo|Description|  
|----------|----------|-----------------|  
|SSPROP_PARAM_UDT_CATALOGNAME|DBTYPE_WSTR|Identificatore del nome in tre parti.<br /><br /> Per i parametri UDT questa proprietà è una stringa che specifica il nome del catalogo in cui viene definito il tipo definito dall'utente.|  
|SSPROP_PARAM_UDT_SCHEMANAME|DBTYPE_WSTR|Identificatore del nome in tre parti.<br /><br /> Per i parametri UDT questa proprietà è una stringa che specifica il nome dello schema in cui viene definito il tipo definito dall'utente.|  
|SSPROP_PARAM_UDT_NAME|DBTYPE_WSTR|Identificatore del nome in tre parti.<br /><br /> Per le colonne con tipo definito dall'utente questa proprietà è una stringa che specifica il nome costituito da una sola parte del tipo definito dall'utente.|  
  
 SSPROP_PARAM_UDT_NAME è obbligatorio. SSPROP_PARAM_UDT_CATALOGNAME e SSPROP_PARAM_UDT_SCHEMANAME sono facoltativi. Se una delle proprietà viene specificata in modo non corretto, verrà restituito DB_E_ERRORSINCOMMAND. Se non vengono specificati SSPROP_PARAM_UDT_CATALOGNAME e SSPROP_PARAM_UDT_SCHEMANAME, il tipo definito dall'utente dovrà essere definito nello stesso database e nello stesso schema della tabella. Se la definizione UDT non è presente nello stesso schema della tabella, ma nello stesso database, sarà necessario specificare SSPROP_PARAM_UDT_SCHEMANAME. Se la definizione UDT è presente in un database diverso, sarà necessario specificare SSPROP_PARAM_UDT_CATALOGNAME e SSPROP_PARAM_UDT_SCHEMANAME.  
  
#### <a name="the-dbpropsetsqlservercolumn-property-set"></a>Set di proprietà DBPROPSET_SQLSERVERCOLUMN  
 Per supportare la creazione di tabelle di **ITableDefinition** interfaccia [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client consente di aggiungere le seguenti tre nuove colonne di proprietà dbpropset_sqlservercolumn.  
  
|Nome|Description|Tipo|Description|  
|----------|-----------------|----------|-----------------|  
|SSPROP_COL_UDT_CATALOGNAME|UDT_CATALOGNAME|VT_BSTR|Per le colonne di tipo DBTYPE_UDT questa proprietà è una stringa che specifica il nome del catalogo in cui viene definito il tipo definito dall'utente.|  
|SSPROP_COL_UDT_SCHEMANAME|UDT_SCHEMANAME|VT_BSTR|Per le colonne di tipo DBTYPE_UDT questa proprietà è una stringa che specifica il nome dello schema in cui viene definito il tipo definito dall'utente.|  
|SSPROP_COL_UDT_NAME|UDT_NAME|VT_BSTR|Per le colonne di tipo DBTYPE_UDT questa proprietà è una stringa che specifica il nome costituito da una singola parte del tipo definito dall'utente. Per gli altri tipi di colonna questa proprietà restituisce una stringa vuota.|  
  
> [!NOTE]  
>  I tipi definiti dall'utente non sono presenti nel set di righe dello schema PROVIDER_TYPES. Tutte le colonne dispongono dell'accesso in lettura e scrittura.  
  
 ADO farà riferimento a queste proprietà tramite la voce corrispondente nella colonna Descrizione.  
  
 SSPROP_COL_UDTNAME è obbligatorio. SSPROP_COL_UDT_CATALOGNAME e SSPROP_COL_UDT_SCHEMANAME sono facoltativi. Se le proprietà vengono specificate in modo errato, **DB_E_ERRORSINCOMMAND** verranno restituiti.  
  
 Se non vengono specificati SSPROP_COL_UDT_CATALOGNAME e SSPROP_COL_UDT_SCHEMANAME, il tipo definito dall'utente dovrà essere definito nello stesso database e nello stesso schema della tabella.  
  
 Se la definizione UDT non è presente nello stesso schema della tabella, ma nello stesso database, sarà necessario specificare SSPROP_COL_UDT_SCHEMANAME.  
  
 Se la definizione UDT è presente in un database diverso, sarà necessario specificare SSPROP_COL_UDT_CATALOGNAME e SSPROP_COL_UDT_SCHEMANAME.  
  
### <a name="ole-db-interface-additions-and-changes"></a>Aggiunte e modifiche alle interfacce OLE DB  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client aggiunge nuovi valori o modifiche a molte delle interfacce OLE DB principali.  
  
#### <a name="the-isscommandwithparameters-interface"></a>Interfaccia ISSCommandWithParameters  
 Per supportare i tipi definiti dall'utente tramite OLE DB, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client implementa una serie di modifiche, inclusa l'aggiunta del **ISSCommandWithParameters** interfaccia. Questa nuova interfaccia eredita dall'interfaccia OLE DB principale **ICommandWithParameters**. Oltre ai tre metodi ereditati da **ICommandWithParameters**; **GetParameterInfo**, **MapParameterNames**, e **SetParameterInfo**; **ISSCommandWithParameters** fornisce il **GetParameterProperties** e **SetParameterProperties** metodi che consentono di gestire i tipi di dati specifici di server.  
  
> [!NOTE]  
>  Il **ISSCommandWithParameters** interfaccia consente inoltre di utilizzare la nuova struttura SSPARAMPROPS struttura.  
  
#### <a name="the-icolumnsrowset-interface"></a>Interfaccia IColumnsRowset  
 Oltre al **ISSCommandWithParameters** interfaccia [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client sono stati aggiunti nuovi valori al set di righe restituito dalla chiamata di **IColumnsRowset:: Getcolumnrowset** (metodo) inclusi i seguenti.  
  
|Nome colonna|Tipo|Description|  
|-----------------|----------|-----------------|  
|DBCOLUMN_SS_UDT_CATALOGNAME|DBTYPE_WSTR|Identificatore del nome di catalogo del tipo definito dall'utente.|  
|DBCOLUMN_SS_UDT_SCHEMANAME|DBTYPE_WSTR|Identificatore del nome dello schema del tipo definito dall'utente.|  
|DBCOLUMN_SS_UDT_NAME|DBTYPE_WSTR|Identificatore del nome del tipo definito dall'utente.|  
|DBCOLUMN_SS_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Nome completo dell'assembly che include il nome del tipo e l'identificazione dell'assembly necessaria a cui deve fare riferimento CLR.|  
  
 È possibile differenziare una colonna con tipo definito dall'utente del server dagli altri tipi binari quando DBCOLUMN_TYPE è impostato su DBTYPE_UDT analizzando i metadati UDT aggiunti sopra specificati. Se tali dati sono parzialmente completi, il tipo di server sarà un tipo definito dall'utente. Per i tipi di server non UDT queste colonne vengono sempre restituite come NULL.  
  
## <a name="sql-server-native-client-odbc-driver"></a>Driver ODBC di SQL Server Native Client  
 È state apportate numerose modifiche nel [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client per supportare i tipi definiti dall'utente. Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mappe driver ODBC di Native Client il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identificatore di tipo definito dall'utente ai dati SQL specifiche del driver SQL_SS_UDT. Le colonne con tipo definito dall'utente vengono rilevate come SQL_SS_UDT. Se si esegue il mapping una colonna di tipo definito dall'utente in modo esplicito a un altro tipo in un'istruzione SQL utilizzando il **ToString** o **ToXMLString** metodi del tipo in questione o tramite il **CAST/CONVERT** (funzione), il tipo della colonna nel risultato set indica il tipo effettivo in che della colonna è stata convertita  
  
### <a name="sqlcolattribute-sqldescribeparam-sqlgetdescfield"></a>SQLColAttribute, SQLDescribeParam, SQLGetDescField  
 Sono stati aggiunti quattro nuovi campi di descrizione specifici del driver per fornire ulteriori informazioni per una colonna di tipo definito dall'utente di un set di risultati o un parametro di tipo definito dall'utente di stored procedure/query con parametri, deve essere recuperato tramite il [SQLColAttribute](../../../relational-databases/native-client-odbc-api/sqlcolattribute.md), [SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md), e [SQLGetDescField](../../../relational-databases/native-client-odbc-api/sqlgetdescfield.md) funzioni.  
  
 I quattro nuovi campi di descrizione aggiunti sono SQL_CA_SS_UDT_CATALOG_NAME, SQL_CA_SS_UDT_SCHEMA_NAME, SQL_CA_SS_UDT_TYPE_NAME e SQL_CA_SS_UDT_ASSEMBLY_TYPE_NAME.  
  
### <a name="sqlcolumns-sqlprocedurecolumns"></a>SQLColumns, SQLProcedureColumns  
 Inoltre, in cui vengono aggiunti tre nuove colonne specifiche del driver per il set di risultati restituito dal [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md) e [SQLProcedureColumns](../../../relational-databases/native-client-odbc-api/sqlprocedurecolumns.md) funzioni per fornire ulteriori informazioni su un risultato di tipo definito dall'utente set di colonne o un parametro di tipo definito dall'utente. Queste tre nuove colonne sono SS_UDT_CATALOG_NAME, SS_UDT_SCHEMA_NAME e SS_UDT_ASSEMBLY_TYPE_NAME.  
  
### <a name="supported-conversions"></a>Conversioni supportate  
 Quando si esegue la conversione dai tipi di dati SQL ai tipi di dati C, SQL_C_WCHAR, SQL_C_BINARY e SQL_C_CHAR possono essere convertiti tutti in SQL_SS_UDT. Tenere tuttavia presente che i dati binari vengono convertiti in una stringa esadecimale durante la conversione dai tipi di dati SQL SQL_C_WCHAR e SQL_C_CHAR.  
  
 Quando si esegue la conversione dai tipi di dati C ai tipi di dati SQL, SQL_C_WCHAR, SQL_C_BINARY e SQL_C_CHAR possono essere convertiti tutti in SQL_SS_UDT. Tenere tuttavia presente che i dati binari vengono convertiti in una stringa esadecimale durante la conversione dai tipi di dati SQL SQL_C_WCHAR e SQL_C_CHAR.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [OLE DB ISSCommandWithParameters &#40; &#41;](../../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
