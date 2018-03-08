---
title: Mappe personalizzate nei report di Reporting Services per dispositivi mobili | Microsoft Docs
ms.custom: 
ms.date: 03/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: mobile-reports
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59a4ebad-587a-4770-afcd-c69216b8afd9
caps.latest.revision: "9"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b4143913d2bab5425fede35cea6758f86820236f
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="custom-maps-in-reporting-services-mobile-reports"></a>Esegue il mapping personalizzato nei report di Reporting Services per dispositivi mobili
Le mappe geografiche in SQL Server Mobile Report Publisher sono definite in un formato noto come *file di forma ESRI*.  
  
Inizialmente progettato da una società privata, oggi è un formato semi aperto molto diffuso, usato in gran parte delle applicazioni GIS. In conformità con questo formato, Mobile Report Publisher richiede di fornire due file durante la definizione di una mappa:  
  
- Un file SHP per geometrie di forma  
- Un file DBF per i metadati  
  
I nomi dei file di base devono corrispondere (ad esempio, *canada.shp* e *canada.dbf*). I metadati devono includere il campo *NAME* con il valore del nome della forma corrispondente (chiave), che verrà usato durante la compilazione della mappa con dati.  
  
> **Nota**: le dimensioni dei due file di mapping, ossia SHP e DBF, non possono superare insieme i 512 KB. Se i file di mapping sono troppo grandi, usare uno strumento come [http://mapshaper.org/](http://mapshaper.org/) per ridurne le dimensioni.  
  
Vedere come [aggiungere mappe personalizzate ai report per dispositivi mobili](../../reporting-services/mobile-reports/add-a-custom-map-to-a-reporting-services-mobile-report.md).  
  
## <a name="technical-information"></a>Informazioni tecniche  
  
- Specifica ufficiale: [http://www.esri.com/library/whitepapers/pdfs/shapefile.pdf](http://www.esri.com/library/whitepapers/pdfs/shapefile.pdf)  
- Articolo di Wikipedia sul file di forma [http://en.wikipedia.org/wiki/Shapefile](http://en.wikipedia.org/wiki/Shapefile)  
  
## <a name="creating--editing-map-geometry"></a>Creazione e modifica della geometria di mapping  
  
La creazione e la modifica dei file di forma è un processo complesso che esula dall'ambito di questo documento. Di seguito sono riportate alcune risorse e applicazioni utili per iniziare:  
  
- ArcGIS: [http://www.arcgis.com/](http://www.arcgis.com/)  
- Plug-in MAPublisher per Adobe Illustrator: [http://www.avenza.com/mapublisher](http://www.avenza.com/mapublisher)  
- QuantumGIS (gratuito): [http://www.qgis.org/](http://www.qgis.org/)  
- Manco ShapeFile Editor: [http://www.mancosoftware.com/ShapeFileEditor](http://www.mancosoftware.com/ShapeFileEditor)  
  
## <a name="existing-shapefiles"></a>File di forma esistenti  
  
Molti file di forma esistenti possono essere scaricati dal Web, da siti come i seguenti:  
  
- Diva-GIS: [http://www.diva-gis.org/Data](http://www.diva-gis.org/Data)  
- OpenStreetMap: [http://openstreetmapdata.com/data](http://openstreetmapdata.com/data)  
  
### <a name="see-also"></a>Vedere anche  
- [Eseguire il mapping nei report di Reporting Services per dispositivi mobili](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)  
- [Creare e pubblicare report per dispositivi mobili con SQL Server Mobile Report Publisher](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)   
  
  
  
