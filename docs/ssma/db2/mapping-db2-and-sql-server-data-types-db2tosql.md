---
title: Mapping di DB2 e tipi di dati SQL Server (DB2ToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-db2
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: e7e939a8-5e76-4509-beaf-5acd1cab505e
caps.latest.revision: "5"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 88d98ac264e853a2bc94be002c2c2e4eeadee9ff
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="mapping-db2-and-sql-server-data-types-db2tosql"></a>Mapping di DB2 e tipi di dati SQL Server (DB2ToSQL)
Tipi di database DB2 sono diversi da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipi di database. Quando si esegue la conversione di oggetti di database DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oggetti, è necessario specificare come eseguire il mapping dei tipi di dati da DB2 a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. È possibile accettare i mapping dei tipi di dati predefinito oppure è possibile personalizzare i mapping, come illustrato nelle sezioni seguenti.  
  
## <a name="default-mappings"></a>Mapping predefiniti  
SSMA è un set predefinito di mapping dei tipi di dati. Per l'elenco dei mapping predefiniti, vedere [impostazioni progetto &#40; Mapping dei tipi di &#41; &#40; DB2ToSQL &#41; ](../../ssma/db2/project-settings-type-mapping-db2tosql.md).  
  
## <a name="type-mapping-inheritance"></a>Mapping di ereditarietà dei tipi  
È possibile personalizzare i mapping dei tipi a livello di progetto, il livello di categoria oggetto (ad esempio, tutte le stored procedure) o livello di oggetto. Le impostazioni vengono ereditate da un livello più alto, a meno che vengano sostituiti con un livello inferiore. Ad esempio, se si esegue il mapping **smallmoney** a **money** a livello di progetto, tutti gli oggetti nel progetto utilizzerà questo mapping, a meno che per personalizzare il mapping a livello di oggetto o alla categoria.  
  
Quando si visualizza il **del mapping dei tipi** scheda SSMA, lo sfondo è contraddistinte da colore per mostrare il mapping dei tipi vengono ereditati. Lo sfondo di un mapping dei tipi è giallo per il mapping dei tipi ereditati e bianco per qualsiasi mapping specificato al livello corrente.  
  
## <a name="customizing-data-type-mappings"></a>Personalizzazione dei mapping dei tipi di dati  
La procedura seguente viene illustrato come eseguire il mapping di tipi di dati nel progetto, database o il livello di oggetto:  
  
**Per eseguire il mapping di tipi di dati**  
  
1.  Per personalizzare i mapping dei tipi di dati per l'intero progetto, aprire il **impostazioni progetto** la finestra di dialogo:  
  
    1.  Nel **strumenti** dal menu **impostazioni progetto**.  
  
    2.  Nel riquadro a sinistra, selezionare **del mapping dei tipi**.  
  
        Il grafico di mapping di tipo e i pulsanti vengono visualizzati nel riquadro di destra.  
  
    In alternativa, per personalizzare il tipo di dati mapping a livello di database, tabella, vista o stored procedure, selezionare il database, la categoria dell'oggetto oppure l'oggetto in Visualizzatore metadati DB2:  
  
    1.  Nel Visualizzatore metadati DB2, selezionare la cartella o oggetto da personalizzare.  
  
    2.  Nel riquadro di destra, fare clic su di **del mapping dei tipi** scheda.  
  
2.  Per aggiungere un nuovo mapping, eseguire le operazioni seguenti:  
  
    1.  Scegliere **Aggiungi**.  
  
    2.  In **tipo di origine**, selezionare il tipo di dati DB2 per eseguire il mapping.  
  
    3.  Se il tipo richiede una lunghezza, specificare la lunghezza minima di dati per il mapping nel **da** casella e la lunghezza massima dei dati nel **a** casella.  
  
        Ciò consente di personalizzare il mapping dei dati per i valori di dimensioni minori e più grandi dello stesso tipo di dati.  
  
    4.  In **tipo di destinazione**, selezionare la destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipo di dati.  
  
        Alcuni tipi richiedono una lunghezza di tipo di dati di destinazione. Se necessario, immettere la nuova lunghezza dei dati nel **sostituire** casella.  
  
    5.  [!INCLUDE[clickOK](../../includes/clickok_md.md)]  
  
3.  Per modificare un mapping dei tipi di dati, eseguire le operazioni seguenti:  
  
    1.  Fare clic su **Modifica**.  
  
    2.  In **tipo di origine**, selezionare il tipo di dati DB2 per eseguire il mapping.  
  
    3.  Se il tipo richiede una lunghezza, specificare la lunghezza minima di dati per il mapping nel **da** casella e la lunghezza massima dei dati nel **a** casella.  
  
        Ciò consente di personalizzare il mapping dei dati per i valori di dimensioni minori e più grandi dello stesso tipo di dati.  
  
    4.  In **tipo di destinazione**, selezionare la destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipo di dati.  
  
        Alcuni tipi richiedono una lunghezza di tipo di dati di destinazione. Se necessario, immettere la nuova lunghezza dei dati nel **sostituire** casella, quindi[!INCLUDE[clickOK](../../includes/clickok_md.md)]  
  
4.  Per rimuovere un mapping dei tipi di dati personalizzati, effettuare le operazioni seguenti:  
  
    1.  Selezionare la riga nell'elenco di mapping di tipo che contiene il mapping dei tipi di dati che si desidera rimuovere.  
  
    2.  Scegliere **Rimuovi**.  
  
        È possibile rimuovere i mapping ereditati. Tuttavia, i mapping ereditati vengono sovrascritte dai mapping personalizzati in un oggetto specifico o una categoria dell'oggetto.  
  
## <a name="next-steps"></a>Next Steps  
Il passaggio successivo del processo di migrazione è su [DB2ToSQL valutazione Report &#40; &#41;](../../ssma/db2/assessment-report-db2tosql.md) o [DB2ToSQL la conversione di schemi di DB2 &#40; &#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md). Se si crea una relazione di valutazione, gli oggetti DB2 vengono convertiti automaticamente durante la valutazione.  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database DB2 a SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
