---
title: Visualizzare un report sui set di raccolta (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.reporthistory.calendar.f1
helpviewer_keywords:
- collection sets [SQL Server], viewing reports
- reports [SQL Server], viewing collection set
ms.assetid: c3b1e791-9aa1-4bba-9622-4954568e1820
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: eef644a11cdf99cc480303972b70925e3fd66d13
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48202671"
---
# <a name="view-a-collection-set-report-sql-server-management-studio"></a>Visualizzare un report sui set di raccolta (SQL Server Management Studio)
  Dopo avere configurato il data warehouse di gestione, è possibile visualizzare un report del set di raccolta in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. I report vengono forniti per i set di raccolta dati di sistema installati durante l'installazione Sono disponibili i report seguenti:  
  
-   Riepilogo utilizzo disco  
  
-   Cronologia statistiche query  
  
-   Cronologia attività server  
  
 Tramite questa procedura viene visualizzato il report per il set di raccolta **Utilizzo disco** . È possibile seguire la stessa procedura generale per visualizzare i report per gli altri set di raccolta dati di sistema.  
  
### <a name="to-view-a-collection-set-report"></a>Per visualizzare un report di un set di raccolta  
  
1.  Le tabelle necessarie per un report vengono create solo la prima volta che i dati raccolti vengono caricati. Se si tenta di visualizzare un report prima che venga effettuato il primo caricamento, si verifica un errore e non viene visualizzato alcun report. Per caricare dati per il set di raccolta Utilizzo disco, in Esplora oggetti espandere la cartella **Gestione** , espandere **Raccolta dati**e **Set di raccolta dati di sistema**, fare clic con il pulsante destro del mouse sul set di raccolta **Utilizzo disco** e quindi scegliere **Raccogli e carica**.  
  
2.  Per visualizzare il report, in Esplora oggetti espandere la cartella **Gestione** , fare clic con il pulsante destro del mouse su **Raccolta dati**, scegliere **Report**, **Data warehouse di gestione**e quindi fare clic su **Riepilogo utilizzo disco**.  
  
    > [!NOTE]  
    >  Alcuni report potrebbero mostrare un pulsante calendario sotto la cronologia della raccolta dati. Fare clic su questo pulsante per accedere al **Calendario report di raccolta dati**.  
  
#### <a name="data-collection-report-calendar"></a>Calendario report di raccolta dati  
 Utilizzare questa finestra di dialogo per specificare la data e l'ora di inizio e la durata relative ai dati per cui si desidera creare il report. Potrebbe essere necessario ad esempio creare un report relativo all'utilizzo del disco di un server per un periodo specifico di 12 ore mercoledì scorso.  
  
 **Data inizio**  
 Immettere una data iniziale per i dati del report o selezionarne una dal calendario.  
  
 **Ora inizio**  
 Immettere un'ora iniziale per i dati del report o fare clic sulle frecce per specificarne una.  
  
 **Durata**  
 Specificare l'intervallo di tempo da includere nel report. Il valore predefinito è 240 minuti. I valori che è possibile selezionare sono 15 minuti, 60 minuti, 240 minuti (4 ore), 720 minuti (12 ore) e 1440 minuti (24 ore).  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta dati](data-collection.md)   
 [Report personalizzati in Management Studio](../../ssms/object/custom-reports-in-management-studio.md)   
 [Configurare il data warehouse di gestione &#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  
