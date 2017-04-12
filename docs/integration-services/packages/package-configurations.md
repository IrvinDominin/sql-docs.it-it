---
title: "Configurazioni di pacchetto | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sintassi di configurazione pacchetti [Integration Services]"
  - "pacchetti di SQL Server Integration Services, configurazioni"
  - "pacchetti SSIS, configurazioni"
  - "XML [Integration Services]"
  - "pacchetti di Integration Services, configurazioni"
  - "sintassi di configurazione [Integration Services]"
  - "configurazioni indirette [Integration Services]"
  - "configurazioni [Integration Services]"
  - "configurazioni dirette [Integration Services]"
  - "pacchetti [Integration Services], configurazioni"
ms.assetid: d20e0311-1fc9-4ddc-a381-6d127cf11b69
caps.latest.revision: 49
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 49
---
# Configurazioni di pacchetto
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dispone di configurazioni di pacchetto che è possibile usare per aggiornare i valori delle proprietà in fase di esecuzione.  
  
> **NOTA:** le configurazioni sono disponibili per il modello di distribuzione del pacchetto. I parametri vengono utilizzati al posto delle configurazioni per il modello di distribuzione del progetto. Con il modello di distribuzione del progetto è possibile distribuire i progetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] al server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Per altre informazioni sui modelli di distribuzione, vedere [Distribuzione di progetti e pacchetti](https://msdn.microsoft.com/library/hh213290.aspx).  
  
 Una configurazione è una coppia proprietà/valore che viene aggiunta a un pacchetto completo. In genere, si crea un pacchetto, si impostano le proprietà per gli oggetti di pacchetto durante lo sviluppo del pacchetto e quindi si aggiunge la configurazione al pacchetto. Quando il pacchetto viene eseguito, ottiene i nuovi valori della proprietà dalla configurazione. Utilizzando ad esempio una configurazione, è possibile modificare la stringa di connessione di una gestione connessione o aggiornare il valore di una variabile.  
  
 Le configurazioni di pacchetto offrono i vantaggi seguenti:  
  
-   Le configurazioni semplificano lo spostamento di pacchetti dall'ambiente di sviluppo all'ambiente di produzione. Tramite una configurazione è ad esempio possibile aggiornare il percorso di un file di origine o modificare il nome di un database o di un server.  
  
-   Le configurazioni risultano utili per la distribuzione di pacchetti in più server diversi. La configurazione di ogni pacchetto distribuito può ad esempio includere una variabile che specifica un diverso valore di spazio su disco. Se lo spazio su disco disponibile non soddisfa tale valore, il pacchetto non verrà eseguito.  
  
-   Le configurazioni rendono i pacchetti più flessibili. Una configurazione, ad esempio, può aggiornare il valore di una variabile utilizzata in un'espressione di proprietà.  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] supporta diversi metodi di archiviazione delle configurazioni di pacchetto, ad esempio file XML, tabelle di un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e variabili di ambiente e di pacchetto.  
  
 Ogni configurazione corrisponde a una coppia proprietà/valore. Il file di configurazione XML e i tipi di configurazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possono includere più configurazioni.  
  
 Le configurazioni vengono incluse quando si crea un'utilità di distribuzione per l'installazione di pacchetti. Quando si installano i pacchetti, le configurazioni possono venire aggiornate in un passaggio dell'installazione.  
  
## Informazioni sull'applicazione delle configurazioni dei pacchetti in fase di esecuzione  
 Quando si usa l'utilità del prompt dei comandi **dtexec** (dtexec.exe) per eseguire un pacchetto distribuito, le configurazioni di pacchetto vengono applicate due volte, ovvero prima e dopo l'applicazione delle opzioni specificate nella riga di comando.  
  
 Durante il caricamento e l'esecuzione del pacchetto da parte dell'utilità, gli eventi si verificano nel seguente ordine:  
  
1.  Il pacchetto viene caricato con l'utilità **dtexec**.  
  
2.  L'utilità consente di applicare le configurazioni specificate nel pacchetto in fase di progettazione, nell'ordine indicato nel pacchetto. L'unica eccezione è rappresentata dalle configurazioni Variabile pacchetto padre, le quali vengono applicate dall'utilità solo una volta e in una fase successiva del processo.  
  
3.  L'utilità applica quindi le opzioni specificate nella riga di comando.  
  
4.  A questo punto l'utilità ricarica le configurazioni specificate nel pacchetto in fase di progettazione, nell'ordine indicato nel pacchetto. L'unica eccezione a questa regola è di nuovo rappresentata dalle configurazioni Variabile pacchetto padre. L'utilità utilizza quindi le opzioni della riga di comando specificate per ricaricare le configurazioni. È pertanto possibile che vengano ricaricati valori diversi da posizioni differenti.  
  
5.  L'utilità consente di applicare le configurazioni Variabile pacchetto padre.  
  
6.  L'utilità consente l'esecuzione del pacchetto.  
  
 Il modo in cui l'utilità **dtexec** applica le configurazioni influisce sulle seguenti opzioni della riga di comando:  
  
-   È possibile usare l'opzione **/Connection** o **/Set** in fase di esecuzione per caricare le configurazioni di pacchetto da una posizione diversa da quella specificata in fase di progettazione.  
  
-   È possibile usare l'opzione **/ConfigFile** per caricare configurazioni aggiuntive non specificate in fase di progettazione.  
  
 Tali opzioni della riga di comando presentano tuttavia alcune restrizioni.  
  
-   Non è possibile usare l'opzione **/Set** o **/Connection** per ignorare valori singoli impostati anche da una configurazione.  
  
-   Non è possibile usare l'opzione **/ConfigFile** per caricare configurazioni che sostituiscono quelle specificate in fase di progettazione.  
  
 Per altre informazioni su queste opzioni e sulla differenza di comportamento di tali opzioni in [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] e versioni precedenti, vedere [Differenze di funzionamento delle funzionalità di Integration Services in SQL Server 2016](../Topic/Behavior%20Changes%20to%20Integration%20Services%20Features%20in%20SQL%20Server%202016.md).  
  
## Tipi di configurazioni di pacchetto  
 Nella tabella seguente vengono descritti i tipi di configurazione di pacchetto.  
  
|Tipo|Description|  
|----------|-----------------|  
|File di configurazione XML|Le configurazioni sono incluse in un file XML. Il file può includere più configurazioni.|  
|Variabile di ambiente|La configurazione è contenuta in una variabile di ambiente.|  
|Voce del Registro di sistema|La configurazione è inclusa in una voce del Registro di sistema.|  
|Variabile pacchetto padre|La configurazione è contenuta in una variabile del pacchetto. Questo tipo di configurazione viene in genere utilizzato per l'aggiornamento di proprietà in pacchetti figlio.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table|La configurazione è inclusa in una tabella di un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La tabella può includere più configurazioni.|  
  
### File di configurazione XML  
 Se si seleziona il tipo di configurazione **File di configurazione XML** è possibile creare un nuovo file di configurazione, riusare un file esistente e aggiungere nuove configurazioni oppure riusare un file esistente sovrascrivendone il contenuto.  
  
 Un file di configurazione XML è suddiviso in due sezioni:  
  
-   Un'intestazione contenente informazioni sul file. Questa sezione include attributi quali la data di creazione del file e il nome dell'utente che ha generato il file.  
  
-   Elementi di configurazione contenenti informazioni su ogni configurazione. Questa sezione include attributi quali il percorso e il valore configurato di una proprietà.  
  
 Nel codice XML seguente viene illustrata la sintassi di un file di configurazione XML. Nell'esempio viene illustrata una configurazione per la proprietà Value di una variabile di tipo Integer denominata `MyVar`.  
  
```  
<?xml version="1.0"?>  
<DTSConfiguration>  
   <DTSConfigurationHeading>  
      <DTSConfigurationFileInfo  
          GeneratedBy="DomainName\UserName"  
          GeneratedFromPackageName="Package"  
          GeneratedFromPackageID="{2AF06766-817A-4E28-9878-0DE37A150648}"  
          GeneratedDate="2/01/2005 5:58:09 PM"/>  
   </DTSConfigurationHeading>  
   <Configuration ConfiguredType="Property" Path="\Package.Variables[User::MyVar].Value" ValueType="Int32">  
      <ConfiguredValue>0</ConfiguredValue>  
   </Configuration>  
</DTSConfiguration>  
  
```  
  
### Voce del Registro di sistema  
 Se si desidera utilizzare una voce del Registro di sistema per archiviare la configurazione, è possibile utilizzare una chiave esistente oppure crearne una nuova in HKEY_CURRENT_USER. Nella chiave del Registro di sistema usata deve essere disponibile un valore denominato **Value**. Il valore può essere un DWORD o una stringa.  
  
 Se si seleziona il tipo di configurazione **Voce del Registro di sistema**, è necessario digitare il nome della chiave del Registro di sistema nella casella Voce del Registro di sistema. Il formato è \<chiave del Registro di sistema>. Se si desidera usare una chiave del Registro di sistema che non si trova nella radice HKEY_CURRENT_USER, per identificare la chiave usare il formato \<chiave Registro di sistema\chiave Registro di sistema\\...>. Per usare la chiave MyPackage in SSISPackages, ad esempio, digitare **SSISPackages\MyPackage**.  
  
### SQL Server  
 Se si seleziona il tipo di configurazione **SQL Server**, è necessario specificare la connessione al database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in cui si desidera archiviare le configurazioni. È possibile salvare le configurazioni in una tabella esistente oppure creare una nuova tabella nel database specificato.  
  
 L'istruzione SQL seguente illustra l'istruzione CREATE TABLE predefinita della Configurazione guidata pacchetto.  
  
```  
CREATE TABLE [dbo].[SSIS Configurations]  
(  
ConfigurationFilter NVARCHAR(255) NOT NULL,  
ConfiguredValue NVARCHAR(255) NULL,  
PackagePath NVARCHAR(255) NOT NULL,  
ConfiguredValueType NVARCHAR(20) NOT NULL  
)  
  
```  
  
 Il nome specificato per la configurazione corrisponde al valore archiviato nella colonna **ConfigurationFilter**.  
  
## Configurazioni dirette e indirette  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dispone di configurazioni dirette e indirette. Se le configurazioni vengono specificate in modo diretto, in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] viene creato un collegamento diretto tra l'elemento di configurazione e la proprietà dell'oggetto di pacchetto. È consigliabile utilizzare le configurazioni dirette quando la posizione dell'origine non cambia. Ad esempio, se per tutte le distribuzioni di pacchetto viene utilizzato sempre lo stesso percorso di file, è possibile specificare un file di configurazione XML.  
  
 Nelle configurazioni indirette vengono utilizzate variabili di ambiente. Anziché specificare l'impostazione di configurazione in modo diretto, la configurazione punta a una variabile di ambiente, la quale contiene il valore di configurazione. È consigliabile utilizzare le configurazioni indirette quando la posizione della configurazione può essere diversa nelle varie distribuzioni di un pacchetto.  
  
## Attività correlate  
 [Creazione di configurazioni dei pacchetti](../../integration-services/packages/create-package-configurations.md)  
  
## Contenuto correlato  
  
-   Articolo tecnico [Understanding Integration Services Package Configurations](http://go.microsoft.com/fwlink/?LinkId=165643) (Informazioni sulle configurazioni dei pacchetti di Integration Services) sul sito Web msdn.microsoft.com  
  
-   Post di blog, [Creating packages in code – Package Configurations](http://go.microsoft.com/fwlink/?LinkId=217663) (Creazione di pacchetti in codice con configurazioni dei pacchetti), su www.sqlis.com.  
  
-   Post di blog [API Sample – Programmatically add a configuration file to a package](http://go.microsoft.com/fwlink/?LinkId=217664) (esempio di API relativo all'aggiunta a livello di programmazione di un file di configurazione a un pacchetto), su blogs.msdn.com.  
  
  