---
title: "Specifiche di capacità massima (Analysis Services) | Documenti Microsoft"
ms.custom: 
ms.date: 07/27/2017
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
- objects [Analysis Services], maximum number
- objects [Analysis Services], maximum size
ms.assetid: 49fe1673-b908-4c7a-88ff-415efd294d27
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 8e60e818b40d2aa7c266903a23d0fec908039b44
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="maximum-capacity-specifications-analysis-services"></a>Specifiche di capacità massima (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Nelle tabelle seguenti vengono indicate le dimensioni e le quantità massime dei diversi oggetti definiti nei componenti di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] con diverse modalità di distribuzione del server.  
  
 In questo argomento sono incluse le sezioni seguenti:  
  
 [Multidimensionale e Data Mining (DeploymentMode = 0)](#bkmk_OLAP)  
  
 [SharePoint (DeploymentMode = 1)](#bkmk_sharepoint)  
  
 [Tabulare (DeploymentMode = 2)](#bkmk_vertipaq)  
  
##  <a name="bkmk_OLAP">Multidimensionale e Data Mining (DeploymentMode = 0)</a>  
 La modalità di archiviazione MOLAP, che prevede l'archiviazione sia di dati che di metadati, prevede limiti fisici aggiuntivi relativi alle dimensioni dei file. Per impostazione predefinita, la dimensione massima dei file di archivio delle stringhe è di 4 GB. Se sono necessari file più grandi per gli archivi di stringhe, è possibile specificare un'architettura di archiviazione di stringhe diversa. Per ulteriori informazioni, vedere [configurare l'archivio di stringhe per partizioni e dimensioni](../../../analysis-services/multidimensional-models/configure-string-storage-for-dimensions-and-partitions.md).  
  
|Oggetto|Quantità/dimensioni massime|  
|------------|----------------------------|  
|Database in un'istanza|2^31-1 = 2,147,483,647|  
|Dimensioni in un database|2^31-1 = 2,147,483,647|  
|Attributi in una dimensione|2^31-1 = 2,147,483,647|  
|Membri in un attributo di dimensione|2^31-1 = 2,147,483,647|  
|Gerarchie definite dall'utente in una dimensione|2^31-1 = 2,147,483,647|  
|Livelli in una gerarchia definita dall'utente|2^31-1 = 2,147,483,647|  
|Cubi in un database|2^31-1 = 2,147,483,647|  
|Gruppi di misure in un cubo|2^31-1 = 2,147,483,647|  
|Misure in un gruppo di misure|2^31-1 = 2,147,483,647|  
|Calcoli in un cubo|2^31-1 = 2,147,483,647|  
|Indicatori di prestazioni chiave in un cubo|2^31-1 = 2,147,483,647|  
|Azioni in un cubo|2^31-1 = 2,147,483,647|  
|Partizioni in un cubo|2^31-1 = 2,147,483,647|  
|Traduzioni in un cubo|2^31-1 = 2,147,483,647|  
|Aggregazioni in una partizione|2^31-1 = 2,147,483,647|  
|Celle restituite da una query|2^31-1 = 2,147,483,647|  
|Dimensioni dei record della query di origine|64 KB|  
|Lunghezza dei nomi degli oggetti|100 caratteri|  
|Numero massimo di stati distinti in una colonna attributo del modello di data mining|2^31-1 = 2,147,483,647|  
|Numero massimo di attributi considerati (caratteristica di selezione degli attributi)|2^31-1 = 2,147,483,647|  
  
 Per ulteriori informazioni sulle convenzioni di denominazione di oggetti, vedere [oggetti ASSL e relative caratteristiche](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-objects-and-object-characteristics.md).  
  
 Per ulteriori informazioni sulle limitazioni di origine dati per l'elaborazione analitica online (OLAP) e il data mining, vedere [supportate origini di dati &#40; SSAS - multidimensionale &#41; ](../../../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md), [Supportate origini dati &#40; SSAS - multidimensionale &#41; ](../../../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md), e [oggetti ASSL e relative caratteristiche](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-objects-and-object-characteristics.md).  
  
##  <a name="bkmk_sharepoint">SharePoint (DeploymentMode = 1)</a>  
  
|Oggetto|Quantità/dimensioni massime|  
|------------|----------------------------|  
|Database in un'istanza|2^31-1 = 2,147,483,647|  
|Tabelle in un database|2^31-1 = 2,147,483,647|  
|Colonne in una tabella|2^31-1 = 2,147,483,647<br /><br /> **Avviso:** numero totale di colonne in una tabella dipende dal numero totale di misure e colonne calcolate associate alla stessa tabella.<br /><br /> Il numero massimo di "colonne + misure + colonne calcolate" per una tabella è di 2^31-1 = 2.147.483.647|  
|Righe in una tabella|Nessuna limitazione<br /><br /> **Avviso:** con la restrizione che nessuna colonna singola può contenere più di 1.999.999.997 valori distinti.|  
|Gerarchie in una tabella|2^31-1 = 2,147,483,647|  
|Livelli in una gerarchia|2^31-1 = 2,147,483,647|  
|Relazioni|2^31-1 = 2,147,483,647|  
|Colonne chiave in una tabella|2^31-1 = 2,147,483,647|  
|Misure in una tabella|2^31-1 = 2,147,483,647<br /><br /> **Avviso:** numero totale di misure in una tabella dipende dal numero totale di colonne e colonne calcolate associate alla stessa tabella.<br /><br /> Il numero massimo di "colonne + misure + colonne calcolate" per una tabella è di 2^31-1 = 2.147.483.647|  
|Colonne calcolate in una tabella|2^31-1 = 2,147,483,647<br /><br /> **Avviso:** numero totale di colonne calcolate in una tabella dipende dal numero totale di colonne e misure associate alla stessa tabella.<br /><br /> Il numero massimo di "colonne + misure + colonne calcolate" per una tabella è di 2^31-1 = 2.147.483.647|  
|Celle restituite da una query|2^31-1 = 2,147,483,647|  
|Dimensioni dei record della query di origine|64 KB|  
|Lunghezza dei nomi degli oggetti|100 caratteri|  
  
##  <a name="bkmk_vertipaq">Tabulare (DeploymentMode = 2)</a>  
Di seguito sono limiti teorici. Prestazioni risulta diminuita in numeri più bassi.   

|Oggetto|Quantità/dimensioni massime|  
|------------|----------------------------|  
|Database in un'istanza|16,000|  
|Numero combinato di tabelle e colonne in un database|16,000|  
|Righe in una tabella|Nessuna limitazione<br /><br /> **Avviso:** con la restrizione che nessuna colonna singola nella tabella può avere più di 1.999.999.997 valori distinti.|  
|Gerarchie in una tabella|15,999|  
|Livelli in una gerarchia|15,999|  
|Relazioni|8.000|  
|Tabella tutte le colonne chiave|15,999|  
|Misure in un tipo di tabelle|2^31-1 = 2,147,483,647|  
|Celle restituite da una query|2^31-1 = 2,147,483,647|  
|Dimensioni dei record della query di origine|64 KB|  
|Lunghezza dei nomi degli oggetti|512 caratteri|  
  
## <a name="see-also"></a>Vedere anche  
 [Determinare la modalità server di un'istanza di Analysis Services](../../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Proprietà generali](../../../analysis-services/server-properties/general-properties.md)  
  
  
