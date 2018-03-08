---
title: Ottimizzare le prestazioni della replica di tipo merge con gli articoli di solo download | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- merge replication [SQL Server replication], download-only articles
- articles [SQL Server replication], download-only
- download-only articles
ms.assetid: 8851faa6-e6df-4ea5-a6ea-2a3471680fa3
caps.latest.revision: "37"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7cf9009385126a41283ce8044acba2bd35d08867
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="optimize-merge-replication-performance-with-download-only-articles"></a>Ottimizzazione delle prestazioni della replica di tipo merge con gli articoli di solo download
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] La replica di tipo merge offre due tipi di articoli diversi per soddisfare le diverse esigenze applicative. Le pubblicazioni possono contenere uno o più di questi tipi di articoli in base al tipo di applicazione:  
  
-   Articoli standard  
  
-   articoli di solo download  
  
 Gli articoli di solo download sono vantaggiosi in termini di prestazioni rispetto agli articoli standard e se ne consiglia l'utilizzo laddove possibile.  
  
> [!NOTE]  
>  Per utilizzare questo tipo di articoli è necessario che il livello di compatibilità della pubblicazione sia impostato almeno su 90RTM.  
  
## <a name="standard-articles"></a>Articoli standard  
 Gli articoli standard sono quelli predefiniti e offrono l'intera gamma di funzionalità della replica di tipo merge, tra cui il rilevamento e la risoluzione dei conflitti. Sono inoltre adatti per le tabelle che vengono aggiornate da più Sottoscrittori. Oggetti diversi dalle tabelle, come stored procedure e viste, vengono sempre pubblicati come articoli standard.  
  
## <a name="download-only-articles"></a>articoli di solo download  
 Gli articoli di solo download sono progettati per le applicazioni contenenti dati che non vengono aggiornati nei Sottoscrittori, ad esempio un set di articoli contenuti in un catalogo prodotti. Un catalogo prodotti viene generalmente aggiornato nel server di pubblicazione, ma non nei Sottoscrittori. Poiché non è possibile aggiornare gli articoli di solo download nel Sottoscrittore, i metadati di rilevamento non vengono inviati ai Sottoscrittori. Ciò può comportare uno spazio di archiviazione ridotto sui Sottoscrittori e un vantaggio in termini di prestazioni, soprattutto se la connessione di rete è lenta.  
  
 Gli articoli di solo download operano insieme ai sottoscrittori client, ovvero se un articolo è progettato come di solo download, non è possibile inserire, aggiornare o eliminare righe per tale articolo nei Sottoscrittori che utilizzano sottoscrizioni client. I server di pubblicazione e i Sottoscrittori che utilizzano il tipo di sottoscrizione server (generalmente Sottoscrittori che ripubblicano dati in altri Sottoscrittori) possono inserire, aggiornare ed eliminare dati. Per altre informazioni sulle sottoscrizioni client, vedere [Sottoscrivere le pubblicazioni](../../../relational-databases/replication/subscribe-to-publications.md).  
  
 Per specificare che un articolo è di solo download, vedere [Specify That a Merge Table Article is Download-Only](../../../relational-databases/replication/publish/specify-that-a-merge-table-article-is-download-only.md).  
  
## <a name="using-different-article-types-in-your-applications"></a>Utilizzo di tipi di articolo differenti nelle applicazioni  
 Se si analizzano i requisiti dell'applicazione in uso, è possibile valutare la soluzione migliore tra massima flessibilità e prestazioni ottimali. Le applicazioni caratterizzate da numerosi conflitti e modifiche sia nel server di pubblicazione che nei Sottoscrittori utilizzeranno, ad esempio, una pubblicazione costituita da articoli standard. Alcune applicazioni, come quelle di automazione della forza vendita (SFA), possono contenere articoli potenzialmente soggetti a conflitti e altri articoli che fungono da tabelle di ricerca e che possono essere specificati come di solo download. Le applicazioni di immissione dati, ad esempio i sistemi POS (Point Of Sales) e le applicazioni di automazione del personale esterno (FFA), spesso partizionano i dati in modo da eliminare i conflitti e non consentirne il passaggio da un Sottoscrittore all'altro. In queste situazioni una combinazione di partizioni non sovrapposte, di articoli di solo download e di partizioni pre-calcolate garantisce prestazioni e scalabilità massime. Per ulteriori informazioni sulle partizioni non sovrapposte e pre-calcolate, vedere [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni degli articoli per la replica di tipo merge](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)   
 [Ottimizzare le prestazioni della replica di tipo merge con il rilevamento condizionale delle eliminazioni](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-conditional-delete-tracking.md)  
  
  
