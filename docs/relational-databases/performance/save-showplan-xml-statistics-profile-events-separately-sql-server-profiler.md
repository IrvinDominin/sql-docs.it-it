---
title: "Salvataggio della classe di eventi Showplan XML Statistics Profile Events in file distinti (SQL Server Profiler) | Microsoft Docs"
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
  - "eventi Showplan XML"
  - "salvataggio di eventi Showplan XML"
  - "eventi [SQL Server], Showplan XML"
ms.assetid: df393f13-d538-4d94-8155-9c2fdf5f755d
caps.latest.revision: 20
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 20
---
# Salvataggio della classe di eventi Showplan XML Statistics Profile Events in file distinti (SQL Server Profiler)
  Questo argomento descrive la procedura da seguire per salvare gli eventi **Showplan XML Statistics Profile** acquisiti in tracce in file SQLPlan distinti tramite [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. È possibile aprire i file di eventi **Showplan XML Statistics Profile** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per visualizzare graficamente il piano di esecuzione di ogni evento.  
  
### Per salvare eventi Showplan XML Statistics Profile in file distinti  
  
1.  Scegliere **Nuova traccia** dal menu **File** e quindi connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Verrà visualizzata la finestra di dialogo **Proprietà traccia**.  
  
    > [!NOTE]  
    >  Se l'opzione **Avvia traccia non appena viene stabilita una connessione**è selezionata, la finestra di dialogo **Proprietà traccia** non viene visualizzata e viene invece avviata la traccia. Per disabilitare questa impostazione, scegliere **Opzioni**dal menu **Strumenti**e deselezionare la casella di controllo **Avvia traccia non appena viene stabilita una connessione** .  
  
2.  Nella finestra di dialogo **Proprietà traccia** digitare un nome per la traccia nella casella **Nome traccia** .  
  
3.  Nell'elenco **Modello** selezionare un modello di traccia su cui basare la traccia oppure selezionare **Vuoto** se non si desidera utilizzare alcun modello.  
  
4.  Eseguire una delle operazioni seguenti:  
  
    -   Fare clic su**Salva nel file**per acquisire la traccia in un file. Specificare un valore per l'opzione **Dimensioni massime del file**.  
  
         Facoltativamente selezionare le caselle di controllo **Consenti rollover dei file** e **Dati di traccia elaborati dal server**.  
  
    -   Fare clic su **Salva nella tabella** per acquisire la traccia in una tabella del database.  
  
         Facoltativamente selezionare la casella di controllo **Numero massimo di righe**e specificare un valore.  
  
5.  Facoltativamente selezionare la casella di controllo **Data e ora di arresto della traccia** e specificare la data e l'ora di arresto desiderate.  
  
6.  Fare clic sulla scheda **Selezione eventi**.  
  
7.  Nella colonna di dati **Events** espandere la categoria di eventi **Performance** e quindi selezionare la casella di controllo **Showplan XML Statistics Profile**. Se la categoria di eventi **Performance** non è visualizzata, selezionare la casella di controllo **Mostra tutti gli eventi** .  
  
     La scheda **Impostazioni estrazione eventi** viene aggiunta alla finestra di dialogo **Proprietà traccia**.  
  
8.  Scegliere **Impostazioni estrazione event**selezionare la casella di controllo **Salva eventi Showplan XML separatamente**.  
  
9. Nella finestra di dialogo **Salva con nome** immettere un nome per il file in cui archiviare gli eventi **Showplan XML Statistics Profile**.  
  
10. Fare clic su **Tutti i batch in un singolo file** per salvare tutti gli eventi **Showplan XML Statistics Profile** in un unico file XML oppure fare clic su **Crea un file distinto per ogni singolo batch Showplan XML** per creare un nuovo file XML per ogni evento **Showplan XML Statistics Profile**.  
  
11. Per visualizzare il file di eventi **Showplan XML Statistics Profile** in SQL Server Management Studio, scegliere **Apri** dal menu **File** e quindi fare clic su **File**. Spostarsi sulla directory in cui è stato salvato il file o i file di eventi **Showplan XML Statistics Profile**, selezionare il file desiderato e quindi aprirlo. I file di eventi **Showplan XML Statistics Profile** sono contraddistinti dall'estensione SQLPlan.  
  
## Vedere anche  
 [Analizzare query con risultati SHOWPLAN in SQL Server Profiler](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)  
  
  