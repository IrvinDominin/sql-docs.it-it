---
title: Elemento DisplayKey (CSDLBI) | Documenti Microsoft
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
ms.assetid: 7d881278-1e77-42e1-8cfc-f1bbd9ec2340
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6c3e0be2d677f87afae5bbdff84947b3d013c23f
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
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
  
  
