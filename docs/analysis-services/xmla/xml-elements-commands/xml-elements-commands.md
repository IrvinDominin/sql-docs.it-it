---
title: Comandi (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- commands [XML for Analysis]
- XML for Analysis, commands
- XMLA, commands
ms.assetid: c8a93ea6-8eb5-4204-b037-69cb442a0082
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3ffde9e4cc1500ee0637225dc76153f3d81b463f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="xml-elements---commands"></a>Elementi XML - comandi
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Questa sezione di riferimento contiene il XML per gli elementi Analysis (XMLA) che possono essere utilizzati all'interno di **comando** elemento durante un' **Execute** chiamata al metodo.  
  
|Elemento|Description|  
|-------------|-----------------|  
|[Elemento Alter (XMLA)](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)|Contiene gli elementi di Analysis Services Scripting Language (ASSL) utilizzati dal [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo per modificare gli oggetti in un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Elemento backup](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)|Esegue il backup di un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database in un file di backup.|  
|[Elemento batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)|Esegue uno o più XML per i comandi Analysis (XMLA) come un'operazione batch, in sequenza o in parallelo, in un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Elemento BeginTransaction](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)|Inizia una transazione nella sessione corrente con un'istanza di Analysis Services.|  
|[Elemento Cancel](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)|Annulla un comando attualmente in esecuzione su un'istanza di Analysis Services.|  
|[Elemento ClearCache](../../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md)|Cancella la cache in memoria per l'oggetto specificato su un'istanza di Analysis Services.|  
|[Elemento CommitTransaction](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)|Completa una transazione nella sessione corrente con un’istanza di Analysis Services.|  
|[Creare l'elemento](../../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)|Contiene gli elementi di Analysis Services Scripting Language (ASSL) utilizzati dal [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo per creare oggetti in un'istanza di Analysis Services.|  
|[Elemento Delete](../../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md)|Elimina un oggetto su un'istanza di Analysis Services.|  
|[Elemento DesignAggregations](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md)|Crea aggregazioni per una progettazione aggregazioni su un’istanza di Analysis Services.|  
|[Elemento DROP](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)|Elimina membri dell'attributo da una dimensione.|  
|[Elemento Insert](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)|Inserisce membri di attributo in una dimensione.|  
|[Blocca elemento](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)|Blocca un oggetto specificato su un'istanza di Analysis Services.|  
|[Elemento MergePartitions](../../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)|Unisce i dati di una o più partizioni di origine in una partizione di destinazione e quindi elimina le partizioni di origine.|  
|[Elemento NotifyTableChange](../../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md)|Notifica a un'istanza di Analysis Services che le tabelle sono state modificate in un'origine dati specificata.|  
|[Elemento Process](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|Elabora oggetti su un'istanza di Analysis Services.|  
|[Elemento Restore](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|Ripristina un database Analysis Services da un file di backup.|  
|[Elemento RollbackTransaction](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)|Esegue il rollback di una transazione nella sessione corrente con un'istanza di Analysis Services.|  
|[Elemento Statement](../../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)|Contiene una query o istruzione da inviare tramite il [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo a un'istanza di Analysis Services.|  
|[Elemento Subscribe](../../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md)|Sottoscrive un'analisi e restituisce un set di righe che contiene gli eventi di traccia da un'istanza di Analysis Services.|  
|[Elemento Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|Sincronizza un database Analysis Services con un altro database esistente.|  
|[Elemento Unlock](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)|Sblocca un blocco specificato su un'istanza di Analysis Services.|  
|[Update (elemento)](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)|Aggiorna i membri attributo in una dimensione|  
|[Elemento UpdateCells](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)|Aggiorna le celle in un cubo abilitato per la scrittura.|  
  
  
