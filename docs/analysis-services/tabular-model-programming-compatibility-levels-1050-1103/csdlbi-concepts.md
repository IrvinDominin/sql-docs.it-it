---
title: Concetti di CSDLBI | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 2fbdf621-a94d-4a55-a088-3d56d65016ac
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 79e7bf085f6bd1faab6fe367a2c8319192c7f2f7
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="csdlbi-concepts"></a>Concetti di CSDLBI
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Il linguaggio CSDL (Conceptual Schema Definition Language) con annotazioni Business Intelligence (CSDLBI) è basato su Entity Data Framework, ovvero un'astrazione per la rappresentazione di dati in modo da rendere possibile l'accesso, l'esecuzione di query o l'esportazione di set di dati diversi a livello di programmazione. CSDLBI viene utilizzato per rappresentare i modelli di dati creati utilizzando [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] perché supporta le applicazioni e la creazione di rapporti guidata dai dati e avanzata.  
  
 In questa sezione viene illustrato come la rappresentazione CSDLBI esegue il mapping ai modelli di dati di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (tabulari e multidimensionali), insieme a esempi per ogni tipo di modello.  
  
 Gli esempi utilizzati per illustrare questi provengono dal database di esempio AdventureWorks, disponibile su Codeplex. Per ulteriori informazioni sugli esempi, vedere [esempi di Adventure Works per SQL Server](http://go.microsoft.com/fwlink/?linkID=220093).  
  
## <a name="structure-of-a-tabular-model-in-csdlbi"></a>Struttura di un modello tabulare in CSDLBI  
 Un documento CSDLBI che descrive un modello di report e i relativi dati inizia con l'istruzione xsd, seguito dalla definizione di un modello.  
  
 Il modello è uno spazio dei nomi che contiene le seguenti entità, associazioni e proprietà principali:  
  
-   Il **EntityContainer** sono elencate le tabelle nel modello.  
  
-   Ogni tabella viene elencato con il **EntityContainer** come un **EntitySet**.  
  
-   Ogni relazione tra due tabelle viene descritto come un **AssociationSet** che definisce i punti finali della relazione e i ruoli della relazione.  
  
-   Il **EntityType** elemento viene esteso per BISM fornire dettagli aggiuntivi sulle tabelle e colonne, incluse le proprietà per l'ordinamento e ai fini della visualizzazione.  
  
-   Il **misura** elemento definisce i calcoli che possono essere utilizzati nel modello. Una misura può essere trasformata in un indicatore KPI aggiungendo un set di attributi di visualizzazione speciali, utilizzando il nuovo **KPI** elemento.  
  
-   Non sono disponibili rappresentazioni di prospettive distinte. Le colonne e tabelle che non sono inclusi in una prospettiva sono presenti in CSDL, ma contrassegnate con il **Hidden** attributo.  
  
### <a name="entities-entitysets-and-entitytypes"></a>Entità, EntitySet ed EntityType  
 La nozione di un'entità in Entity Data Framework viene estesa per rappresentare colonne e tabelle del modello di dati. L'estratto di codice seguente mostra un elenco di **EntitySet** elementi in un semplice modello che contiene solo tre tabelle.  
  
```  
<EntityContainer Name="SimpleModel">  
<EntitySet Name="DimCustomer"EntityType="SimpleModel.DimCustomer">  
     <bi:EntitySet />  
   </EntitySet>  
<EntitySet Name="DimDate" EntityType="SimpleModel.DimDate">  
     <bi:EntitySet />  
   </EntitySet>  
<EntitySet Name="DimGeography" EntityType="SimpleModel.DimGeography">  
     <bi:EntitySet />  
   </EntitySet> />  
  
```  
  
 Il **EntitySet** non contiene informazioni su colonne o i dati nella tabella. La descrizione dettagliata delle colonne e delle relative proprietà viene fornita nell'elemento EntityType.  
  
 Il **EntitySet** elemento per ogni entità (tabella) include una raccolta di proprietà che definiscono la colonna chiave, il tipo di dati e la lunghezza della colonna, ammissione di valori null, ordinamento e così via. Ad esempio, nell'estratto di CSDL seguente vengono descritte tre colonne nella tabella Customer. La prima colonna è una colonna nascosta speciale utilizzata internamente dal modello.  
  
```  
<EntityType Name="Customer">  
  <Key>  
     <PropertyRef Name="RowNumber" />  
  </Key>  
    <Property Name="RowNumber" Type="Int64" Nullable="false">  
     <bi:Property Hidden="true" Contents="RowNumber"  
       Stability="RowNumber" />  
    </Property>  
    <Property Name="CustomerKey" Type="Int64" Nullable="false">  
      <bi:Property />  
    </Property>  
     <Property Name="FirstName" Type="String" MaxLength="Max" FixedLength="false">  
       <bi:Property />  
      </Property>  
  
```  
  
 Per limitare le dimensioni del documento CSDLBI generato, le proprietà visualizzate più di una volta in un'entità vengono specificate mediante un riferimento a una proprietà esistente, in modo che sia necessario elencare la proprietà una sola volta per il **EntityType**. L'applicazione client può ottenere il valore della proprietà mediante la ricerca di **EntityType** corrispondente il **a OriginEntityType**.  
  
### <a name="relationships"></a>Relazioni  
 In Entity Data Framework, le relazioni sono definite come *associazioni* tra entità.  
  
 Le associazioni dispongono sempre esattamente di due endpoint, ognuno dei quali punta a un campo o una colonna in una tabella. Tra due tabelle sono pertanto possibili più relazioni, se queste ultime dispongono di endpoint diversi. Agli endpoint dell'associazione viene assegnato un nome di ruolo, che indica come viene utilizzata l'associazione nel contesto del modello di dati. Un esempio di un nome di ruolo potrebbe essere **ShipTo**, quando applicato a un ID cliente correlato all'ID cliente in una tabella Orders.  
  
 La rappresentazione CSDLBI del modello contiene inoltre attributi relativi all'associazione che determinano la modalità di mapping tra loro in termini di entità di *molteplicità* dell'associazione. La molteplicità indica se l'attributo o la colonna corrispondente all'endpoint di una relazione tra tabelle si trova sul lato uno o sul lato molti di una relazione. Non sono presenti valori distinti per le relazioni uno-a-uno. Le annotazioni CSDLBI supportano una molteplicità pari a 0 (ovvero l'entità non è associata ad alcun elemento) oppure 0..1, per indicare una relazione uno-a-uno o uno-a-molti.  
  
 Nell'esempio seguente viene rappresentato l'output di CSDLBI per una relazione tra le tabelle Date e ProductInventory di cui è stato creato un join alla colonna DateAlternateKey. Si noti che, per impostazione predefinita, il nome del **AssociationSet** è il nome completo delle colonne coinvolte nella relazione. È tuttavia possibile modificare questo comportamento quando si progetta il modello, in modo da utilizzare un formato di denominazione diverso.  
  
```  
<AssociationSet Name="ProductInventory_Date_DateKey" Association="Model.ProductInventory_Date_DateKey">  
              <End EntitySet="ProductInventory" />  
              <End EntitySet="Date" />  
              <bi:AssociationSet />  
            </AssociationSet>  
  
```  
  
### <a name="visualization-and-navigation-properties"></a>Proprietà di visualizzazione e navigazione  
 Una parte importante delle annotazioni CSDLBI sono le proprietà per la definizione della presentazione nel livello del report e per la navigazione all'interno delle relazioni tra entità. In genere, quando si crea un modello di dati non si considera importante controllare la modalità di ordinamento o raggruppamento dei dati o quale potrebbe essere il valore predefinito, supponendo che l'ordinamento e gli altri dettagli di presentazione verranno specificati dall'applicazione client. I modelli tabulari di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vengono tuttavia progettati per l'integrazione con il client di creazione report [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] e includono proprietà e attributi che supportano la presentazione di entità dal modello di dati nell'area di progettazione del report.  
  
 Nelle estensioni per la visualizzazione sono inclusi attributi che consentono di specificare l'aggregazione predefinita da utilizzare con i dati numerici, di indicare che un campo di testo punta all'URL di un'immagine o di specificare il campo utilizzato per l'ordinamento del campo corrente.  
  
### <a name="name-properties-and-naming-conventions"></a>Proprietà dei nomi e convenzioni di denominazione  
 Lo schema CSDLBI indica che ogni entità dispone di un nome univoco e un identificatore che può essere utilizzato come una chiave. Alcune entità possono inoltre disporre di didascalie utilizzate a fini della visualizzazione e di nomi contestuali che vengono modificati a seconda della posizione in cui viene utilizzata l'entità.  
  
 Il **documentazione** elemento offre ai progettisti di report fornire una descrizione dell'entità, per consentire agli utenti aziendali di comprendere il significato dei dati. Alcune entità supportano inoltre uno o più **annotazione** gli attributi, che forniscono metadati aggiuntivi utilizzabili dall'applicazione o dai client.  
  
 Quando si genera un modello per gli strumenti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], i nomi creati per gli oggetti seguono le convenzioni di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per la denominazione degli oggetti e l'univocità dei nomi. Poiché tuttavia CSDLBI si basa su Entity Data Framework (EDF), in cui è necessario che i nomi rispettino le convenzioni per gli identificatori C#, quando il server crea l'output CSDLBI per un modello, ottiene i nomi utilizzati all'interno dello schema di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e crea automaticamente nuovi nomi di oggetti conformi ai requisiti di EDF. Nella tabella seguente vengono descritte le operazioni tramite le quali vengono generati i nuovi nomi.  
  
|Rule|Azione|  
|----------|------------|  
|Nessun carattere non consentito|I caratteri non consentiti vengono sostituiti da caratteri di sottolineatura.|  
|I nomi devono essere univoci|Se due stringhe sono uguali, una viene resa univoca aggiungendovi un carattere di sottolineatura più un numero|  
  
> [!WARNING]  
>  Sono presenti traduzioni sia per didascalie che per qualificatori e, per un determinato linguaggio, potrebbe essere presenti le une o gli altri. Ciò significa che nei casi in cui siano concatenati un qualificatore e un nome o un qualificatore e una didascalia, è possibile che le stringhe siano in due linguaggi diversi.  
  
## <a name="additions-to-support-multidimensional-models"></a>Aggiunte per supportare modelli multidimensionali  
 La versione 1.0 delle annotazioni CSDLBI supporta solo i modelli tabulari. Nella versione 1.1, è stato aggiunto il supporto per i modelli multidimensionali (cubi OLAP) creati utilizzando gli strumenti di sviluppo tradizionali di Business Intelligence. Pertanto, è ora possibile generare una richiesta XML a un modello multidimensionale e ricevere una definizione CSDLBI del modello da utilizzare nella creazione di rapporti.  
  
 **Cubi:** un Server SQL [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database tabulare può contenere solo una modalità. Ciascun database multidimensionale, invece, può contenere più cubi, ogni database associato a un cubo predefinito. Pertanto quando si invia una richiesta XML a un server multidimensionale, è necessario specificare il cubo; in caso contrario, sarà restituito l'XML per il cubo predefinito.  
  
 La rappresentazione di un cubo è molto simile a quella di un database modello tabulare. Il nome del cubo e il cubo corrispondono all'identificatore del database e al nome del database tabulare.  
  
 **Dimensioni:** una dimensione è rappresentata in CSDLBI come entità (tabella) con colonne e le proprietà. Si noti che, anche se non è incluso in una prospettiva, una dimensione inclusa nel modello verrà rappresentata nell'output CSDL, contrassegnata come **Hidden**.  
  
 **Prospettive:** un client può richiedere a CSDL le singole prospettive. Per ulteriori informazioni, vedere [set di righe DISCOVER_CSDL_METADATA](../../analysis-services/schema-rowsets/xml/discover-csdl-metadata-rowset.md).  
  
 **Gerarchie:** gerarchie sono supportate e rappresentate in CSDLBI come set di livelli.  
  
 **Membri:** il supporto per il membro predefinito è stato aggiunto e i valori predefiniti vengono aggiunti automaticamente all'output di CSDLBI.  
  
 **I membri calcolati:** i modelli multidimensionali supportano i membri calcolati per l'elemento figlio di **tutti** con un membro reale singolo.  
  
 **Attributi della dimensione:** nell'output di CSDLBI, gli attributi della dimensione sono supportati e automaticamente contrassegnati come non aggregabile.  
  
 **Gli indicatori KPI:** gli indicatori KPI sono supportati in CSDLBI versione 1.1, ma la rappresentazione è stata modificata. Prima, un indicatore KPI era la proprietà di una misura. Nella versione 1.1, l'elemento KPI può essere aggiunto a una misura  
  
 **Nuove proprietà:** attributi aggiuntivi sono stati aggiunti per supportare i modelli DirectQuery.  
  
 **Limitazioni:** sicurezza della cella non è supportata.  
  
## <a name="see-also"></a>Vedere anche  
 [Annotazioni CSDL per Business Intelligence &#40; CSDLBI &#41;](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdl-annotations-for-business-intelligence-csdlbi.md)  
  
  
