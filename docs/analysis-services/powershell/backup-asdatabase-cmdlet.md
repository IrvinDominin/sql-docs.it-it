---
title: "Cmdlet Backup-ASDatabase | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 03d58a82-021c-4e13-b265-c084f42a8bb2
caps.latest.revision: 13
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 13
---
# Cmdlet Backup-ASDatabase
  Eseguire il backup di un database multidimensionale o tabulare di Analysis Services in un file di backup di Analysis Services (con estensione abf).  
  
## Sintassi  
 `Backup-ASDatabase [-BackupFile] <string> [-Name] <string> [-AllowOverwrite <SwitchParameter>] [-BackupRemotePartitions <SwitchParameter>] [-ApplyCompression <SwitchParameter>] [-FilePassword <SecureString>] [-Locations <Microsoft.AnalysisServices.BackupLocation[]>] [-Server <string>] [-Credential <PSCredential>] [<CommonParameters>]`  
  
 `Backup-ASDatabase –Database <Microsoft.AnalysisServices.Database> [-AllowOverwrite <SwitchParameter>] [-BackupRemotePartitions <SwitchParameter>] [-ApplyCompression <SwitchParameter>] [-FilePassword <SecureString>] [-Locations <Microsoft.AnalysisServices.BackupLocation[]>] [-Server <string>] [-Credential <PSCredential>] [<CommonParameters>]`  
  
## Description  
 Consente a un amministratore di sistema di Analysis Services di eseguire il backup di un database multidimensionale o tabulare in un file di backup. Se non si specifica un percorso, viene utilizzato il percorso di backup predefinito specificato durante l'installazione.  
  
 È possibile crittografare i file di cui si esegue il backup. Utilizzare -FilePassword per crittografare il file. Quando si ripristina il file in un secondo momento, è necessario fornire la stessa password specificata per la crittografia.  
  
 Questo cmdlet supporta il parametro -Credential, che può essere utilizzato se è stata configurata l'istanza di Analysis Services per l'accesso HTTP. Il parametro -Credential accetta un oggetto PSCredential che fornisce un'identità utente di Windows. In IIS verrà quindi rappresentato questo utente durante la connessione ad Analysis Services. Per eseguire il backup, è necessario che l'identità disponga delle autorizzazioni di amministratore di sistema nell'istanza di Analysis Services.  
  
## Parametri  
  
### -BackupFile \<string>  
 Specifica il percorso e il nome del file di backup. Se si specifica solo un nome file senza un percorso, verrà utilizzato il percorso di backup predefinito. Questo parametro viene utilizzato solo con il parametro -Name.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -Name \<string>  
 Specifica il database di Analysis Services di cui eseguire il backup. È possibile specificare un database utilizzando il parametro -Database o -Name se si desidera passare il nome come una stringa.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|1|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -AllowOverwrite \<SwitchParameter>  
 Sovrascrive un file di backup con lo stesso nome.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -BackupRemotePartitions \<SwitchParameter>  
 Specifica se le partizioni remote saranno incluse nel backup.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -ApplyCompression\<SwitchParameter>  
 Specifica se comprimere il file di backup.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -FilePassword \<SecureString>  
 Specifica una password da utilizzare con la crittografia del file di backup.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -Locations \<Microsoft.AnalysisServices.BackupLocation[]>  
 Specifica il percorso in cui verrà archiviato il file di backup.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -Server \<string>  
 Specifica l'istanza di Analysis Services a cui il cmdlet deve connettersi per l'esecuzione. Se non viene fornito alcun nome del server, la connessione verrà effettuata a localhost. Per le istanze predefinite è sufficiente specificare il nome del server, mentre per quelle denominate, utilizzare il formato nomeserver\nomeistanza. Per le connessioni HTTP, utilizzare il formato http[s]://server[:porta]/virtualdirectory/msmdpump.dll.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|localhost|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -Credential \<PSCredential>  
 Specifica un oggetto PSCredential che fornisce un nome utente e una password di Windows. Specificare questo parametro solo se l'istanza di Analysis Services viene configurata per l'accesso HTTP, utilizzando l'autenticazione di base. Per le connessioni native in cui viene utilizzata la sicurezza integrata, questo parametro viene ignorato.  
  
 Se questo parametro è presente, le credenziali fornite vengono accodate alla stringa di connessione. In IIS verrà quindi rappresentata questa identità utente durante la connessione ad Analysis Services. Se non vengono specificate credenziali, verrà utilizzato l'account di Windows predefinito dell'utente che esegue lo strumento.  
  
 Per usare questo parametro, creare innanzitutto un oggetto PSCredential usando Get-Credential per specificare il nome utente e la password, ad esempio, `$Cred=Get-Credential “adventure-works\admin”`. Successivamente è possibile inoltrare tramite pipe questo oggetto al parametro -Credential `(-Credential:$Cred`.  
  
 Per altre informazioni sull'uso di autenticazione e credenziali, vedere [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md) (Script di PowerShell in Analysis Services). Per altre informazioni sull'accesso HTTP, vedere [Configurare l'accesso HTTP ad Analysis Services in Internet Information Services &#40;IIS&#41; 8.0](../../analysis-services/instances/configure http access to analysis services on iis 8.0.md).  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|True (ByValue)|  
|Accettare caratteri jolly?|false|  
  
### -Database \<Microsoft.AnalysisServices.Database[]>  
 Specifica un oggetto di database di Analysis Services di cui eseguire il backup. Un database può essere specificato utilizzando il parametro -Database o -Name. Utilizzare -Database se si desidera inoltrare tramite pipe il nome del database.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|true|  
|Accettare caratteri jolly?|false|  
  
### \<CommonParameters>  
 In questo cmdlet vengono supportati i parametri comuni: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable. Per altre informazioni, vedere [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Input e output  
 Il tipo di input è il tipo degli oggetti che è possibile inoltrare tramite pipe al cmdlet. Il tipo restituito è il tipo degli oggetti restituiti dal cmdlet.  
  
|||  
|-|-|  
|Input|Microsoft.AnalysisServices.Database<br /><br /> È possibile inoltrare tramite pipe più database di cui si desidera eseguire il backup, ad esempio tutti i database di un'istanza specifica.|  
|Output|Nessuno|  
  
## Esempio 1  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default >backup-asdatabase awdb-20110930.abf “Adventure Works” -AllowOverwrite -ApplyCompression  
```  
  
 Questo comando esegue il backup del database Adventure Works in un file con estensione abf nel percorso di backup predefinito. Se nel percorso è presente un file con lo stesso nome, verrà sovrascritto.  
  
## Esempio 2  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default >$AWDB = get-item “databases\Adventure Works”   
PS SQLSERVER:\SQLAS\Localhost\default >Backup-asdatabase –database:$AWDB –AllowOverwrite  
```  
  
 Per questo comando viene utilizzato -Database anziché -Backupfile e -Name. Utilizzare il parametro -Database se si desidera inoltrare tramite pipe il nome del database al cmdlet.  
  
## Esempio 3  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default\databases >dir * | backup-asdatabase  
```  
  
 Questo comando esegue il backup di tutti i database nel server locale.  
  
## Esempio 4  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default > $pwd = read-host –AsSecureString –Prompt “Password”   
PS SQLSERVER:\SQLAS\Localhost\default > $pwd -is [System.IDisposable]   
PS SQLSERVER:\SQLAS\Localhost\default > backup-asdatabase –backupfile test.abf –name contoso_retail –filepassword:$pwd server myremoteserver  
PS SQLSERVER:\SQLAS\Localhost\default >$pwd.Dispose()  
PS SQLSERVER:\SQLAS\Localhost\default >Remove-Variable –Name pwd  
```  
  
 Le righe 1 e 2 vengono utilizzate per richiedere una password che verrà utilizzata per crittografare il file.  
  
 La riga 3 esegue il backup del database di esempio Contoso_Retail presente sul server Analysis Services remoto in un file di backup di Analysis Services denominato test.abf, ugualmente sul remoto. Il file viene salvato nella cartella di backup predefinita dell'istanza predefinita.  
  
 Le righe 4 e 5 rimuovono la password.  
  
## Vedere anche  
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)   
 [Post sulla gestione dei modelli tabulari tramite PowerShell](http://go.microsoft.com/fwlink/?linkID=227685)  
  
  