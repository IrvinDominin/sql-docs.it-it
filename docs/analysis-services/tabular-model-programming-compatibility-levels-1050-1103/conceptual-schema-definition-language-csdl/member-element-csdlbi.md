---
title: Elemento member (CSDLBI) | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 1ba225f5-3867-4aae-a519-e3c277688d1e
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7bc33ebc0cd970c58f4f27d4b49a972c9ed724c0
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="member-element-csdlbi"></a>Elemento Member (CSDLBI)
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
  
  