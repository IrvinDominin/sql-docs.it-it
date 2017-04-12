---
title: "Editor trasformazione Conversione dati | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.dataconversiontransformation.f1"
helpviewer_keywords: 
  - "Editor trasformazione Conversione dati"
ms.assetid: 7b4e4873-e8fe-4549-a965-65bebdb270bc
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# Editor trasformazione Conversione dati
  Usare la finestra di dialogo **Editor trasformazione Conversione dati** per selezionare le colonne da convertire e i tipi di dati in cui convertire la colonna e impostare gli attributi di conversione.  
  
> [!NOTE]  
>  La proprietà **FastParse** delle colonne di output della trasformazione Conversione dati non è disponibile nell'**Editor trasformazione Conversione dati** ma può essere impostata tramite l'**Editor avanzato**. Per altre informazioni su questa proprietà, vedere la sezione relativa alla trasformazione Conversione dati in [Proprietà personalizzate delle trasformazioni](../../../integration-services/data-flow/transformations/transformation-custom-properties.md).  
  
 Per sapere di più sulla trasformazione conversione dati, vedere [Trasformazione Conversione dati](../../../integration-services/data-flow/transformations/data-conversion-transformation.md).  
  
## Opzioni  
 **Colonne di input disponibili**  
 Consente di selezionare le colonne da convertire utilizzando le caselle di controllo. Le selezioni effettuate determinano l'aggiunta delle colonne di input nella tabella sottostante.  
  
 **Colonna di input**  
 Consente di selezionare le colonne da convertire nell'elenco delle colonne di input disponibili. Le selezioni effettuate vengono riflesse nelle selezioni delle caselle di controllo descritte in precedenza.  
  
 **Alias di output**  
 Consente di digitare un alias per ogni nuova colonna. L'impostazione predefinita è **Copia di** seguita dal nome della colonna di input.  È comunque possibile scegliere qualsiasi nome descrittivo univoco.  
  
 **Tipo di dati**  
 Consente di selezionare un tipo di dati disponibile nell'elenco. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../../integration-services/data-flow/integration-services-data-types.md).  
  
 **Length**  
 Consente di selezionare la lunghezza della colonna per dati di tipo stringa.  
  
 **Precisione**  
 Consente di impostare la precisione per dati numerici.  
  
 **Scala**  
 Consente di impostare la scala per dati numerici.  
  
 **Tabella codici**  
 Consente di selezionare la tabella codici appropriata per le colonne di tipo DT_STR.  
  
 **Configura output errori**  
 Consente di indicare come gestire gli errori tramite la finestra di dialogo [Configura output errori](../Topic/Configure%20Error%20Output.md).  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Conversione di dati in un tipo di dati diverso utilizzando la trasformazione Conversione dati](../../../integration-services/data-flow/transformations/convert-data-type-by-using-data-conversion-transformation.md)  
  
  