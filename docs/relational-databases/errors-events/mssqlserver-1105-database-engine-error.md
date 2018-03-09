---
title: MSSQLSERVER_1105 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 1105 (Database Engine error)
ms.assetid: e7f4ad02-8c7f-4bb9-9781-2c86253f2138
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 28cb37ebdca0e3bb0078c591a78ff099ac44c5a7
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver1105"></a>MSSQLSERVER_1105
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|1105|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|NO_MORE_SPACE_IN_FG|  
|Testo del messaggio|Impossibile allocare spazio per l'oggetto '%.*ls'%.\*ls nel database'%.\*ls'. Il filegroup '%.\*ls' è pieno. Liberare spazio su disco eliminando i file non necessari, eliminando oggetti dal filegroup, aggiungendo file al filegroup oppure attivando l'aumento automatico delle dimensioni per i file esistenti nel filegroup.|  
  
## <a name="explanation"></a>Spiegazione  
Nel filegroup indicato non vi è spazio disponibile su disco.  
  
## <a name="user-action"></a>Azione dell'utente  
Eseguire le azioni seguenti per tentare di liberare spazio sufficiente nel filegroup:  
  
-   Attivare l'aumento automatico delle dimensioni dei file.  
  
-   Aggiungere altri file al gruppo di file.  
  
-   Liberare spazio su disco eliminando indici o tabelle che non sono più necessari.  
  
-   Per ulteriori informazioni, vedere "Risoluzione dei problemi relativi a spazio su disco insufficiente" nella documentazione online di SQL Server.  
  
> [!NOTE]  
> Se un indice si trova in più file, **ALTER INDEX REORGANIZE** può restituire un errore 1105 quando uno dei file è pieno. Il processo di riorganizzazione viene bloccato quando il processo prova a spostare le righe nel file pieno. Per risolvere questa limitazione, eseguire **ALTER INDEX REBUILD** anziché **ALTER INDEX REORGANIZE** o modificare il limite di aumento delle dimensioni dei file pieni.  
  
