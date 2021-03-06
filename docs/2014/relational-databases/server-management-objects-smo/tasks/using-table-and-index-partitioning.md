---
title: Con partizionamento di tabelle e indici | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- partitions [SMO]
- storing data [SMO]
- partitioned tables [SQL Server], SMO
- partitioned indexes [SQL Server], SMO
ms.assetid: 0e682d7e-86c3-4d73-950d-aa692d46cb62
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f98d4337dbd5a43adf1e83d80b24b8286193e19d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48166111"
---
# <a name="using-table-and-index-partitioning"></a>Utilizzo del partizionamento di tabelle e indici
  I dati possono essere archiviati tramite gli algoritmi di archiviazione forniti da [Partitioned Tables and Indexes](../../partitions/partitioned-tables-and-indexes.md). Il partizionamento semplifica la gestione delle tabelle e degli indici di grandi dimensioni e li rende più scalabili.  
  
## <a name="index-and-table-partitioning"></a>Partizionamento di indici e tabelle  
 La funzionalità consente la distribuzione di dati relativi a indici e tabelle in più filegroup all'interno delle partizioni. Una funzione di partizione definisce la modalità di mapping delle righe di una tabella o di un indice a un set di partizioni in base ai valori di alcune colonne definite colonne di partizionamento. Uno schema di partizione consente di eseguire il mapping di ogni partizione specificata dalla funzione di partizione a un filegroup. In questo modo, è possibile sviluppare strategie di archiviazione che prevedano la scalabilità delle tabelle tra filegroup e di conseguenza tra dispositivi fisici.  
  
 Il <xref:Microsoft.SqlServer.Management.Smo.Database> oggetto contiene una raccolta di <xref:Microsoft.SqlServer.Management.Smo.PartitionFunction> gli oggetti che rappresentano le funzioni di partizione implementate e una raccolta di <xref:Microsoft.SqlServer.Management.Smo.PartitionScheme> oggetti che descrivono come viene eseguito il mapping dei dati ai filegroup.  
  
 Ogni oggetto <xref:Microsoft.SqlServer.Management.Smo.Table> e <xref:Microsoft.SqlServer.Management.Smo.Index> specifica lo schema di partizione utilizzato nella proprietà <xref:Microsoft.SqlServer.Management.Smo.PartitionScheme> e specifica le colonne in <xref:Microsoft.SqlServer.Management.Smo.PartitionSchemeParameterCollection>.  
  
## <a name="example"></a>Esempio  
 Per l'esempio di codice seguente, è necessario selezionare l'ambiente, il modello e il linguaggio di programmazione per la creazione dell'applicazione. Per altre informazioni, vedere [creare un progetto Visual Basic SMO in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) e [creare un Visual C#&#35; progetto SMO in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="setting-up-a-partition-scheme-for-a-table-in-visual-basic"></a>Configurazione di uno schema di partizione per una tabella in Visual Basic  
 L'esempio di codice viene illustrato come creare una funzione di partizione e uno schema di partizione per il `TransactionHistory` tabella di [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database di esempio. Le partizioni sono divise in base alla data con l'intenzione di separare i record obsoleti nella tabella `TransactionHistoryArchive` .  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBPartition1](SMO How to#SMO_VBPartition1)]  -->  
  
## <a name="setting-up-a-partition-scheme-for-a-table-in-visual-c"></a>Configurazione di uno schema di partizione per una tabella in Visual C#  
 L'esempio di codice viene illustrato come creare una funzione di partizione e uno schema di partizione per il `TransactionHistory` tabella di [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database di esempio. Le partizioni sono divise in base alla data con l'intenzione di separare i record obsoleti nella tabella `TransactionHistoryArchive` .  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Define and create three new file groups on the database.   
FileGroup fg2;   
fg2 = new FileGroup(db, "Second");   
fg2.Create();   
FileGroup fg3;   
fg3 = new FileGroup(db, "Third");   
fg3.Create();   
FileGroup fg4;   
fg4 = new FileGroup(db, "Fourth");   
fg4.Create();   
//Define a partition function by supplying the parent database and name arguments in the constructor.   
PartitionFunction pf;   
pf = new PartitionFunction(db, "TransHistPF");   
//Add a partition function parameter that specifies the function uses a DateTime range type.   
PartitionFunctionParameter pfp;   
pfp = new PartitionFunctionParameter(pf, DataType.DateTime);   
pf.PartitionFunctionParameters.Add(pfp);   
//Specify the three dates that divide the data into four partitions.   
object[] val;   
val = new object[] {"1/1/2003", "1/1/2004", "1/1/2005"};   
pf.RangeValues = val;   
//Create the partition function.   
pf.Create();   
//Define a partition scheme by supplying the parent database and name arguments in the constructor.   
PartitionScheme ps;   
ps = new PartitionScheme(db, "TransHistPS");   
//Specify the partition function and the filegroups required by the partition scheme.   
ps.PartitionFunction = "TransHistPF";   
ps.FileGroups.Add("PRIMARY");   
ps.FileGroups.Add("second");   
ps.FileGroups.Add("Third");   
ps.FileGroups.Add("Fourth");   
//Create the partition scheme.   
ps.Create();   
}   
```  
  
## <a name="setting-up-a-partition-scheme-for-a-table-in-powershell"></a>Configurazione di uno schema di partizione per una tabella in PowerShell  
 L'esempio di codice viene illustrato come creare una funzione di partizione e uno schema di partizione per il `TransactionHistory` tabella di [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database di esempio. Le partizioni sono divise in base alla data con l'intenzione di separare i record obsoleti nella tabella `TransactionHistoryArchive` .  
  
```powershell  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
$db = $srv.Databases["AdventureWorks"]  
#Create four filegroups  
$fg1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "First"  
$fg2 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Second"  
$fg3 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Third"  
$fg4 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Fourth"  
  
#Define a partition function by supplying the parent database and name arguments in the constructor.  
$pf =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.PartitionFunction -argumentlist $db, "TransHistPF"  
$T = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$T  
$T.GetType()  
#Add a partition function parameter that specifies the function uses a DateTime range type.  
$pfp =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.PartitionFunctionParameter -argumentlist $pf, $T  
  
#Specify the three dates that divide the data into four partitions.   
#Create an array of type object to hold the partition data  
$val = "1/1/2003"."1/1/2004","1/1/2005"  
$pf.RangeValues = $val  
$pf  
#Create the partition function  
$pf.Create()  
  
#Create partition scheme  
$ps = New-Object -TypeName Microsoft.SqlServer.Management.SMO.PartitionScheme -argumentlist $db, "TransHistPS"  
$ps.PartitionFunction = "TransHistPF"  
  
#add the filegroups to the scheme   
$ps.FileGroups.Add("PRIMARY")  
$ps.FileGroups.Add("Second")  
$ps.FileGroups.Add("Third")  
$ps.FileGroups.Add("Fourth")  
  
#Create it at the server  
$ps.Create()  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Partitioned Tables and Indexes](../../partitions/partitioned-tables-and-indexes.md)  
  
  
