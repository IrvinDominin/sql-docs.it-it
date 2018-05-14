---
title: Elemento DisplayKey (CSDLBI) | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 01c6272e3007202bae4f3f2f595579fc095ddc5a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="displaykey-element-csdlbi"></a>Elemento DisplayKey (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  L'elemento DisplayKey contiene un elenco degli elementi seguenti che insieme costituiscono un identificatore sicuro. DisplayKey è presente unicamente come elemento figlio dell'elemento EntityType. Può fare riferimento a colonne o estremità del ruolo.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi dell'elemento DisplayKey.  
  
|Nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|IsDisplayKey|No|True o false.|  
  
## <a name="remarks"></a>Osservazioni  
 Questo elemento è relativo ai report. L'elemento a cui si applica questo attributo non deve essere la chiave della tabella effettiva, solo un elemento che verrà presentato come chiave. Tuttavia la colonna utilizzata per DisplayKey deve contenere valori univoci.  
  
## <a name="example"></a>Esempio  
 **Tabulare**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, viene indicata una colonna nel modello di esempio AdventureWorks che è stata specificata come DisplayKey per la tabella.  
  
```  
<sample in progress>  
```  
  
## <a name="example"></a>Esempio  
 **Multidimensionale**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, viene illustrato un estratto della rappresentazione del cubo Operations di Contoso. In questo modello, la colonna Color è stata contrassegnata come chiave di visualizzazione per la tabella Bikes.  
  
```  
  
<EntityType   
    Name="Bike">  
.. .. ..  
<Property   
    Name="Color"   
    Type="String"   
    MaxLength="Max"   
    Unicode="true"   
    FixedLength="false">  
<bi:Property   
    ContextualNameRule="Context"   
    Alignment="Left" Units="counts"   
    SortDirection="Descending"   
    IsRightToLeft="true"   
    DefaultAggregateFunction="Max" />  
</Property>  
.. .. ..  
<bi:EntityType>  
   <bi:DisplayKey>  
      <bi:MemberRef Name="Color" />  
   </bi:DisplayKey>>  
.. .. ..  
</bi:EntityType>  
</EntityType>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul modello a oggetti tabulare alla compatibilità 1050 1103 tramite i livelli](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Concetti di CSDLBI](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdlbi-concepts.md)  
  
  
