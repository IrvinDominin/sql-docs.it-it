---
title: MSSQLSERVER_21889 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 21889 (Database Engine error)
ms.assetid: ae199540-7986-4cc2-b782-cd22793236d3
caps.latest.revision: 7
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 13c7ae116929c0178e9a9b2e0f381574a5cbfd75
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055910"
---
# <a name="mssqlserver21889"></a>MSSQLSERVER_21889
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|21889|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQLErrorNum21889|  
|Testo del messaggio|L'istanza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] '%s' non è un server di pubblicazione della replica. Eseguire `sp_adddistributor` sull'istanza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] '%s' con il database di distribuzione '%s' per consentire all'istanza di ospitare il database di pubblicazione '%s.' Assicurarsi di specificare lo stesso account di accesso e password di quello utilizzato per il server di pubblicazione originale.|  
  
## <a name="explanation"></a>Spiegazione  
 Per ospitare il database del server di pubblicazione, l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere un server di pubblicazione di replica. `sp_validate_redirected_publisher` richiama `sp_helpdistributor` sul server remoto per determinare se il server è un server di pubblicazione di replica. Questo errore viene restituito quando l'esecuzione della stored procedure `sp_helpdistributor` indica che l'istanza di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è un server di pubblicazione di replica.  
  
## <a name="user-action"></a>Azione dell'utente  
 Eseguire `sp_adddistributor` sull'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che ospita il database del server di pubblicazione. Quando si esegue `sp_adddistributor`, specificare il database di distribuzione corretto. Utilizzare lo stesso valore per il *@password* parametro a quello utilizzato quando `sp_adddistributor` è stato eseguito inizialmente nel server di distribuzione.  
  
  