---
title: "Interfaccia utente di Progettazione query SAP NetWeaver BI | Microsoft Docs"
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
f1_keywords: 
  - "sql13.rtp.rptdesigner.dataview.sapbwquerydesigner.f1"
  - "10014"
helpviewer_keywords: 
  - "origini dati [Reporting Services], SAP NetWeaver Business Intelligence"
  - "SAP NetWeaver Business Intelligence [Reporting Services], progettazione query"
  - "strumenti di progettazione query [Reporting Services]"
ms.assetid: 102da66e-ca31-41aa-ab4b-c9b5ab752a72
caps.latest.revision: 38
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 38
---
# Interfaccia utente di Progettazione query SAP NetWeaver BI
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] offre una finestra Progettazione query con interfaccia grafica per la compilazione di query MDX (Multidimensional Expression) per un'origine dati SAP NetWeaver® Business Intelligence. Nella finestra Progettazione query con interfaccia grafica MDX sono disponibili due modalità: progettazione e query. In ogni modalità è disponibile un riquadro metadati dal quale è possibile trascinare membri da un InfoCube, un MultiProvider o una query Web definita sull'origine dei dati per la compilazione di una query MDX che recupera dati quando il report viene elaborato.  
  
> [!IMPORTANT]  
>  Gli utenti accedono alle origini dati quando creano ed eseguono query. È necessario concedere autorizzazioni minime per le origini dati, ad esempio autorizzazioni di sola lettura.  
  
 Per altre informazioni sull'uso di un'origine dei dati multidimensionale SAP, vedere [Tipo di connessione SAP NetWeaver BI &#40;SSRS&#41;](../../reporting-services/report-data/sap-netweaver-bi-connection-type-ssrs.md).  
  
 In questa sezione vengono descritti i pulsanti della barra degli strumenti e i riquadri di Progettazione query per ogni modalità della finestra Progettazione query con interfaccia grafica.  
  
## Finestra Progettazione query con interfaccia grafica in modalità progettazione  
 Quando si modifica la query di un set di dati che utilizza un'origine di dati [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] , la finestra Progettazione query con interfaccia grafica verrà aperta in modalità progettazione. Nella figura seguente vengono etichettati i riquadri per la modalità progettazione.  
  
 ![Progettazione query mediante MDX in modalità progettazione](../../reporting-services/report-data/media/rsqd-dssapbw-mdx-designmode.gif "Progettazione query mediante MDX in modalità progettazione")  
  
 Nella tabella seguente vengono elencati i riquadri disponibili in questa modalità.  
  
|Riquadro|Funzione|  
|----------|--------------|  
|Pulsante Seleziona cubo|Consente di visualizzare la query InfoCube, MultiProvider o Web attualmente selezionata.|  
|Riquadro dei metadati|Consente di visualizzare un elenco gerarchico di InfoCube, MultiProvider e query. È possibile che le query create a livello di origine dei dati siano visualizzate nel cubo corrispondente.|  
|Riquadro Membri calcolati|Consente di visualizzare i membri calcolati attualmente definiti disponibili per l'utilizzo nella query.|  
|Riquadro Dati|Consente di visualizzare i risultati dell'esecuzione della query.|  
  
 È possibile trascinare dimensioni e cifre chiave dal riquadro Metadati e membri calcolati dal riquadro Membro calcolato nel riquadro Dati. Se il pulsante Mostra/Nascondi **Esecuzione automatica** sulla barra degli strumenti è attivo, Progettazione query esegue la query ogni volta che si trascina un oggetto nel riquadro Dati. Se **Esecuzione automatica** non è attivo, Progettazione query non esegue la query quando il riquadro Dati viene modificato. È possibile eseguire manualmente la query utilizzando il pulsante **Esegui** sulla barra degli strumenti.  
  
### Barra degli strumenti della finestra Progettazione query con interfaccia grafica in modalità progettazione  
 I pulsanti della barra degli strumenti di Progettazione query consentono di progettare query MDX utilizzando l'interfaccia grafica. Nella tabella seguente vengono illustrati i pulsanti con le relative funzioni.  
  
|Pulsante|Description|  
|------------|-----------------|  
|**Modifica come testo**|Consente di passare dalla finestra Progettazione query basata su testo alla finestra Progettazione query con interfaccia grafica e viceversa. Non è disponibile per questo tipo di origine dati.|  
|**Importa**|Consente di importare una query esistente da un file di definizione di report (con estensione rdl) nel file system. Per altre informazioni, vedere [Set di dati condivisi e incorporati del report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).|  
|![Refresh dataset fields](../../reporting-services/report-data/media/rsqdicon-refreshfields.gif "Refresh dataset fields")|Consente di aggiornare i metadati dall'origine dati.|  
|![Aggiungi membro calcolato](../../reporting-services/report-data/media/rsqdicon-addcalculatedmember.png "Aggiungi membro calcolato")|Consente di visualizzare la finestra di dialogo **Generatore membri calcolati** ,|  
|![Mostra/Nascondi celle vuote](../../reporting-services/report-data/media/rsqdicon-showemptycells.png "Mostra/Nascondi celle vuote")|Consente di visualizzare o nascondere le celle vuote nel riquadro Dati. Questa operazione equivale a utilizzare la clausola NON EMPTY in MDX.|  
|![Esecuzione automatica della query](../../reporting-services/report-data/media/rsqdicon-autoexecute.png "Esecuzione automatica della query")|Consente di eseguire automaticamente la query e visualizza il risultato a ogni modifica, ad esempio, quando viene eliminata una colonna nel riquadro Dati. I risultati verranno visualizzati nel riquadro Dati.|  
|![Elimina](../../reporting-services/report-data/media/rsqdicon-delete.png "Elimina")|Consente di eliminare dalla query la colonna selezionata nel riquadro Dati.|  
|![Icona della finestra di dialogo Parametri query](../../reporting-services/report-data/media/iconqueryparameter.png "Icona della finestra di dialogo Parametri query")|Consente di visualizzare la finestra di dialogo **Variabili**. Questo pulsante è abilitato solo quando il cubo selezionato è una query sul cubo, dato che solo le query sui cubi supportano le variabili. Quando si assegna un valore predefinito a una variabile, viene creato un parametro corrispondente del report.|  
|![Esecuzione della query](../../reporting-services/report-data/media/rsqdicon-run.png "Esecuzione della query")|Consente di eseguire la query di e visualizzare i risultati nel riquadro Dati.|  
|![Cancel the query](../../reporting-services/report-data/media/rsqdicon-cancel.gif "Cancel the query")|Consente di annullare la query.|  
|![Passaggio alla modalità progettazione](../../reporting-services/media/rsqdicon-designmode.png "Passaggio alla modalità progettazione")|Consente di passare dalla modalità progettazione alla modalità query e viceversa.|  
  
## Finestra Progettazione query con interfaccia grafica in modalità query  
 Per modificare l'interfaccia grafica della finestra Progettazione query con interfaccia grafica attivando la modalità query, fare clic sul pulsante Mostra/Nascondi **Modalità progettazione** sulla barra degli strumenti.  
  
 Nella figura seguente vengono illustrati i componenti di Progettazione query in modalità query.  
  
 ![Progettazione query MDX per SAP BW in visualizzazione query](../../reporting-services/report-data/media/rsqd-dssapbw-mdx-querymode.gif "Progettazione query MDX per SAP BW in visualizzazione query")  
  
 Nella tabella seguente viene descritta la funzione di ogni riquadro.  
  
|Riquadro|Funzione|  
|----------|--------------|  
|Pulsante Seleziona cubo|Consente di visualizzare InfoCube, MultiProvider o altro cubo attualmente selezionato.|  
|Riquadro Metadati/Funzioni|Consente di visualizzare una finestra a schede che mostra un elenco dei metadati o delle funzioni utilizzabili per compilare il testo della query.|  
|Riquadro Variabili|Consente di visualizzare le variabili attualmente definite disponibili per l'utilizzo nella query.|  
|Riquadro query|Consente di visualizzare il testo della query corrente.|  
|Riquadro Risultati|Consente di visualizzare i risultati della query.|  
  
 Dal riquadro Metadati è possibile trascinare cifre chiave e dimensioni dalla scheda **Metadati** nel riquadro Query MDX. Il nome tecnico per i metadati viene inserito in corrispondenza del cursore. È possibile trascinare funzioni dalla scheda **Funzioni** nel riquadro Query MDX. Quando si esegue la query, nel riquadro Risultati verranno visualizzati i risultati per la query MDX corrente.  
  
 Se il cubo selezionato è una query Web, verrà richiesto di impostare valori predefiniti statici per le variabili esistenti. È possibile trascinare le variabili nel riquadro Query MDX.  
  
 Nei riquadri metadati e Variabili sono visualizzati i nomi descrittivi. Quando si trascinano gli oggetti nel riquadro Query MDX, verranno visualizzati i nomi tecnici necessari all'origine dei dati immessa nella query MDX.  
  
### Barra degli strumenti della finestra Progettazione query con interfaccia grafica in modalità query  
 I pulsanti della barra degli strumenti di Progettazione query consentono di progettare query MDX utilizzando l'interfaccia grafica. I pulsanti della barra degli strumenti sono identici in modalità progettazione e in modalità query, ma i pulsanti seguenti non sono abilitati in modalità query:  
  
-   **Modifica come testo**  
  
-   **Aggiungi membro calcolato** (![Aggiungi membro calcolato](../../reporting-services/report-data/media/rsqdicon-addcalculatedmember.png "Aggiungi membro calcolato"))  
  
-   **Mostra celle vuote** (![Mostra/Nascondi celle vuote](../../reporting-services/report-data/media/rsqdicon-showemptycells.png "Mostra/Nascondi celle vuote"))  
  
-   **Esecuzione automatica** (![Esecuzione automatica della query](../../reporting-services/report-data/media/rsqdicon-autoexecute.png "Esecuzione automatica della query"))  
  
-   **Elimina** (![Elimina](../../reporting-services/report-data/media/rsqdicon-delete.png "Elimina"))  
  
## Vedere anche  
 [Creare un set di dati condiviso o un set di dati incorporato &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [File di configurazione RSReportDesigner](../../reporting-services/report-server/rsreportdesigner-configuration-file.md)  
  
  