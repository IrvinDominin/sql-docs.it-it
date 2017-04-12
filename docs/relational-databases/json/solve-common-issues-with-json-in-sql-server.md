---
title: "Domande frequenti su JSON in SQL Server | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "07/07/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JSON, domande frequenti"
ms.assetid: feae120b-55cc-4601-a811-278ef1c551f9
caps.latest.revision: 9
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 9
---
# Domande frequenti su JSON in SQL Server
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 In questo articolo sono contenute le risposte ad alcune domande comuni sul supporto JSON integrato in SQL Server.  
 
## Output di FOR JSON e JSON

### FOR JSON PATH o FOR JSON AUTO?  
 **Domanda.** È necessario creare un risultato di testo JSON da una semplice query SQL su una singola tabella. FOR JSON PATH e FOR JSON AUTO producono lo stesso output. Quali di queste due opzioni deve essere usata?  
  
 **Risposta.** Usare FOR JSON PATH. Anche se non esiste alcuna differenza nell'output JSON, la modalità AUTO dispone di una logica aggiuntiva che controlla se le colonne devono essere nidificate. Considerare PATH come opzione predefinita.  

### Creare una struttura JSON nidificata  
 **Domanda.** È necessario produrre una struttura JSON complessa con numerose matrici sullo stesso livello. FOR JSON PATH è in grado di creare oggetti nidificati usando percorsi e FOR JSON AUTO crea livelli di nidificazione aggiuntivi per ciascuna tabella. Nessuna di queste due opzioni consente di generare l'output desiderato. Come è possibile creare un formato JSON personalizzato che le opzioni esistenti non supportano direttamente?  
  
 **Risposta.** È possibile creare qualsiasi struttura di dati aggiungendo query FOR JSON come espressioni di colonna che restituiscono testo JSON o creano JSON manualmente usando la funzione JSON_QUERY, come illustrato nell'esempio seguente.  
  
```tsql  
SELECT col1, col2, col3,  
             (SELECT col11, col12, col13 FROM t11 WHERE t11.FK = t1.PK FOR JSON PATH) as t11,  
             (SELECT col21, col22, col23 FROM t21 WHERE t21.FK = t1.PK FOR JSON PATH) as t21,  
             (SELECT col31, col32, col33 FROM t31 WHERE t31.FK = t1.PK FOR JSON PATH) as t31,  
             JSON_QUERY('{"'+col4'":"'+col5+'"}' as t41  
FROM t1  
FOR JSON PATH  
```  
  
Ogni risultato di una query FOR JSON o della funzione JSON_QUERY nelle espressioni di colonna è formattato come un oggetto secondario JSON nidificato a parte e incluso nel risultato principale.  

### Evitare JSON con doppi caratteri di escape nell'output FOR JSON  
 **Domanda.** Il testo JSON è archiviato in una colonna di tabella. Si desidera includerlo nell'output di FOR JSON. FOR JSON usa caratteri di escape per tutti i caratteri nel file JSON, quindi si ottiene una stringa JSON anziché un oggetto nidificato, come illustrato nell'esempio seguente.  
  
```tsql  
SELECT 'Text' as myText, '{"day":23}' as myJson  
FOR JSON PATH  
```  
  
 Questa query produce l'output riportato di seguito.  
  
```json  
[{"myText":"Text","myJson":"{\"day\":23}"}]  
```  
  
 Come è possibile evitare questo comportamento? Si desidera che `{"day":23}` venga restituito come oggetto JSON e non come testo con caratteri di escape.  
  
 **Risposta.** L'oggetto JSON archiviato in una colonna di testo o in un valore letterale viene trattato come qualsiasi testo. È racchiuso tra virgolette doppie e caratteri di escape. Se si desidera restituire un oggetto JSON senza caratteri di escape, è necessario passare questa colonna come argomento alla funzione JSON_QUERY, come illustrato nell'esempio seguente.  
  
```tsql  
SELECT col1, col2, col3, JSON_QUERY(jsoncol1) AS jsoncol1  
FROM tab1  
FOR JSON PATH  
```  
  
 JSON_QUERY, senza il secondo parametro facoltativo, restituisce il primo argomento come risultato. Poiché JSON_QUERY restituisce un oggetto JSON valido, FOR JSON sa che questo risultato non deve essere preceduto da caratteri di escape.

### JSON generato con la clausola WITHOUT_ARRAY_WRAPPER viene preceduto da caratteri di escape nell'output FOR JSON  
 **Domanda.** Si tenta di formattare un'espressione di colonna con FOR JSON e l'opzione WITHOUT_ARRAY_WRAPPER.  
  
```tsql  
SELECT 'Text' as myText,  
       (SELECT 12 day, 8 mon FOR JSON PATH, WITHOUT_ARRAY_WRAPPER) as myJson  
FOR JSON PATH   
```  
  
 Sembra che il testo restituito dalla query FOR JSON sia preceduto da caratteri di escape come testo normale. Ciò si verifica solo se la clausola WITHOUT_ARRAY_WRAPPER è specificata. Perché non viene trattato come un oggetto JSON e incluso senza caratteri di escape nel risultato?  
  
 **Risposta.** Se si specifica l'opzione WITHOUT_ARRAY_WRAPPER, il testo JSON generato non è necessariamente valido. Pertanto l'outer FOR JSON presuppone che si tratti di testo normale e usa caratteri di escape per la stringa. Se si è certi che l'output JSON sia valido, eseguirne il wrapping con la funzione JSON_QUERY per convertirlo in oggetto JSON formattato correttamente, come illustrato nell'esempio seguente.  
  
```tsql  
SELECT 'Text' as myText,  
      JSON_QUERY((SELECT 12 day, 8 mon FOR JSON PATH, WITHOUT_ARRAY_WRAPPER)) as myJson  
FOR JSON PATH    
```  

## Input di OPENJSON e JSON

### Restituire l'oggetto secondario JSON nidificato dal testo JSON con OPENJSON  
 **Domanda.** Non è possibile aprire una matrice di oggetti di documenti JSON complessi che contiene sia valori scalari sia oggetti, e matrici usando OPENJSON con uno schema esplicito. Quando si aggiunge un riferimento a una chiave nella clausola WITH, vengono restituiti solo i valori scalari. Oggetti e matrici vengono restituiti come valori null. Come è possibile estrarre oggetti o matrici dagli oggetti JSON?  
  
 **Risposta.** Se si desidera restituire un oggetto o una matrice come colonna, usare l'opzione AS JSON nella definizione di colonna, come illustrato nell'esempio seguente.  
  
```tsql  
SELECT scalar1, scalar2, obj1, obj2, arr1  
FROM OPENJSON(@json)  
             WITH ( scalar1 int,  
                          scalar2 datetime2,  
                          obj1 NVARCHAR(MAX) AS JSON,  
                          obj2 NVARCHAR(MAX) AS JSON,  
                          arr1 NVARCHAR(MAX) AS JSON)  
```  

### Usare OPENJSON anziché JSON_VALUE per restituire valori long text  
 **Domanda.** La chiave di descrizione nel testo JSON contiene testo lungo. `JSON_VALUE(@json, '$.description')` restituisce NULL anziché un valore.  
  
 **Risposta.** JSON_VALUE è progettato per restituire valori scalari piccoli. In genere la funzione restituisce NULL anziché un errore di overflow. Se si desidera restituire valori più lunghi, usare OPENJSON, che supporta valori NVARCHAR (MAX), come illustrato nell'esempio seguente.  
  
```tsql  
SELECT myText FROM OPENJSON(@json) WITH (myText NVARCHAR(MAX) '$.description')  
```  

### Usare OPENJSON anziché JSON_VALUE per gestire le chiavi duplicate  
 **Domanda.** Il testo JSON contiene chiavi duplicate. JSON_VALUE restituisce solo la prima chiave trovata nel percorso. Come è possibile visualizzare tutte le chiavi con lo stesso nome?  
  
 **Risposta.** Le funzioni scalari JSON integrate restituiscono solo la prima occorrenza dell'oggetto di riferimento. Se è necessaria più di una chiave, usare la funzione con valori di tabella OPENJSON, come illustrato nell'esempio seguente.  
  
```tsql  
SELECT value FROM OPENJSON(@json, '$.info.settings')  
WHERE [key] = 'color'  
```  

### OPENJSON richiede il livello di compatibilità 130  
 **Domanda.** È in corso un tentativo di esecuzione di OPENJSON in SQL Server 2016 e viene visualizzato l'errore riportato di seguito.  
  
 `Msg 208, Level 16, State 1 ‘Invalid object name OPENJSON’`  
  
 **Risposta.** La funzione OPENJSON è disponibile solo nel livello di compatibilità 130. Se il livello di compatibilità del database è inferiore a 130, la funzione OPENJSON è nascosta. Altre funzioni JSON sono disponibili in tutti i livelli di compatibilità.  
 
## Altre domande

### Aggiungere il riferimento alle chiavi che contengono caratteri non alfanumerici nel testo JSON  
 **Domanda.** Le chiavi del testo JSON contengono caratteri non alfanumerici. Come è possibile aggiungere un riferimento a queste proprietà?  
  
 **Risposta.** È necessario racchiuderle tra virgolette nei percorsi JSON. Ad esempio, `JSON_VALUE(@json, '$."$info"."First Name".value')`.
 