---
title: Elemento di EntitySet (CSDLBI) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
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
ms.assetid: d4703c9e-5594-472e-a85b-0f5bd0d73d6f
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4ae8366ecec5bf25e1fd27a63d22ac796c080660
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="entityset-element-csdlbi"></a>Elemento EntitySet (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
L'elemento EntitySet definisce una raccolta di entità di un particolare tipo un modello di dati CSDLBI.  
  
 L'elemento EntitySet deve specificare ognuno dei tipi di entità inclusi nel modello di dati. Le informazioni su queste entità del modello vengono specificate elencando le entità figlio del tipo, l'elemento Entità. Per altre informazioni, vedere [Elemento EntityType &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/entitytype-element-csdlbi.md).  
  
 Le proprietà come le regole di confronto e la lingua vengono definite al livello di EntityContainer, non sui singoli oggetti. Tuttavia, le colonne e gli attributi di testo all'interno del modello possono presentare didascalie o traduzioni in altre lingue.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli elementi e gli attributi che definiscono un elemento EntitySet.  
  
|Nome attributo|Obbligatorio|Description|  
|--------------------|-----------------|-----------------|  
|Caption|No|Descrizione intuitiva del set di entità.|  
|CollectionCaption|No|Stringa contenente il nome plurale dell'entità.|  
|ReferenceName|No|Contiene il nome completo e non unito dell'entità. In un modello multidimensionale, corrisponde al nome di CubeDimension.|  
|Hidden|No|Indica se l'entità è nascosta. Per impostazione predefinita le entità non sono nascoste.|  
  
## <a name="example"></a>Esempio  
 **Tabulare**  
  
 Nel seguente esempio, in CSDLBI versione 1.1, vengono illustrate le definizioni delle tabelle Date e Geography del modello tabulare di AdventureWorks.  
  
```  
  
<EntitySet   
   Name="Date"   
   EntityType="Sandbox. Date">  
<bi:EntitySet />  
</EntitySet>  
  
<EntitySet   
   Name="Geography"   
   EntityType="Sandbox.Geography">  
<bi:EntitySet />  
</EntitySet>  
```  
  
## <a name="example"></a>Esempio  
 **Multidimensionale**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, vengono illustrati diversi elementi EntitySet del cubo Operations di Contoso Retail.  
  
```  
  
<EntitySet Name="Outage" EntityType="Sandbox.Outage">  
       <bi:EntitySet />  
</EntitySet>  
  
<EntitySet Name="Store" EntityType="Sandbox.Store">  
     <bi:EntitySet />  
</EntitySet>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento tecnico per le annotazioni di Business Intelligence per CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  
