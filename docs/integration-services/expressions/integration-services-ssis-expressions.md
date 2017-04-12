---
title: "Espressioni di Integration Services (SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pacchetti [Integration Services], espressioni"
  - "pacchetti di Integration Services, espressioni"
  - "pacchetti di SQL Server Integration Services, espressioni"
  - "espressioni [Integration Services], pacchetti"
  - "pacchetti SSIS, espressioni"
ms.assetid: 26d2e242-7f60-4fa9-a70d-548a80eee667
caps.latest.revision: 51
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 51
---
# Espressioni di Integration Services (SSIS)
  Un'espressione è una combinazione di simboli, ovvero identificatori, valori letterali, funzioni e operatori, che restituiscono un singolo valore di dati. È possibile creare espressioni semplici, costituite da un'unica costante, variabile o funzione, In genere le espressioni sono complesse in quanto includono più operatori e funzioni e fanno riferimento a più colonne e variabili. In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] è possibile usare le espressioni per definire condizioni per istruzioni CASE, creare e aggiornare valori in colonne di dati, assegnare valori a variabili, aggiornare o popolare proprietà in fase di esecuzione, definire vincoli in vincoli di precedenza e definire espressioni usate dal contenitore Ciclo For.  
  
 Le espressioni sono basate su un linguaggio delle espressioni e sull'analizzatore di espressioni. L'analizzatore di espressioni consente di analizzare l'espressione e di verificare se le regole del linguaggio delle espressioni sono rispettate. Per ulteriori informazioni sulla sintassi delle espressioni e sui valori letterali e identificatori supportati, vedere gli argomenti seguenti.  
  
-   [Sintassi &#40;SSIS&#41;](../../integration-services/expressions/syntax-ssis.md)  
  
-   [Valori letterali &#40;SSIS&#41;](../../integration-services/expressions/literals-ssis.md)  
  
-   [Identificatori &#40;SSIS&#41;](../../integration-services/expressions/identifiers-ssis.md)  
  
## Componenti che utilizzano espressioni  
 Le espressioni possono essere usate negli elementi di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] seguenti:  
  
-   La trasformazione Suddivisione condizionale implementa una struttura decisionale basata su espressioni per dirigere righe di dati su destinazioni diverse. Le espressioni usate in una trasformazione Suddivisione condizionale devono restituire **true** o **false**. Ad esempio, le righe che soddisfano la condizione dell'espressione "Column1 > Column2" possono essere indirizzate a un output separato.  
  
-   La trasformazione Colonna derivata utilizza i valori creati tramite espressioni per popolare nuove colonne del flusso di dati o per aggiornare le colonne esistenti. Ad esempio, l'espressione Colonna1 + " ABC" consente di aggiornare un valore o di creare un nuovo valore con la stringa concatenata.  
  
-   Il valore delle variabili viene impostato tramite un'espressione. Ad esempio, GETDATE() imposta il valore della variabile sulla data corrente.  
  
-   Nei vincoli di precedenza le espressioni consentono di impostare le condizioni che determinano se l'attività o il contenitore vincolato di un pacchetto viene eseguito. Le espressioni usate in un vincolo di precedenza devono restituire **true** o **false**. Ad esempio, l'espressione @A > @B esegue un confronto tra due variabili definite dall'utente per determinare se l'attività vincolata viene eseguita.  
  
-   In un contenitore Ciclo For le espressioni consentono di compilare le istruzioni di inizializzazione, valutazione e incremento utilizzate dalla struttura del ciclo. Ad esempio, l'espressione @Counter = 1 inizializza il contatore del ciclo.  
  
 Con le espressioni è inoltre possibile aggiornare i valori delle proprietà di pacchetti, contenitori quali ciclo For e ciclo Foreach, attività, gestioni connessioni a livello di pacchetto e progetto, provider di log ed enumeratori Foreach. Ad esempio, tramite un'espressione di proprietà, è possibile assegnare la stringa "Localhost.AdventureWorks" alla proprietà ConnectionName dell'attività Esegui SQL. Per altre informazioni, vedere [Utilizzo delle espressioni di proprietà nei pacchetti](../../integration-services/expressions/use-property-expressions-in-packages.md).  
  
## Marcatori icona per espressioni  
 In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], un marcatore icona speciale viene visualizzato accanto a gestioni connessione, variabili e attività su cui sono impostate espressioni. La proprietà **HasExpressions** è disponibile in tutti gli oggetti SSIS che supportano le espressioni, ad eccezione delle variabili. La proprietà consente di identificare facilmente gli oggetti che contengono espressioni.  
  
## Generatore di espressioni  
 Generatore di espressioni è uno strumento grafico per la compilazione di espressioni. È disponibile nelle finestre di dialogo **Editor trasformazione Suddivisione condizionale**, **Editor trasformazione Colonna derivata** e **Generatore di espressioni** ed è uno strumento grafico per la compilazione di espressioni.  
  
 Il Generatore di espressioni include cartelle contenenti elementi specifici dei pacchetti e cartelle contenenti le funzioni, i cast di tipo e gli operatori del linguaggio delle espressioni. Gli elementi specifici dei pacchetti sono variabili definite dall'utente e di sistema. Nelle finestre di dialogo **Editor trasformazione Suddivisione condizionale** e **Editor trasformazione Colonna derivata** è inoltre possibile visualizzare le colonne di dati. Per compilare espressioni per le trasformazioni, è possibile trascinare elementi dalle cartelle alla colonna **Condizione** o **Espressione** o digitare l'espressione direttamente nella colonna. Generatore di espressioni aggiunge automaticamente gli elementi di sintassi necessari, ad esempio il prefisso @ per i nomi delle variabili.  
  
> [!NOTE]  
>  I nomi delle variabili di sistema e delle variabili definite dall'utente devono essere specificati rispettando la distinzione tra maiuscole e minuscole.  
  
 Alle variabili è associato un ambito. Nella cartella **Variabili** del Generatore di espressioni sono elencate solo le variabili incluse nell'ambito e utilizzabili. Per altre informazioni, vedere [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md).  
  
## Attività correlate  
 [Utilizzo di un'espressione in un componente flusso di dati](../Topic/Use%20an%20Expression%20in%20a%20Data%20Flow%20Component.md)  
  
## Contenuto correlato  
 Articolo tecnico [SSIS Expression Examples](http://go.microsoft.com/fwlink/?LinkId=220761) (Esempi di espressioni SSIS) nel sito Web social.technet.microsoft.com  
  
## Vedere anche  
 [SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)  
  
  