---
title: Installare i modelli di training preliminare machine learning in SQL Server | Documenti Microsoft
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 5d9f60684cc749c35674233fbdaaa222953396d9
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2018
---
# <a name="install-pretrained-machine-learning-models-on-sql-server"></a>Installare training preliminare di machine learning i modelli in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo descrive come aggiungere i modelli di training preliminare a un'istanza di SQL Server che già dispone di R Services o installato Servizi di Machine Learning.

L'opzione per installare i modelli di training preliminare è disponibile quando si utilizza il programma di installazione di Windows separato per Microsoft R Server o Server di Machine Learning. È possibile utilizzare il programma di installazione per ottenere i modelli di training preliminare o è possibile utilizzarlo per [l'aggiornamento di machine learning componenti](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md) in un'istanza di SQL Server 2016 o SQL Server 2017.

Dopo avere scaricato i modelli con training preliminare eseguendo il programma di installazione, esistono alcuni passaggi aggiuntivi per configurare i modelli per l'utilizzo con SQL Server. In questo articolo viene descritto il processo.

Per un esempio di come utilizzare i modelli con training preliminare con dati di SQL Server, vedere il blog dal team di SQL Server Machine Learning: 

+ [Analisi del sentiment con Python in servizi di SQL Server Machine Learning](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/11/01/sentiment-analysis-with-python-in-sql-server-machine-learning-services/)

## <a name="benefits-of-using-pretrained-models"></a>Vantaggi dell'utilizzo di modelli di training preliminare

Questi modelli con training preliminare sono stati creati per aiutare i clienti che necessitano di eseguire attività, ad esempio sentiment analysis o immagine featurization, ma non hanno le risorse per ottenere il set di dati di grandi dimensioni o eseguire il training di un modello complesso. Utilizzo di modelli con training preliminare consente un'introduzione a testo e immagine in modo efficiente l'elaborazione.

Attualmente i modelli disponibili sono i modelli di rete neurali profonde (DNN) per la classificazione di analisi e l'immagine di valutazione. Tutti i modelli di training preliminare sono stati eseguito il training utilizzando Microsoft [calcolo rete Toolkit](https://cntk.ai/Features/Index.html), o **CNTK**.

La configurazione di ciascuna rete è stato in base alle implementazioni di riferimento seguente:

+ ResNet-18
+ ResNet-50
+ ResNet-101
+ AlexNet

Per ulteriori informazioni su questi modelli, vedere [con training preliminare modelli di machine learning per il rilevamento di analisi e l'immagine di valutazione](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)

Per ulteriori informazioni sulle reti di formazione e la relativa implementazione utilizzando CNTK, vedere i seguenti articoli:

+ [Algoritmo i ricercatori Microsoft imposta attività cardine ImageNet richiesta](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/)

+ [Microsoft calcolo rete Toolkit offre più efficiente deep distribuite le prestazioni di calcolo di apprendimento](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/)

## <a name="how-to-install-the-models-on-sql-server"></a>Come installare i modelli in SQL Server

1. Eseguire l'installazione basata su Windows separato per il Server di Machine Learning. Per i percorsi di download, vedere:

    + [Installazione di Machine Learning Server per Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
    + [Installare R Server 9.1 per Windows](https://docs.microsoft.com/r-server/install/r-server-install-windows)

2. La selezione di funzionalità da installare varia a seconda che si sono solo i modelli di recupero o l'esecuzione di altri aggiornamenti tramite il programma di installazione.
 
    + Se si tratta di una nuova installazione di Server di Machine Learning e non si desidera apportare altre modifiche ai componenti R o Python, selezionare **solo** l'opzione di modelli di training preliminare. Accettare tutte le altre richieste, inclusi i contratti di licenza.

    + Per aggiornare i componenti di R o Python allo stesso tempo, selezionare la lingua (R, Python o entrambi) che si desidera aggiornare e selezionare l'opzione di modelli di training preliminare. Selezionare una o più istanze per applicare le modifiche.

    + Se precedentemente installato Machine Learning Server e aggiornare i componenti di R o Python utilizzando l'opzione di associazione, lasciare tutte le selezioni precedenti **come**, quindi selezionare le opzioni di modelli di training preliminare. Non deselezionare le opzioni selezionate in precedenza; Se si esegue questa operazione, il programma di installazione rimuove i componenti.

3. Quando l'installazione è stata completata, aprire un prompt dei comandi di Windows **come amministratore**e passare alla cartella bootstrap il programma di installazione per SQL Server, che contiene anche il programma di installazione di Microsoft R. In un'istanza predefinita di SQL Server 2017, la cartella è:
    
    `C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\SQL2017\x64\`

4. Eseguire RSetup.exe e indicare il componente per installare la versione e la cartella contenente i file di origine del modello, utilizzando gli argomenti della riga di comando indicati in questi esempi:

    + Per utilizzare i modelli con **R_SERVICES**:

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "<SQL_DB_instance_folder>\R_SERVICES\library\MicrosoftML\mxLibs\x64"`

    Per abilitare l'utilizzo della versione più recente dei modelli di training preliminare per R, in un'istanza predefinita di SQL Server 2017, ad esempio, eseguire l'istruzione seguente:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\MicrosoftML\mxLibs\x64"`

    In un'istanza denominata, il comando sarebbe simile al seguente:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MyInstanceName\R_SERVICES\library\MicrosoftML\mxLibs\x64"`

    + Per utilizzare i modelli di training preliminare con R Server (Standalone) o di Machine Learning Server (Standalone):

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "~\R_SERVER\library\MicrosoftML\mxLibs\x64"`

    Ad esempio, per abilitare l'utilizzo della versione più recente dei modelli di training preliminare per R, in un'installazione predefinita del Server di R con SQL Server 2016, eseguire l'istruzione seguente:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir ‘C:\Program Files\Microsoft SQL Server\130\R_SERVER\library\MicrosoftML\mxLibs\"`
    
    + Per utilizzare i modelli con training preliminare **PYTHON_SERVICES**:

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "<SQL_DB_instance_folder>\PYTHON_SERVICES\library\MicrosoftML\mxLibs\x64"`

    Per abilitare l'utilizzo della versione più recente dei modelli di training preliminare per Python, in un'istanza predefinita di SQL Server 2017, ad esempio, eseguire l'istruzione seguente:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\library\MicrosoftML\mxLibs\x64"`

    In un'istanza denominata, il comando sarebbe simile al seguente:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MyInstanceName\PYTHON_SERVICES\library\MicrosoftML\mxLibs\x64"`

    + Per utilizzare Python pretrained modelli con Machine Learning Server (Standalone):

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "<sql_folder>\PYTHON_SERVER\site-packages\microsoftml\mxLibs"`

    Ad esempio, presupponendo un'installazione predefinita di Machine Learning Server (Standalone) utilizzando il programma di installazione di SQL Server 2017, eseguire l'istruzione seguente:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER\Lib\site-packages\microsoftml\mxLibs"`

5. I valori seguenti sono supportati per il parametro version:

    + Versione finale candidata 0: **9.1.0.0**
    + Versione finale candidata 1: **9.2.0.22**
    + RTM: **9.2.0.100**
    + Aggiornamento cumulativo 1: **9.2.0.24**

6. Se l'installazione ha esito positivo, i modelli seguenti devono essere aggiunti al R\_servizi o PYTHON\_cartelle SERVICES:

    - AlexNet\_Updated.model
    - ImageNet1K\_mean.xml
    - pretrained.model
    - ResNet\_101\_Updated.model
    - ResNet\_18\_Updated.model
    - ResNet\_50\_Updated.model


> [!NOTE]
> 
> Se il percorso del file di modello è troppo lungo, è possibile che venga visualizzato un errore quando si chiama il file del modello dal codice Python. Si tratta di una limitazione nell'implementazione corrente di Python. Questo problema verrà risolto in una prossima service release.

## <a name="examples"></a>Esempi

Dopo aver installato i modelli, è possibile utilizzare i modelli tramite chiamata dal codice.

### <a name="image-featurization-example"></a>Esempio di immagine featurization

Il modello con training preliminare per le immagini supporta featurization delle immagini fornite. Questo modello specifico è stato eseguito il training usando [CNTK](https://docs.microsoft.com/cognitive-toolkit/). 

Per utilizzare il modello, si chiama il **featurizeImage** trasformare.

+ [featurizeImage: trasformare Featurization immagine di Machine Learning](https://docs.microsoft.com/r-server/r-reference/microsoftml/featurizeimage)

In questo esempio, vedere il secondo blocco di codice. L'immagine viene caricata, ridimensionamento e trasformato dal modello DNN convolutional training preliminare. L'output dell'utilità di DNN viene quindi utilizzato per il training di un modello lineare per la classificazione delle immagini.

L'immagine deve essere ridimensionato per soddisfare i requisiti del modello con Training: le immagini utilizzate per il training sono stati 224 x 224 px. Se si utilizza un modello AlexNet, l'immagine verrà ridimensionata a 227 x 227 px.

```R
 model <- rxFastLinear(
     Label ~ Features,
     data = train,
     mlTransforms = list(
         loadImage(vars = list(Features = "Path")),
         resizeImage(vars = "Features", width = 224, height = 224), 
         extractPixels(vars = "Features"),
         featurizeImage(var = "Features")
         ),
     mlTransformVars = "Path")
```

> [!NOTE]
> Non è possibile leggere o modificare i modelli con training preliminare, perché queste vengono compresse utilizzando un formato nativo, per migliorare le prestazioni.

### <a name="text-analysis-example"></a>Esempio di analisi di testo

Vedere l'esempio seguente per una dimostrazione di come utilizzare il modello di testo training preliminare featurization classificazione del testo:

[Analisi del sentiment utilizzando l'utilità di testo](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)
