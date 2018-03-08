---
title: Configurare le dimensioni di caricamento massime del File (PowerPivot per SharePoint) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac516c63-1e79-4ae8-bca6-32d3c1a09c00
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: d30e4644eed3d695db28a246aa9d05cba6e2cecc
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="configure-maximum-file-upload-size-power-pivot-for-sharepoint"></a>Configurare la dimensione massima per il caricamento dei file (PowerPivot per SharePoint)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Nelle cartelle di lavoro sono spesso contenute grandi quantità di dati che comportano il superamento della dimensione massima di file consentita per il caricamento in SharePoint. Quando si tenta di caricare un file che supera il limite massimo, verrà visualizzato l'errore seguente in SharePoint:  
  
-   "Le dimensioni del file specificato superano le dimensioni massime supportate".  
  
 Per aumentare le dimensioni del file, iniziare impostando l'opzione Dimensioni massime cartella di lavoro per Excel Services su 50 megabyte. In questo modo, i limiti delle dimensioni massime del file per Excel vengono allineati a quelli delle applicazioni Web di SharePoint (impostati su 50 megabyte in SharePoint 2010 e su 200 in SharePoint 2013 per impostazione predefinita). Se le dimensioni del file superano i 50 megabyte, aumentare i limiti delle dimensioni del file sia per Excel Services sia per l'applicazione Web.  
  
 Per modificare le dimensioni massime di caricamento del file è necessario essere un amministratore di SharePoint.  
  
### <a name="configure-maximum-file-size-for-excel-services"></a>Configurare le dimensioni massime del file per Excel Services  
  
1.  In Gestione applicazioni di Amministrazione centrale fare clic su **Gestisci applicazioni di servizio**.  
  
2.  Fare clic sul nome dell'applicazione Excel Services.  
  
3.  Fare clic su **Percorsi attendibili file**.  
  
4.  Fare clic sulla posizione per modificare le proprietà. Per impostazione predefinita, in Excel Services l'applicazione Web predefinita viene considerata sito attendibile. Se si usa l'applicazione Web predefinita, fare clic su **http://** per aprire la pagina di configurazione per questo percorso.  
  
5.  Scorrere fino a **Proprietà cartella di lavoro**.  
  
6.  In Dimensioni massime cartella di lavoro aumentare le dimensioni del file da 10 (valore predefinito) a 50 o a una dimensione maggiore, appropriata ai file in uso.  
  
     Per impostazione predefinita, 50 megabyte rappresenta la dimensione di caricamento file massima per le applicazioni Web di SharePoint. Se l'opzione Dimensioni massime cartella di lavoro viene impostata su un valore maggiore di 50 megabyte, seguire i passaggi nella procedura descritta di seguito per aumentare Dimensioni massime caricamento per l'applicazione Web di SharePoint allo stesso valore.  
  
     Il valore massimo che è possibile specificare è 2 gigabyte (o 2047 megabyte come specificato in Amministrazione centrale).  
  
7.  Scegliere **OK**.  
  
### <a name="configure-maximum-file-size-for-a-sharepoint-web-application"></a>Configurare le dimensioni massime del file per un'applicazione Web di SharePoint  
  
1.  In Gestione applicazioni di Amministrazione centrale fare clic su **Gestisci applicazioni Web**.  
  
    > [!NOTE]  
    >  Effettuare i passaggi seguenti solo se è stato aumentato il valore dell'opzione Dimensioni massime cartella di lavoro in Excel Services.  
  
2.  Selezionare l'applicazione, ad esempio **SharePoint - 80**.  
  
3.  Sulla barra multifunzione delle applicazioni Web, fare clic sulla freccia GIÙ sul pulsante Impostazioni generali.  
  
4.  Fare clic su **Impostazioni generali**.  
  
5.  Scorrere fino a **Dimensioni massime caricamento**.  
  
6.  Impostare la proprietà sul numero uguale o maggiore di quello impostato in Dimensioni massime cartella di lavoro in Excel Services.  
  
7.  Scegliere **OK**.  
  
  
