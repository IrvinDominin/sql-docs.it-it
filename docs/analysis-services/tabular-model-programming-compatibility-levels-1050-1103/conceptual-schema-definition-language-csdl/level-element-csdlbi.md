---
title: Livello di elemento (CSDLBI) | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
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
ms.assetid: fdf75c47-77dc-4bdb-9931-8eca198fdb88
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6d2896a01a8efeacb42bde203ad93e0efdb52be4
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="level-element-csdlbi"></a>Elemento Level (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
L'elemento Level è un tipo complesso che definisce un solo livello in una gerarchia.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi e gli elementi che definiscono l'elemento Level.  
  
|Nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|Origine|Sì|Contenitore per il riferimento alla proprietà.|  
|PropertyRef|Sì|Riferimento a una proprietà dell'istanza. Altri attributi del livello, ad esempio didascalie, nome e nome del riferimento, possono essere prese dalla proprietà dell'istanza a cui si fa riferimento. In tal caso, non è necessario specificarli nell'elemento Level.|  
  
## <a name="remarks"></a>Osservazioni  
 Per altre informazioni sulle gerarchie nei modelli tabulari, vedere [Elemento Hierarchy &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/hierarchy-element-csdlbi.md).  
  
## <a name="example"></a>Esempio  
 **Tabulare**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, viene mostrata la definizione di più livelli in una gerarchia del modello tabulare di esempio di AdventureWorks.  
  
```  
  
<bi:Hierarchy Name="Category">  
   <bi:Level Name="CategoryName">  
     <bi:Source>  
       <bi:PropertyRef Name="CategoryName" />  
     </bi:Source>  
   </bi:Level>  
   <bi:Level Name="ProductName">  
     <bi:Source>  
       <bi:PropertyRef Name="ProductName" />  
     </bi:Source>  
   </bi:Level>  
</bi:Hierarchy>  
```  
  
## <a name="example"></a>Esempio  
 **Multidimensionale**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, è riportato una gerarchia con più livelli del cubo Operations di Contoso.  
  
```  
<bi:Hierarchy   
   Name="Product_Hierarchy"   
   Caption="Product Hierarchy"   
   ReferenceName="Product Hierarchy">  
     <bi:Documentation>  
        <bi:Summary>DESCRIPTION_ProductModelCateg_Hierarchies</bi:Summary>  
     </bi:Documentation>  
  
     <bi:Level Name="ProductLine">  
        <bi:Source>  
        <bi:PropertyRef Name="ProductLine" />  
        </bi:Source>  
     </bi:Level>  
  
     <bi:Level Name="ModelName">  
        <bi:Source>  
        <bi:PropertyRef Name="ModelName" />  
        </bi:Source>  
     </bi:Level>  
</bi:Hierarchy>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul modello a oggetti tabulare alla compatibilità 1050 1103 tramite i livelli](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Informazioni sulle funzioni per gerarchie padre-figlio in DAX](http://msdn.microsoft.com/en-us/b11f0cff-cee4-4ae7-a5b3-ebe288fc42d3)   
 [Configurare il &#40; Tutti i &#41; Livello per le gerarchie di attributi](../../../analysis-services/multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
