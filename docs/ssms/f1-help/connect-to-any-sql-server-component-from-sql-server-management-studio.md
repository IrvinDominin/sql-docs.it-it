---
title: Connettersi ai componenti di SQL Server da SSMS | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], SQL Server Management Studio
- saving connections
- components [SQL Server], connections
- SQL Server Management Studio [SQL Server], connections
ms.assetid: 5eeb41bd-b25b-4d3b-a005-a7d9e4b5978e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3acb06bf912f0c5f9195ad002c9aab8b721e60d4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47720149"
---
# <a name="connect-to-any-sql-server-component-from-sql-server-management-studio"></a>Connessione ai componenti di SQL Server da SQL Server Management Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] offre funzionalità per la gestione di qualsiasi componente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Utilizzare [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] per collegarsi a:  
  
-   Istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)].  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)].  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)](Indici per tabelle con ottimizzazione per la memoria).  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)](Indici per tabelle con ottimizzazione per la memoria).  
  
Sebbene [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] consenta di lavorare con le query senza prima stabilire una connessione a un'origine dei dati, la maggior parte delle altre attività richiede una connessione. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] offre la finestra di dialogo **Connetti al server** per configurare le proprietà di connessione ai componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . All'avvio di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] , si apre la finestra di dialogo **Connetti al server** in cui viene chiesto di connettersi a un server. La finestra di dialogo **Connetti al server** visualizza le ultime impostazioni di connessione usate.  
  
> [!NOTE]  
> È possibile disattivare questa caratteristica per impedire che venga iniziata automaticamente una connessione. Per altre informazioni, vedere [Opzioni di avvio del servizio del motore di database](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
## <a name="saving-connections"></a>salvataggio di connessioni  
È possibile salvare le connessioni in specifici server in Server registrati, oppure salvarle in progetti con Esplora soluzioni.  
  
### <a name="saving-connections-in-registered-servers"></a>Salvataggio delle connessioni in Server registrati  
Quando viene registrato un server, in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] le informazioni di connessione vengono salvate in Server registrati. Per connettersi a un server registrato, fare doppio clic sul nome desiderato in Server registrati. Esplora oggetti aprirà una connessione al server.  
  
### <a name="saving-connections-in-solution-explorer"></a>Salvataggio delle connessioni in Esplora soluzioni  
Esplora soluzioni consente di archiviare query correlate, script, connessioni e altre informazioni associate in un progetto. Ogni progetto script contiene un nodo chiamato **Connessioni**, in cui è possibile salvare una o più connessioni. Per aggiungere una connessione, fare clic con il pulsante destro del mouse su **Connessioni**e scegliere **Nuova connessione**. Per accedere a una connessione salvata, espandere **Connessioni** e fare doppio clic sulla connessione. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] apre una finestra di query associata a quella connessione. Gli script salvati mantengono l'associazione con una specifica connessione.  
  
## <a name="see-also"></a>Vedere anche  
[Utilizzo di SQL Server Management Studio](../../ssms/use-sql-server-management-studio.md)  
[Esplora oggetti](../../ssms/object/object-explorer.md)  
  
