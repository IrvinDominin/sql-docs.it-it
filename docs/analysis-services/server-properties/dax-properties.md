---
title: "Propriet&#224; DAX | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: aa928dc5-d00d-4f8a-80b9-7e6973d2196c
caps.latest.revision: 6
author: "HeidiSteen"
ms.author: "heidist"
manager: "erikre"
caps.handback.revision: 6
---
# Propriet&#224; DAX
   La sezione DAX del file msmdsrv.ini contiene impostazioni che consentono di controllare particolari comportamenti delle query in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], ad esempio il limite superiore del numero di righe restituite in un set di risultati di query DAX. 
  
  Per i set di righe di maggiori dimensioni, ad esempio quelli restituiti nei modelli DirectQuery, l'impostazione predefinita pari a un milione di righe può risultare insufficiente. La necessità di adeguare il limite è segnalata da un messaggio di errore simile al seguente: "Il set di risultati di una query sull'origine dati esterna ha superato le dimensioni massime consentite di '1000000' righe."
 
Per aumentare il limite superiore, specificare l'impostazione di configurazione **MaxIntermediateRowSize**. Sarà necessario aggiungere manualmente l'intero elemento alla sezione DAX del file di configurazione. L'impostazione non è presente nel file fino a quando non viene aggiunta.
  
## Frammento di configurazione

```
<ConfigurationSettings>
. . .
<DAX>   
  <PredicateCheckSpoolCardinalityThreshold>5000
  </PredicateCheckSpoolCardinalityThreshold>
  <DQ>
     <MaxIntermediateRowsetSize>1000000
     </MaxIntermediateRowsetSize>
  </DQ>
</DAX>
. . . 
```

## Descrizioni delle proprietà

Impostazione |Valore |Description
--------|-------|-----------
MaxIntermediateRowsetSize | 1000000 | Numero massimo di righe restituito in una query DAX. Aggiungere manualmente questa voce al file msmdsrv.ini e aumentarne il valore se l'impostazione predefinita è troppo bassa. 
PredicateCheckSpoolCardinalityThreshold| 5000 | Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico Microsoft.

Per altre informazioni sulle proprietà aggiuntive del server e sulla relativa impostazione, vedere [Proprietà server in Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md). 