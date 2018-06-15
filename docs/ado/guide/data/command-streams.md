---
title: Comando flussi | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- command streams [ADO]
- streams [ADO], command
ms.assetid: 0ac09dbe-2665-411e-8fbb-d1efe6c777be
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d3f37202ccd4586d3a485f18d070c0af0434a303
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35269970"
---
# <a name="command-streams"></a>Comando flussi
ADO ha sempre supportato l'input del comando nel formato di stringa specificato da di **CommandText** proprietà. In alternativa, con ADO 2.7 o versioni successiva, è possibile anche utilizzare un flusso di informazioni per l'input comando assegnando il flusso di **CommandStream** proprietà. È possibile assegnare un oggetto ADO **flusso** oppure qualsiasi oggetto che supporta COM **IStream** interfaccia.  
  
 Il contenuto di flusso del comando viene passato semplicemente da ADO al provider, quindi il provider deve supportare l'input del comando dal flusso usare questa funzionalità. Ad esempio, SQL Server supporta le query sotto forma di estensioni di OpenXML per Transact-SQL o modelli XML.  
  
 Poiché i dettagli del flusso devono essere interpretati dal provider, è necessario specificare il sottolinguaggio del comando impostando il **sottolinguaggio** proprietà. Il valore di **sottolinguaggio** è una stringa contenente un GUID, che è definito dal provider. Per informazioni sui valori validi per **sottolinguaggio** supportati dal provider, vedere la documentazione del provider.  
  
## <a name="xml-template-query-example"></a>Esempio di Query XML modello  
 Nell'esempio seguente viene scritto in VBScript al database Northwind.  
  
 In primo luogo, inizializzare e aprire il **flusso** oggetto che verrà utilizzato per contenere il flusso di query:  
  
```  
Dim adoStreamQuery  
Set adoStreamQuery = Server.CreateObject("ADODB.Stream")  
adoStreamQuery.Open  
```  
  
 Il contenuto del flusso di query sia una query del modello XML.  
  
 La query del modello richiede un riferimento per lo spazio dei nomi XML identificato da sql: prefisso di \<SQL: query > tag. Un'istruzione SQL SELECT è incluso il contenuto del modello XML e assegnata a una variabile di stringa, come indicato di seguito:  
  
```  
sQuery = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'>  
<sql:query> SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME </sql:query>  
</ROOT>"  
```  
  
 Successivamente, scrivere la stringa nel flusso:  
  
```  
adoStreamQuery.WriteText sQuery, adWriteChar  
adoStreamQuery.Position = 0  
```  
  
 AdoStreamQuery per assegnare il **CommandStream** proprietà di un oggetto ADO **comando** oggetto:  
  
```  
Dim adoCmd  
Set adoCmd  = Server.CreateObject("ADODB.Command"")  
adoCmd.CommandStream = adoStreamQuery  
```  
  
 Specificare il linguaggio di comando **sottolinguaggio**, che indica come il Provider OLE DB di SQL Server deve interpretare il flusso del comando. Il sottolinguaggio specificato da un GUID specifico del provider:  
  
```  
adoCmd.Dialect = "{5D531CB2-E6Ed-11D2-B252-00C04F681B71}"  
```  
  
 Infine, eseguire la query e restituire i risultati in un **Recordset** oggetto:  
  
```  
Set objRS = adoCmd.Execute  
```
