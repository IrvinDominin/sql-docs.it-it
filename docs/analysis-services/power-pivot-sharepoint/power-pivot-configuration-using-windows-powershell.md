---
title: Power Pivot configurazione tramite Windows PowerShell | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d83e53e-04f1-417d-9039-d9e81ae0483d
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f70a2f37df18dfae9ced1a1de2d9e4d991702db7
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="power-pivot-configuration-using-windows-powershell"></a>Configurazione di Power Pivot con Windows PowerShell
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] include i cmdlet di Windows PowerShell che è possibile usare per configurare un'installazione di [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. Per configurare completamente un'installazione con PowerShell, è necessario usare cmdlet sia di SharePoint che di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint. La maggior parte della configurazione può essere completata usando uno degli strumenti di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Per altre informazioni sugli strumenti, vedere [Strumenti di configurazione di Power Pivot](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md).  
  
> [!IMPORTANT]  
>  Per una farm di SharePoint 2010, prima di poter configurare [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint o una farm di SharePoint in cui viene usato un server di database [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] è necessario che SharePoint 2010 SP1 sia installato. Se il Service Pack non è ancora stato installato, eseguire questa operazione prima di iniziare a configurare il server.  
  
## <a name="benefits-of-configuring-power-pivot-for-sharepoint-using-powershell"></a>Vantaggi della configurazione di Power Pivot per SharePoint usando PowerShell  
 È possibile compilare i file di script di Windows PowerShell (con estensione ps1) per rendere automatiche le attività di configurazione. Si consiglia di adottare questo approccio se sono necessari passaggi di installazione e configurazione controllati da script eseguibili in qualsiasi server. Uno script di questo tipo può essere necessario come parte di un piano di ripristino di emergenza per ricompilare un server in caso di errore hardware.  
  
## <a name="view-a-list-of-the-power-pivot-cmdlets-on-a-server"></a>Visualizzare un elenco di cmdlet Power Pivot in un server  
 Per visualizzare il contenuto ed esempi dei cmdlet di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , vedere [Informazioni di riferimento su PowerShell per Power Pivot per SharePoint](../../analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint.md).  
  
 Per usare PowerShell per visualizzare un elenco di cmdlet di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] :  
  
1.  Aprire una shell di gestione di SharePoint usando l'opzione **Esegui come amministratore** .  
  
2.  Immettere il comando seguente:  
  
    ```  
    Get-help *powerpivot*  
    ```  
  
     Viene visualizzato un elenco di cmdlet nel cui nome è incluso [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Ad esempio `Get-PowerPivotServiceApplication`. Il numero di cmdlet disponibili dipende dalla versione di Analysis Services in uso.  
  
    -   10 cmdlet con il server SQL Server 2012 SP1 Analysis Services configurato nella modalità SharePoint e SharePoint 2013. La versione 2012 SP1 utilizza una nuova architettura che consente l'esecuzione di Analysis Server all'esterno della farm di SharePoint e richiede meno cmdlet di Windows PowerShell di gestione.  
  
    -   17 cmdlet con il server SQL Server 2012 SP1 Analysis Services configurato nella modalità SharePoint e SharePoint 2010.  
  
     Se nell'elenco non viene restituito alcun comando o se viene visualizzato un messaggio di errore simile a "`get-help could not find *powerpivot* in a help file in this session.`", vedere la sezione successiva in questo argomento per istruzioni sull'abilitazione dei cmdlet [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nel server.  
  
     Per tutti i cmdlet è disponibile la Guida. Nell'esempio seguente viene illustrato come visualizzare la Guida per il cmdlet **New-PowerPivotServiceApplication** :  
  
    ```  
    Get-help new-powerpivotserviceapplication -full  
    ```  
  
     In alternativa, per visualizzare solo gli esempi, utilizzare la sintassi seguente:  
  
    ```  
    Get-help new-powerpivotserviceapplication -example  
    ```  
  
## <a name="enable-power-pivot-cmdlets-on-a-server"></a>Abilitare i cmdlet di Power Pivot in un server  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] I cmdlet sono disponibili dopo l'installazione di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint e la distribuzione della soluzione della farm. Le soluzioni vengono distribuite una volta eseguito lo strumento di configurazione [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Attenersi a questi passaggi per abilitare l'utilizzo dei cmdlet:  
  
1.  Aprire una shell di gestione di SharePoint usando l'opzione **Esegui come amministratore** .  
  
2.  Eseguire il primo cmdlet:  
  
    ```  
    Add-SPSolution –LiteralPath “C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp”  
    ```  
  
     Il cmdlet restituisce il nome e l'ID della soluzione e Deployed=False. Nel passaggio successivo la soluzione viene distribuita.  
  
3.  Eseguire il secondo cmdlet per distribuire la soluzione:  
  
    ```  
    Install-SPSolution –Identity PowerPivotFarm.wsp –GACDeployment -Force  
    ```  
  
4.  Chiudere la finestra. Riaprirla usando nuovamente l'opzione **Esegui come amministratore** .  
  
## <a name="related-content"></a>Contenuto correlato  
 [Amministrazione e configurazione del server PowerPivot in Amministrazione centrale](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
 [Strumenti di configurazione di Power Pivot](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md)  
  
 [Informazioni di riferimento su PowerShell per Power Pivot per SharePoint](../../analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint.md)  
  
  
