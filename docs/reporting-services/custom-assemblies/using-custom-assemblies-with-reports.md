---
title: Uso di assembly personalizzati con i report | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: custom-assemblies
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- custom assemblies [Reporting Services]
- assemblies [Reporting Services], custom
- custom assemblies [Reporting Services], about custom assemblies
ms.assetid: 53d141d0-2185-466a-84dc-7b90d284da3d
caps.latest.revision: "32"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 254dea52c61a5e06f51cc5ddb81efed175a5da46
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="using-custom-assemblies-with-reports"></a>Utilizzo di assembly personalizzati con i report
  In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è possibile scrivere codice personalizzato per i valori, gli stili e la formattazione degli elementi dei report. È ad esempio possibile utilizzare il codice personalizzato per formattare le valute in base alle impostazioni locali, per contrassegnare determinati valori con una formattazione speciale o per applicare altre regole di business in uso nella società. Un metodo per includere questo codice nei report consiste nel creare un assembly di codice personalizzato usando [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], a cui sia possibile fare riferimento dai file di definizione del report. Il server chiama le funzioni degli assembly personalizzati durante l'esecuzione di un report. Gli assembly personalizzati possono essere utilizzati per recuperare funzioni specifiche che si intende utilizzare nei report.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Riferimento agli assembly in un file RDL](../../reporting-services/custom-assemblies/referencing-assemblies-in-an-rdl-file.md)  
 Viene descritto come fare riferimento agli assembly personalizzati in un file RDL (Report Definition Language).  
  
 [Distribuzione di un assembly personalizzato](../../reporting-services/custom-assemblies/deploying-a-custom-assembly.md)  
 Viene descritto come distribuire un assembly personalizzato in Progettazione report e nel server di report.  
  
 [Uso di assembly personalizzati con nome sicuro](../../reporting-services/custom-assemblies/using-strong-named-custom-assemblies.md)  
 Viene descritto come utilizzare gli assembly personalizzati con nomi sicuri.  
  
 [Asserzione di autorizzazioni negli assembly personalizzati](../../reporting-services/custom-assemblies/asserting-permissions-in-custom-assemblies.md)  
 Viene descritto come distribuire assembly personalizzati con autorizzazioni limitate e specifiche e come effettuare l'asserzione di tali autorizzazioni nel codice.  
  
 [Accesso agli assembly personalizzati tramite espressioni](../../reporting-services/custom-assemblies/accessing-custom-assemblies-through-expressions.md)  
 Viene descritto come chiamare metodi di assembly personalizzati come espressioni di report nelle definizioni del report.  
  
 [Inizializzazione di oggetti assembly personalizzati](../../reporting-services/custom-assemblies/initializing-custom-assembly-objects.md)  
 Viene descritto come inizializzare i valori per gli oggetti degli assembly personalizzati chiamati da un report.  
  
 [Procedura: Debug di assembly personalizzati](../../reporting-services/custom-assemblies/how-to-debug-custom-assemblies.md)  
 Viene descritto come eseguire il debug del codice dell'assembly personalizzato.  
  
## <a name="see-also"></a>Vedere anche  
 [Report Definition Language &#40;SSRS&#41;](../../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
