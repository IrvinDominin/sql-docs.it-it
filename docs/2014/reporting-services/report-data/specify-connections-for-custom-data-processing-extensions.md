---
title: Specificare le connessioni per le estensioni per l'elaborazione dati personalizzate | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- custom data processing extensions [Reporting Services]
- IDbConnection interface, connection strings
- impersonation [Reporting Services]
- IDbConnectionExtension interface, connection strings
- data sources [Reporting Services], security
- connection strings [Reporting Services]
- credentials [Reporting Services]
- authentication [Reporting Services]
- external data sources [Reporting Services]
- data processing extensions [Reporting Services], connections
ms.assetid: 2cddc9ea-0e28-4350-80ae-332412908e47
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: cd8f137735e33a64a14327cb170fc9b5a0c7b89a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48223831"
---
# <a name="specify-connections-for-custom-data-processing-extensions"></a>Specificare le connessioni per le estensioni per l'elaborazione dati personalizzate
  È possibile creare o utilizzare estensioni per l'elaborazione dei dati personalizzate di terze parti in un server di report per migliorare la funzionalità di elaborazione dei dati delle origini dati supportate o per supportare ulteriori tipi di origini dati non disponibili in un'installazione predefinita di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Le connessioni vengono gestite in modo diverso a seconda dell'implementazione. Per le estensioni per l'elaborazione dati sono disponibili le implementazioni seguenti:  
  
-   Provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] personalizzati (se l'accesso ai dati viene eseguito da origini dati DB2.NET, Oracle, ODP.NET o Teradata, è possibile che si stia usando un provider di dati .NET personalizzato)  
  
-   Estensioni per l'elaborazione dati personalizzate che supportano <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>  
  
-   Estensioni per l'elaborazione dati personalizzate che supportano <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>  
  
> [!NOTE]  
>  Per informazioni sulla modalità di implementazione dell'estensione per l'elaborazione dati personalizzata in uso, rivolgersi al provider di terze parti.  
  
## <a name="impersonation-and-custom-data-processing-extensions"></a>Rappresentazione ed estensioni per l'elaborazione dati personalizzate  
 Se l'estensione per l'elaborazione dati personalizzata in uso si connette a origini dei dati mediante la rappresentazione, è necessario usare il metodo Open sull'interfaccia <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> o <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> per eseguire la richiesta. In alternativa è possibile archiviare l'oggetto identità dell'utente (System.Security.Principal.WindowsIdentity), quindi riusarlo nelle altre API dell'estensione per l'elaborazione dati.  
  
 Nelle precedenti versioni di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], tutte le estensioni per l'elaborazione dei dati personalizzate vengono chiamate durante la rappresentazione utente. Nella presente versione, invece, solo il metodo Open viene chiamato durante tale rappresentazione. Se si dispone di un'estensione per l'elaborazione dati che richiede una sicurezza integrata, è necessario modificare il codice per usare il metodo Open o archiviare l'oggetto identità dell'utente.  
  
## <a name="connections-for-custom-net-framework-data-providers"></a>Connessioni per i provider di dati .NET Framework personalizzati  
 Quando si configura un report per l'utilizzo di una specifica origine dei dati, vengono impostate proprietà che determinano il tipo di origine dei dati, la stringa di connessione e le credenziali utilizzate per accedere all'origine dei dati. Nella tabella seguente vengono descritti i tipi di credenziali supportati per i provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] . Per altre informazioni sull'impostazione delle proprietà dell'origine dati report, vedere [specificare le credenziali e informazioni di connessione per origini dati del Report](specify-credential-and-connection-information-for-report-data-sources.md).  
  
|Credenziali|Connessioni|  
|-----------------|-----------------|  
|sicurezza integrata|Se il provider di dati in uso la supporta, è possibile utilizzare la sicurezza integrata di Windows. La richiesta viene inviata utilizzando le credenziali dell'utente corrente.<br /><br /> Quando si definisce la stringa di connessione, assicurarsi di includere argomenti che specifichino la sicurezza integrata (ad esempio, una connessione a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] origine dati potrà includere `Integrated Security=SSPI` nella stringa di connessione).|  
|Autenticazione di Windows|Se il provider di dati in uso lo supporta, è possibile utilizzare un account utente di dominio di Windows. Il server di report rappresenta l'account utente prima che venga chiamata l'estensione per l'elaborazione dati.<br /><br /> Quando si definisce la stringa di connessione, assicurarsi di includere argomenti che specifichino la sicurezza integrata (ad esempio, una connessione a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] origine dati potrà includere `Integrated Security=SSPI` nella stringa di connessione).|  
|Credenziali di database|L'autenticazione del database non è supportata per le connessioni stabilite mediante un provider di dati .NET personalizzato. La connessione avrà esito negativo in tutti i casi.|  
|Nessuna credenziale|È possibile utilizzare l'opzione Nessuna credenziale con provider di dati .NET personalizzati. Se viene specificato l'account per l'esecuzione automatica, la stringa di connessione determina le credenziali che verranno utilizzate. Il server di report rappresenta l'account per l'esecuzione automatica per stabilire la connessione.<br /><br /> Se l'account per l'esecuzione automatica non è definito, la connessione avrà esito negativo. Per altre informazioni sulla definizione dell'account, vedere [configurare l'Account di esecuzione automatica &#40;Gestione configurazione SSRS&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).|  
  
## <a name="connections-for-idbconnection"></a>Connessioni per IDbConnection  
 Se si usa un'estensione per l'elaborazione dati personalizzata che supporta solo <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>, è necessario specificare la connessione nel modo seguente:  
  
1.  Configurazione dell'account di esecuzione automatica. Configurazione di questo account è necessaria per le connessioni effettuate con `IDbConnection`. Il server di report rappresenta l'account quando viene stabilita la connessione.  
  
2.  Configurare le proprietà dell'origine dei dati nel report per l'utilizzo dell'opzione **Nessuna credenziale**.  
  
3.  Inserire le credenziali utilizzate per connettersi all'origine dei dati nella stringa di connessione.  
  
 Quando si usa `IDbConnection`, non sono supportati i seguenti tipi di credenziali: sicurezza integrata, account utente di Windows e le credenziali del database. Se in una connessione a un'origine dei dati vengono utilizzate queste opzioni, la connessione avrà esito negativo sul server di report.  
  
## <a name="connections-for-idbconnectionextension"></a>Connessioni per IDbConnectionExtension  
 Se si usa un'estensione per l'elaborazione dati personalizzata che supporta <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>, è possibile specificare la connessione nel modo seguente:  
  
|Credenziali|Connessioni|  
|-----------------|-----------------|  
|sicurezza integrata|Se il provider di dati lo supporta, è possibile usare la sicurezza integrata di Windows con estensioni per l'elaborazione dati personalizzate che usano `IDbConnectionExtension`.<br /><br /> Quando si definisce la stringa di connessione, assicurarsi di includere argomenti che specifichino la sicurezza integrata (ad esempio, una connessione a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] origine dati potrà includere `Integrated Security=SSPI` nella stringa di connessione).|  
|Autenticazione di Windows|Se il provider di dati lo supporta, è possibile usare un account utente di dominio di Windows per estensioni per l'elaborazione dati personalizzate che usano `IDbConnectionExtension`.<br /><br /> Il server di report rappresenta l'account utente prima che venga chiamata l'estensione per l'elaborazione dati. Quando si definisce la stringa di connessione, assicurarsi di includere argomenti che specifichino la sicurezza integrata (ad esempio, una connessione a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] origine dati potrà includere `Integrated Security=SSPI` nella stringa di connessione).|  
|Credenziali di database|È possibile utilizzare l'autenticazione del database per configurare connessioni per estensioni per l'elaborazione dati personalizzate che utilizzano `IDbConnectionExtension`.|  
|Nessuna credenziale|Se viene specificato l'account per l'esecuzione automatica, la stringa di connessione determina le credenziali che verranno utilizzate.<br /><br /> Se l'account per l'esecuzione automatica non è definito, la connessione avrà esito negativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare l'Account di esecuzione automatica &#40;Gestione configurazione SSRS&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)   
 [Specificare le credenziali e le informazioni sulla connessione per le origini dati del report](specify-credential-and-connection-information-for-report-data-sources.md)   
 [Connessioni dati, origini dati e stringhe di connessione in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Implementazione di un'estensione per l'elaborazione dati](../extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Gestione report &#40;modalità nativa SSRS&#41;](../report-manager-ssrs-native-mode.md)   
 [Creare, eliminare o modificare un'origine dati condivisa &#40;gestione Report&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md)   
 [Configurare le proprietà di origine dati per un Report &#40;gestione Report&#41;](configure-data-source-properties-for-a-report-report-manager.md)  
  
  
