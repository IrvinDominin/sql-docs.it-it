---
title: MSSQLSERVER_17194 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "17194"
helpviewer_keywords:
- 17194 (Database Engine error)
ms.assetid: 0d03eb20-28a7-4ceb-8903-7f9420a620f7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d5425431d465c9bddba23c959aab41cefbfcdd89
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48203641"
---
# <a name="mssqlserver17194"></a>MSSQLSERVER_17194
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|17194|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico||  
|Testo del messaggio|Impossibile caricare la libreria di provider SSL necessaria per l'accesso. La connessione è stata chiusa. SSL viene utilizzato per crittografare la sequenza di accesso o tutte le comunicazioni, a seconda della configurazione del server. Consultare la documentazione online per informazioni su questo messaggio di errore:  0xXXXX. [CLIENT: 11.11.11.11]|  
  
## <a name="explanation"></a>Spiegazione  
 Questo errore indica che la connessione è stata chiusa dal client. Questo errore potrebbe verificarsi poiché è scaduto il timeout della connessione. Nel messaggio di errore viene visualizzato un valore del sistema operativo che descrive il problema sottostante.  
  
## <a name="user-action"></a>Azione dell'utente  
 Se il codice di errore nel messaggio è 0x2746 (valore decimale 10054), la connessione è stata reimpostata dal client, in genere a causa di un timeout. Per risolvere l'errore, aumentare il timeout della connessione nel client o nel programma che esegue la chiamata.  
  
 Per determinare una possibile soluzione per altri valori del messaggio di errore, usare il comando **net helpmsg** del sistema operativo e specificare il valore decimale del codice di errore.  
  
 Per altre informazioni sulla connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Configurazione di rete del server](../../database-engine/configure-windows/server-network-configuration.md) e [Configurazione di rete dei client](../../database-engine/configure-windows/client-network-configuration.md).  
  
## <a name="internal-only"></a>Solo interno  
  
