---
title: MSSQLSERVER_8974 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8974 (Database Engine error)
ms.assetid: 52098678-0858-4a14-ad07-37ebbafca5fc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fe6bc228759f937a2da08e9599d2ee28fba99c9f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47671230"
---
# <a name="mssqlserver8974"></a>MSSQLSERVER_8974
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|8974|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC3_OFF_ROW_DATA_NODE_HAS_TWO_PARENTS|  
|Testo del messaggio|Errore di tabella: ID di oggetto ID_O, ID di indice ID_I, ID di partizione ID_PN, ID di unità di allocazione ID_A (tipo TIPO). La pagina P_ID2, slot S_ID2 e la pagina P_ID3, slot P_ID3 puntano al nodo di dati all'esterno di righe alla pagina P_ID1, slot S_ID1, ID di testo TEXT_ID.|  
  
## <a name="explanation"></a>Spiegazione  
Un nodo di dati all'esterno di righe viene elencato come nodo figlio da due record di dati o di indice. Un nodo può disporre di un solo nodo padre.  
  
## <a name="user-action"></a>Azione dell'utente  
  
### <a name="look-for-hardware-failure"></a>Individuare errori hardware  
Eseguire gli strumenti di diagnostica hardware e risolvere eventuali problemi. Esaminare inoltre il registro di sistema di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows e il registro delle applicazioni, nonché il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per stabilire se l'errore è dovuto a un problema hardware. Risolvere tutti i problemi relativi all'hardware indicati nei log.  
  
In caso di problemi persistenti che provocano il danneggiamento dei dati, provare a sostituire i vari componenti hardware per isolare il problema. Verificare che nel sistema non sia abilitata la memorizzazione nella cache in scrittura sul controller del disco. Se si ritiene che il problema sia dovuto alla memorizzazione nella cache in scrittura, rivolgersi al fornitore dell'hardware.  
  
Infine, potrebbe essere conveniente passare a un nuovo sistema hardware. A tale scopo può essere necessario riformattare le unità disco e reinstallare il sistema operativo.  
  
### <a name="restore-from-backup"></a>Eseguire un ripristino da backup  
Se il problema non è correlato all'hardware ed è disponibile un backup valido noto, ripristinare il database dal backup.  
  
### <a name="run-dbcc-checkdb"></a>Eseguire DBCC CHECKDB  
Se non è disponibile un backup valido, eseguire DBCC CHECKDB senza la clausola REPAIR per determinare l'entità del danno. Verrà automaticamente suggerita la clausola REPAIR da usare. Eseguire quindi DBCC CHECKDB con la clausola REPAIR appropriata per correggere il database.  
  
> [!CAUTION]  
> Se non si è certi dell'effetto prodotto sui dati dall'esecuzione di DBCC CHECKDB con la clausola REPAIR, contattare il personale del supporto tecnico prima di eseguire l'istruzione.  
  
Se l'esecuzione di DBCC CHECKDB con una clausola REPAIR non consente di risolvere il problema, contattare il personale del supporto tecnico.  
  
#### <a name="results-of-running-repair-options"></a>Risultati dell'esecuzione delle opzioni REPAIR  
Il nodo di dati all'esterno di righe della pagina *P_ID1* verrà eliminato così come entrambi i riferimenti nelle pagine *P_ID2* e *P_ID3*.  
  
> [!CAUTION]  
> L'operazione di correzione potrebbe comportare la perdita di dati.  
  
