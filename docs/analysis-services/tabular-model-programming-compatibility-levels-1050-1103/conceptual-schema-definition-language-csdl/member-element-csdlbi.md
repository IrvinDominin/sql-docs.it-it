---
title: Elemento member (CSDLBI) | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
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
ms.assetid: 1ba225f5-3867-4aae-a519-e3c277688d1e
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5507e746f2f87abe2c4a08b5bda47a2eab5f61b5
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="member-element-csdlbi"></a>Elemento Member (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
L'elemento Member è un tipo complesso che funge da base per altri elementi.  
  
 Gli attributi vengano visualizzati in colonne, misure, proprietà di navigazione, gerarchie e livelli.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi e gli elementi che definiscono l'elemento Member.  
  
|Nome|Obbligatorio|Descrizione|  
|----------|-----------------|-----------------|  
|Nome||Il nome assegnato al membro (colonna, misura, proprietà di navigazione, gerarchia o livello) definito dall'implementazione del tipo TMember|  
|Caption|Sì|Nome visualizzato per il membro.|  
|ContextualNameRule|Sì|Il formato di denominazione utilizzato per eliminare le ambiguità dei membri. Il contenuto di questo attributo è definito dal tipo semplice ContextualNameRule.|  
|Hidden||Valore booleano che indica se il membro sarà nascosto per il client.<br /><br /> Il valore predefinito è false, ovvero le colonne sono visibili nel client.|  
|ReferenceName||Identificatore utilizzato per fare riferimento al membro in una query DAX. Se questo attributo viene omesso, il nome del campo viene utilizzato|  
  
## <a name="contextualnamerule-element"></a>Elemento ContextualNameRule  
 Questo tipo semplice definisce il formato di denominazione utilizzato per eliminare le ambiguità dei membri.  
  
|Valore|Description|  
|-----------|-----------------|  
|Nessuno|Utilizzare il nome dell'attributo.|  
|Contesto|Utilizzare il nome della relazione in entrata.|  
|Merge|Concatenare il nome della relazione in entrata e il nome della proprietà.|  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul modello a oggetti tabulare alla compatibilità 1050 1103 tramite i livelli](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
