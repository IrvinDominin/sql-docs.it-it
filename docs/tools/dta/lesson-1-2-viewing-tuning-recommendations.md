---
title: Visualizzazione delle indicazioni di ottimizzazione | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: dta
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-query-tuning
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords: Database Engine [SQL Server], tutorials
ms.assetid: e4e690c9-434f-4b01-b4de-0b905323ddd6
caps.latest.revision: "25"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 634534fb9fa7f97e61431a481ab847bd87e2806a
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="lesson-1-2---viewing-tuning-recommendations"></a>Lezione 1-2 - visualizzazione indicazioni di ottimizzazione
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Questa attività viene utilizzata la sessione di ottimizzazione che è stato creato in [ottimizzazione di un carico di lavoro](../../tools/dta/lesson-1-1-tuning-a-workload.md). Dopo aver ottimizzato il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] tramite lo script [!INCLUDE[tsql](../../includes/tsql-md.md)] MyScript.sql, Ottimizzazione guidata [!INCLUDE[ssDE](../../includes/ssde-md.md)] visualizza i risultati nella scheda **Indicazioni** . L'attività seguente presenta la scheda **Indicazioni** dell'interfaccia utente grafica di Ottimizzazione guidata [!INCLUDE[ssDE](../../includes/ssde-md.md)] e descrive come visualizzare le informazioni della scheda sui risultati della sessione di ottimizzazione.  
  
### <a name="view-tuning-recommendations"></a>Visualizzazione delle indicazioni di ottimizzazione  
  
1.  Avviare Ottimizzazione guidata [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Vedere [Avvio dello strumento Ottimizzazione guidata motore di database](../../tools/dta/lesson-1-1-launching-database-engine-tuning-advisor.md). Verificare di essere connessi alla stessa istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usata nell'esercitazione [Ottimizzazione di un carico di lavoro](../../tools/dta/lesson-1-1-tuning-a-workload.md).  
  
2.  Nel riquadro **Monitoraggio sessione** fare doppio clic su **MySession** . [!INCLUDE[ssDE](../../includes/ssde-md.md)]Ottimizzazione guidata Carica le informazioni sulla sessione dalla sessione di ottimizzazione precedente e viene visualizzato il **indicazioni** scheda. Si noti che in Ottimizzazione guidata [!INCLUDE[ssDE](../../includes/ssde-md.md)] non sono disponibili **Indicazioni relative alle partizioni** dal momento che sono state accettate tutte le opzioni di ottimizzazione predefinite ed è stata selezionata l'opzione **Nessun partizionamento** nella scheda **Opzioni di ottimizzazione** .  
  
3.  Nella scheda **Indicazioni** usare la barra di scorrimento disponibile nella parte inferiore della pagina a schede per visualizzare le colonne **Indicazioni relative agli indici** . Ogni riga rappresenta un oggetto di database (ovvero indici o viste indicizzate) che Ottimizzazione guidata [!INCLUDE[ssDE](../../includes/ssde-md.md)] consiglia di eliminare o creare. Scorrere fino alla colonna all'estrema destra e fare clic su **Definizione**. [!INCLUDE[ssDE](../../includes/ssde-md.md)]Ottimizzazione guidata consente di visualizzare un **anteprima Script SQL** finestra in cui è possibile visualizzare il [!INCLUDE[tsql](../../includes/tsql-md.md)] script che crea o Elimina l'oggetto di database in tale riga. Fare clic su **Chiudi** per chiudere la finestra di anteprima.  
  
    In caso di difficoltà nell'individuazione di una **Definizione** contenente un collegamento, deselezionare la casella di controllo **Mostra oggetti esistenti** nella parte inferiore della pagina a schede. In questo modo verrà ridotto il numero di righe visualizzate. Quando viene deselezionata questa casella di controllo, in Ottimizzazione guidata [!INCLUDE[ssDE](../../includes/ssde-md.md)] vengono visualizzati solo gli oggetti per i quali è stata generata un'indicazione. Selezionare la casella di controllo **Mostra oggetti esistenti** per visualizzare tutti gli oggetti di database attualmente esistenti nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Utilizzare la barra di scorrimento sul lato sinistro della pagina a schede per visualizzare tutti gli oggetti.  
  
4.  Fare clic con il pulsante destro del mouse sulla griglia nel riquadro **Indicazioni relative agli indici** . Il menu di scelta rapida consente di selezionare e deselezionare le indicazioni. Consente inoltre di modificare il carattere del testo utilizzato nella griglia.  
  
5.  Scegliere **Salva indicazioni** dal menu **Azioni** per salvare tutte le indicazioni in uno script [!INCLUDE[tsql](../../includes/tsql-md.md)] . Denominare lo script **MySessionRecommendations.sql**.  
  
    Aprire lo script MySessionRecommendations.sql nell'editor di query di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per visualizzarlo. Sebbene sia possibile applicare le indicazioni al database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] eseguendo lo script nell'editor di query, ciò non è consigliabile. Chiudere lo script nell'editor di query senza eseguirlo.  
  
    In alternativa, è possibile applicare le indicazioni scegliendo **Applica indicazioni** dal menu **Azioni** di Ottimizzazione guidata [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Si consiglia tuttavia di non applicare le indicazioni in questa esercitazione.  
  
6.  Se nella scheda **Indicazioni** sono disponibili più indicazioni, deselezionare alcune righe relative agli oggetti di database nella griglia **Indicazioni relative agli indici** .  
  
7.  Scegliere **Valuta indicazioni** dal menu **Azioni**. [!INCLUDE[ssDE](../../includes/ssde-md.md)] Ottimizzazione guidata crea una nuova sessione di ottimizzazione nella quale è possibile valutare un subset delle indicazioni originali di MySession.  
  
8.  Digitare **EvaluateMySession** come nuovo **Nome sessione**e fare clic sul pulsante **Avvia analisi** sulla barra degli strumenti. È possibile ripetere i passaggi 2 e 3 per questa nuova sessione di ottimizzazione in modo da visualizzare le indicazioni.  
  
## <a name="summary"></a>Riepilogo  
In questa attività è stato illustrato il contenuto della scheda **Indicazioni** per la sessione di ottimizzazione MySession ed è stato valutato un subset di indicazioni nella nuova sessione di ottimizzazione EvaluateMySession.  
  
La valutazione di un subset di indicazioni può essere necessaria se le opzioni di ottimizzazione devono essere modificate dopo aver eseguito una sessione. Si supponga ad esempio di richiedere a Ottimizzazione guidata [!INCLUDE[ssDE](../../includes/ssde-md.md)] di considerare le viste indicizzate quando si specificano le opzioni di ottimizzazione per una sessione, ma che dopo la generazione dell'indicazione si decida di non utilizzare le viste indicizzate. In questo caso è possibile scegliere **Valuta indicazioni** dal menu **Azioni** per valutare nuovamente la sessione in Ottimizzazione guidata [!INCLUDE[ssDE](../../includes/ssde-md.md)] senza tenere in considerazione le viste indicizzate. Quando viene utilizzata l'opzione **Valuta indicazioni** , le indicazioni generate precedentemente vengono applicate in maniera ipotetica alla progettazione fisica corrente per poi arrivare alla progettazione fisica per la seconda sessione di ottimizzazione.  
  
Altre informazioni sui risultati delle ottimizzazioni sono disponibili nella scheda **Report** che verrà illustrata nell'attività successiva di questa lezione.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Visualizzazione dei report di ottimizzazione](../../tools/dta/lesson-1-3-viewing-tuning-reports.md)  
  
  
  
