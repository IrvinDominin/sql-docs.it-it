---
title: "Data Sources Supported (SSAS Tabular) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6c2b1b3-91fc-4175-af25-509946dc7f24
caps.latest.revision: 28
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 28
---
# Data Sources Supported (SSAS Tabular)
  In questo argomento vengono descritti i tipi di origini dati che possono essere utilizzati con i modelli tabulari.  
  
##  <a name="bkmk_supported_ds"></a> Origini dati supportate per i modelli in memoria  
 È possibile importare dati dalle origini dati riportate nella tabella seguente. Il programma di installazione di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]non consente di installare i provider elencati per ogni origine dati. Alcuni provider potrebbero già essere installati con altre applicazioni nel computer; negli altri casi sarà necessario scaricare e installare il provider.  
  
|||||  
|-|-|-|-|  
|Origine|Versioni|Tipo di file|Provider|  
|Database di Access|Microsoft Access 2010 e versioni successive.|Estensione accdb o mdb|Provider OLE DB per ACE 14|  
|Database relazionali di SQL Server|Microsoft SQL Server 2008 e versioni successive, Microsoft SQL Server Data Warehouse 2008 e versioni successive, Database SQL di Microsoft Azure, Microsoft Analytics Platform System (APS)<br /><br /> <br /><br /> Piattaforma di strumenti analitici era precedentemente noto come SQL Server Parallel Data Warehouse (PDW). Originariamente la connessione a PDW da Analysis Services richiedeva un provider di dati speciale. Questo provider è stato sostituito in SQL Server 2012. A partire da SQL Server 2012, per le connessioni a PDW/piattaforma di strumenti analitici viene usato SQL Server Native Client. Per altre informazioni su APS, visitare il sito Web di [Microsoft Analytics Platform System](http://www.microsoft.com/en-us/server-cloud/products/analytics-platform-system/resources.aspx).|(non applicabile)|Provider OLE DB per SQL Server<br /><br /> Provider OLE DB di SQL Server Native Client<br /><br /> Provider OLE DB per SQL Server Native Client 10.0<br /><br /> Provider di dati .NET Framework per SQL Client|  
|Database relazionali Oracle|Oracle 9i e versioni successive.|(non applicabile)|Provider OLE DB Oracle<br /><br /> Provider di dati .NET Framework per il client Oracle<br /><br /> Provider di dati .NET Framework per SQL Server<br /><br /> OraOLEDB<br /><br /> MSDASQL|  
|Database relazionali di Teradata|Teradata V2R6 e versioni successive|(non applicabile)|Provider OLE DB TDOLEDB<br /><br /> Provider di dati .NET per Teradata|  
|Database relazionali di Informix||(non applicabile)|Provider OLE DB per Informix|  
|Database relazionali di IBM DB2|8.1|(non applicabile)|DB2OLEDB|  
|Database relazionali di Sybase Adaptive Server Enterprise (ASE)|15.0.2|(non applicabile)|Provider OLE DB per Sybase|  
|Altri database relazionali|(non applicabile)|(non applicabile)|Provider OLE DB o driver ODBC|  
|File di testo|(non applicabile)|Con estensione txt, tab, csv|Provider OLE DB per ACE 14 per Microsoft Access|  
|File di Microsoft Excel|Excel 2010 e versioni successive|Con estensione xlsx, xlsm, xlsb, xltx, xltm|Provider OLE DB per ACE 14|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] cartella di lavoro|Microsoft SQL Server 2008 e versioni successive di Analysis Services|Con estensione xlsx, xlsm, xlsb, xltx, xltm|ASOLEDB 10.5<br /><br /> (usato solo con le cartelle di lavoro [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pubblicate nelle farm di SharePoint con [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] installato)|  
|Cubo di Analysis Services|Microsoft SQL Server 2008 e versioni successive di Analysis Services|(non applicabile)|ASOLEDB 10|  
|Feed di dati<br /><br /> (utilizzato per importare dati dai report di Reporting Services, documenti di servizio Atom, Microsoft Azure Marketplace DataMarket e singoli feed di dati)|Formato Atom 1.0<br /><br /> Qualsiasi database o documento esposto come Windows Communication Foundation (WCF) Data Service (precedentemente ADO.NET Data Services).|Con estensione atomsvc per un documento di servizio che consente di definire uno o più feed<br /><br /> Con estensione atom per un documento di feed Web Atom|Provider di feed di dati Microsoft per [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]<br /><br /> Provider di feed di dati .NET Framework per [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]|  
|File Office Database Connection||Con estensione odc||  
  
  
##  <a name="bkmk_supported_ds_dq"></a> Origini dati supportate per i modelli DirectQuery  
 DirectQuery rappresenta un'alternativa alla modalità di archiviazione in memoria perché instrada le query ai sistemi di dati di backend e restituisce i risultati direttamente da tali sistemi anziché archiviare tutti i dati all'interno del modello (e nella RAM una volta caricato il modello). Analysis Services deve formulare query nella sintassi della query sul database nativo, quindi per questa modalità è supportato un subset più piccolo di origini dati.  
  
Origine dati   |Versioni  |Provider
---------|---------|---------
Microsoft SQL Server    |  2008 e versioni successive      |       Provider OLE DB per SQL Server, provider OLE DB di SQL Server Native Client, provider di dati .NET Framework per SQL Client  
Database SQL di Microsoft Azure    |   Tutto      |  Provider OLE DB per SQL Server, provider OLE DB di SQL Server Native Client, provider di dati .NET Framework per SQL Client            
Microsoft Azure SQL Data Warehouse     |   Tutto     |  Provider OLE DB di SQL Server Native Client, provider di dati .NET Framework per SQL Client       
Piattaforma di strumenti analitici Microsoft SQL     |   Tutto      |  Provider OLE DB per SQL Server, provider OLE DB di SQL Server Native Client, provider di dati .NET Framework per SQL Client       
Database relazionali Oracle     |  Oracle 9i e versioni successive       |  Provider OLE DB Oracle       
Database relazionali di Teradata    |  Teradata V2R6 e versioni successive     | Provider di dati .NET per Teradata    

  
##  <a name="bkmk_tips"></a> Suggerimenti per la scelta delle origini dati  
  
L'importazione di tabelle dai database relazionali consente di risparmiare alcuni passaggi perché le relazioni di *chiave esterna* vengono utilizzate durante l'importazione per creare relazioni tra tabelle in Progettazione modelli.  
  
È possibile risparmiare alcuni passaggi anche importando più tabelle e quindi eliminando quelle non necessarie. Se si importano le tabelle una alla volta, potrebbe essere ancora necessario creare manualmente le relazioni tra le tabelle.  
  
Le colonne in cui sono contenuti dati simili in origini dati diverse costituiscono la base per la creazione di relazioni all'interno di Progettazione modelli. Quando si utilizzano origini dati eterogenee, scegliere tabelle con colonne di cui è possibile eseguire il mapping alle tabelle in altre origini dati in cui sono contenuti dati identici o simili.  
  
I provider OLE DB offrono talvolta prestazioni migliori in termini di velocità per dati in larga scala. Quando si sceglie tra provider diversi per la stessa origine dati, provare innanzitutto il provider OLE DB.  
  
## Vedere anche  
 [Origini dati &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/data-sources-ssas-tabular.md)   
 [Importare dati &#40;SSAS tabulare&#41;](../Topic/Import%20Data%20\(SSAS%20Tabular\).md)  
  
  