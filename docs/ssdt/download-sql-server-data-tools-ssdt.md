---
title: Scaricare SQL Server Data Tools (SSDT) | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssdt
ms.reviewer: ''
ms.suite: sql
ms.technology: ssdt
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords:
- installare ssdt, scaricare ssdt, versione più recente di ssdt
ms.assetid: b0fc4987-d260-4d0a-9dd1-98099835b361
caps.latest.revision: 113
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: 907b8a7d11bbd7889f3796d3f56633caec22a529
ms.sourcegitcommit: c929887686eabd6b754cf644a45656f0a0eb0445
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/05/2018
ms.locfileid: "43743484"
---
# <a name="download-and-install-sql-server-data-tools-ssdt-for-visual-studio"></a>Scaricare e installare SQL Server Data Tools (SSDT) per Visual Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md.md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
**SQL Server Data Tools** è uno strumento di sviluppo moderno che consente di compilare database relazionali SQL Server, database SQL di Azure, modelli di dati di Analysis Services (AS), pacchetti di Integration Services (IS) e report di Reporting Services (RS). Con SSDT è possibile progettare e distribuire qualsiasi tipo di contenuto SQL Server con la stessa facilità con la quale si sviluppa un'applicazione in Visual Studio.

*Per la maggior parte degli utenti, SQL Server Data Tools (SSDT) viene installato durante l'installazione di Visual Studio. Se si installa SSDT usando il programma di installazione di Visual Studio, vengono aggiunte le funzionalità SSDT di base. È pertanto necessario eseguire il [programma di installazione di SSDT autonomo](#ssdt-for-vs-2017-standalone-installer) per ottenere AS, IS ed RS.*

## <a name="install-ssdt-with-visual-studio-2017"></a>Installare SSDT con Visual Studio 2017

Per installare SSDT durante l'[installazione di Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio), selezionare il carico di lavoro **Elaborazione ed archiviazione dati** e quindi selezionare **SQL Server Data Tools**. Se Visual Studio è già installato, è possibile [modificare l'elenco dei carichi di lavoro](https://docs.microsoft.com/visualstudio/install/modify-visual-studio) per includere SSDT: ![Carico di lavoro Elaborazione ed archiviazione dati](../ssdt/media/download-sql-server-data-tools-ssdt/data-workload.png)



## <a name="install-analysis-services-integration-services-and-reporting-services-tools"></a>Installare Analysis Services, Integration Services e Reporting Services
Per installare AS, IS ed RS come supporto per i progetti, eseguire il [programma di installazione di SSDT autonomo](#ssdt-for-vs-2017-standalone-installer). 

Il programma di installazione elenca le istanze di Visual Studio disponibili per l'aggiunta degli strumenti di SSDT. Se Visual Studio non è installato, selezionando **Install a new SQL Server Data Tools instance** (Installa una nuova istanza di SQL Server Data Tools) è possibile installare SSDT con una versione minima di Visual Studio. Per un'esperienza ottimale, tuttavia, è consigliabile usare SSDT con [la versione più recente di Visual Studio](https://www.visualstudio.com/downloads). 

![Selezionare AS, IS, RS](../ssdt/media/download-sql-server-data-tools-ssdt/select-services.png)



## <a name="ssdt-for-vs-2017-standalone-installer"></a>SSDT per Visual Studio 2017 (programma di installazione autonomo)

[![download](../ssdt/media/download.png) Download di SSDT per Visual Studio 2017 (15.8) ](https://go.microsoft.com/fwlink/?linkid=2014060) 

> [!IMPORTANT]
> - Prima di installare SSDT per Visual Studio 2017 (15.8), disinstallare le estensioni *Progetti di Analysis Services* e *Progetti di Reporting Services*, se già installate, e chiudere tutte le istanze di Visual Studio.



**Informazioni sulla versione**  
  
Numero di versione: 15.8  
Numero di build: 14.0.16174.0  
Data di rilascio: 05 settembre 2018  

Per un elenco completo delle modifiche, vedere il [log delle modifiche](changelog-for-sql-server-data-tools-ssdt.md).

SSDT per Visual Studio 2017 ha gli stessi [requisiti di sistema](https://docs.microsoft.com/visualstudio/productinfo/vs2017-system-requirements-vs) di Visual Studio.  

### <a name="available-languages---ssdt-for-vs-2017"></a>Lingue disponibili - SSDT per VS 2017

Questa versione di **SSDT per VS 2017** può essere installata nelle lingue seguenti:  

[Cinese (semplificato)]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x804) | 
[Cinese (tradizionale)]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x404) | 
[Inglese (Stati Uniti)]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x409) | 
[Francese]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x40c)  
[Tedesco]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x407) | 
[Italiano]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x410) | 
[Giapponese]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x411) | 
[Coreano]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x412) | 
[Portoghese (Brasile)]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x416) | 
[Russo]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x419) | 
[Spagnolo]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x40a)  





## <a name="supported-sql-versions"></a>Versioni di SQL supportate
  
|Modelli di progetto|Piattaforme SQL supportate|  
|-------------------|--------------------|  
Database relazionali|  SQL Server 2005* - SQL Server 2017<br> (usare SSDT 17.x o SSDT per Visual Studio 2017 per la connessione a [SQL Server in Linux](../linux/sql-server-linux-overview.md))<br /><br />Database SQL di Azure<br /><br />Azure SQL Data Warehouse (supporta solo query, i progetti di database non sono ancora supportati)<br /><br />  * Il supporto per SQL Server 2005 è deprecato<br /><br /> e si consiglia di passare a una versione di SQL supportata ufficialmente|
  |Modelli di Analysis Services<br /><br />Report di Reporting Services | SQL Server 2008 - SQL Server 2017|
  |pacchetti di Integration Services| SQL Server 2012 - SQL Server 2017    |
  
## <a name="dacfx"></a>DacFx
SSDT per Visual Studio 2015 e SSDT per Visual Studio 2017 usano entrambi DacFx 17.4.1: [scaricare Data-Tier Application Framework (DacFx) 17.4.1](https://www.microsoft.com/download/details.aspx?id=56508).

## <a name="previous-versions"></a>Versioni precedenti

Per scaricare e installare SSDT per Visual Studio 2015 o una versione precedente di SSDT, vedere [Versioni precedenti di SQL Server Data Tools (SSDT e SSDT-BI)](previous-releases-of-sql-server-data-tools-ssdt-and-ssdt-bi.md).



## <a name="next-steps"></a>Passaggi successivi  
Dopo l'installazione di SSDT, consultare queste esercitazioni per imparare a creare database, pacchetti, modelli di dati e report mediante SSDT:  

- [Sviluppo di database offline orientato ai progetti](project-oriented-offline-database-development.md)  
- [Esercitazione SSIS: Creare un pacchetto ETL semplice](../integration-services/ssis-how-to-create-an-etl-package.md)  
- [Esercitazioni su Analysis Services](../analysis-services/analysis-services-tutorials-ssas.md)  
- [Creare un report tabella semplice (esercitazione su SSRS)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]


## <a name="see-also"></a>Vedere anche  
[Forum MSDN di SSDT](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[Blog del Team di SSDT](http://blogs.msdn.com/b/ssdt/)  
[Riferimento all'API DACFx](https://msdn.microsoft.com/library/dn645454.aspx)  
[Scaricare SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  
