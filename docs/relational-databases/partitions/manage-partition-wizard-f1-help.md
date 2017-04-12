---
title: "Guida sensibile al contesto della Gestione guidata partizione | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-partition"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "sql13.swb.managepartition.createjob.f1"
  - "sql13.swb.managepartition.progress.f1"
  - "sql13.swb.managepartition.getstart.f1"
  - "sql13.swb.managepartition.selectswitchtables.f1"
  - "sql13.swb.managepartition.stagingtable.f1"
  - "sql13.swb.managepartition.switchin.f1"
  - "sql13.swb.managepartition.switchout.f1"
  - "sql13.swb.managepartition.partitionaction.f1"
  - "sql13.swb.managepartition.summary.f1"
  - "sql13.swb.managepartition.selectoutput.f1"
helpviewer_keywords: 
  - "procedure guidate [SQL Server Management Studio] Vedere Gestione guidata partizione"
ms.assetid: e2478d26-dea4-428d-98c5-aad2d2a30da8
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# Guida sensibile al contesto della Gestione guidata partizione
  Usare la **Gestione guidata partizione** per gestire e modificare tabelle partizionate esistenti tramite il cambio della partizione o l'implementazione di uno scenario basato su finestra temporale scorrevole. Questa procedura guidata può semplificare la gestione delle partizioni e la normale migrazione di dati all'interno e all'esterno delle tabelle.  
  
### Per avviare la Gestione guidata partizione  
  
-   In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] selezionare il database, fare clic con il pulsante destro del mouse sulla tabella in cui si desidera creare partizioni, scegliere **Archiviazione** e quindi fare clic su **Gestione partizione**.  
  
     **Nota** Se **Gestione partizione** non è disponibile, potrebbe essere stata selezionata una tabella che non contiene partizioni. Fare clic su **Crea partizione** nel sottomenu **Archiviazione** e usare la **Creazione guidata partizione** per creare partizioni nella tabella.  
  
 Per informazioni generali su indici e partizioni, vedere [Tabelle e indici partizionati](../../relational-databases/partitions/partitioned-tables-and-indexes.md).  
  
 Questa sezione include le informazioni necessarie per gestire, modificare e implementare partizioni tramite la **Gestione guidata partizione**.  
  
##  <a name="Top"></a> Argomenti della sezione  
 Le sezioni seguenti forniscono informazioni sulle pagine della **Gestione guidata partizione**.  
  
 [Gestione guidata partizione (pagina Selezionare un'azione relativa alla partizione)](#SelectPartitionAction)  
  
 [Gestione guidata partizione (pagina Attiva)](#SwitchIn)  
  
 [Gestione guidata partizione (pagina Disattiva)](#SwitchOut)  
  
 [Gestione guidata partizione (pagina Seleziona opzioni per la tabella di gestione temporanea)](#StagingTableOptions)  
  
 [Gestione guidata partizione (pagina Seleziona un'opzione di output)](#OutputOption)  
  
 [Gestione guidata partizione (pagina Nuova pianificazione processo)](#NewJob)  
  
 [Gestione guidata partizione (pagina Riepilogo)](#Summary)  
  
 [Gestione guidata partizione (pagina Stato)](#Progress)  
  
##  <a name="SelectPartitionAction"></a> Pagina Selezionare un'azione relativa alla partizione  
 Usare la pagina **Selezionare un'azione relativa alla partizione** per scegliere l'azione che si desidera eseguire sulla partizione.  
  
### Creazione di una tabella di gestione temporanea  
 Il cambio della partizione rappresenta un'attività di partizionamento comune se si dispone di una tabella partizionata in e da cui si esegue regolarmente la migrazione di dati, ad esempio se si dispone di una tabella partizionata in cui vengono archiviati dati trimestrali correnti ed è necessario spostare nuovi dati e archiviare i dati precedenti al termine di ogni trimestre.  
  
 La procedura guidata consente di progettare la tabella di gestione temporanea con la stessa colonna di partizionamento, la stessa struttura di tabelle e colonne e gli stessi indici e di archiviare la nuova tabella nel filegroup in cui è inclusa la partizione di origine.  
  
 Per creare una tabella di gestione temporanea in cui e da cui spostare i dati della partizione, selezionare **Crea tabella di gestione temporanea per il cambio della partizione**.  
  
### Scenario basato su finestra temporale scorrevole  
 Per gestire le partizioni in uno scenario basato su finestra temporale scorrevole, selezionare **Gestisci dati partizionati in uno scenario basato su finestra temporale scorrevole**.  
  
## Elenco degli elementi di interfaccia  
 **Crea tabella di gestione temporanea per il cambio della partizione**  
 Consente di creare una tabella di gestione temporanea per i dati da spostare all'interno o all'esterno della tabella partizionata esistente.  
  
 **Partizione di disattivazione**  
 Fornisce le opzioni per la rimozione di una partizione dalla tabella.  
  
 **Partizione di attivazione**  
 Fornisce le opzioni per l'aggiunta di una partizione alla tabella.  
  
 **Gestisci dati partizionati in uno scenario basato su finestra temporale scorrevole**  
 Consente di aggiungere una partizione vuota alla tabella esistente da utilizzare per spostare i dati. La procedura guidata supporta attualmente lo spostamento all'interno dell'ultima partizione e all'esterno della prima partizione.  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../analysis-services/instances/media/uparrow16x16.png "Icona freccia usata con il collegamento Torna all'inizio") [Argomenti della sezione](#Top)  
  
##  <a name="SwitchIn"></a> Pagina Seleziona opzioni per l'attivazione della partizione  
 Usare la pagina **Seleziona opzioni per l'attivazione della partizione** per selezionare la tabella di gestione temporanea che si desidera attivare nella tabella partizionata.  
  
## Elenco degli elementi di interfaccia  
 **Mostra tutte le partizioni**  
 Selezionare questa opzione per visualizzare tutte le partizioni, incluse le partizioni correnti nella tabella partizionata.  
  
 **Griglia partizione**  
 Consente di visualizzare il nome della partizione e i valori per **Limite sinistro**, **Limite destro**, **Filegroup** e **Conteggio righe** delle partizioni selezionate.  
  
 **Tabella di attivazione**  
 Consente di selezionare la tabella di gestione temporanea contenente la partizione che si desidera aggiungere alla tabella partizionata. È necessario creare questa tabella di gestione temporanea prima di attivare partizioni usando la **Gestione guidata partizione**.  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../analysis-services/instances/media/uparrow16x16.png "Icona freccia usata con il collegamento Torna all'inizio") [Argomenti della sezione](#Top)  
  
##  <a name="SwitchOut"></a> Pagina Seleziona opzioni per la disattivazione della partizione  
 Usare la pagina **Seleziona opzioni per la disattivazione della partizione** per selezionare la partizione e la tabella di gestione temporanea contenente i dati partizionati che si desidera disattivare dalla tabella partizionata.  
  
## Elenco degli elementi di interfaccia  
 **Griglia partizione**  
 Consente di visualizzare il nome della partizione e i valori per **Limite sinistro**, **Limite destro**, **Filegroup** e **Conteggio righe** delle partizioni selezionate.  
  
 **Tabella di disattivazione**  
 Consente di scegliere una nuova tabella o una esistente in cui spostare i dati.  
  
 **Nuovi**  
 Consente di immettere un nuovo nome per la tabella di gestione temporanea che si desidera utilizzare per la partizione da disattivare per la tabella di origine corrente.  
  
 **Esistente**  
 Consente di selezionare una tabella di gestione temporanea esistente che si desidera utilizzare per la partizione che si desidera disattivare per la tabella di origine corrente. Gli eventuali dati contenuti nella tabella verranno sovrascritti con i dati utilizzati per la disattivazione.  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../analysis-services/instances/media/uparrow16x16.png "Icona freccia usata con il collegamento Torna all'inizio") [Argomenti della sezione](#Top)  
  
##  <a name="StagingTableOptions"></a> Pagina Seleziona opzioni per la tabella di gestione temporanea  
 Usare la pagina **Seleziona opzioni per la tabella di gestione temporanea** per creare la tabella di gestione temporanea che si desidera utilizzare per lo spostamento dei dati partizionati.  
  
 Le tabelle di gestione temporanea devono risiedere nello stesso filegroup della partizione selezionata in cui è presente la tabella di origine. La tabella di gestione temporanea deve riflettere la struttura della tabella di origine e della tabella di destinazione.  
  
 È inoltre possibile creare gli stessi indici nella tabella di gestione temporanea presenti nella partizione di origine. La tabella di gestione temporanea contiene automaticamente un vincolo basato sugli elementi della partizione di origine. In genere tale vincolo viene generato dal valore limite della partizione di origine.  
  
## Elenco degli elementi di interfaccia  
 **Nome tabella di gestione temporanea**  
 Consente di creare un nome per la tabella di gestione temporanea o di accettare il nome predefinito visualizzato nella casella di modifica.  
  
 **Cambia partizione**  
 Consente di selezionare la partizione di origine che si desidera rimuovere dalla tabella corrente.  
  
 **Nuovo valore limite**  
 Consente di selezionare o di immettere il valore limite desiderato per la partizione nella tabella di gestione temporanea.  
  
 **Filegroup**  
 Consente di selezionare un filegroup per la nuova tabella.  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../analysis-services/instances/media/uparrow16x16.png "Icona freccia usata con il collegamento Torna all'inizio") [Argomenti della sezione](#Top)  
  
##  <a name="OutputOption"></a> Pagina Seleziona un'opzione di output  
 Usare la pagina **Seleziona un'opzione di output** per specificare il modo in cui si desidera completare le modifiche alle partizioni.  
  
### Crea script  
 Al termine della procedura guidata, nell'editor di query viene creato uno script per la modifica delle partizioni nella tabella. Selezionare **Crea script** se si desidera controllare lo script e quindi eseguirlo manualmente.  
  
 **Genera script nel file**  
 Consente di generare lo script in un file con estensione sql. Specificare **Unicode** o **Testo ANSI**. Per specificare un nome e un percorso per il file, scegliere **Sfoglia**.  
  
 **Genera script negli Appunti**  
 Consente di salvare lo script negli Appunti.  
  
 **Genera script in nuova finestra Query**  
 Consente di generare lo script in una finestra dell'editor di query. Se non è aperta alcuna finestra dell'editor, ne viene aperta una nuova da utilizzare come destinazione per lo script.  
  
### Esegui immediatamente  
 **Esegui immediatamente**  
 Per completare l'applicazione di modifiche alle partizioni nella procedura guidata, fare clic su **Avanti** o **Fine**.  
  
### Pianificazione  
 Selezionare questa opzione per modificare le partizioni della tabella a una data e a un'ora pianificata.  
  
 **Cambia pianificazione**  
 Viene aperta la finestra di dialogo **Nuova pianificazione processo**, in cui è possibile selezionare, modificare o visualizzare le proprietà del processo pianificato.  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../analysis-services/instances/media/uparrow16x16.png "Icona freccia usata con il collegamento Torna all'inizio") [Argomenti della sezione](#Top)  
  
##  <a name="NewJob"></a> Pagina Nuova pianificazione processo  
 Usare la pagina **Nuova pianificazione processo** per visualizzare e modificare le proprietà della pianificazione.  
  
### Opzioni  
 Selezionare il tipo di pianificazione desiderata per il processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 **Nome**  
 Consente di digitare un nuovo nome per la pianificazione.  
  
 **Processi nella pianificazione**  
 Consente di visualizzare i processi esistenti che utilizzano la pianificazione.  
  
 **Tipo pianificazione**  
 Consente di selezionare il tipo di pianificazione.  
  
 **Abilitata**  
 Consente di abilitare o disabilitare la pianificazione.  
  
### Opzioni relative ai tipi di pianificazione periodica  
 Selezionare la frequenza del processo pianificato.  
  
 **Ricorrenza**  
 Consente di selezionare l'intervallo in base al quale ripetere la pianificazione.  
  
 **Ogni**  
 Consente di selezionare il numero di giorni o di settimane quale intervallo di esecuzione delle pianificazioni. Questa opzione non è disponibile per pianificazioni mensili.  
  
 **Lunedì**  
 Consente di impostare l'esecuzione del processo ogni lunedì. Questa opzione è disponibile solo per pianificazioni settimanali.  
  
 **Martedì**  
 Consente di impostare l'esecuzione del processo ogni martedì. Questa opzione è disponibile solo per pianificazioni settimanali.  
  
 **Mercoledì**  
 Consente di impostare l'esecuzione del processo ogni mercoledì. Questa opzione è disponibile solo per pianificazioni settimanali.  
  
 **Giovedì**  
 Consente di impostare l'esecuzione del processo ogni giovedì. Questa opzione è disponibile solo per pianificazioni settimanali.  
  
 **Venerdì**  
 Consente di impostare l'esecuzione del processo ogni venerdì. Questa opzione è disponibile solo per pianificazioni settimanali.  
  
 **Sabato**  
 Consente di impostare l'esecuzione del processo ogni sabato. Questa opzione è disponibile solo per pianificazioni settimanali.  
  
 **Domenica**  
 Consente di impostare l'esecuzione del processo ogni domenica. Questa opzione è disponibile solo per pianificazioni settimanali.  
  
 **Day**  
 Consente di selezionare il giorno del mese in cui eseguire la pianificazione. Questa opzione è disponibile solo per pianificazioni mensili.  
  
 **ogni**  
 Consente di selezionare il numero di mesi tra una pianificazione e l'altra. Questa opzione è disponibile solo per pianificazioni mensili.  
  
 **Ogni**  
 Consente di specificare una pianificazione per un giorno specifico di una determinata settimana del mese. Questa opzione è disponibile solo per pianificazioni mensili.  
  
 **Una sola volta alle**  
 Consente di impostare l'ora per l'esecuzione giornaliera di un processo.  
  
 **Ogni**  
 Consente di impostare il numero di ore o di minuti di intervallo tra un'esecuzione e l'altra.  
  
 **Data inizio**  
 Consente di impostare la data iniziale di validità per la pianificazione.  
  
 **Data fine**  
 Consente di impostare la data finale di validità per la pianificazione.  
  
 **Nessuna data di fine**  
 Consente di specificare una validità illimitata per la pianificazione.  
  
### Opzioni relative ai tipi di pianificazione da eseguire una sola volta  
 Se si pianifica una singola esecuzione per un processo, è necessario selezionare una data e un'ora nel futuro.  
  
 **Data**  
 Selezionare la data di esecuzione del processo.  
  
 **Time**  
 Selezionare l'ora di esecuzione del processo.  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../analysis-services/instances/media/uparrow16x16.png "Icona freccia usata con il collegamento Torna all'inizio") [Argomenti della sezione](#Top)  
  
##  <a name="Summary"></a> Pagina Riepilogo  
 Usare la pagina **Riepilogo** per verificare le opzioni selezionate nelle pagine precedenti.  
  
## Elenco degli elementi di interfaccia  
 **Controlla selezioni**  
 Consente di visualizzare le opzioni selezionate in ogni pagina della procedura guidata. Fare clic su un nodo per espandere e visualizzare le opzioni selezionate in precedenza.  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../analysis-services/instances/media/uparrow16x16.png "Icona freccia usata con il collegamento Torna all'inizio") [Argomenti della sezione](#Top)  
  
##  <a name="Progress"></a> Pagina Stato  
 Usare la pagina **Stato** per monitorare le informazioni sullo stato delle azioni eseguite nella **Gestione guidata partizione**. A seconda delle opzioni selezionate nella procedura guidata, la pagina **Stato** può contenere una o più azioni. Nella casella superiore viene visualizzato lo stato complessivo della procedura guidata e viene indicato il numero di messaggi di stato, di errore e di avviso restituiti durante l'esecuzione della procedura guidata.  
  
### Opzioni  
 **Dettagli**  
 Consente di visualizzare i messaggi di azione, di stato e di altro tipo restituiti dall'azione eseguita nella procedura guidata.  
  
 **Azione**  
 Specifica il tipo e il nome di ciascuna azione.  
  
 **Stato**  
 Indica se l'intera azione della procedura guidata ha restituito il valore **Esito positivo** o **Esito negativo**.  
  
 **Message**  
 Fornisce tutti i messaggi di errore o di avviso restituiti dal processo.  
  
 **Arresta**  
 Consente di arrestare l'azione della procedura guidata.  
  
 **Report**  
 Consente di creare un report contenente i risultati della **Gestione guidata partizione**. Le opzioni disponibili sono le seguenti:  
  
-   **Visualizza report**  
  
-   **Salva report su file**  
  
-   **Copia report negli Appunti**  
  
-   **Invia report per posta elettronica**  
  
 **Visualizza report**  
 Consente di aprire la finestra di dialogo **Visualizza report**, che contiene un report di testo dello stato della **Gestione guidata partizione**.  
  
 **Chiudi**  
 Consente di chiudere la procedura guidata.  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../analysis-services/instances/media/uparrow16x16.png "Icona freccia usata con il collegamento Torna all'inizio") [Argomenti della sezione](#Top)  
  
## Vedere anche  
 [Tabelle e indici partizionati](../../relational-databases/partitions/partitioned-tables-and-indexes.md)  
  
  