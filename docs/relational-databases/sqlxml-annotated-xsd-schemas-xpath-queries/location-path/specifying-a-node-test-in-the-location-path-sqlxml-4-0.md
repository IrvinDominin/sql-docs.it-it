---
title: Specifica di un Test di nodo nel percorso (SQLXML 4.0) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], location paths
- principal node types [SQLXML]
- node tests [SQLXML]
- location path for XPath query
ms.assetid: f46c30bf-1e24-4435-9ac2-f8ba43a8ff94
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e7e2483b8bf861a677e1fbe7b417376bb266e7f4
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>Specifica di un test di nodo nel percorso (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Un test di nodo specifica il tipo di nodo selezionato dal passo. Ogni asse (**figlio**, **padre**, **attributo**, o **self**) è un tipo di nodo principale. Per il **attributo** è il tipo di nodo principale dell'asse,  **\<attributo >**. Per il **padre**, **figlio**, e **self** assi, il tipo di nodo principale è  **\<elemento >**.  
  
> [!NOTE]  
>  Il test di nodo con carattere jolly *, ad esempio `child::*`, non è supportato.  
  
## <a name="node-test-example-1"></a>Test di nodo: Esempio 1  
 Il percorso `child::Customer` seleziona  **\<cliente >** gli elementi figlio del nodo di contesto.  
  
 In questo esempio `child` è l'asse e `Customer` è il test di nodo. Il tipo di nodo principale per il **figlio** asse è  **\<elemento >**. Pertanto, il test di nodo è TRUE se il  **\<cliente >** nodo è un  **\<elemento >** nodo. Se il nodo di contesto non ha alcun  **\<cliente >** elementi figlio, viene restituito un set di nodi vuoto.  
  
## <a name="node-test-example-2"></a>Test di nodo: esempio 2  
 Il percorso `attribute::CustomerID` seleziona il **CustomerID** attributo del nodo di contesto.  
  
 Nell'esempio `attribute` è l'asse e `CustomerID` è il test di nodo. Il tipo di nodo principale di **attributo** asse è  **\<attributo >**. Pertanto, il test di nodo è TRUE se **CustomerID** è un  **\<attributo >** nodo. Se il nodo di contesto non ha alcun **CustomerID**, viene restituito un set di nodi vuoto.  
  
> [!NOTE]  
>  In questa implementazione di XPath, se un passo si riferisce a un  **\<elemento >** o  **\<attributo >** tipo che non è dichiarato nello schema, viene generato un errore. a differenza di quanto avviene con l'implementazione di XPath in MSXML, che restituisce un set di nodi vuoto.  
  
## <a name="abbreviated-syntax-for-the-axes"></a>Sintassi abbreviata per gli assi  
 Per il percorso è supportata la sintassi abbreviata seguente:  
  
-   `attribute::` può essere abbreviato utilizzando `@`.  
  
     Il percorso `Customer[@CustomerID="ALFKI"]` è uguale a `child::Customer[attribute::CustomerID="ALFKI"]`.  
  
-   `child::` può essere omesso da un passo.  
  
     Di conseguenza, **figlio** è l'asse predefinito. Il percorso `Customer/Order` è uguale a `child::Customer/child::Order`.  
  
-   `self::node()` può essere abbreviato utilizzando un punto (.), mentre `parent::node()` può essere abbreviato utilizzando due punti (..).  
  
  
