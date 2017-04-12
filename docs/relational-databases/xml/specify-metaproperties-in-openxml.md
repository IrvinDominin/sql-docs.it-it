---
title: "Impostazione di metapropriet&#224; in OPENXML | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "overflow nei documenti XML [SQL Server]"
  - "metaproprietà [XML in SQL Server]"
  - "dati non utilizzati"
  - "estrazione di informazioni dei nodi XML [SQL Server]"
  - "OPENXML, metaproprietà dell'istruzione"
ms.assetid: 29bfd1c6-3f9a-43c4-924a-53d438e442f4
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Impostazione di metapropriet&#224; in OPENXML
  Gli attributi delle metaproprietà in un documento XML sono attributi che descrivono le proprietà di un elemento XML (elemento, attributo o qualsiasi altro nodo DOM). Tali attributi non sono fisicamente presenti nel testo del documento XML, tuttavia OPENXML fornisce tali metaproprietà per tutti gli elementi XML. Queste metaproprietà consentono di estrarre informazioni, ad esempio la posizione locale o le informazioni sullo spazio dei nomi, dei nodi XML, ovvero informazioni più dettagliate rispetto a quelle disponibili nella rappresentazione testuale.  
  
 Per eseguire il mapping le metaproprietà alle colonne del set di righe, è possibile specificare il parametro *ColPattern* in un'istruzione OPENXML. Le colonne conterranno i valori delle metaproprietà alle quali è stato eseguito il mapping. Per informazioni sulla sintassi di OPENXML, vedere [OPENXML &#40;Transact-SQL&#41;](../../t-sql/functions/openxml-transact-sql.md).  
  
 Per accedere agli attributi delle metaproprietà, è possibile utilizzare uno spazio dei nomi specifico di SQL Server, Questo spazio dei nomi, **urn:schemas-microsoft-com:xml-metaprop** consente all'utente di accedere agli attributi delle metaproprietà. Se il risultato di una query OPENXML viene restituito nel formato tabella edge, in tale tabella sarà inclusa una colonna per ogni attributo della metaproprietà, a eccezione della metaproprietà **xmltext**.  
  
 Alcuni attributi delle metaproprietà vengono utilizzati per attività di elaborazione. Ad esempio, l'attributo della metaproprietà **xmltext** consente di gestire l'overflow. La gestione dell'overflow implica la gestione dei dati non utilizzati e non elaborati del documento. Una delle colonne del set di righe generato da OPENXML può essere identificata come la colonna di overflow. A tale scopo, è possibile eseguirne il mapping alla metaproprietà **xmltext** usando il parametro *ColPattern*. Nella colonna verranno inseriti i dati di overflow e il parametro *flags* determinerà se la colonna includerà solo i dati non utilizzati oppure tutti i dati.  
  
 Nella tabella seguente sono elencati gli attributi delle metaproprietà per ogni elemento XML analizzato. Per accedere a tali attributi, è necessario usare lo spazio dei nomi **urn:schemas-microsoft-com:xml-metaprop**. Qualsiasi valore impostato dall'utente direttamente nel documento XML tramite queste metaproprietà verrà ignorato.  
  
> [!NOTE]  
>  Non è possibile fare riferimento a queste metaproprietà nelle strutture di navigazione XPath.  
  
|Attributo della metaproprietà|Descrizione|  
|----------------------------|-----------------|  
|**@mp:id**|Restituisce un identificatore del nodo DOM generato dal sistema e valido a livello globale per il documento. Se il documento non viene nuovamente analizzato, questo ID fa riferimento allo stesso nodo XML.<br /><br /> Un ID XML **0** indica che l'elemento è un elemento radice. Il relativo ID XML padre è NULL.|  
|**@mp:localname**|Archivia la parte locale del nome del nodo. Viene utilizzato insieme a un prefisso e a un URI dello spazio dei nomi per definire i nodi di elementi o attributi.|  
|**@mp:namespaceuri**|Restituisce l'URI dello spazio dei nomi dell'elemento corrente. Se il valore di questo attributo è NULL, non sono presenti spazi dei nomi.|  
|**@mp:prefix**|Archivia il prefisso dello spazio dei nomi del nome dell'elemento corrente.<br /><br /> Se non è presente alcun prefisso (NULL) e viene specificato un URI, indica che lo spazio dei nomi specificato è lo spazio dei nomi predefinito. Se non viene specificato alcun URI, non verranno associati spazi dei nomi.|  
|**@mp:prev**|Archivia l'elemento di pari livello precedente in un nodo e fornisce informazioni sull'ordinamento degli elementi nel documento.<br /><br /> **@mp:prev** contiene l'ID XML dell'elemento di pari livello precedente con lo stesso elemento padre. Se un elemento si trova all'inizio dell'elenco di elementi di pari livello, **@mp:prev** è NULL.|  
|**@mp:xmltext**|Utilizzato per attività di elaborazione. Rappresenta la serializzazione testuale dell'elemento e dei relativi attributi nonché dei sottoelementi, come vengono utilizzati nella gestione dell'overflow di OPENXML.|  
  
 Nella tabella seguente vengono illustrate le proprietà padre aggiuntive che consentono di recuperare le informazioni relative alla gerarchia.  
  
|Attributo della metaproprietà padre|Descrizione|  
|-----------------------------------|-----------------|  
|**@mp:parentid**|Corrisponde a **../@mp:id**|  
|**@mp:parentlocalname**|Corresponds to **../@mp:localname**|  
|**@mp:parentnamespacerui**|Corrisponde a **../@mp:namespaceuri**|  
|**@mp:parentprefix**|Corrisponde a **../@mp:prefix**|  
  
## Esempi  
 Negli esempi seguenti viene illustrato l'utilizzo di OPENXML per visualizzare i set di righe in modi diversi.  
  
### A. Mapping tra le colonne del set di righe OPENXML e le metaproprietà  
 In questo esempio, l'istruzione OPENXML viene utilizzata per visualizzare il documento XML di esempio come un set di righe. In particolare, viene illustrato come eseguire il mapping di più attributi delle metaproprietà alle colonne del set di righe in un'istruzione OPENXML usando il parametro *ColPattern*.  
  
 Nell'istruzione OPENXML si noti quanto segue:  
  
-   Viene eseguito il mapping della colonna **id** all'attributo della metaproprietà **@mp:id** per indicare che la colonna includerà l'ID XML univoco generato dal sistema dell'elemento.  
  
-   Viene eseguito il mapping della colonna **parent** a **@mp:parentid** per indicare che la colonna includerà l'ID XML del padre dell'elemento.  
  
-   Viene eseguito il mapping della colonna **parentLocalName** a **@mp:parentlocalname** a indicare che la colonna includerà il nome locale del padre.  
  
 L'istruzione SELECT restituisce quindi il set di righe fornito da OPENXML:  
  
```  
DECLARE @idoc int  
DECLARE @doc nvarchar(1000)  
-- Sample XML document  
SET @doc = N'<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was very satisfied</Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue white red">  
          <Urgency>Important</Urgency>  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @idoc OUTPUT, @doc  
  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@idoc, '/root/Customer/Order', 9)  
      WITH (id int '@mp:id',   
            oid char(5),   
            date datetime,   
            amount real,   
            parentIDNo int '@mp:parentid',   
            parentLocalName varchar(40) '@mp:parentlocalname')  
EXEC sp_xml_removedocument @idoc  
```  
  
 Risultato:  
  
```  
id   oid         date                amount    parentIDNo  parentLocalName    
--- ------- ---------------------- ---------- ------------ ---------------  
6    O1    1996-01-20 00:00:00.000     3.5         2        Customer  
10   O2    1997-04-30 00:00:00.000     13.4        2        Customer  
19   O3    1999-07-14 00:00:00.000     100.0       15       Customer  
25   O4    1996-01-20 00:00:00.000     10000.0     15       Customer  
```  
  
### B. Recupero dell'intero documento XML  
 In questo esempio, l'istruzione OPENXML visualizza il documento XML di esempio come un set di righe a una colonna. Viene eseguito il mapping della colonna, **Col1**, alla metaproprietà **xmltext** e diventa una colonna di overflow, pertanto vi verranno inseriti i dati non utilizzati che in questo caso sono rappresentati dall'intero documento.  
  
 L'istruzione SELECT restituisce quindi l'intero set di righe.  
  
```  
DECLARE @idoc int  
DECLARE @doc nvarchar(1000)  
SET @doc = N'<?xml version="1.0"?>  
<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was very   
             satisfied</Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue   
             white red">  
     <MyTag>Testing to see if all the subelements are returned</MyTag>  
          <Urgency>Important</Urgency>  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @idoc OUTPUT, @doc  
  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@idoc, '/')  
   WITH (Col1 ntext '@mp:xmltext')  
```  
  
 Per recuperare l'intero documento senza la dichiarazione XML, è possibile specificare la query nel modo seguente:  
  
```  
SELECT *  
FROM OPENXML (@idoc, '/root')  
   WITH (Col1 ntext '@mp:xmltext')  
EXEC sp_xml_removedocument @idoc  
```  
  
 La query restituisce l'elemento radice insieme al relativo nome, nonché i dati contenuti in tale elemento.  
  
### C. Impostazione della metaproprietà xmltext per il recupero dei dati non utilizzati in una colonna  
 In questo esempio, l'istruzione OPENXML viene utilizzata per visualizzare il documento XML di esempio come un set di righe. L'esempio descrive inoltre come recuperare i dati XML non utilizzati tramite il mapping tra l'attributo della metaproprietà **xmltext** e una colonna del set di righe nell'istruzione OPENXML.  
  
 La colonna **comment** viene definita come colonna di overflow tramite il mapping alla metaproprietà **@mp:xmltext**. Il parametro *flags* viene impostato su **9** (XML_ATTRIBUTE e XML_NOCOPY), per indicare che il mapping è **incentrato sugli attributi** e che nella colonna di overflow verranno copiati solo i dati non utilizzati.  
  
 L'istruzione SELECT restituisce quindi il set di righe definito dall'istruzione OPENXML.  
  
 In questo esempio, la metaproprietà **@mp:parentlocalname** viene impostata per una colonna, **ParentLocalName**, del set di righe generato dall'istruzione OPENXML. Questa colonna includerà pertanto il nome locale dell'elemento padre.  
  
 Nel set di righe vengono definite altre due colonne, **parent** e **comment**. Viene eseguito il mapping della colonna **parent** a **@mp:parentid** per indicare che la colonna includerà l'ID XML dell'elemento padre dell'elemento. La colonna comment viene definita come colonna di overflow tramite il mapping alla metaproprietà **@mp:xmltext**.  
  
```  
DECLARE @idoc int  
DECLARE @doc nvarchar(1000)  
-- sample XML document  
SET @doc = N'<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was very satisfied</Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue white red">  
          <Urgency>Important</Urgency>  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>  
'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @idoc OUTPUT, @doc  
  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@idoc, '/root/Customer/Order', 9)  
      WITH (oid char(5),   
            date datetime,  
            comment ntext '@mp:xmltext')  
EXEC sp_xml_removedocument @idoc  
```  
  
 Di seguito è riportato il risultato. Poiché le colonne oid e date sono già utilizzate, non sono riportate nella colonna di overflow.  
  
```  
oid   date                        comment                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
----- --------------------------- ----------------------------------------  
O1    1996-01-20 00:00:00.000     <Order amount="3.5"/>  
O2    1997-04-30 00:00:00.000     <Order amount="13.4">Customer was very   
                                   satisfied</Order>  
O3    1999-07-14 00:00:00.000     <Order amount="100" note="Wrap it blue   
                                   white red"><Urgency>   
                                   Important</Urgency></Order>  
O4    1996-01-20 00:00:00.000     <Order amount="10000"/>  
```  
  
## Vedere anche  
 [OPENXML &#40;Transact-SQL&#41;](../../t-sql/functions/openxml-transact-sql.md)   
 [OPENXML &#40;SQL Server&#41;](../../relational-databases/xml/openxml-sql-server.md)  
  
  