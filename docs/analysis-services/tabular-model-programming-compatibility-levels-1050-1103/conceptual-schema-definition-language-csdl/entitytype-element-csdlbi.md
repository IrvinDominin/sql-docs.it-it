---
title: Elemento EntityType (CSDLBI) | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8fe1635c9360f2f00dc98348d64d2080f93332bf
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2018
ms.locfileid: "40394081"
---
# <a name="entitytype-element-csdlbi"></a>Elemento EntityType (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Il **EntityType** elemento è un tipo complesso che rappresenta la struttura di un'entità ad alto livello, ad esempio un cliente o un ordine, in un modello di dati. Il **bi: EntityType** elemento estende la definizione di [EntityType](http://msdn.microsoft.com/library/bb399206.aspx) utilizzato nella [Entity Data Framework](/dotnet/framework/data/adonet/ef/overview).  
  
 Un elemento EntityType deve essere specificato per ognuna delle entità incluse nel modello di dati. I sottoelementi di EntityType descrivono le colonne e le misure nella tabella. Le relazioni tra tabelle vengono incluse nel **EntityContainer**.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 La tabella seguente elenca gli elementi e attributi che definiscono i **EntityType** elemento. Vedere anche gli attributi applicabili per il [EntityType](http://msdn.microsoft.com/library/bb399206.aspx) elemento.  
  
|nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|Sommario|no|Stringa contenente i possibili tipi di dati in una colonna. Il valore è derivato dal valore di DimensionAttributeTypeEnumType nel modello di dati.<br /><br /> Se il valore di DimensionAttributeTypeEnumType è "ExtendedType", il valore del contenuto è derivato dall'elemento ExtendedType di DimensionAttribute. Il client non è necessario per rispondere a tali valori.|  
|DefaultDetails|no|Elenco di riferimenti a proprietà che rappresentano il set di colonne nella tabella.<br /><br /> Visualizzare [elemento DefaultDetails &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/defaultdetails-element-csdlbi.md).|  
|DefaultImage|no|Riferimento a una colonna contenente l'immagine che illustra l'entità.<br /><br /> Nei modelli multidimensionali, questo elemento corrisponde a un attributo binario dell'attributo della dimensione. Se questo attributo è presente, l'elemento deve contenere un solo elemento MemberRef.<br /><br /> Visualizzare [elemento MemberRef &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/memberref-element-csdlbi.md).|  
|DefaultMeasure|no|Riferimento a una misura dell'entità che deve essere utilizzato come impostazione predefinita durante l'esecuzione dei calcoli dell'entità. Se omesso, il valore predefinito è SUM.<br /><br /> Visualizzare [elemento MemberRef &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/memberref-element-csdlbi.md).|  
|DisplayKey|no|Elenco di riferimenti a colonne o estremità del ruolo che costituiscono un identificatore sicuro che identifica in modo univoco un'istanza di entità.<br /><br /> Visualizzare [elemento DisplayKey &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/displaykey-element-csdlbi.md).|  
|Gerarchia|no|Elenco delle gerarchie nel modello.<br /><br /> Visualizzare [elemento Hierarchy &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/hierarchy-element-csdlbi.md).|  
|ReferenceName|Sì|Identificatore che può essere utilizzato per fare riferimento a questa entità in una query DAX (Data Analysis Expressions).<br /><br /> Se tale attributo non è presente, viene utilizzato il nome completo del campo dell'entità.|  
|SortMembers|no|Elenco di proprietà utilizzato per l'ordinamento. L'attributo SortDirection indica se l'ordinamento è crescente o decrescente.|  
  
## <a name="contents-element"></a>Elemento Contents  
 Il **contenuto** elemento è un tipo semplice che descrive il tipo di dati dell'entità.  
  
 Il contenuto dell'entità (colonna) può essere uno dei valori seguenti:  
  
|valore|Description|  
|-----------|-----------------|  
|Regular|Non altrimenti definito.|  
|Time|Attributi che rappresentano periodi di tempo, ad esempio anni, semestri, trimestri, mesi o giorni.|  
|Geography|Attributi che rappresentano informazioni geografiche, ad esempio città o CAP.|  
|Organization|Attributi che rappresentano informazioni sull'organizzazione, ad esempio dipendenti o filiali.|  
|BillOfMaterials|Attributi che rappresentano informazioni relative alle scorte o alla produzione, ad esempio elenchi di parti di prodotti.|  
|Accounts|Attributi che rappresentano un grafico dei conti per la creazione di rapporti finanziari.|  
|Customers|Attributi che rappresentano informazioni sui clienti o sui contatti.|  
|Products|Attributi che rappresentano informazioni sui prodotti.|  
|Scenario|Attributi che rappresentano informazioni di pianificazione o di analisi strategica.|  
|Quantitative|Attributi che rappresentano informazioni sulle quantità.|  
|Utilità|Attributi che rappresentano informazioni di vario tipo.|  
|Currency|Contiene i dati e i metadati della valuta.|  
|Rates|Attributi che rappresentano informazioni sui tassi valutari.|  
|Channel|Attributi che rappresentano informazioni sui canali.|  
|Promotion|Attributi che rappresentano informazioni sulle promozioni marketing.|  
  
## <a name="example"></a>Esempio  
 **Tabella**  
  
 Nel seguente esempio viene illustrata una parte della rappresentazione CSDLBI versione 1.1 della tabella Geography utilizzata nel modello tabulare AdventureWorks. La colonna RowNumber è una colonna nascosta che viene generata automaticamente come un identificatore di riga nei modelli tabulari e pertanto dispone dell'attributo Contents, **RowNumber**.  
  
```  
  
<EntityType   
     Name="DimGeography">  
     <Key>  
        <PropertyRef Name="RowNumber" />  
     </Key>  
     <Property   
        Name="RowNumber"   
        Type="Int64" Nullable="false">  
     <bi:Property   
        Hidden="true"   
        Contents="RowNumber"   
        Stability="RowNumber" />  
     </Property>  
....  
  
```  
  
## <a name="example"></a>Esempio  
 **Multidimensionale**  
  
 Nell'esempio seguente vengono illustrati gli elementi EntityType di CSDLBI versione 1.1 che rappresentano una parte della dimensione temporale del cubo Operations di Contoso.  
  
```  
<EntityType   
       Name="CalendarQuarter">  
    <Key>  
       <PropertyRef Name="RowNumber" />  
    </Key>  
  
    <Property Name="RowNumber"   
       Type="Int64"   
       Nullable="false">  
    <bi:Property   
       Hidden="true"   
       Contents="RowNumber"   
       Stability="RowNumber"   
    />  
    </Property>  
  
    <Property Name="CalendarQuarter2"   
       Type="String"   
       MaxLength="Max"   
       Unicode="true"   
       FixedLength="false"   
       Nullable="false">  
    <bi:Property   
       Caption="CalendarQuarter"   
       ReferenceName="CalendarQuarter"   
    />  
    </Property>  
   <bi:EntityType />  
</EntityType>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento tecnico per le annotazioni di Business Intelligence per CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  
