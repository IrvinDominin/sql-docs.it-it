---
title: "Cmdlet Set-PowerPivotSystemService | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: f6ef197b-3d74-4339-ae73-8a7c1eaf0e91
caps.latest.revision: 11
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 11
---
# Cmdlet Set-PowerPivotSystemService
  Imposta le proprietà globali dell'oggetto PowerPivotSystemService a livello di farm.  
  
 **Applicabile a:** SharePoint 2010 e SharePoint 2013.  
  
## Sintassi  
  
```  
Set-PowerPivotSystemService [-Identity <PowerPivotMidTierServicePipeBind>] [-UpdateAssemblyInformation <switch>] [-WorkbookUpgradeOnDataRefresh <boolean>] [-DirectTCPConnections <boolean>] [-Confirm <switch>] [<CommonParameters>]  
```  
  
## Description  
 Il cmdlet Set-PowerPivotSystemService aggiorna le proprietà dell'oggetto padre del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nella farm.  
  
## Parametri  
  
### -Identity \<PowerPivotMidTierServicePipeBind>  
 Specifica l'oggetto padre per il quale si stanno aggiornando le proprietà. Il valore deve essere un GUID valido tramite cui si identifica in modo univoco l'oggetto nella farm.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|true|  
|Accettare caratteri jolly?|false|  
  
### -UpdateAssemblyInformation \<switch>  
 Utilizzato solo a scopo di aggiornamento. Se la versione dell'assembly distribuita nella farm è diversa dalla versione archiviata nel database di configurazione di SharePoint, è possibile eseguire questo cmdlet per aggiornare le informazioni sull'assembly nel database di configurazione. Le informazioni sulla versione dell'assembly sono disponibili nelle proprietà del file Microsoft.AnalysisServices.SharePoint.Integration.dll, archiviato nell'assembly globale.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|1|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -WorkbookUpgradeOnDataRefresh \<boolean>  
 Consente di aggiornare automaticamente una cartella di lavoro di [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] all'inizio di un aggiornamento dati pianificato nel server. L'aggiornamento dati è supportato solo per le cartelle di lavoro che corrispondono alla versione corrente del server. Se si abilita questa proprietà, una cartella di lavoro verrà aggiornata automaticamente in modo che l'aggiornamento dati possa continuare. Questa proprietà viene impostata a livello di istanza del server. Non è possibile modificarla per cartelle di lavoro, librerie, siti o utenti specifici.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|2|  
|Valore predefinito|false|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -DirectTCPConnections \<boolean>  
 Specifica che Excel Services invia tutte le query direttamente all'istanza di SQL Server Analysis Services (POWERPIVOT) in cui è stato caricato un database [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], ignorando il provider di dati MSOLAP e il trasporto del canale che verrebbero altrimenti usati per ogni richiesta di query inviata a un database [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].  
  
 L'impostazione di questo parametro consente di migliorare le prestazioni e la scalabilità delle query [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] rendendo più efficienti le connessioni ai database caricati. Si noti che questo parametro non comporta la modifica del comportamento di allocazione della richiesta di caricamento iniziale. Altri parametri, ad esempio RoundRobinAllocation e HealthBasedAllocation, usati per allocare richieste di caricamento del database tra più istanze di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint nella farm, non sono interessati perché DirectTCPConnections si applica solo alle query inviate dopo il caricamento del database.  
  
 Per topologie di farm che includono Excel Services e [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint in esecuzione in server applicazioni separati, è necessario aprire una porta nel firewall per garantire che le richieste raggiungano l'istanza di SQL Server Analysis Services (POWERPIVOT). Per istruzioni sull'abilitazione di connessioni in ingresso per un'istanza denominata di Analysis Services, vedere [Configurare Windows Firewall per consentire l'accesso ad Analysis Services](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|3|  
|Valore predefinito|false|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -Confirm \<switch>  
 Richiede la conferma dell'utente prima dell'esecuzione del comando. Questo valore è abilitato per impostazione predefinita. Per ignorare la risposta di conferma in un comando, specificare Confirm:$false nel comando.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### \<CommonParameters>  
 Questo cmdlet supporta i parametri comuni, ovvero Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer e OutVariable. Per altre informazioni, vedere [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Input e output  
 Il tipo di input è il tipo degli oggetti che è possibile inoltrare tramite pipe al cmdlet. Il tipo restituito è il tipo degli oggetti restituiti dal cmdlet.  
  
|||  
|-|-|  
|Input|Nessuno|  
|Output|Nessuno|  
  
## Esempio 1  
  
```  
C:\PS>Set-PowerPivotSystemService -WorkbookUpgradeOnDataRefresh:$true  
```  
  
 Viene abilitato l'aggiornamento automatico di cartelle di lavoro di versioni precedenti in modo che l'aggiornamento dati pianificato possa continuare.  
  
  