---
title: "Estrazione dei dati tramite l&#39;origine XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "estrazione di dati [Integration Services]"
  - "origini [Integration Services], XML"
  - "origine XML [Integration Services]"
ms.assetid: 5d5be54c-2b7e-4957-9193-c5ea5c5d6d15
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 21
---
# Estrazione dei dati tramite l&#39;origine XML
  È possibile aggiungere e configurare un'origine XML solo se il pacchetto include già almeno un'attività Flusso di dati.  
  
### Per estrarre dati tramite un'origine XML  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di dati** e quindi, dalla **casella degli strumenti**, trascinare l'origine XML sull'area di progettazione.  
  
4.  Fare doppio clic sull'origine XML.  
  
5.  Nella pagina **Gestione connessione** della finestra di dialogo **Editor origine XML** selezionare una modalità di accesso ai dati:  
  
    -   Per la modalità di accesso **Percorso file XML**, fare clic su **Sfoglia** e individuare la cartella che contiene il file XML.  
  
    -   Per la modalità di accesso **File XML da variabile**, selezionare la variabile definita dall'utente che contiene il percorso del file XML.  
  
    -   Per la modalità di accesso **Dati XML da variabile**, selezionare la variabile definita dall'utente che contiene i dati XML.  
  
    > [!NOTE]  
    >  La variabile deve essere definita nell'ambito dell'attività Flusso di dati che contiene l'origine XML, oppure nell'ambito del pacchetto, e deve avere un tipo di dati string.  
  
6.  Facoltativamente, selezionare **Usa schema inline** per indicare che il documento XML include informazioni sullo schema.  
  
7.  Per specificare uno schema XSD (XML Schema Definition Language) esterno per il file XML, eseguire una delle operazioni seguenti:  
  
    -   Fare clic su **Sfoglia** per individuare un file XSD esistente.  
  
    -   Fare clic su **Genera XSD** per creare un file XSD dal file XML.  
  
8.  Per aggiornare i nomi delle colonne di output, fare clic su **Colonne** e modificare i valori nell'elenco **Colonna di output**.  
  
9. Per configurare l'output degli errori, fare clic su **Output errori**. Per altre informazioni, vedere [Configurare un output degli errori in un componente del flusso di dati](../../integration-services/troubleshooting/configure-an-error-output-in-a-data-flow-component.md).  
  
10. Scegliere **OK**.  
  
11. Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
## Vedere anche  
 [Origine XML](../../integration-services/data-flow/xml-source.md)   
 [Trasformazioni di Integration Services](../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Percorsi in Integration Services](../../integration-services/data-flow/integration-services-paths.md)   
 [Attività Flusso di dati](../../integration-services/control-flow/data-flow-task.md)  
  
  