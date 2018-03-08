---
title: Working with Schema Rowsets in ADOMD.NET | Documenti Microsoft
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
- metadata [ADOMD.NET]
- retrieving metadata
- schema rowsets [ADOMD.NET]
ms.assetid: 7bf75bf8-f1e1-44f6-ac42-c38a681654cf
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 279cc537776f6c96193026d5f0bccafcbd8f0c8b
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="retrieving-metadata---working-with-schema-rowsets"></a>Il recupero dei metadati - Working with Schema Rowsets
  Quando è necessario utilizzare un numero di metadati maggiore rispetto a quello disponibile nel modello a oggetti ADOMD.NET, è possibile utilizzare la funzionalità presente in ADOMD.NET per recuperare l'intervallo completo di set di righe dello schema XMLA (XML for Analysis), OLE DB, OLE DB per OLAP e OLE DB per il data mining:  
  
 **XML per i metadati di analisi**  
 I set di righe dello schema di XML for Analysis consentono di recuperare informazioni di basso livello relative al server. Le informazioni disponibili includono le origini dati disponibili nel server, le parole chiave riservate dal provider, i valori letterali supportati dal provider e altre informazioni. È possibile inoltre utilizzare un set di righe dello schema di XML for Analysis per individuare tutti i set di righe dello schema supportati dal provider.  
  
 Per ulteriori informazioni: [XML for Analysis i rowset dello Schema](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
 **Metadati OLE DB**  
 I set di righe dello schema OLE DB costituisco un metodo standard di recupero delle informazioni da un'ampia gamma di provider.  
  
 Per ulteriori informazioni: [rowset dello Schema OLE DB](../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
 **Metadati OLAP**  
 Le informazioni sullo schema fornite per un'origine dati analitici includono i database oppure i cataloghi disponibili dall'origine dati, i cubi e modelli di data mining in un database, i ruoli che esistono per i cubi nell'origine dati e altre informazioni.  
  
 Per ulteriori informazioni: [OLE DB per OLAP i rowset dello Schema](../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
 **Metadati di Data Mining**  
 Oltre ai metadati OLAP, i set di righe dello schema consentono di recuperare metadati di data mining. I set di righe disponibili espongono informazioni sui modelli di data mining presenti nel database, sugli algoritmi di data mining disponibili, sui parametri necessari per l'algoritmo, sulle strutture di data mining e altre informazioni.  
  
 Per ulteriori informazioni: [rowset dello Schema di Data Mining dei dati](../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
 Per ciascuno dei set di righe dello schema descritti, i metadati vengono recuperati dal set di righe passando un valore GUID oppure un nome XMLA con il metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A> dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
## <a name="retrieving-metadata-by-passing-guids"></a>Recupero di metadati passando valori GUID  
 La classe <xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid> contiene un elenco di campi che rappresentano i set di righe dello schema supportati più comunemente dai provider e dalle origini dati analitici. Per recuperare sia i metadati generali che quelli specifici del provider da un provider o da un'origine dati analitici, utilizzare i valori GUID contenuti nell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid> con uno dei metodi seguenti:  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
> [!NOTE]  
>  Il provider di dati ADOMD.NET espone informazioni sullo schema tramite funzionalità rese disponibili dal provider e dall'origine dati analitici specifici dell'utente. Ogni provider e ogni origine dati possono fornire metadati diversi.  
  
## <a name="retrieving-metadata-by-passing-xmla-names"></a>Recupero di metadati passando nomi XMLA  
 I metodi seguenti accettano come argomenti il nome di schema XMLA che identifica le informazioni sullo schema da restituire e una matrice di restrizioni relative alle colonne restituite:  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
 Ognuno di questi metodi restituisce un'istanza di un **DataSet** oggetto popolato con le informazioni sullo schema. Il **DataSet** oggetto deriva dal **System. Data** dello spazio dei nomi della libreria di classi Microsoft .NET Framework.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, la funzione GetActions accetta una connessione, il nome del cubo, una coordinata e un tipo di coordinata, recupera un [set di righe MDSCHEMA_ACTIONS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-actions-rowset.md)e restituisce le azioni disponibili per la coordinata selezionata.  
  
 [!code-cs[Adomd.NetClient#GetActions](../../analysis-services/multidimensional-models-adomd-net-client/codesnippet/csharp/retrieving-metadata-work_0_1.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 [Recupero di metadati da un'origine dati analitici](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)  
  
  
