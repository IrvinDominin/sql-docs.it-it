---
title: "Visualizzazione della Guida di SQL Server PowerShell | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Guida [PowerShell]"
  - "Guida [SQL Server], PowerShell"
  - "PowerShell [SQL Server], Guida"
ms.assetid: 968c316d-db83-4c24-8ea6-9f18736842f7
caps.latest.revision: 18
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 18
---
# Visualizzazione della Guida di SQL Server PowerShell
  Vi sono diverse fonti di informazione per l'utilizzo dei cmdlet e del provider di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per Windows PowerShell. Tra queste è inclusa la Guida disponibile nell'ambiente di Windows PowerShell.  
  
## Prima di iniziare  
 Per informazioni su Windows PowerShell, vedere la [Guida introduttiva a Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=217083).  
  
 Per una panoramica dei cmdlet e del provider di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md).  
  
### Guida all'ambiente di Windows PowerShell  
 Usare il cmdlet **Get-Help** per ottenere informazioni sull'ambiente di Windows PowerShell. **Get-Help** fornisce informazioni di base sul linguaggio di Windows PowerShell e sui vari cmdlet e provider disponibili in Windows PowerShell.  
  
 Per altre informazioni su come usare **Get-Help**, vedere [Visualizzazione della Guida: Get-Help](http://go.microsoft.com/fwlink/?LinkId=102136).  
  
### Guida del provider PowerShell per SQL Server  
 Il provider PowerShell di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implementa diverse cartelle su un'unità virtuale SQLSERVER, come ad esempio le cartelle SQLSERVER:\SQL e SQLSERVER:\DAC. Ogni cartella è associata a uno dei modelli a oggetti per la gestione di SQL Server. È possibile elencare i metodi e le proprietà associati a ogni nodo in un percorso di SQL Server, ma non è possibile ottenerne la guida nell'ambiente PowerShell. Per una tabella delle cartelle con i collegamenti al riferimento di programmazione associato, vedere [Provider PowerShell per SQL Server](../../relational-databases/scripting/sql-server-powershell-provider.md).  
  
### Guida di Invoke-Sqlcmd  
 Il cmdlet **Invoke-Sqlcmd** accetta come input qualsiasi query o file script che può essere eseguito dall'utilità **sqlcmd**. È possibile usare **Get-Help** per ottenere informazioni su **Invoke-Sqlcmd** e i relativi parametri, ma **Get-Help** non fornisce informazioni sulle query **sqlcmd**.  
  
 L'input *-Query* o *-QueryFromFile* può contenere:  
  
-   Variabili e comandi di **sqlcmd**. Per informazioni su variabili e comandi, vedere la sezione Osservazioni di [Utilità sqlcmd](../../tools/sqlcmd-utility.md).  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] . Per altre informazioni sul linguaggio [!INCLUDE[tsql](../../includes/tsql-md.md)], vedere [Guida di riferimento a Transact-SQL &#40;Motore di database&#41;](../../t-sql/transact-sql-reference-database-engine.md).  
  
-   Istruzioni XQuery. Per altre informazioni sul linguaggio XQuery supportato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Riferimento al linguaggio XQuery &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md).  
  
## Ottenere la Guida per un cmdlet di SQL Server  
 **Per ottenere la Guida per un cmdlet**  
  
-   Eseguire Get-Help specificando il nome del cmdlet e il livello della Guida da restituire.  
  
### Esempio: cmdlet Get-Help  
 Negli esempi seguenti vengono restituiti vari livelli della Guida per **Invoke-Sqlcmd**:  
  
```  
## Get the basic help.  
Get-Help Invoke-Sqlcmd  
  
## Get the full help.  
Get-Help Invoke-Sqlcmd –Full  
  
## Get the parameter descriptions.  
Get-Help Invoke-Sqlcmd -Parameter *  
  
## Get the code examples.  
Get-Help Invoke-Sqlcmd –Examples  
  
## Get the syntax diagram.  
Get-Help Invoke-Sqlcmd –Syntax  
```  
  
## Ottenere un elenco di provider  
 **Per ottenere un elenco di provider attivi**  
  
1.  Eseguire Get-Help specificando la categoria del provider.  
  
 Per altre informazioni su come ottenere informazioni sul provider in Windows PowerShell, vedere [Unità e provider](http://go.microsoft.com/fwlink/?LinkId=102137).  
  
### Esempio: ottenere un elenco di provider  
 Questo codice restituisce un elenco dei provider attualmente abilitati nella sessione di Windows PowerShell:  
  
```  
Get-Help -Category provider  
```  
  
## Ottenere la Guida sul provider SQL Server  
 **Per ottenere la Guida sul provider**  
  
1.  Eseguire Get-Help specificando il nome SQLServer  
  
### Esempio: ottenere la Guida del provider SQL Server  
 In questo esempio vengono restituite informazioni di base sul provider di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
```  
Get-Help SQLServer  
```  
  
## Elencare metodi e proprietà  
 **Per elencare i metodi e le proprietà per un nodo in un percorso del provider SQL Server**  
  
1.  Usare il comando CD in un nodo nel percorso di SQL Server o creare un set di variabili nel percorso.  
  
2.  Eseguire il cmdlet **Get-Member** con il parametro –Type impostato su Methods o Properties  
  
### Esempi: elencare metodi e proprietà  
 In questo esempio vengono elencati i metodi supportati per il nodo Database:  
  
```  
Set-Location SQL:\MyComputer\DEFAULT\Databases  
Get-Item . | Get-Member -Type Methods  
```  
  
 In questo esempio vengono elencate le proprietà di una variabile impostata su un oggetto della tabella SMO:  
  
```  
$MyVar = New-Object Microsoft.SqlServer.Management.SMO.Table  
$MyVar | Get-Member -Type Properties  
```  
  
## Vedere anche  
 [Provider PowerShell per SQL Server](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [Utilizzo di cmdlet del motore di database](../../relational-databases/scripting/use-the-database-engine-cmdlets.md)  
  
  