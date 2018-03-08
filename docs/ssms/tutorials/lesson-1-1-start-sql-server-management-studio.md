---
title: Avviare SQL Server Management Studio | Microsoft Docs
ms.custom: 
ms.date: 07/11/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: 25ffaea6-0eee-4169-8dd0-1da417c28fc6
caps.latest.revision: "45"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
ms.openlocfilehash: ca25b34da611f2142c0889949c0c5d0c868984f7
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="lesson-1-1---start-sql-server-management-studio"></a>Lezione 1-1 - Avviare SQL Server Management Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Prima di iniziare questa esercitazione, è opportuno esaminare brevemente [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="opening-sql-server-management-studio"></a>Apertura di SQL Server Management Studio  
  
#### <a name="to-open-sql-server-management-studio"></a>Per aprire SQL Server Management Studio  
  
1.  La modalità di avvio di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] (SSMS) dipende dal sistema operativo.  
  * Nelle versioni più recenti di Windows con una **pagina Start** digitare **[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]** nella **pagina Start** per visualizzare il programma. Fare clic sul programma per aprire SSMS. Fare clic con il pulsante destro del mouse sul programma se si vuole aggiungerlo alla **Pagina iniziale**.   
  * Se si usano versioni precedenti di Windows, scegliere **Tutti i programmi** dal menu **Start**, selezionare [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]e fare clic su **SQL Server Management Studio**. In alternativa, nella finestra di dialogo **Esegui** digitare **SSMS.exe** e fare clic su **OK**.  
  
    > [!NOTE]  
    >  Se SSMS non si apre è possibile che non sia stato installato correttamente. Installare SSMS dall' [Area download](../download-sql-server-management-studio-ssms.md). SSMS non viene installato automaticamente con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016. Usare l'ultima versione per accedere a tutte le funzionalità.  
  
2.  Nel passaggio successivo viene definita la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite il componente **Esplora oggetti** di SSMS. Se il riquadro Esplora oggetti non viene visualizzato, scegliere **Esplora oggetti** dal menu **Visualizza**. Sulla barra degli strumenti di Esplora oggetti fare clic sul pulsante **Connetti** e selezionare **Motore di database**. Si aprirà la finestra di dialogo **Connetti al server** . Se SSMS è già stato installo, è possibile che, in base alle impostazioni utenti, la finestra di dialogo **Connetti al server** si apra automaticamente.  
  
3.  Nella finestra di dialogo **Connetti al server** completare la casella **Nome server** . È possibile connettersi a uno dei tre tipi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il formato da inserire nella casella **Nome server** è leggermente diverso a seconda del tipo. Usare uno dei seguenti formati:  
  -  **Istanza predefinita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:** quando si installa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un computer, è possibile specificare che l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sarà un valore predefinito, quindi un'istanza senza nome, oppure un'istanza denominata. Se ci si connette a un'istanza predefinita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], inserire il nome del computer. Ad esempio, se si esegue SQL Server Management Studio in un computer denominato Accounting e ci si connette a un'istanza predefinita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  installato nel computer, digitare **Accounting** nella casella **Nome server** .  
  -  **Istanza denominata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:** durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è possibile specificare un nome per l'istanza. Ad esempio, in un computer denominato Finanze, è possibile specificare un'istanza denominata **Entrate**. Per connettersi a un'istanza denominata, digitare il nome dell'istanza separandolo con la barra rovesciata dal nome del computer nella casella **Nome server** , ad esempio **Accounting\Receivables**.  
  -  **Database SQL di Azure:** il formato del nome del server per il database SQL è SQL_Server_name.database.windows.net,, ad esempio **mydb2.database.windows.net**. In caso di difficoltà a determinare il nome del server, visitare il portale di Azure per informazioni sulla creazione di una stringa di connessione.  
  
4. Nell'area **Autenticazione** selezionare un metodo di autenticazione.  
  - Se si è l'amministratore del computer e SQL Server è stato appena installato, provare **Autenticazione di Windows**.  Questa opzione funziona anche se l'utente è configurato come utente di dominio con accesso a SQL Server. Dato che per il tentativo di accesso vengono usate le credenziali specificate per accedere a Windows, entrambe le caselle **Nome utente** e **Password** sono disattivate. 
  -  Se si conosce il nome e la password di un account utente, selezionare **Autenticazione di SQL Server** e quindi specificare **Nome utente** e **Password**.
  - Se è disponibile la versione più recente di SSMS, saranno disponibili altre 3 opzioni, a partire da **Autenticazione di Active Directory**. Per informazioni su queste opzioni più avanzate, vedere [Autenticazione universale con database SQL e SQL Data Warehouse (supporto SSMS per MFA)](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-ssms-mfa-authentication).  
  
## <a name="management-studio-components"></a>Componenti di Management Studio  
[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] offre informazioni in finestre dedicate a tipi di informazioni specifiche. Le informazioni di database vengono visualizzate in Esplora oggetti e nelle finestre dei documenti.  
  
-   In Esplora oggetti è visualizzato l'albero di tutti gli oggetti di database presenti in un server. Possono essere inclusi i database del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]e di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Esplora oggetti contiene informazioni su tutti i server ai quali è connesso. All'apertura di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]viene chiesto di connettere Esplora oggetti alle ultime impostazioni utilizzate. È possibile fare doppio clic su un qualsiasi server nel componente Server registrati per eseguire la connessione, tuttavia non è necessario registrare un server per connettersi.  
  
-   La finestra del documento rappresenta la parte più estesa di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Le finestre dei documenti possono contenere editor di query e finestre del browser. Per impostazione predefinita, viene visualizzata la pagina Riepilogo connessa all'istanza di [!INCLUDE[ssDE](../../includes/ssde-md.md)] nel computer corrente.  
  
## <a name="showing-additional-windows"></a>Visualizzazione di finestre aggiuntive  
  
#### <a name="to-show-the-registered-servers-window"></a>Per visualizzare la finestra Server registrati  
  
1.  Scegliere **Server registrati** dal menu **Visualizza**.  
  
    La finestra Server registrati si aprirà sopra o accanto a Esplora oggetti. È possibile trascinarla e ancorarla in punti diversi. In Server registrati sono elencati i server gestiti più di frequente. È possibile aggiungere e rimuovere server dall'elenco. Gli unici server elencati saranno le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel computer in cui si esegue [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
2.  Se il server non viene visualizzato, in Server registrati fare clic con il pulsante destro del mouse su **Motore di database**, selezionare **Attività**e scegliere **Aggiorna registrazione server locale**. Per aggiungere altri server SQL o un database SQL, fare doppio clic in un punto nella finestra Server registrati e fare clic su **Nuova registrazione server**. Completare l'area **Account di accesso** con gli stessi valori usati per completare la finestra di dialogo **Connetti al server** .  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Connettersi con Server registrati ed Esplora oggetti](../../tools/sql-server-management-studio/lesson-1-2-connect-with-registered-servers-and-object-explorer.md)  

  
