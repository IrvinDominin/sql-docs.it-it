---
title: Generazione di report (MySQLToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-mysql
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
helpviewer_keywords: Generating reports
ms.assetid: 1c0202e8-546d-4cb3-a37f-1d2e35d53839
caps.latest.revision: "6"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: baf2bf9e68f60bd4c9f2afc7033430e19ef96a3e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="generating-reports-mysqltosql"></a>Generazione di report (MySQLToSQL)
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
    |4|Convert-istruzione|ConvertSQLReport&lt;n&gt;. XML|  
    |5|sincronizzare-destinazione|TargetSynchronizationReport&lt;n&gt;. XML|  
    |6|aggiornamento da database|SourceDBRefreshReport&lt;n&gt;. XML|  
  
    > [!IMPORTANT]  
    > Un report di output è diverso dalla relazione di valutazione. Il primo è un report sulle prestazioni di un comando eseguito durante, quest'ultimo è un report XML per l'utilizzo a livello di codice.  
  
    Per le opzioni di comando per i report di output (da Sl. No. 2-4 sopra), consultare il [in esecuzione la Console di SSMA &#40; MySQLToSQL &#41; ](../../ssma/mysql/executing-the-ssma-console-mysqltosql.md) sezione.  
  
2.  Indica il livello di dettaglio desiderato nel report di output utilizzando le impostazioni di Report livello di dettaglio:  
  
    ||||  
    |-|-|-|  
    |**SL. No.**|**Comando e parametro**|**Descrizione di output**|  
    |1|verbose = "false"|Genera un report di riepilogo dell'attività.|  
    |2|verbose = "true"|Genera un report di riepilogo e dettagliate sullo stato per ogni attività.|  
  
    > [!NOTE]  
    > Le impostazioni del livello di dettaglio Report specificata in precedenza sono applicabili per generare report di valutazione, convert-schema, eseguire la migrazione di dati, comandi istruzione convert.  
  
3.  Indica il livello di dettaglio desiderato nei report di errore utilizzando le impostazioni di segnalazione errori:  
  
    ||||  
    |-|-|-|  
    |**SL. No.**|**Comando e parametro**|**Descrizione di output**|  
    |1|report errori = "false"|Nessun dettaglio in caso di errore / avviso / i messaggi di informazioni.|  
    |2|report errori = "true"|Ulteriori informazioni sull'errore / avviso / i messaggi di informazioni.|  
  
    > [!NOTE]  
    > Le impostazioni di segnalazione di errori specificato in precedenza sono applicabili per generare report di valutazione, convert-schema, eseguire la migrazione di dati, comandi istruzione convert.  
  
```xml  
<generate-assessment-report  
  
   object-name="<object-name>"  
  
   object-type="<object-type>"  
  
   verbose="<true/false>"  
  
   report-erors="<true/false>"  
  
   write-summary-report-to="<file-name/folder-name>"  
  
   assessment-report-folder="<folder-name>"  
  
   assessment-report-overwrite="<true/false>"  
  
/>  
```  
  
### <a name="synchronize-target"></a>destinazione sincronizzare:  
Il comando **destinazione sincronizzare** è **report errori di** parametro che specifica il percorso del report di errore per l'operazione di sincronizzazione. Quindi, un file con nome **TargetSynchronizationReport&lt;n&gt;. XML** viene creato nel percorso specificato, in cui  **&lt; n &gt;**  è il numero di file univoco che viene incrementato con una cifra a ogni esecuzione del comando stesso.  
  
**Nota:** se viene specificato il percorso della cartella, quindi 'report errori-a-' parametro diventa un attributo facoltativo per il comando 'sincronizzare-target'.  
  
```xml  
<!-- Example: Synchronize target entire Database with all attributes-->  
  
<synchronize-target  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/report-each-as-warning/fail-script>"  
  
   report-errors-to="<file-name/folder-name>"  
  
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
  
   object-name="<object-name>"  
  
   object-type ="<object-type>"  
  
   on-error="<report-total-as-warning/report-each-as-warning/fail-script>"  
  
   report-errors-to="<file-name/folder-name>"  
  
/>  
```  
**il nome di oggetto:** specifica gli oggetti considerati per l'aggiornamento (può anche avere un nome di oggetto gruppo o nomi di oggetto di indivdual).  
  
**Errore:** specifica se specificare gli errori di aggiornamento come avvisi o errori. Opzioni disponibili in errore:  
  
-   Totale report come avviso  
  
-   report-ogni-come-avviso  
  
-   Errore-script  
  
## <a name="see-also"></a>Vedere anche  
[L'esecuzione la Console SSMA (MySQL)](http://msdn.microsoft.com/en-us/e3e9f7e4-0619-4861-a202-3d5d39953b26)  
  
