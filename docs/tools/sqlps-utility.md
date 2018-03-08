---
title: "Utilità sqlps | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: sqlps
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sqlps utility
- PowerShell [SQL Server], sqlps utility
ms.assetid: 4b2515a6-12c3-44fb-b263-1c567681cd2b
caps.latest.revision: "22"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: bd4e67397b52b3e7248ce061312517841eef38e5
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="sqlps-utility"></a>sqlps - utilità
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]Il **sqlps** utilità avvia una sessione di Windows PowerShell con il [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider PowerShell e i cmdlet caricati e registrati. È possibile immettere comandi o script di PowerShell che utilizzano componenti di PowerShell per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per utilizzare istanze di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e i relativi oggetti.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)]Utilizzare il **sqlps** modulo PowerShell invece. Per altre informazioni sul modulo **sqlps** , vedere [Import the SQLPS Module](../relational-databases/scripting/import-the-sqlps-module.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sqlps   
[ [ [ -NoLogo ][ -NoExit ][ -NoProfile ]  
    [ -OutPutFormat { Text | XML } ] [ -InPutFormat { Text | XML } ]  
  ]  
  [ -Command { -  
             | script_block [ -args argument_array ]  
             | string [ command_parameters ]  
             }  
  ]  
]  
[ -? | -Help ]  
```  
  
## <a name="arguments"></a>Argomenti  
 **-NoLogo**  
 Specifica che l'utilità **sqlps** deve nascondere le informazioni sul copyright all'avvio.  
  
 **-NoExit**  
 Specifica che l'esecuzione dell'utilità **sqlps** deve proseguire una volta completati i comandi di avvio.  
  
 **-NoProfile**  
 Specifica che l'utilità **sqlps** non deve caricare un profilo utente. I profili utente registrano alias, funzioni e variabili di uso comune per l'utilizzo nelle sessioni di PowerShell.  
  
 **-OutPutFormat** { **Text** | **XML** }  
 Specifica che l'output dell'utilità **sqlps** deve essere formattato come stringhe di testo (**Text**) o in un formato CLIXML serializzato (**XML**).  
  
 **-InPutFormat** { **Text** | **XML** }  
 Specifica che l'input dell'utilità **sqlps** deve essere formattato come stringhe di testo (**Text**) o in un formato CLIXML serializzato (**XML**).  
  
 **-Command**  
 Specifica il comando per l'esecuzione dell'utilità **sqlps** . L'utilità **sqlps** esegue il comando e quindi viene chiusa, a meno che non si specifichi anche **-NoExit** . Non specificare altre opzioni dopo **-Command**, in quanto verranno lette come parametri del comando.  
  
 **-**  
 **-Command-** specifica che l'utilità **sqlps** deve leggere l'input dall'input standard.  
  
 *script_block* [ **-args***argument_array* ]  
 Specifica un blocco di comandi di PowerShell da eseguire. Il blocco deve essere incluso in parentesi graffe: {}. È possibile specificare*Script_block* solo quando l'utilità **sqlps** viene chiamata da **PowerShell** o da un'altra sessione dell'utilità **sqlps** . *argument_array* è una matrice di variabili PowerShell che contiene gli argomenti per i comandi di PowerShell in *script_block*.  
  
 *string* [ *command_parameters* ]  
 Specifica una stringa che contiene i comandi di PowerShell da eseguire. Utilizzare il formato **"& {***comando***}"**. Le virgolette indicano una stringa e l'operatore invoke (&) determina l'esecuzione del comando da parte dell'utilità **sqlps**.  
  
 [ **-?** | **-Help** ]  
 Visualizza il riepilogo della sintassi delle opzioni dell'utilità **sqlps** .  
  
## <a name="remarks"></a>Osservazioni  
 L'utilità **sqlps** avvia l'ambiente PowerShell (PowerShell.exe) e carica il modulo di PowerShell per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Il modulo, denominato anche **sqlps**, carica e registra gli snap-in di PowerShell per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] seguenti:  
  
-   Microsoft.SqlServer.Management.PSProvider.dll  
  
     Implementa il provider PowerShell per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e i cmdlet associati, ad esempio **Encode-SqlName** e **Decode-SqlName**.  
  
-   Microsoft.SqlServer.Management.PSSnapin.dll  
  
     Implementa i cmdlet **Invoke-Sqlcmd** e **Invoke-PolicyEvaluation** .  
  
 È possibile usare l'utilità **sqlps** per le operazioni seguenti:  
  
-   Eseguire in modo interattivo comandi di PowerShell.  
  
-   Eseguire file script di PowerShell.  
  
-   Eseguire cmdlet di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
-   Utilizzare i percorsi del provider di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per spostarsi nella gerarchia degli oggetti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 Per impostazione predefinita, l'utilità **sqlps** viene eseguita con i criteri di esecuzione degli script impostati su **Con restrizioni**. Questa impostazione impedisce l'esecuzione di qualsiasi script di PowerShell. Per abilitare l'esecuzione di script firmati o di qualsiasi script, è possibile usare il cmdlet **Set-ExecutionPolicy** . Eseguire solo script provenienti da origini attendibili e proteggere tutti i file di input e di output utilizzando le autorizzazioni NTFS appropriate. Per ulteriori informazioni sull'abilitazione degli script di PowerShell, vedere la pagina relativa all' [esecuzione di script di Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=103166).  
  
 La versione dell'utilità **sqlps** in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] e [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] viene implementata come minishell di Windows PowerShell 1.0. Alle minishell si applicano alcune restrizioni, ad esempio agli utenti non è consentito caricare snap-in diversi da quelli caricati dalla minishell. Queste restrizioni non si applicano a [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] e versioni successive dell'utilità, modificate per utilizzare il modulo **sqlps** .  
  
## <a name="examples"></a>Esempi  
 **A. Eseguire l'utilità sqlps in predefinito, la modalità interattiva, senza le informazioni sul copyright**  
  
```  
sqlps -NoLogo  
```  
  
 **B. Eseguire uno script di PowerShell per SQL Server dal prompt dei comandi**  
  
```  
sqlps -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
 **C. Eseguire uno script di PowerShell per SQL Server dal prompt dei comandi e proseguimento dell'esecuzione dopo il completamento dello script**  
  
```  
sqlps -NoExit -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Abilitare o disabilitare un protocollo di rete del server](../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)  
  
  
