---
title: "Precaricare la cache (Gestione report) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "cache [Reporting Services]"
  - "precaricamento della cache"
ms.assetid: 152a1051-8aa5-4c01-bc85-f8be8971b0cd
caps.latest.revision: 35
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 35
---
# Precaricare la cache (Gestione report)
  Per precaricare la cache per un set di dati condiviso, è possibile creare un piano di aggiornamento della cache per il set di dati stesso.  
  
 Di seguito vengono indicate le due modalità di precaricamento della cache.  
  
1.  Creazione di un piano di aggiornamento della cache per il report Questo è il metodo consigliato.  
  
2.  Utilizzo di una sottoscrizione guidata dai dati per il precaricamento della cache con istanze di report con parametri. Questo metodo consente di precaricare la cache solo in versioni di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] precedenti a [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]. Per altre informazioni, vedere [Memorizzazione dei report nella cache &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md).  
  
 Per memorizzare nella cache un report o un set di dati condiviso, è necessario che siano soddisfatte le condizioni seguenti:  
  
-   Il set di dati condiviso o il report deve essere abilitato per la memorizzazione nella cache.  
  
-   Le origini dati condivise per il set di dati condiviso o il report devono essere configurate per l'utilizzo di credenziali archiviate o di nessuna credenziale.  
  
-   È necessario che il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sia in esecuzione.  
  
### Per precaricare la cache creando un piano di aggiornamento della cache  
  
1.  Avviare [Gestione report &#40;modalità nativa SSRS&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md).  
  
2.  In Gestione report passare alla pagina **Contenuto** e quindi passare all'elemento che si vuole memorizzare nella cache.  
  
3.  Posizionarsi sull'elemento e quindi fare clic sull'elenco a discesa e selezionare **Gestisci**.  
  
4.  Fare clic sulla scheda **Opzioni di aggiornamento cache**.  
  
5.  Sulla barra degli strumenti fare clic su **Nuovo piano di aggiornamento della cache**.  
  
    > [!NOTE]  
    >  Se per l'elemento la memorizzazione nella cache non è abilitata, verrà richiesto di abilitarla. Per abilitare la memorizzazione nella cache, fare clic su **OK**.  
  
     Verrà visualizzata la pagina Piano di aggiornamento della cache.  
  
6.  Se si desidera, digitare una descrizione per il piano di aggiornamento.  
  
7.  Per una pianificazione condivisa, fare clic su **Pianificazione condivisa** e quindi selezionare il nome della pianificazione da usare.  
  
     Per una pianificazione personalizzata, fare clic su **Pianificazione specifica dell'elemento** e quindi fare clic su **Configura**.  
  
8.  Configurare la pianificazione  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### Per precaricare la cache con un report specifico dell'utente tramite una sottoscrizione guidata dai dati  
  
1.  Avviare [Gestione report &#40;modalità nativa SSRS&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md).  
  
2.  In Gestione report passare alla pagina **Contenuto** e quindi al report per il quale si vuole creare una sottoscrizione.  
  
3.  Fare clic sul report e quindi sulla scheda **Sottoscrizioni** e su **Nuova sottoscrizione guidata dai dati**.  
  
4.  Se lo si desidera, digitare una descrizione per la sottoscrizione.  
  
5.  Selezionare **Provider recapito Null** dall'elenco **Specificare la modalità di notifica ai destinatari**.  
  
6.  Per configurare un'origine dati, specificare un tipo di origine dati e quindi fare clic su **Avanti**.  
  
7.  Specificare il tipo di connessione, la stringa di connessione e le credenziali per l'accesso all'origine dei dati che contiene i dati relativi ai sottoscrittori. Nell'esempio seguente viene illustrata una stringa di connessione utilizzata per la connessione al database Subscribers di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    ```  
    data source=<servername>; initial catalog=Subscribers  
    ```  
  
8.  Scegliere **Avanti**.  
  
9. Specificare la query o il comando per il recupero dei dati relativi ai sottoscrittori. Se lo si desidera, aumentare il periodo di timeout per le query che richiedono un'elaborazione prolungata. Esempio:  
  
    ```  
    Select * from UserInfo  
    ```  
  
10. Fare clic su **Convalida**. È necessario convalidare la query prima di proseguire. Quando viene visualizzato il messaggio **Query convalidata**, fare clic su **Avanti**.  
  
11. Poiché non è possibile configurare le impostazioni dell'estensione per il recapito per il provider recapito Null, fare clic su **Avanti**.  
  
12. Specificare i valori dei parametri del report per la sottoscrizione e quindi fare clic su **Avanti**.  
  
13. Specificare quando viene elaborata la sottoscrizione. Non fare clic su **Quando i dati del report vengono aggiornati nel server di report**. Questa impostazione è solo per gli snapshot. Se si vuole usare una pianificazione preesistente, selezionare **In base a una pianificazione condivisa**.  
  
     In alternativa, per creare una pianificazione personalizzata fare clic su **In base a una pianificazione creata per questa sottoscrizione** e quindi su **Avanti**. Configurare la pianificazione e quindi fare clic su **Fine**.  
  
    > [!NOTE]  
    >  Perché i sottoscrittori possano ricevere il report più recente, è necessario che la pianificazione configurata dall'utente sia coerente con la pianificazione di recapito del report che è stata definita per i sottoscrittori. Per altre informazioni, vedere [Portale Web &#40;modalità nativa SSRS&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md).  
  
14. Configurare le opzioni di esecuzione del report come segue. Nella pagina del report fare clic sulla scheda **Proprietà**.  
  
15. Nel riquadro a sinistra fare clic sulla scheda **Esecuzione**.  
  
16. Nella pagina scegliere **Esegui il rendering del report con i dati più recenti**.  
  
17. Selezionare una delle due opzioni della cache e configurare la scadenza come segue:  
  
    -   Per impostare la scadenza della copia memorizzata nella cache dopo un determinato periodo di tempo, fare clic su **Memorizza nella cache una copia temporanea del report. La copia del report scadrà dopo il numero di minuti seguente.** Digitare il numero di minuti alla scadenza del report.  
  
    -   Per impostare la scadenza della copia memorizzata nella cache in base a una pianificazione, fare clic su **Memorizza nella cache una copia temporanea del report. La scadenza della copia è determinata dalla pianificazione seguente.** Per impostare una pianificazione per la scadenza del report, fare clic su **Configura** oppure selezionare una pianificazione condivisa.  
  
18. Fare clic su **Applica**.  
  
## Vedere anche  
 [Sottoscrizioni guidate dai dati](../../reporting-services/subscriptions/data-driven-subscriptions.md)   
 [Creare una sottoscrizione guidata dai dati &#40;esercitazione su SSRS&#41;](../../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md)   
 [Prestazioni, snapshot, memorizzazione nella cache &#40;Reporting Services&#41;](../../reporting-services/report-server/performance-snapshots-caching-reporting-services.md)   
 [Impostare proprietà di elaborazione dei report](../../reporting-services/report-server/set-report-processing-properties.md)   
 [Memorizzazione dei report nella cache &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md)  
  
  