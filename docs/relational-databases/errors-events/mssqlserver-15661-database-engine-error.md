---
title: MSSQLSERVER_15661 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 15661 (Database Engine error)
ms.assetid: 88b01bfb-74ce-4aa0-aec0-7885261c7ef3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0271487ec01b29afe5485f754628d20fa4f74322
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47823634"
---
# <a name="mssqlserver15661"></a>MSSQLSERVER_15661
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|15661|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQLErrorNum15661|  
|Testo del messaggio|Impossibile utilizzare la stored procedure sp_estimate_data_compression_savings per le tabelle temporanee.|  
  
## <a name="explanation"></a>Spiegazione  
Una tabella temporanea è stata usata come argomento per la stored procedure sp_estimate_data_compression_savings. Sebbene la compressione delle tabelle temporanee sia supportata, non è possibile usare sp_estimate_data_compression_savings per stimare il risparmio in caso di compressione.  
  
## <a name="user-action"></a>Azione dell'utente  
Rimuovere la tabella temporanea come argomento per sp_estimate_data_compression_savings.  
  
