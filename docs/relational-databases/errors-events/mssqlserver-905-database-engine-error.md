---
title: MSSQLSERVER_905 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 905 (Database Engine error)
ms.assetid: c828bb2e-e554-4f81-b76c-2b3740d2b944
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0eb7d90ffaba480c897f51e205edf7ce582a04cd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47619699"
---
# <a name="mssqlserver905"></a>MSSQLSERVER_905
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|905|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBSTARTUP_EE_PARTITIONING|  
|Testo del messaggio|Impossibile avviare il database '%.*ls' in questa edizione di SQL Server, perché contiene la funzione di partizione '%.\*ls'. Il partizionamento è supportato solo in SQL Server Enterprise Edition.|  
  
## <a name="explanation"></a>Spiegazione  
Il database contiene uno o più tabelle o indici partizionati. Il partizionamento non è supportato in questa edizione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il database non può pertanto essere avviato in modo corretto. Le tabelle e gli indici partizionati sono disponibili solo in alcune edizioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Funzionalità supportate dalle edizioni di SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
## <a name="user-action"></a>Azione dell'utente  
Scollegare il database utilizzando la stored procedure sp_detach_db. Se necessario, spostare i file, quindi collegare il database a un'istanza di un'edizione supportata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando CREATE DATABASE con l'opzione FOR ATTACH o FOR ATTACH_REBUILD_LOG. Disabilitare il partizionamento in tutte le tabelle e rimuovere le funzioni di partizionamento. Scollegare di nuovo il database e ricollegarlo al server corrente.  
  
