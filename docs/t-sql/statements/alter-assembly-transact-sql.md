---
title: ALTER ASSEMBLY (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 04/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_ASSEMBLY_TSQL
- ALTER ASSEMBLY
dev_langs:
- TSQL
helpviewer_keywords:
- assemblies [CLR integration], modifying
- refreshing assemblies
- assemblies [CLR integration], versioning
- assemblies [CLR integration], adding files
- modifying assemblies
- adding files
- ALTER ASSEMBLY statement
ms.assetid: 87bca678-4e79-40e1-bb8b-bd5ed8f34853
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 8b8918d653d6d9ff5f26588ad1626bfc62e3679d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="alter-assembly-transact-sql"></a>ALTER ASSEMBLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica un assembly mediante la modifica delle proprietà di catalogo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di un assembly. Istruzione ALTER ASSEMBLY esegue un aggiornamento per la copia più recente del [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] moduli che includono la relativa implementazione e aggiunge o rimuove i file associati. Gli assembly vengono creati utilizzando [CREATE ASSEMBLY](../../t-sql/statements/create-assembly-transact-sql.md).  

>  [!WARNING]
>  CLR usa la Sicurezza dall'accesso di codice (CAS, Code Access Security) in .NET Framework, non più supportata come limite di sicurezza. Un assembly CLR creato con `PERMISSION_SET = SAFE` potrebbe essere in grado di accedere alle risorse di sistema esterne, chiamare codice non gestito e acquisire privilegi sysadmin. A partire da [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)], viene introdotta un'opzione `sp_configure` denominata `clr strict security` per migliorare la sicurezza degli assembly CLR. `clr strict security` è abilitata per impostazione predefinita e considera gli assembly CLR `SAFE` e `UNSAFE` come se fossero contrassegnati `EXTERNAL_ACCESS`. È possibile disabilitare l'opzione `clr strict security` per la compatibilità con le versioni precedenti, ma questa operazione è sconsigliata. Microsoft consiglia che tutti gli assembly siano firmati con un certificato o una chiave asimmetrica con un account di accesso corrispondente che disponga dell'autorizzazione `UNSAFE ASSEMBLY` nel database master. Per altre informazioni, vedere [CLR strict security](../../database-engine/configure-windows/clr-strict-security.md).  

 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
ALTER ASSEMBLY assembly_name  
    [ FROM <client_assembly_specifier> | <assembly_bits> ]  
    [ WITH <assembly_option> [ ,...n ] ]  
    [ DROP FILE { file_name [ ,...n ] | ALL } ]  
    [ ADD FILE FROM   
    {   
        client_file_specifier [ AS file_name ]   
      | file_bits AS file_name   
    } [,...n ]   
    ] [ ; ]  
<client_assembly_specifier> :: =  
    '\\computer_name\share-name\[path\]manifest_file_name'  
  | '[local_path\]manifest_file_name'  
  
<assembly_bits> :: =  
    { varbinary_literal | varbinary_expression }  
  
<assembly_option> :: =  
    PERMISSION_SET = { SAFE | EXTERNAL_ACCESS | UNSAFE }   
  | VISIBILITY = { ON | OFF }  
  | UNCHECKED DATA  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *assembly_name*  
 Nome dell'assembly da modificare. *nome_assembly* deve esistere nel database.  
  
 DA \<client_assembly_specifier > | \<assembly_bits >  
 Aggiorna un assembly in base alla copia più recente dei moduli [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] contenenti la relativa implementazione. È possibile usare questa opzione solo se non esistono file associati all'assembly specificato.  
  
 \<client_assembly_specifier > specifica il percorso di rete o locale in cui si trova l'assembly da aggiornare. Il percorso di rete include il nome del computer e della condivisione, nonché un percorso all'interno di quest'ultima. *manifest_file_name* specifica il nome del file che contiene il manifesto dell'assembly.  
  
 \<assembly_bits > rappresenta il valore binario per l'assembly.  
  
 È necessario usare istruzioni ALTER ASSEMBLY separate per ogni assembly dipendente che inoltre richiede un aggiornamento.  
  
 PERMISSION_SET = { SAFE | EXTERNAL_ACCESS | UNSAFE }   
>  [!IMPORTANT]  
>  Il `PERMISSION_SET` opzione è interessato dal `clr strict security` opzione, descritto nel messaggio di avviso di apertura. Quando `clr strict security` è abilitata, tutti gli assembly vengono considerati come `UNSAFE`.  
 Specifica la proprietà del set di autorizzazioni per l'accesso al codice di [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] per l'assembly. Per ulteriori informazioni su questa proprietà, vedere [CREATE ASSEMBLY &#40; Transact-SQL &#41; ](../../t-sql/statements/create-assembly-transact-sql.md).  
  
> [!NOTE]  
>  Le opzioni EXTERNAL_ACCESS e UNSAFE non sono disponibili in un database indipendente.  
  
 VISIBILITY = { ON | OFF }  
 Specifica se l'assembly risulta visibile per la creazione in base a esso di funzioni CLR (Common Language Runtime), stored procedure, trigger, tipi definiti dall'utente e funzioni di aggregazione definite dall'utente. Se l'opzione è impostata su OFF, l'assembly verrà chiamato solo da altri assembly. Se esistono oggetti di database CLR precedentemente creati in base all'assembly, non è possibile modificare la visibilità dell'assembly. Tutti gli assembly a cui fa riferimento *nome_assembly* vengono caricati come non visibili per impostazione predefinita.  
  
 UNCHECKED DATA  
 Per impostazione predefinita, ALTER ASSEMBLY ha esito negativo se deve verificare la consistenza delle singole righe di tabella. Questa opzione consente di posticipare le verifiche a un momento successivo tramite DBCC CHECKTABLE. Se viene specificata, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegue l'istruzione ALTER ASSEMBLY anche se nel database sono presenti tabelle contenenti quanto segue:  
  
-   Colonne calcolate persistenti che direttamente o indirettamente fanno riferimento a metodi nell'assembly tramite funzioni o metodi [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   Vincoli CHECK che direttamente o indirettamente fanno riferimento a metodi nell'assembly.  
  
-   Colonne di un tipo definito dall'utente CLR che dipendono l'assembly e il tipo implementa un **UserDefined** (non -**nativo**) formato di serializzazione.  
  
-   Colonne di tipo CLR definito dall'utente che fanno riferimento a viste create tramite WITH SCHEMABINDING.  
  
 Se sono presenti vincoli CHECK, essi vengono disabilitati e contrassegnati come non attendibili. Le tabelle contenenti colonne che dipendono dall'assembly vengono contrassegnate come contenenti dati non controllati finché tali tabelle non vengono verificate in modo esplicito.  
  
 Solo i membri del **db_owner** e **db_ddlowner** ruoli predefiniti del database è possono specificare questa opzione.  
  
 Richiede il **ALTER ANY SCHEMA** dell'autorizzazione per specificare questa opzione.  
  
 Per ulteriori informazioni, vedere [gli assembly che implementa](../../relational-databases/clr-integration/assemblies-implementing.md).  
  
 [DROP FILE { *file_name*[**, *... n*] | ALL}]  
 Rimuove il nome file associato all'assembly oppure tutti i file associati all'assembly dal database. Se specificata assieme all'opzione ADD FILE (descritto di seguito), l'opzione DROP FILE viene eseguita per prima. Ciò consente di sostituire un file con lo stesso nome.  
  
> [!NOTE]  
>  Questa opzione non è disponibile in un database indipendente.  
  
 [ADD FILE FROM { *client_file_specifier* [AS *file_name*] | *file_bits*AS *file_name*}  
 Carica un file da associare all'assembly, ad esempio di codice sorgente, file di debug o altre informazioni correlate, nel server e resi visibile nel **assembly_files** vista del catalogo. *client_file_specifier* specifica la posizione da cui caricare il file. *file_bits* consente invece di specificare l'elenco di valori binari che compongono il file. *file_name* specifica il nome con cui il file deve essere archiviato nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *file_name* deve essere specificato se *file_bits* è specificato ma è facoltativo se *client_file_specifier* specificato. Se *file_name* non viene specificato, la parte file_name di *client_file_specifier* viene utilizzato come *file_name*.  
  
> [!NOTE]  
>  Questa opzione non è disponibile in un database indipendente.  
  
## <a name="remarks"></a>Osservazioni  
 ALTER ASSEMBLY non interferisce con le sessioni in esecuzione che eseguono codice nell'assembly in fase di modifica. Le sessioni correnti completano l'esecuzione tramite l'utilizzo dei bit non modificati dell'assembly.  
  
 Se si specifica la clausola FROM, ALTER ASSEMBLY aggiorna l'assembly in base alle copie più recenti dei moduli specificati. Poiché nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potrebbero essere presenti funzioni CLR, stored procedure, trigger, tipi di dati e funzioni di aggregazione definite dall'utente già definiti in base all'assembly, l'istruzione ALTER ASSEMBLY riassocia questi elementi all'implementazione più recente dell'assembly. Per eseguire questa riassociazione, è necessario che i metodi che eseguono il mapping alle funzioni CLR, alle stored procedure e ai trigger esistano nell'assembly modificati con le stesse firme. Le classi che implementano i tipi CLR definiti dall'utente e le funzioni di aggregazione definite dall'utente devono continuare a soddisfare i requisiti richiesti per i tipi e le funzioni di aggregazione definiti dall'utente.  
  
> [!CAUTION]  
>  Se non è specificata la clausola WITH UNCHECKED DATA, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tenta di impedire l'esecuzione dell'istruzione ALTER ASSEMBLY nel caso in cui la nuova versione dell'assembly modifichi i dati esistenti in tabelle, indici o altre posizioni persistenti. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non garantisce tuttavia la consistenza di colonne calcolate, indici, viste indicizzate o espressioni con i tipi e le routine sottostanti in caso di aggiornamento dell'assembly CLR. Quando si esegue ALTER ASSEMBLY è pertanto necessario verificare che non siano presenti discrepanze tra il risultato di una determinata espressione e i valori basati su tale espressione archiviati nell'assembly.  
  
 ALTER ASSEMBLY modifica la versione dell'assembly. La lingua e il token di chiave pubblica dell'assembly restano invariati.  
  
 L'istruzione ALTER ASSEMBLY non può essere usata per modificare:  
  
-   Le firme di funzioni CLR, funzioni di aggregazione, stored procedure e trigger in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che fa riferimento all'assembly. L'istruzione ALTER ASSEMBLY ha esito negativo se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è in grado di riassociare gli oggetti di database di [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con la nuova versione dell'assembly.  
  
-   Le firme dei metodi nell'assembly chiamati da altri assembly.  
  
-   L'elenco di assembly che dipendono dall'assembly, a cui fa riferimento il **DependentList** proprietà dell'assembly.  
  
-   L'indicizzabilità di un metodo a meno che non esista alcun indice o colonna calcolata persistente che dipende da tale metodo, direttamente o indirettamente.  
  
-   Il **FillRow** attributo nome del metodo per le funzioni con valori di tabella CLR.  
  
-   Il **Accumulate** e **Terminate** firma del metodo per le aggregazioni definite dall'utente.  
  
-   Gli assembly di sistema.  
  
-   La proprietà degli assembly. Utilizzare [ALTER AUTHORIZATION &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-authorization-transact-sql.md) invece.  
  
 Per gli assembly che implementano tipi definiti dall'utente, inoltre, è possibile usare ALTER ASSEMBLY per apportare soltanto le modifiche seguenti:  
  
-   Modifica di metodi pubblici della classe di un tipo definito dall'utente, a condizione che non vengano modificati attributi o firme.  
  
-   Aggiunta di nuovi metodi pubblici.  
  
-   Modifica di metodi privati.  
  
 I campi contenuti in un tipo definito dall'utente con serializzazione nativa, inclusi i membri dei dati o le classi base, non possono essere modificati mediante ALTER ASSEMBLY. Tutte le altre modifiche non sono supportate.  
  
 Se si omette ADD FILE FROM, ALTER ASSEMBLY elimina i file associati all'assembly.  
  
 Se l'istruzione ALTER ASSEMBLY viene eseguita senza la clausola di dati UNCHECKED, vengono eseguite le verifiche per controllare che la nuova versione dell'assembly non abbia un impatto negativo sui dati delle tabelle. Le prestazioni potrebbero dipendere dalla quantità di dati che devono essere sottoposti a verifica.  
  
## <a name="permissions"></a>Autorizzazioni  
 È necessaria l'autorizzazione ALTER per l'assembly. È inoltre necessario disporre dei requisiti seguenti:  
  
-   Per modificare un assembly la cui autorizzazione esistente è EXTERNAL_ACCESS set, è necessario**EXTERNAL ACCESS ASSEMBLY**autorizzazione nel server.  
  
-   Per modificare un assembly la cui autorizzazione esistente è UNSAFE richiede **ASSEMBLY UNSAFE** autorizzazione nel server.  
  
-   Per modificare il set di autorizzazioni di un assembly e impostarlo su EXTERNAL_ACCESS, è necessario**EXTERNAL ACCESS ASSEMBLY** autorizzazione nel server.  
  
-   Per modificare il set di autorizzazioni di un assembly e impostarlo su UNSAFE, è necessario **ASSEMBLY UNSAFE** autorizzazione nel server.  
  
-   È necessario specificare WITH UNCHECKED DATA, **ALTER ANY SCHEMA** autorizzazione.  


### <a name="permissions-with-clr-strict-security"></a>Autorizzazioni di sicurezza rigidi CLR    
Le seguenti autorizzazioni necessarie per modificare un assembly CLR quando `CLR strict security` è abilitato:

- L'utente deve disporre dell'autorizzazione `ALTER ASSEMBLY`  
- Inoltre, una delle condizioni seguenti deve essere rispettata:  
  - L'assembly è firmato con un certificato o una chiave asimmetrica con un account di accesso corrispondente con l'autorizzazione `UNSAFE ASSEMBLY` nel server. È consigliabile firmare l'assembly.  
  - La proprietà `TRUSTWORTHY` del database è impostata su `ON` e il database è di proprietà di un accesso che dispone dell'autorizzazione `UNSAFE ASSEMBLY` nel server. Questa opzione non è consigliata.  
  
  
 Per ulteriori informazioni sui set di autorizzazioni di assembly, vedere [progettazione assembly](../../relational-databases/clr-integration/assemblies-designing.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-refreshing-an-assembly"></a>A. Aggiornamento di un assembly  
 Nell'esempio seguente l'assembly `ComplexNumber` viene aggiornato in base alla copia più recente dei moduli [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] contenenti la relativa implementazione.  
  
> [!NOTE]  
>  Per creare l'assembly `ComplexNumber`, eseguire gli script di esempio UserDefinedDataType. Per ulteriori informazioni, vedere [tipo definito dall'utente](http://msdn.microsoft.com/library/a9b75f36-d7f5-47f7-94d6-b4448c6a2191).  
  
 ```
 ALTER ASSEMBLY ComplexNumber 
 FROM 'C:\Program Files\Microsoft SQL Server\130\Tools\Samples\1033\Engine\Programmability\CLR\UserDefinedDataType\CS\ComplexNumber\obj\Debug\ComplexNumber.dll' 
  ```
### <a name="b-adding-a-file-to-associate-with-an-assembly"></a>B. Aggiunta di un file da associare a un assembly  
 Nell'esempio seguente viene caricato il file del codice sorgente `Class1.cs` da associare all'assembly `MyClass`. In questo esempio si presuppone che l'assembly `MyClass` sia già stato creato nel database.  
  
```  
ALTER ASSEMBLY MyClass   
ADD FILE FROM 'C:\MyClassProject\Class1.cs';  
```  
  
### <a name="c-changing-the-permissions-of-an-assembly"></a>C. Modifica delle autorizzazioni di un assembly  
 Nell'esempio seguente il set di autorizzazioni dell'assembly `ComplexNumber` viene modificato da SAFE a `EXTERNAL ACCESS`.  
  
```  
ALTER ASSEMBLY ComplexNumber WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/create-assembly-transact-sql.md)   
 [DROP ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-assembly-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
