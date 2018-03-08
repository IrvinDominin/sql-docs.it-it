---
title: Funzioni definite dall'utente e Stored procedure | Documenti Microsoft
ms.custom: 
ms.date: 02/14/2018
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
helpviewer_keywords:
- stored procedures [ADOMD.NET]
- ADOMD.NET, user defined functions
- user defined functions [ADOMD.NET]
- ADOMD.NET, UDFs
- ADOMD.NET, stored procedures
ms.assetid: 07e8aa47-37d4-4bbc-8bff-49e422d12897
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f737165dbc65f112d8c6f0d8ea846abf9cee8344
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="user-defined-functions-and-stored-procedures"></a>Funzioni definite dall'utente e stored procedure
  Gli oggetti server ADOMD.NET, è possibile creare la funzione definita dall'utente (UDF) o stored procedure per [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] che interagiscono con i metadati e dati dal server. Questi metodi in-process vengono chiamati tramite istruzioni MDX (Multidimensional Expressions) o DMX (Data Mining Extensions) per fornire funzionalità aggiunte senza le latenze associate alle comunicazioni di rete.  
  
## <a name="udf-examples"></a>Esempi di funzioni definite dall'utente  
 Una funzione definita dall'utente è un metodo che può essere chiamato nel contesto di un'istruzione MDX o DMX, accettare un numero qualsiasi di parametri e restituire qualsiasi tipo di dati.  
  
 Una funzione definita dall'utente creata utilizzando MDX è analoga a una creata per DMX. La differenza principale consiste nel fatto che alcune proprietà dell'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.Context>, ad esempio le proprietà <xref:Microsoft.AnalysisServices.AdomdServer.Context.CurrentCube%2A> e <xref:Microsoft.AnalysisServices.AdomdServer.Context.CurrentMiningModel%2A>, sono disponibili solo per uno dei due linguaggi di scripting.  
  
 Negli esempi seguenti viene illustrato come utilizzare una funzione definita dall'utente per restituire una descrizione del nodo e tuple di filtri e per applicare un filtro a una tupla.  
  
### <a name="returning-a-node-description"></a>Restituzione di una descrizione del nodo  
 Nell'esempio seguente viene creata una funzione definita dall'utente che restituisce la descrizione per un nodo specificato. La funzione definita dall'utente utilizza il contesto corrente in cui è in esecuzione e recupera il nodo dal modello di data mining corrente tramite una clausola FROM DMX.  
  
```  
public string GetNodeDescription(string nodeUniqueName)  
{  
   return Context.CurrentMiningModel.GetNodeFromUniqueName(nodeUniqueName).Description;  
}  
```  
  
 Una volta distribuito, l'esempio di funzione definita dall'utente precedente può essere chiamato dall'espressione DMX seguente, che recupera il nodo relativo alla stima più probabile. La descrizione contiene informazioni che specificano le condizioni che costituiscono il nodo relativo alla stima.  
  
```  
select Cluster(), SampleAssembly.GetNodeDescription( PredictNodeId(Cluster()) ) FROM [Customer Clusters]  
```  
  
### <a name="returning-tuples"></a>Restituzione di tuple  
 Nell'esempio seguente vengono accettati un set e un conteggio di risultati, vengono recuperate tuple dal set in modo causale e viene restituito un subset finale.  
  
```  
public Set RandomSample(Set set, int returnCount)  
{  
   //Return the original set if there are fewer tuples  
   //in the set than the number requested.  
   if (set.Tuples.Count <= returnCount)  
      return set;  
  
   System.Random r = new System.Random();  
   SetBuilder returnSet = new SetBuilder();  
  
   //Retrieve random tuples until the return set is filled.  
   int i = set.Tuples.Count;  
   foreach (Tuple t in set.Tuples)  
   {  
      if (r.Next(i) < returnCount)  
      {  
         returnCount--;  
         returnSet.Add(t);  
      }  
      i--;  
      //Stop the loop if we have enough tuples.  
      if (returnCount == 0)  
         break;  
   }  
   return returnSet.ToSet();  
}  
```  
  
 L'esempio precedente viene chiamato nell'esempio MDX seguente, In questo esempio MDX cinque casuale stati o province vengono recuperate dal **Adventure Works** database.  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
### <a name="applying-a-filter-to-a-tuple"></a>Applicazione di un filtro a una tupla  
 Nell'esempio seguente viene creata una funzione definita dall'utente che accetta un set e applica un filtro a ogni tupla del set tramite l'oggetto Expression. Tutte le tuple conformi al filtro verranno aggiunte a un set restituito.  
  
 [!code-cs[Adomd.NetServer#FilterSet](../../analysis-services/multidimensional-models-adomd-net-server/codesnippet/csharp/user-defined-functions-a_1.cs)]  
  
 L'esempio precedente viene chiamato nell'esempio MDX seguente che filtra il set in base alle città i cui nomi iniziano con la lettera "A".  
  
```  
Select Measures.Members on Rows,  
SampleAssembly.FilterSet([Customer].[Customer Geography].[City], "[Customer].[Customer Geography].[City].CurrentMember.Name < 'B'") on Columns  
From [Adventure Works]  
```  
  
## <a name="stored-procedure-example"></a>Esempio di stored procedure  
 Nell'esempio seguente una stored procedure basata su MDX utilizza AMO per creare partizioni per Internet Sales, qualora siano necessarie.  
  
 [!code-cs[Adomd.NetServer#CreateInternetSalesMeasureGroupPartitions](../../analysis-services/multidimensional-models-adomd-net-server/codesnippet/csharp/user-defined-functions-a_2.cs)]  
  
  
