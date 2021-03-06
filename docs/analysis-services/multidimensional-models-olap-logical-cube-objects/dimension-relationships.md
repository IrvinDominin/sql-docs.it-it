---
title: Relazioni | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 454527cf0e2e5d444e87cc18b0277b861eb03d48
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34020528"
---
# <a name="dimension-relationships"></a>Relazioni tra dimensioni
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  L'utilizzo delle dimensioni definisce le relazioni tra le dimensioni e i gruppi di misure di un cubo. Una dimensione di un cubo è un'istanza di una dimensione del database utilizzata in un cubo specifico. Spesso un cubo contiene dimensioni che non sono correlate direttamente a un gruppo di misure, ma che possono essere correlate indirettamente al gruppo di misure tramite un'altra dimensione o un altro gruppo di misure. Quando si aggiunge un gruppo di misura o dimensione del database a un cubo, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tenta di determinare l'utilizzo delle dimensioni esaminando le relazioni tra le tabelle delle dimensioni e tabelle dei fatti nella vista origine dati del cubo ed esaminando le relazioni tra attributi nelle dimensioni. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] consente di configurare automaticamente le impostazioni delle dimensioni per le relazioni che è possibile rilevare.  
  
 Una relazione tra una dimensione e un gruppo di misure è costituita dalle tabelle delle dimensioni e dei fatti che partecipano alla relazione e da un attributo di granularità che specifica la granularità della dimensione nel particolare gruppo di misure.  
  
## <a name="regular-dimension-relationships"></a>Relazioni di tipo Regolare  
 Una relazione di tipo Regolare tra una dimensione del cubo e un gruppo di misure si verifica quando la colonna chiave della dimensione è unita in join direttamente alla tabella dei fatti. Questa relazione diretta è basata su una relazione tra chiave primaria e chiave esterna nel database relazionale sottostante, ma potrebbe anche essere basata su una relazione logica definita nella vista origine dati. Una relazione di tipo Regolare rappresenta la relazione tra le tabelle delle dimensioni e una tabella dei fatti in una progettazione con schema star tradizionale. Per ulteriori informazioni sulle relazioni regolari, vedere [definire una relazione di tipo regolare e regolare le proprietà della relazione](../../analysis-services/multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md).  
  
## <a name="reference-dimension-relationships"></a>Relazioni di tipo Riferimento  
 Una relazione di tipo Riferimento tra una dimensione del cubo e un gruppo di misure si verifica quando la colonna chiave della dimensione è unita in join direttamente alla tabella dei fatti tramite una chiave in un'altra tabella della dimensione, come illustrato nella figura seguente.  
  
 ![Diagramma logico, relazione di tipo riferimento](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-refdimension1.gif "diagramma logico, relazione di tipo riferimento")  
  
 Una relazione di tipo Riferimento rappresenta la relazione tra le tabelle delle dimensioni e una tabella dei fatti in una progettazione con schema snowflake. Quando le tabelle delle dimensioni sono connesse in uno schema snowflake, è possibile definire una singola dimensione utilizzando colonne di più tabelle oppure definire dimensioni diverse in base a tabelle delle dimensioni separate e quindi definire un collegamento tra di esse utilizzando l'impostazione della relazione di tipo Riferimento. La figura seguente mostra una tabella dei fatti denominata **InternetSales**, e due tabelle delle dimensioni denominate **cliente** e **Geography**, in uno schema snowflake.  
  
 ![Schema logico, relazione di tipo riferimento](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-refdim-schema1.gif "schema logico, relazione di tipo riferimento")  
  
 È possibile creare una dimensione con la **cliente** tabella come tabella della dimensione principale e **Geography** tabella inclusa come una tabella correlata. Viene quindi definita una relazione di tipo Regolare tra la dimensione e il gruppo di misure InternetSales.  
  
 In alternativa, è possibile creare due dimensioni correlate al gruppo di misure InternetSales: una dimensione basata sul **cliente** tabella e una dimensione basata sul **Geography** tabella. È quindi possibile correlare la dimensione Geography al gruppo di misure InternetSales utilizzando una relazione di tipo Riferimento tramite la dimensione Customer. In questo caso, quando i fatti del gruppo di misure InternetSales vengono dimensionati in base alla dimensione Geography, essi sono dimensionati in base a Customer e Geography. Se il cubo contenesse un secondo gruppo di misure denominato Reseller Sales, non sarebbe possibile dimensionare i fatti in tale gruppo di misure in base a Geography in quanto non esisterebbe alcuna relazione tra Reseller Sales e Geography.  
  
 Come illustrato nella figura seguente, non è previsto alcun limite per il numero di dimensioni di riferimento che è possibile concatenare.  
  
 ![Diagramma logico, relazione di tipo riferimento](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-refdimension2.gif "diagramma logico, relazione di tipo riferimento")  
  
 Per ulteriori informazioni sulle relazioni di cui viene fatto riferimento, vedere [definire una relazione di tipo riferimento e le proprietà della relazione di riferimento](../../analysis-services/multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md).  
  
## <a name="fact-dimension-relationships"></a>Relazioni di tipo Fatti  
 Le dimensioni dei fatti, spesso denominate dimensioni degenerate, sono dimensioni standard create da colonne attributo di tabelle dei fatti anziché da colonne attributo di tabelle delle dimensioni. A volte, i dati dimensionali utili vengono archiviati in una tabella dei fatti per ridurre la duplicazione. Ad esempio, il diagramma seguente consente di visualizzare il **FactResellerSales** tabella dei fatti dal [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] database di esempio.  
  
 ![Le colonne in realtà tabella può supportare dimensioni](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-factdim.gif "colonne infatti tabella può supportare dimensioni")  
  
 Nella tabella sono contenute informazioni sugli attributi non solo per ogni riga di un ordine emesso da un rivenditore, ma anche per l'ordine stesso. Gli attributi di un cerchio nel diagramma precedente identificano le informazioni contenute nel **FactResellerSales** tabella che può essere utilizzata come attributi in una dimensione. In questo caso, due ulteriori informazioni, ovvero il numero di registrazione dello spedizioniere e il numero dell'ordine di acquisto emesso dal rivenditore, vengono rappresentate dalle colonne attributo CarrierTrackingNumber e CustomerPONumber. Si tratta di informazioni interessanti. Gli utenti, ad esempio, saranno senz'altro interessati a visualizzare le informazioni aggregate, ad esempio il costo totale del prodotto per tutti gli ordini spediti con lo stesso numero di registrazione dello spedizioniere. Senza una dimensione, tuttavia, non è possibile organizzare o aggregare i dati per questi due attributi.  
  
 In teoria, sarebbe possibile creare una tabella della dimensione che utilizzi le stesse informazioni chiave della tabella FactResellerSales e spostare le altre due colonne attributo, CarrierTrackingNumber e CustomerPONumber, in questa tabella. In questo modo, tuttavia, si duplicherebbe una parte significativa dei dati e si aggiungerebbe complessità superflua al data warehouse per rappresentare solo due attributi come dimensione distinta.  
  
> [!NOTE]  
>  Le dimensioni dei fatti vengono spesso utilizzate per supportare azioni drill-through. Per altre informazioni sulle azioni, vedere [Azioni &#40;Analysis Services - Dati multidimensionali&41#;](../../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md).  
  
> [!NOTE]  
>  Le dimensioni dei fatti devono essere aggiornate in modo incrementale dopo ogni aggiornamento del gruppo di misure cui fa riferimento la relazione di tipo Fatti. Se la dimensione dei fatti è una dimensione ROLAP, il motore di elaborazione di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] elimina qualsiasi cache ed elabora in modo incrementale il gruppo di misure.  
  
 Per ulteriori informazioni sulle relazioni delle tabelle dei fatti, vedere [definire una relazione di tipo fatti e le relative proprietà](../../analysis-services/multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md).  
  
## <a name="many-to-many-dimension-relationships"></a>Relazioni molti-a-molti  
 Nella maggior parte delle dimensioni, ogni fatto si unisce in join a un solo membro della dimensione e un singolo membro della dimensione può essere associato a più fatti. Nella terminologia dei database relazionali, questa viene definita una relazione uno-a-molti. Spesso, tuttavia, può essere utile unire in join un unico fatto a più membri della dimensione. Un cliente di una banca può ad esempio avere più conti (conti correnti, conti di risparmio, carta di credito e conti titoli) e ogni conto può avere più proprietari. La dimensione relativa ai clienti creata da una relazione di questo tipo includerebbe più membri correlati a un'unica transazione relativa al conto corrente.  
  
 ![Relazione di dimensione logico dello schema o molti-a-molti](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-many-dimension1.gif "relazione della dimensione logica dello schema o molti-a-molti")  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Consente di definire una relazione molti-a-molti tra una dimensione e una tabella dei fatti.  
  
> [!NOTE]  
>  Per supportare una relazione tra dimensioni molti-a-molti, la vista origine dati deve includere una relazione di chiave esterna tra tutte le tabelle coinvolte, come illustrato nella figura precedente. In caso contrario, non sarà possibile selezionare il gruppo di misure intermedio corretto quando si stabilisce la relazione nella **utilizzo dimensioni** scheda della finestra di progettazione dimensioni.  
  
 Per ulteriori informazioni sulle relazioni molti-a-molti, vedere [definire molti a molti relazione e molti-a-molti, le proprietà della relazione](../../analysis-services/multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Dimensioni & #40; Analysis Services - dati multidimensionali & #41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
