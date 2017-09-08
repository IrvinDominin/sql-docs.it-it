---
title: Metodo Execute (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Execute Method
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- EXECUTE
- urn:schemas-microsoft-com:xml-analysis#
- http://schemas.microsoft.com/analysisservices/2003/engine#
- microsoft.xml.analysis.execute
- urn:schemas-microsoft-com:xml-analysis#Execute
helpviewer_keywords:
- Execute method
ms.assetid: 0fff5221-7164-4bbc-ab58-49cf04c52664
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 22bf60ae16e6b4e5f30bf694505e77857b6c0600
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="xml-elements---methods---execute"></a>Eseguire gli elementi XML - metodi-
  Invia XML per i comandi Analysis (XMLA) a un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Include richieste che comportano il trasferimento dei dati, ad esempio recuperando o aggiornando dati nel server.  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis  
  
 **Azione SOAP** "urn: schemas-microsoft-com: XML-analysis: eseguire"  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Execute>  
   <Command>...</Command>  
   <Properties>...</Properties>  
   <Parameters>...</Parameters>  
</Execute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che ricorre una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|Nessuno|  
|Elementi figlio|[Comando](../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md), [parametri](../../analysis-services/xmla/xml-elements-properties/parameters-element-xmla.md), [proprietà](../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Il **Execute** comandi XMLA forniti nell'esecuzione del metodo di **comando** elemento e restituisce eventuali dati risultanti utilizzando XMLA [set di righe](../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md) tipo di dati (per i risultati tabulari Imposta) o XMLA [MDDataSet](../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) del tipo di dati (per il set di risultati multidimensionali.)  
  
## <a name="example"></a>Esempio  
 Esempio di codice riportato di seguito è riportato un esempio di un **Execute** chiamata al metodo che contiene un'istruzione SELECT di MDX (Multidimensional Expressions).  
  
```  
<Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <Command>  
      <Statement>  
         SELECT [Measures].MEMBERS ON COLUMNS FROM [Adventure Works]  
      </Statement>  
   </Command>  
   <Properties>  
      <PropertyList>  
         <DataSourceInfo>Provider=MSOLAP;Data Source=local;</DataSourceInfo>  
         <Catalog>Adventure Works DW Multidimensional 2012</Catalog>  
         <Format>Multidimensional</Format>  
         <AxisFormat>ClusterFormat</AxisFormat>  
      </PropertyList>  
   </Properties>  
</Execute>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati XML &#40; XMLA &#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [Individuare metodo &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-methods-discover.md)   
 [Metodi &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-methods.md)   
 [Gli elementi XML &#40; XMLA &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Set di righe dello Schema di Analysis Services](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  