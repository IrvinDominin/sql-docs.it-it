---
title: "Ordinamento dei dati per le trasformazioni Unione e Merge Join | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "attributi di ordinamento [Integration Services]"
  - "colonne di output [Integration Services]"
ms.assetid: 22ce3f5d-8a88-4423-92c2-60a8f82cd4fd
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 31
---
# Ordinamento dei dati per le trasformazioni Unione e Merge Join
  In [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] le trasformazioni Unione e Merge Join richiedono dati di input ordinati. I dati di input devono essere ordinati fisicamente ed è necessario impostare le opzioni di ordinamento sugli output e sulle colonne di output nell'origine o nella trasformazione a monte. Se le opzioni di ordinamento indicano che i dati sono ordinati, mentre in realtà non lo sono, l'operazione di Unione o Merge join restituisce risultati imprevisti.  
  
## Ordinamento dei dati  
 È possibile ordinare i dati mediante uno dei seguenti metodi:  
  
-   Utilizzare nell'origine una clausola ORDER BY nell'istruzione utilizzata per caricare i dati.  
  
-   Inserire nel flusso di dati una trasformazione Ordinamento prima della trasformazione Unione o Merge join.  
  
 Se i dati sono di tipo stringa, le trasformazioni Unione e Merge join presuppongono che i valori stringa siano stati ordinati mediante le regole di confronto di Windows. Per fornire i valori stringa alle trasformazioni Unione e Merge join ordinate mediante le regole di confronto di Windows, utilizzare la procedura seguente:  
  
#### Per fornire valori stringa ordinati tramite regole di confronto di Windows  
  
-   Utilizzare una trasformazione Ordinamento per ordinare i dati.  
  
     La trasformazione Ordinamento utilizza le regole di confronto di Windows per ordinare i valori stringa.  
  
     -oppure-  
  
-   Usare l'operatore CAST Transact-SQL per eseguire innanzitutto il cast dei valori **varchar** in valori **nvarchar** e quindi usare la clausola ORDER BY Transact-SQL per ordinare i dati.  
  
    > [!IMPORTANT]  
    >  Non è possibile utilizzare solo la clausola ORDER BY perché tale clausola utilizza le regole di confronto di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per ordinare i valori stringa. L'uso delle regole di confronto di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] può restituire un ordinamento diverso rispetto alle regole di confronto di Windows, con risultati imprevisti nella trasformazione Unione o Merge join.  
  
## Impostazione delle opzioni di ordinamento nei dati  
 È necessario impostare due importanti proprietà di ordinamento per l'origine o per la trasformazione a monte che fornisce i dati alle trasformazioni Unione e Merge join:  
  
-   La proprietà **IsSorted** dell'output che indica se i dati sono stati ordinati. Questa proprietà deve essere impostata su **True**.  
  
    > [!IMPORTANT]  
    >  L'impostazione del valore della proprietà **IsSorted** su **True** non determina l'ordinamento dei dati. Questa proprietà fornisce solo un hint ai componenti a valle in relazione all'ordinamento precedente dei dati.  
  
-   La proprietà **SortKeyPosition** delle colonne di output che indica se una colonna è ordinata, l'ordinamento della colonna e la sequenza di ordinamento di più colonne. Questa proprietà deve essere impostata per ogni colonna di dati ordinati.  
  
 Se si utilizza una trasformazione Ordinamento per ordinare i dati, entrambe le proprietà vengono impostate come richiesto dalla trasformazione Unione o Merge join, ovvero, la trasformazione Ordinamento imposta la proprietà **IsSorted** dell'output su **True** e le proprietà **SortKeyPosition** delle colonne di output.  
  
 Tuttavia, se non si utilizza una trasformazione Ordinamento per ordinare i dati, è necessario impostare manualmente queste proprietà di ordinamento nell'origine o nella trasformazione a monte. Per impostare manualmente le proprietà di ordinamento nell'origine o nella trasformazione a monte, utilizzare la procedura seguente.  
  
#### Per impostare manualmente gli attributi di ordinamento in un componente dell'origine o della trasformazione  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] aprire il progetto di [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] contenente il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Nella scheda **Flusso di dati** individuare l'origine o la trasformazione a monte appropriata o trascinarla dalla **Casella degli strumenti** nell'area di progettazione.  
  
4.  Fare clic sul componente con il pulsante destro del mouse e scegliere **Visualizza editor avanzato**.  
  
5.  Fare clic sulla scheda **Proprietà input e output**.  
  
6.  Fare clic su **Output \<nome componente>** e impostare la proprietà **IsSorted** su **True**.  
  
    > [!NOTE]  
    >  Se si imposta manualmente la proprietà **IsSorted** dell'output su **True** e se i dati non sono ordinati, quando si esegue il pacchetto alcuni dati potrebbero risultare mancanti o danneggiati nella trasformazione Unione o Merge Join.  
  
7.  Espandere **Colonne di output**.  
  
8.  Fare clic sulla colonna che si vuole indicare come ordinata e impostarne la proprietà **SortKeyPosition** su un valore intero diverso da zero attenendosi alle linee guida seguenti:  
  
    -   Il valore intero deve rappresentare una sequenza numerica che inizia con 1 e che ha incrementi di 1.  
  
    -   Un valore intero positivo indica un ordinamento crescente.  
  
    -   Un valore intero negativo indica un ordinamento decrescente. Se impostato su un numero negativo, il valore assoluto del numero determina la posizione della colonna nella sequenza di ordinamento.  
  
    -   Il valore predefinito 0 indica che la colonna non è ordinata. Lasciare il valore 0 per colonne di output che non vengono incluse nell'ordinamento.  
  
     Come esempio per l'impostazione della proprietà **SortKeyPosition**, considerare l'istruzione Transact-SQL seguente che carica i dati in un'origine:  
  
     `SELECT * FROM MyTable ORDER BY ColumnA, ColumnB DESC, ColumnC`  
  
     Per questa istruzione, impostare la proprietà **SortKeyPosition** per ogni colonna come indicato di seguito:  
  
    -   Impostare la proprietà **SortKeyPosition** di ColumnA su 1. In questo modo viene indicato che ColumnA è la prima colonna da ordinare e che l'ordinamento deve essere crescente.  
  
    -   Impostare la proprietà **SortKeyPosition** di ColumnB su -2. In questo modo viene indicato che ColumnB è la seconda colonna da ordinare e che l'ordinamento deve essere decrescente.  
  
    -   Impostare la proprietà **SortKeyPosition** di ColumnC su 3. In questo modo viene indicato che ColumnC è la terza colonna da ordinare e che l'ordinamento deve essere crescente.  
  
9. Ripetere il passaggio 8 per ogni colonna ordinata.  
  
10. Scegliere **OK**.  
  
11. Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
## Vedere anche  
 [Trasformazione Unione](../../../integration-services/data-flow/transformations/merge-transformation.md)   
 [Trasformazione Merge join](../../../integration-services/data-flow/transformations/merge-join-transformation.md)   
 [Trasformazioni di Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Percorsi in Integration Services](../../../integration-services/data-flow/integration-services-paths.md)   
 [Attività Flusso di dati](../../../integration-services/control-flow/data-flow-task.md)  
  
  