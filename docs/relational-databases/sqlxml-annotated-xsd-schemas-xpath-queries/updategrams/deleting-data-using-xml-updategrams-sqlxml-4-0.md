---
title: L'eliminazione dei dati mediante Updategram XML (SQLXML 4.0) | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
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
- <after> block
- updategrams [SQLXML], deleting data
- <before> block
- mapping-schema attribute
- record deletions [SQLXML]
ms.assetid: 4fb116d7-7652-474a-a567-cb475a20765c
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ec9979c3c6f474cfd0702da990fa71be57d37bbf
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="deleting-data-using-xml-updategrams-sqlxml-40"></a>Eliminazione di dati mediante updategram XML (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Un updategram indica un'operazione di eliminazione quando è presente un'istanza di record di  **\<prima >** blocco senza record corrispondenti nel  **\<dopo >** blocco. In questo caso, l'updategram Elimina il record di  **\<prima >** blocco dal database.  
  
 Di seguito viene illustrato il formato dell'updategram per un'operazione di eliminazione:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema="SampleSchema.xml"]  >  
   <updg:before>  
       <ElementName />  
      [<ElementName .../>... ]  
   </updg:before>  
    [<updg:after>  
    </updg:after>]  
  </updg:sync>  
</ROOT>  
```  
  
 È possibile omettere il  **\<dopo >** tag se l'updategram esegue un'operazione di eliminazione. Se non si specifica l'opzione facoltativa **dello schema di mapping** attributo, il  **\<ElementName >** specificato nell'updategram esegue il mapping a una tabella di database e la mappa di elementi o attributi figlio per colonne della tabella.  
  
 Se un elemento specificato nell'updategram corrisponde a più di una riga nella tabella o non corrisponde ad alcuna riga, l'updategram restituisce un errore e Annulla l'intero  **\<sincronizzazione >** blocco. Un elemento dell'updategram può eliminare un solo record per volta.  
  
## <a name="examples"></a>Esempi  
 Negli esempi presentati in questa sezione viene utilizzato il mapping predefinito, ovvero non viene specificato alcuno schema di mapping nell'updategram. Per ulteriori esempi di updategram che utilizzano schemi di mapping, vedere [specifica di uno Schema di Mapping con annotazioni in un Updategram &#40; SQLXML 4.0 &#41; ](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
 Per creare esempi reali utilizzando gli esempi seguenti, è necessario soddisfare i requisiti indicati in [requisiti per esecuzione esempi SQLXML](../../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-deleting-a-record-by-using-an-updategram"></a>A. Eliminazione di un record mediante un updategram  
 Negli updategram seguenti vengono eliminati due record dalla tabella HumanResources.Shift.  
  
 In questi esempi l'updategram non specifica uno schema di mapping, pertanto utilizza il mapping predefinito nel quale il nome dell'elemento esegue il mapping a un nome di tabella e gli attributi o i sottoelementi eseguono il mapping alle colonne.  
  
 Questo primo updategram è incentrato sugli attributi e identifica due turni (giorno-sera e sera-notte) nei  **\<prima >** blocco. Poiché non esiste alcun record corrispondente nel  **\<dopo >** blocco, si tratta di un'operazione di eliminazione.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
       <HumanResources.Shift ShiftID="4"  
                        Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift ShiftID="5"  
                        Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
  </updg:before>  
  <updg:after>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>Per testare l'updategram  
  
1.  Completare l'esempio B ("inserimento di più record mediante un updategram") in [inserimento di dati mediante Updategram XML &#40; SQLXML 4.0 &#41; ](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
2.  Copiare l'updategram sopra indicato in blocco note e salvarlo come Updategram-RemoveShifts.xml nella stessa cartella utilizzata per completare ("inserimento di più record mediante un updategram") in [inserimento di dati mediante Updategram XML &#40; SQLXML 4.0 &#41; ](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
3.  Creare e utilizzare lo script di test SQLXML 4.0 (Sqlxml4test.vbs) per eseguire l'updategram.  
  
     Per ulteriori informazioni, vedere [utilizzando ADO per eseguire query di SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Considerazioni sulla sicurezza di updategram &#40; SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
