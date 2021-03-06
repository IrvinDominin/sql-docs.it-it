---
title: Elemento NavigationProperty (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: a36b4d3b-6a6c-489b-8a46-2e6b925b568f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fbb0d38a4bcab7592893aaa63acb1bbb96dac5c3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48157581"
---
# <a name="navigationproperty-element-csdlbi"></a>Elemento NavigationProperty (CSDLBI)
  L'elemento NavigationProperty è un tipo complesso che estende il tipo Member di CSDL per supportare la navigazione nei modelli di dati di Business Intelligence.  
  
> [!WARNING]  
>  Questo elemento è destinato alla creazione di report e non può essere modificato.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi e gli elementi che definiscono l'elemento NavigationProperty.  
  
|nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|CollectionCaption|no|Nome plurale per fare riferimento a un set di istanze della proprietà di navigazione.<br /><br /> Se questo attributo viene omesso, viene utilizzato l'attributo Caption dell'elemento Member di base.|  
  
## <a name="example"></a>Esempio  
 **Tabella**  
  
 L'esempio seguente mostra una proprietà di navigazione in CSDLBI versione 1.1 che descrive il collegamento tra la tabella Product SubCategory e la tabella Product in un modello tabulare.  
  
```  
  
<NavigationProperty   
    Name="Product_Sub_Category_ProductSubcategoryKey"      
    Relationship="Sandbox.Product_Product_Sub_Category_Product_Sub_Category_ProductSubcategoryKey"  
     FromRole="Product_ProductSubcategoryKey"   
    ToRole="Product_Sub_Category_ProductSubcategoryKey">  
<bi:NavigationProperty   
     ReferenceName="Product Sub-Category_ProductSubcategoryKey" />  
</NavigationProperty>  
```  
  
## <a name="example"></a>Esempio  
 **Multidimensionale**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, viene illustrata una proprietà di navigazione che descrive la relazione tra due tabelle nel cubo Operations di Contoso. La relazione connette la tabella Bike Category con la tabella Product Subcategory.  
  
```  
  
<NavigationProperty   
     Name="BikeSubcategory_ProductSubcategoryKey"   
     Relationship="Sandbox.Bike_BikeSubcategory_BikeSubcategory_ProductSubcategoryKey"   
     FromRole="Bike_ProductSubcategoryKey"   
     ToRole="BikeSubcategory_ProductSubcategoryKey">  
   <bi:NavigationProperty />  
</NavigationProperty>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul modello a oggetti tabulare](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
