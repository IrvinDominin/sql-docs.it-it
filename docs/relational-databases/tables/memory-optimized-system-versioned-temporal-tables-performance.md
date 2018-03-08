---
title: Prestazioni delle tabelle temporali con controllo delle versioni di sistema e ottimizzazione per la memoria | Microsoft Docs
ms.custom: 
ms.date: 03/28/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: tables
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e110984-7703-4806-a24b-b41e8c3018c6
caps.latest.revision: "14"
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0cc7a8ac4a47a479e87702ddd429a95ca00b8336
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="memory-optimized-system-versioned-temporal-tables-performance"></a>Prestazioni delle tabelle temporali con controllo delle versioni di sistema e ottimizzazione per la memoria
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Questo argomento presenta alcune considerazioni sulle prestazioni specifiche quando si usano le tabelle temporali ottimizzate per la memoria con controllo delle versioni di sistema.  
  
-   Quando si aggiunge il controllo elle versioni di sistema a una tabella non temporale è prevedibile un impatto sulle prestazioni nelle operazioni di aggiornamento ed eliminazione perché la tabella di cronologia viene aggiornata automaticamente.  
  
-   Ogni operazione di aggiornamento ed eliminazione viene registrata nella tabella di cronologia ottimizzata per la memoria interna, per cui può verificarsi un utilizzo imprevisto di memoria se il carico di lavoro fa un uso massiccio di queste due operazioni. Pertanto si consiglia quanto segue:  
  
    -   Non eseguire eliminazioni massicce dalla tabella corrente per aumentare la RAM disponibile con la pulizia dello spazio. È consigliabile eliminare manualmente i dati in più batch intervallando lo scaricamento dati richiamato manualmente richiamando [sp_xtp_flush_temporal_history](../../relational-databases/system-stored-procedures/temporal-table-sp-xtp-flush-temporal-history.md)oppure mentre **SYSTEM_VERSIONING = OFF**.  
  
    -   Non eseguire aggiornamenti massicci della tabella in una sola volta perché questo può comportare un consumo di memoria due volte superiore rispetto alla memoria necessaria per aggiornare una tabella non temporale ottimizzata per la memoria. Il consumo di memoria raddoppiato è temporaneo perché l'attività di svuotamento dati è regolarmente all'opera per mantenere il consumo di memoria della tabella di staging interna entro i limiti previsti per lo stato stabile (circa il 10% del consumo di memoria della tabella temporale corrente). È consigliabile eseguire gli aggiornamenti massicci in più batch o mentre **SYSTEM_VERSIONING = OFF**, ad esempio usando gli aggiornamenti per impostare i valori predefiniti per le colonne aggiunte.  
  
-   Il periodo di attivazione per le attività di scaricamento dati non è configurabile ma è possibile applicare il processo richiamando [sp_xtp_flush_temporal_history](../../relational-databases/system-stored-procedures/temporal-table-sp-xtp-flush-temporal-history.md).  
  
-   Si consiglia di usare columnstore cluster come opzione di archiviazione per la tabella di cronologia basata su disco, soprattutto se si prevede di eseguire query di analisi sui dati cronologici che usano funzioni di aggregazione o windowing. In questo caso columnstore cluster è una soluzione ottimale per la tabella di cronologia perché fornisce una buona compressione dei dati e si comporta in modo "favorevole all'inserimento", in linea con il modo in cui vengono generati i dati cronologici.  
  
## <a name="did-this-article-help-you-were-listening"></a>Questo articolo è stato utile? Commenti e suggerimenti  
 Quali informazioni si stanno cercando? La ricerca ha restituito i risultati desiderati? Microsoft incoraggia gli utenti a inviare i propri commenti per migliorare i contenuti Inviare eventuali commenti all'indirizzo [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Performance%20Considerations%20with%20Memory-Optimized%20System-Versioned%20Temporal%20Tables%20page)  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle temporali con controllo delle versioni di sistema con tabelle con ottimizzazione per la memoria](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Creazione di una tabella temporale con controllo delle versioni di sistema e ottimizzazione per la memoria](../../relational-databases/tables/creating-a-memory-optimized-system-versioned-temporal-table.md)   
 [Utilizzo di una tabella temporale con controllo delle versioni di sistema e ottimizzazione per la memoria](../../relational-databases/tables/working-with-memory-optimized-system-versioned-temporal-tables.md)   
 [Monitoraggio di una tabella temporale con controllo delle versioni di sistema e ottimizzazione per la memoria](../../relational-databases/tables/monitoring-memory-optimized-system-versioned-temporal-tables.md)   
 [Tabelle temporali](../../relational-databases/tables/temporal-tables.md)   
 [Verifiche di coerenza del sistema della tabella temporale](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [Gestire la conservazione dei dati cronologici nelle tabelle temporali con controllo delle versioni di sistema](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Funzioni e viste per i metadati delle tabelle temporali](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  
