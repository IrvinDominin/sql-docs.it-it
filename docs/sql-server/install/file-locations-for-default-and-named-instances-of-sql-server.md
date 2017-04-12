---
title: "Percorsi dei file per le istanze predefinite e denominate di SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 463c570e-9f75-4653-b3b8-4d61753b0013
caps.latest.revision: 16
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 16
---
# Percorsi dei file per le istanze predefinite e denominate di SQL Server
  Un'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è costituita da una o più istanze separate. Un'istanza, predefinita o denominata, contiene un proprio set di file di programma e di dati, oltre a un set di file comuni condivisi tra tutte le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] presenti nel computer.  
  
 Per un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che include [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]e [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], ogni componente ha un set completo di file di dati, file eseguibili e file comuni condivisi da tutti i componenti.  
  
 Per isolare i percorsi di installazione di ogni componente, vengono generati ID istanza univoci per ogni componente all'interno di una determinata istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Non è possibile installare i file di programma e i file di dati in un'unità disco rimovibile, in un file system che utilizza la compressione, in una directory in cui sono presenti file di sistema o in unità condivise in un'istanza del cluster di failover.  
>  
>  Potrebbe essere necessario configurare software di scansione, ad esempio applicazioni antivirus e antispyware, per escludere le cartelle e i tipi di file di SQL Server. Per altre informazioni, leggere l’articolo del supporto tecnico relativo al [software antivirus nei computer che eseguono SQL Server](https://support.microsoft.com/kb/309422).
> 
>  I database di sistema (master, model, MSDB e tempdb) e i database utente del [!INCLUDE[ssDE](../../includes/ssde-md.md)] possono essere installati con il file server SMB (Server Message Block) come opzione di archiviazione. Questa condizione è valida per le installazioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autonome e per le installazioni del cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [Install SQL Server with SMB Fileshare as a Storage Option](../../database-engine/install-windows/install-sql-server-with-smb-fileshare-as-a-storage-option.md).  
>   
>  Non eliminare alcuna delle directory seguenti o il relativo contenuto: Binn, Data, Ftdata, HTML o 1033. Se necessario, è possibile eliminare altre directory; potrebbe non essere tuttavia possibile recuperare funzionalità o dati non più disponibili se prima non si disinstalla e quindi si reinstalla [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Non eliminare o modificare nessuno dei file htm disponibile nella directory HTML. Questi file sono necessari per il corretto funzionamento degli strumenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## File condivisi per tutte le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 I file comuni usati da tutte le istanze presenti in un singolo computer vengono installati nella cartella [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)], dove \<*unità*> corrisponde alla lettera dell'unità in cui vengono installati i componenti. L'unità C è in genere quella predefinita.  
  
## Percorsi dei file e mapping del Registro di sistema  
 Durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , viene generato un ID istanza per ogni componente. I componenti server di questa versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono il [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]e [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 L'ID dell'istanza predefinita viene creato utilizzando il formato seguente:  
  
-   MSSQL per [!INCLUDE[ssDE](../../includes/ssde-md.md)], seguito dal numero di versione principale, da un carattere di sottolineatura e, se possibile, dalla versione secondaria e quindi da un punto, seguiti dal nome di istanza.  
  
-   MSAS per [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], seguito dal numero di versione principale, da un carattere di sottolineatura e, se possibile, dalla versione secondaria e quindi da un punto, seguiti dal nome di istanza.  
  
-   MSRS per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], seguito dal numero di versione principale, da un carattere di sottolineatura e, se possibile, dalla versione secondaria e quindi da un punto, seguiti dal nome di istanza.  
  
 Di seguito vengono indicati alcuni esempi di ID delle istanze predefinite utilizzati in questa versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   MSSQL13.MSSQLSERVER per un'istanza predefinita di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   MSAS13.MSSQLSERVER per un'istanza predefinita di [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)].  
  
-   MSSQL13.MyInstance per un'istanza denominata di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] il cui nome è "MyInstance".  
  
 Di seguito viene indicata la struttura di directory per un'istanza denominata di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] che include [!INCLUDE[ssDE](../../includes/ssde-md.md)] e [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], denominata "Istanza" e installata nelle directory predefinite:  
  
-   C:\Programmi\Microsoft SQL Server\MSSQL13.MyInstance\  
  
-   C:\Programmi\Microsoft SQL Server\MSAS13.MyInstance\  
  
 È possibile specificare qualsiasi valore per l'ID istanza, evitando tuttavia caratteri speciali e parole chiave riservate.  
  
 È possibile specificare l'ID di un'istanza non predefinita durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se l'utente sceglie di modificare la directory di installazione predefinita, viene usato un \<percorso personalizzato>\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anziché \<Programmi>\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si noti che gli ID delle istanze che iniziano con un carattere di sottolineatura (_) o che contengono il simbolo cancelletto (#) o il segno di dollaro ($) non sono supportati.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e i componenti client non sono specifici dell'istanza e non dispongono pertanto di un ID istanza assegnato. Per impostazione predefinita, i componenti non specifici dell'istanza vengono installati in un'unica directory: [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]. Se si modifica il percorso di installazione di un componente condiviso, la modifica sarà valida anche per tutti gli altri componenti condivisi. Nelle successive installazioni i componenti non specifici dell'istanza verranno installati nella stessa directory dell'installazione originale.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è l'unico componente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che supporta la ridenominazione delle istanze in seguito all'installazione. Se un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] viene rinominata, l'ID istanza non cambierà di conseguenza. Al termine della ridenominazione dell'istanza, le directory e le chiavi del Registro di sistema continueranno a utilizzare l'ID istanza creato durante l'installazione.  
  
 L'hive del Registro di sistema viene creato in HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\<*Instance_ID*> per i componenti specifici dell'istanza. Ad esempio,  
  
-   HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.MyInstance  
  
-   HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSAS13.MyInstance  
  
-   HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSRS13.MyInstance  
  
 Nel Registro di sistema viene inoltre gestito un mapping degli ID istanza ai nomi delle istanze. Il mapping degli ID istanza in base ai nomi delle istanze è gestito nel modo seguente:  
  
-   [HKEY_LOCAL_MACHINE\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Instance Names\SQL] "InstanceName"="MSSQL13"  
  
-   [HKEY_LOCAL_MACHINE\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Instance Names\OLAP] "InstanceName"="MSAS13"  
  
-   [HKEY_LOCAL_MACHINE\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Instance Names\RS] "InstanceName"="MSRS13"  
  
## Specifica dei percorsi dei file  
 Durante l'installazione è possibile modificare il percorso di installazione delle funzionalità seguenti:  
  
 Durante la procedura di installazione viene visualizzato il percorso di installazione delle caratteristiche con una cartella di destinazione configurabile dall'utente:  
  
|Componente|Percorso predefinito|Percorso configurabile o fisso|  
|---------------|------------------|--------------------------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] componenti server|\Programmi\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.\<InstanceID>\|Configurabile|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] file di dati|\Programmi\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.\<InstanceID>\|Configurabile|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server|\Programmi\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSAS13.\<InstanceID>\|Configurabile|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] file di dati|\Programmi\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSAS13.\<InstanceID>\|Configurabile|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] server di report|\Programmi\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSRS13.\<InstanceID>\Reporting Services\ReportServer\Bin\|Configurabile|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Gestione report|\Programmi\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSRS13.\<InstanceID>\Reporting Services\ReportManager\|Percorso fisso|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|\<Directory di installazione>\130\DTS\|Configurabile*|  
|Componenti client (ad eccezione di bcp.exe e sqlcmd.exe)|\<Directory di installazione>\130\Tools\|Configurabile*|  
|Componenti client (bcp.exe e sqlcmd.exe)|\<Directory di installazione>\Client SDK\ODBC\110\Tools\Binn|Percorso fisso|  
|Oggetti di replica e oggetti COM sul lato server|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]COM\\**|Percorso fisso|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] DLL del componente per il motore di run-time e il motore della pipeline Data Transformation Services e l'utilità della riga di comando **dtexec**|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]DTS\Binn|Percorso fisso|  
|DLL che forniscono supporto per connessioni gestite di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]DTS\Connections|Percorso fisso|  
|DLL per ogni tipo di enumeratore supportato da [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]DTS\ForEachEnumerators|Percorso fisso|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, provider WMI|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]Shared\|Percorso fisso|  
|Componenti condivisi tra tutte le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]Shared\|Percorso fisso|  
  
 **\*\* Nota di sicurezza \*\*** Assicurarsi che la cartella \Programmi\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\ sia protetta con autorizzazioni limitate.  
  
 L'unità predefinita per i percorsi dei file è *systemdrive*, che in genere corrisponde a C. I percorsi di installazione per le funzionalità figlio sono determinati dal percorso di installazione della funzionalità padre.  
  
 *Un singolo percorso di installazione viene condiviso tra [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e i componenti client. La modifica del percorso di installazione per un componente si applica quindi a tutti i componenti. Nel caso di installazioni successive i componenti vengono installati nello stesso percorso dell'installazione iniziale.  
  
 **Questa directory viene usata da tutte le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] presenti in un computer. Se si applica un aggiornamento a una delle istanze nel computer, le modifiche apportate ai file inclusi in questa cartella interesseranno tutte le istanze presenti nel computer. Quando si aggiungono funzionalità a un'installazione esistente, non è possibile modificare il percorso di una caratteristica installata in precedenza, né specificare il percorso di una nuova caratteristica. È necessario installare le caratteristiche aggiuntive nelle directory già stabilite durante l'installazione iniziale oppure disinstallare e reinstallare il prodotto.  
  
> [!NOTE]  
>  Per le configurazioni cluster, è necessario selezionare un'unità locale che sia disponibile per ogni nodo del cluster.  
  
 Se durante l'installazione si specifica un percorso di installazione per i componenti server o i file di dati, oltre al percorso specificato per i file di dati e di programma, verrà utilizzato l'ID istanza. L'ID istanza non viene utilizzato per gli strumenti e altri file condivisi, né per i file di dati e di programma di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], ma solo per il repository di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Se si imposta un percorso di installazione per la caratteristica [!INCLUDE[ssDE](../../includes/ssde-md.md)], nell'istallazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tale percorso verrà utilizzato come directory radice di tutte le cartelle specifiche dell'istanza per l'installazione, inclusi i file di dati SQL. In questo caso, se si imposta la radice su "C:\Programmi\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.\<InstanceName>\MSSQL\\", le directory specifiche dell'istanza vengono aggiunte alla fine del percorso.  
  
 Se si utilizza la funzionalità di aggiornamento USESYSDB nell'Installazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (modalità interfaccia utente del programma di installazione), è probabile che si verifichino le condizioni per un'installazione del prodotto in una struttura di cartelle ricorsiva, Ad esempio, \<*SQLProgramFiles*>\MSSQL13\MSSQL\MSSQL10_50\MSSQL\Data\\. Per utilizzare la funzionalità USESYSDB, impostare invece un percorso di installazione per la funzionalità dei file di dati SQL anziché per la funzionalità [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
> [!NOTE]  
>  I file di dati si trovano in genere in una directory figlio denominata Data. Ad esempio, specificare C:\Programmi\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.\<InstanceName>\ per indicare il percorso radice della directory dei dati dei database di sistema durante l'aggiornamento quando i file di dati si trovano in C:\Programmi\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.\<InstanceName>\MSSQL\Data.  
  
## Vedere anche  
 [Configurazione Motore di database - Directory dati](../Topic/Database%20Engine%20Configuration%20-%20Data%20Directories.md)   
 [Configurazione di Analysis Services - Directory dati](../Topic/Analysis%20Services%20Configuration%20-%20Data%20Directories.md)  
  
  