---
title: Implementazione di un'estensione per l'elaborazione dati | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: extensions
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- custom data processing extensions [Reporting Services]
- data sources [Reporting Services], data processing extensions
- data processing extensions [Reporting Services]
- extensions [Reporting Services], data processing
ms.assetid: 8dc2b44e-5ad9-411d-a29f-7213e29321a9
caps.latest.revision: "35"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0af2bbfa0c6a02f57c1d09092ce05ac36f8d3c42
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="implementing-a-data-processing-extension"></a>Implementazione di un'estensione per l'elaborazione dati
  Le estensioni per l'elaborazione dati in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] consentono di eseguire la connessione a un'origine dati e di recuperare i dati. Fungono inoltre da ponte tra un'origine dati e un set di dati. Le estensioni per l'elaborazione dati di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] sono modellate in base a un subset delle interfacce dei provider di dati [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Panoramica delle estensioni per l'elaborazione dati](../../../reporting-services/extensions/data-processing/data-processing-extensions-overview.md)  
 Vengono fornite informazioni introduttive per la scrittura di un'estensione per l'elaborazione dati per [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Preparazione all'implementazione di un'estensione per l'elaborazione dati](../../../reporting-services/extensions/data-processing/preparing-to-implement-a-data-processing-extension.md)  
 Vengono descritte le interfacce disponibili quando si implementa un'estensione per l'elaborazione dati di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] e vengono indicati i casi in cui è necessario implementare un'interfaccia specifica.  
  
 [Creazione di una libreria di estensioni per l'elaborazione dati](../../../reporting-services/extensions/data-processing/creating-a-data-processing-extension-library.md)  
 Vengono descritte le operazioni di assegnazione di uno spazio dei nomi per l'estensione per l'elaborazione dati di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] e di compilazione dell'estensione per l'elaborazione dati nella DLL di una libreria.  
  
 [Implementazione di una classe Connection per un'estensione per l'elaborazione dati](../../../reporting-services/extensions/data-processing/implementing-a-connection-class-for-a-data-processing-extension.md)  
 Vengono descritti gli attributi di una connessione e come implementare una classe **Connection** personalizzata per l'estensione per l'elaborazione dati.  
  
 [Implementazione di una classe Command per un'estensione per l'elaborazione dati](../../../reporting-services/extensions/data-processing/implementing-a-command-class-for-a-data-processing-extension.md)  
 Vengono descritti gli attributi di un comando e come implementare una classe **Command** personalizzata per l'estensione per l'elaborazione dati.  
  
 [Implementazione di una classe DataReader per un'estensione per l'elaborazione dati](../../../reporting-services/extensions/data-processing/implementing-a-datareader-class-for-a-data-processing-extension.md)  
 Vengono descritti gli attributi di un lettore di dati e come implementare una classe **DataReader** personalizzata per l'estensione per l'elaborazione dati.  
  
 [Uso di un set di dati esterno con Reporting Services](../../../reporting-services/extensions/data-processing/using-an-external-dataset-with-reporting-services.md)  
 Viene descritto come esporre gli oggetti **DataSet** personalizzati nel server di report per l'uso.  
  
 [Distribuzione di un'estensione per l'elaborazione dati](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)  
 Viene descritto come distribuire un'estensione per l'elaborazione dati.  
  
 [Debug del codice di un'estensione per l'elaborazione dati](../../../reporting-services/extensions/data-processing/debugging-data-processing-extension-code.md)  
 Viene descritto come eseguire il debug del codice nelle estensioni per l'elaborazione dati.  
  
 [Rimozione di un'estensione per l'elaborazione dati](../../../reporting-services/extensions/data-processing/removing-a-data-processing-extension.md)  
 Viene descritto come rimuovere un'estensione per l'elaborazione dati da un server di report o da Progettazione report.  
  
 Per un esempio di estensione per l'elaborazione dati completamente implementata, vedere la pagina degli [esempi del prodotto SQL Server Reporting Services](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
