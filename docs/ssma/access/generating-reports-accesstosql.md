---
title: Generazione di report (AccessToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-access
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
ms.assetid: abb4264a-622e-4215-af5b-14e309b8a399
caps.latest.revision: "7"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8e8af206d514c49676cde2c2d26b9cbb01575803
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="generating-reports-accesstosql"></a>Generazione di report (AccessToSQL)
I report di determinate attività eseguite utilizzando i comandi vengono generati nella Console di SSMA a livello di struttura ad albero di oggetti.  
  
Utilizzare la procedura seguente per generare rapporti:  
  
1.  Specificare il **scrittura riepilogo-report-a-** parametro. Il report viene archiviato come il nome del file (se specificato) o nella cartella specificati. Il nome del file è di sistema predefiniti come indicato nella tabella seguente, dove  **&lt; n &gt;**  è il numero di file univoco che viene incrementato con una cifra a ogni esecuzione del comando stesso.  
  
    I comandi nei confronti di report sono:  
  
    ||||  
    |-|-|-|  
    |**SL. No.**|**Command**|**Titolo del report**|  
    |1|generare report di valutazione|AssessmentReport&lt;n&gt;. XML|  
    |2|Converti schema|SchemaConversionReport&lt;n&gt;. XML|  
    |3|eseguire la migrazione di dati|DataMigrationReport&lt;n&gt;. XML|  
    |4|sincronizzare-destinazione|TargetSynchronizationReport&lt;n&gt;. XML|  
    |5|aggiornamento da database|SourceDBRefreshReport&lt;n&gt;. XML|  
  
    > [!IMPORTANT]  
    > Un report di output è diverso dalla relazione di valutazione. Il primo è un report sulle prestazioni di un comando eseguito durante, quest'ultimo è un report XML per l'utilizzo a livello di codice.  
  
    Per le opzioni di comando per i report di output (da Sl. No. 2-4 sopra), consultare il [in esecuzione la Console di SSMA &#40; AccessToSQL &#41; ](../../ssma/access/executing-the-ssma-console-accesstosql.md) sezione.  
  
2.  Indica il livello di dettaglio desiderato nel report di output utilizzando le impostazioni di Report livello di dettaglio:  
  
    ||||  
    |-|-|-|  
    |**SL. No.**|**Comando e parametro**|**Descrizione di output**|  
    |1|verbose = "false"|Genera un report di riepilogo dell'attività.|  
    |2|verbose = "true"|Genera un report di riepilogo e dettagliate sullo stato per ogni attività.|  
  
    > [!NOTE]  
    > Le impostazioni del livello di dettaglio Report specificata in precedenza sono applicabili per generare report di valutazione, convert-schema, i comandi di eseguire la migrazione di dati.  
  
3.  Indica il livello di dettaglio desiderato nei report di errore utilizzando le impostazioni di segnalazione errori:  
  
    ||||  
    |-|-|-|  
    |**SL. No.**|**Comando e parametro**|**Descrizione di output**|  
    |1|report errori = "false"|Nessun dettaglio in caso di errore / avviso / i messaggi di informazioni.|  
    |2|report errori = "true"|Ulteriori informazioni sull'errore / avviso / i messaggi di informazioni.|  
  
    > [!NOTE]  
    > Le impostazioni di segnalazione di errori specificato in precedenza sono applicabili per generare report di valutazione, convert-schema, i comandi di eseguire la migrazione di dati.  
  
**Esempio:**  
  
```xml  
<generate-assessment-report  
  
    object-name="testschema"  
  
    object-type="Schemas"  
  
    verbose="yes"  
  
    report-erors="yes"  
  
    write-summary-report-to="$AssessmentFolder$\Report1.xml"  
  
    assessment-report-folder="$AssessmentFolder$\assesment_report"  
  
    assessment-report-overwrite="true"  
  
/>  
```  
  
### <a name="synchronize-target"></a>destinazione sincronizzare:  
Il comando **destinazione sincronizzare** è **report errori di** parametro che specifica il percorso del report di errore per l'operazione di sincronizzazione. Quindi, un file con nome **TargetSynchronizationReport&lt;n&gt;. XML** viene creato nel percorso specificato, in cui  **&lt; n &gt;**  è il numero di file univoco che viene incrementato con una cifra a ogni esecuzione del comando stesso.  
  
**Nota:** se viene specificato il percorso della cartella, quindi 'report errori-a-' parametro diventa un attributo facoltativo per il comando 'sincronizzare-target'.  
  
```xml  
<!-- Example: Synchronize target entire Database with all attributes-->  
  
<synchronize-target  
  
    object-name="$TargetDB$.dbo"  
  
    on-error="fail-script"  
  
    report-errors-to="$SynchronizationReports$"  
  
/>  
```  
**il nome di oggetto:** specifica gli oggetti considerati per la sincronizzazione (può anche avere un nome di oggetto gruppo o nomi di oggetto di indivdual).  
  
**Errore:** specifica se specificare gli errori di sincronizzazione come avvisi o errori. Opzioni disponibili in errore:  
  
-   Totale report come avviso  
  
-   report-ogni-come-avviso  
  
-   Errore-script  
  
### <a name="refresh-from-database"></a>l'aggiornamento dal database:  
Il comando **l'aggiornamento da database** è **report errori di** parametro che specifica il percorso del report di errore per l'operazione di aggiornamento. Quindi, un file con nome **SourceDBRefreshReport&lt;n&gt;. XML** viene creato nel percorso specificato, in cui  **&lt; n &gt;**  è il numero di file univoco che viene incrementato con una cifra a ogni esecuzione del comando stesso.  
  
**Nota:** se viene specificato il percorso della cartella, quindi 'report errori-a-' parametro diventa un attributo facoltativo per il comando 'sincronizzare-target'.  
  
```xml  
<!-- Example: Refresh entire Schema (with all attributes)-->  
  
<refresh-from-database  
  
    object-name="$SourceDatabaseStandard$"  
  
    object-type ="Databases"  
  
    on-error="fail-script"  
  
    report-errors-to="$RefreshDBFolder$\RefreshReport.xml"  
  
/>  
```  
**il nome di oggetto:** specifica gli oggetti considerati per l'aggiornamento (può anche avere un nome di oggetto gruppo o nomi di oggetto di indivdual).  
  
**Errore:** specifica se specificare gli errori di aggiornamento come avvisi o errori. Opzioni disponibili in errore:  
  
-   Totale report come avviso  
  
-   report-ogni-come-avviso  
  
-   Errore-script  
  
## <a name="see-also"></a>Vedere anche  
[L'esecuzione la Console SSMA (accesso)](http://msdn.microsoft.com/en-us/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  
