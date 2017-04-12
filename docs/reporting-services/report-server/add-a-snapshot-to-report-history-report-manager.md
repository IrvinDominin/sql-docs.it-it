---
title: "Aggiungere uno snapshot alla cronologia del report (Gestione report) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "cronologia del report [Reporting Services], aggiunta di snapshot"
  - "dati della cronologia [Reporting Services]"
  - "snapshot [Reporting Services], aggiunta di snapshot di report"
  - "aggiunta di snapshot alla cronologia del report"
  - "snapshot di report [Reporting Services], aggiunta"
ms.assetid: 3aafb183-789e-46ac-966c-881dc549b31d
caps.latest.revision: 35
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 35
---
# Aggiungere uno snapshot alla cronologia del report (Gestione report)
  La cronologia di un report è una raccolta di snapshot del report creati nel tempo. Uno snapshot del report indica un report che include informazioni sul layout e i risultati di query recuperati in un momento specifico. Diversamente dai report su richiesta, per i quali vengono recuperati risultati di query aggiornati quando si seleziona il report, gli snapshot dei report vengono elaborati in base a una pianificazione e quindi salvati nel server di report. Quando si seleziona uno snapshot per la visualizzazione, il server di report recupera il report archiviato dal database del server di report e visualizza i dati e il layout del report aggiornati al momento della creazione dello snapshot.  
  
 Gli snapshot dei report non vengono salvati in un formato di rendering specifico, ma ne viene eseguito il rendering nel formato di visualizzazione finale, ad esempio HTML, solo quando vengono richiesti da un utente o un'applicazione. Il rendering posticipato rende uno snapshot portabile. È possibile eseguire il rendering del report nel formato corretto per il dispositivo o il browser da cui proviene la richiesta.  
  
### Per aggiungere manualmente snapshot alla cronologia del report  
  
1.  In Gestione report passare alla pagina **Contenuto** e posizionare il puntatore del mouse sull'elemento per il quale si vuole visualizzare la cronologia, quindi fare clic sulla freccia a discesa.  
  
2.  Nel menu a discesa fare clic su **Visualizza cronologia report**.  
  
3.  Fare clic su **Nuovo snapshot**. Verrà creato un nuovo snapshot nella colonna **Data ultima esecuzione**.  
  
    > [!NOTE]  
    >  A tale scopo la cronologia del report dovrà essere configurata dall'amministratore su **Consenti creazione manuale della cronologia**. Per altre informazioni, vedere [Limitare la cronologia dei report &#40;Gestione report&#41;](../../reporting-services/reports/limit-report-history-report-manager.md).  
  
4.  Fare clic su **Applica**.  
  
### Per aggiungere automaticamente tutti gli snapshot alla cronologia del report  
  
1.  Per un report già configurato per essere eseguito come snapshot dell'esecuzione del report, è possibile impostare proprietà aggiuntive per salvare una copia dello snapshot nella cronologia del report ogni volta che lo snapshot viene aggiornato.  
  
2.  In Gestione report passare alla pagina **Contenuto**, posizionare il puntatore del mouse sull'elemento per il quale si vuole visualizzare la cronologia e quindi fare clic sulla freccia a discesa.  
  
3.  Nel menu a discesa fare clic su **Gestisci**.  
  
4.  Fare clic su **Opzioni snapshot**.  
  
5.  Selezionare la casella di controllo **Archivia tutti gli snapshot dell'esecuzione del report nella cronologia**.  
  
6.  Fare clic su **Applica**.  
  
### Per aggiungere automaticamente snapshot alla cronologia del report in base a una pianificazione  
  
1.  In Gestione report passare alla pagina **Contenuto** e posizionare il puntatore del mouse sull'elemento per il quale si vuole visualizzare la cronologia, quindi fare clic sulla freccia a discesa.  
  
2.  Nel menu a discesa fare clic su **Gestisci**.  
  
3.  Fare clic su **Opzioni snapshot**.  
  
4.  Selezionare la casella di controllo **Usa la pianificazione seguente per aggiungere snapshot alla cronologia del report**. Eseguire una delle operazioni seguenti:  
  
    -   Selezionare **Pianificazione in base al report**. Compilare i dettagli della pianificazione, selezionare le date di inizio e fine e quindi fare clic su **OK**.  
  
    -   Selezionare **Pianificazione condivisa**. Dall'elenco selezionare la pianificazione preferita.  
  
5.  Fare clic su **Applica**.  
  
## Vedere anche  
 [Configurare le proprietà di esecuzione per un report &#40;Gestione report&#41;](../../reporting-services/reports/configure-execution-properties-for-a-report-report-manager.md)   
 [Aprire e chiudere un report &#40;Gestione report&#41;](../../reporting-services/reports/open-and-close-a-report-report-manager.md)   
 [Limitare la cronologia dei report &#40;Gestione report&#41;](../../reporting-services/reports/limit-report-history-report-manager.md)   
 [Pianificazioni](../../reporting-services/subscriptions/schedules.md)   
 [Gestione report &#40;modalità nativa SSRS&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md)  
  
  