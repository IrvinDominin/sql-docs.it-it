---
title: 'Attività 3: Creazione ed esecuzione di un progetto Data Quality per la corrispondenza | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 6260e911-ea8b-4c69-a39d-d1bccd565a32
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 00f4c86dd09dd9b88959415459151d4cef518d57
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099531"
---
# <a name="task-3-creating-and-running-a-data-quality-project-for-matching"></a>Attività 3: Creazione ed esecuzione di un progetto Data Quality per la corrispondenza
  In questa attività viene creato un progetto Data Quality per l'attività di corrispondenza e viene eseguito il processo di corrispondenza nei dati puliti del fornitore per rimuovere tutti i duplicati nei dati.  
  
1.  Nella pagina principale della **Client DQS**, fare clic su **nuovo progetto Data Quality**.  
  
2.  Tipo di **Rimuovi duplicati fornitore** dalle **nome del progetto**.  
  
3.  Selezionare **Suppliers** dall'elenco di Knowledge base per il **Usa Knowledge Base** campo. Sono stati creati i criteri di corrispondenza in questa Knowledge Base nella lezione precedente.  
  
4.  Selezionare **corrispondenti** dalle **l'elenco di attività** nel riquadro in basso a destra.  
  
     ![Nuovo progetto di Data Quality - corrispondenza selezionata](../../2014/tutorials/media/et-creatingandrunningadqpformatching.jpg "nuovo progetto di Data Quality - corrispondenza selezionata")  
  
5.  Scegliere **Avanti**.  
  
6.  Nella pagina **Mappa** selezionare **File di Excel** per **Origine dati**.  
  
7.  Fare clic su **esplorare** e selezionare **Cleansed Supplier List. xls**, ovvero il file di output dell'attività di pulizia.  
  
8.  Mappa **SupplierID** colonna di origine per il **Supplier ID** dominio **Supplier Name** colonna da **Supplier Name** al dominio e **ContactEmailAddress** colonna **Contact Email** dominio.  
  
9. Fare clic su **successivo** per passare alle **corrispondenti** pagina.  
  
10. Fare clic su **avviare** per avviare il processo di corrispondenza. Verranno visualizzati risultati simili a quelli dell'attività precedente poiché è stato utilizzato lo stesso file di input per la definizione dei criteri di corrispondenza.  
  
11. Controllare tutti i record corrispondenti e il punteggio di corrispondenza nella casella di riepilogo. I risultati devono essere uguali a quelli visualizzati nell'attività precedente. Vedere i passaggi dell'attività precedente per analizzare i risultati di questa attività di corrispondenza.  
  
12. Fare clic su **successivo** per passare alle **esportare** pagina.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 4: Esportazione dei risultati dell'attività di corrispondenza in un file di Excel](../../2014/tutorials/task-4-exporting-the-results-from-matching-activity-to-an-excel-file.md)  
  
  
