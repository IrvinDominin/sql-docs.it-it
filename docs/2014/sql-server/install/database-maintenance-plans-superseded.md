---
title: Sostituito i piani di manutenzione del database | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- suspended database maintenance plans
- database maintenance plans [SQL Server Agent]
- maintenance plans [SQL Server Agent]
ms.assetid: efac127c-6c81-4c7a-a6c4-9aae5d15545d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 769bc3ad8b330afd81b14aed1340a67c1d7812ef
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48181441"
---
# <a name="database-maintenance-plans-superseded"></a>Piani di manutenzione del database sostituiti
    
## <a name="component"></a>Componente  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
## <a name="description"></a>Description  
 I piani di manutenzione del database esistenti sono stati aggiornati e continuano a funzionare. Tuttavia, non sarà possibile creare nuovi piani di manutenzione del database utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per visualizzare i piani di manutenzione in Esplora oggetti, espandere Gestione, quindi espandere Legacy. È possibile eseguire la migrazione di piani di manutenzione di database esistenti al nuovo formato selezionando **Migrate** dal menu di scelta rapida per qualsiasi piano di manutenzione del database. Poiché la nuova caratteristica del piano di manutenzione del database non è una sostituzione diretta dei piani di manutenzione del database, dopo la migrazione è possibile che alcune funzionalità vadano perse. Poiché il piano precedente non viene eliminato con la migrazione di un piano di manutenzione del database, è possibile testarne la funzionalità prima di rimuoverlo.  
  
 Le caratteristiche seguenti non sono più supportate all'interno di piani di manutenzione del database:  
  
-   Log shipping  
  
-   Il **tentarne la riparazione dei problemi non gravi** opzione delle **Controlla integrità Database** attività  
  
## <a name="corrective-action"></a>Azione correttiva  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] impedisce l'inserimento del log shipping in un piano di manutenzione del database. Per ulteriori informazioni, vedere "Log shipping" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
