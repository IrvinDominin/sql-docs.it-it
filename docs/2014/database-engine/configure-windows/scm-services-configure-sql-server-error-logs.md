---
title: Configurare log degli errori di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.configurelogs.configureerrorlogs.f1
ms.assetid: 03f0d463-9b0b-4af9-a853-da936d75e5af
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: dc22c30c6aace8c1d67a4ff92b26deeb56e42a86
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48217871"
---
# <a name="configure-sql-server-error-logs"></a>Configura log degli errori di SQL Server
  In questo argomento viene descritto come visualizzare o modificare la modalità di riciclo dei log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a>Per aprire la finestra di dialogo Configura log degli errori di SQL Server  
  
1.  In Esplora oggetti espandere l'istanza di SQL Server, espandere **Gestione**, fare clic con il pulsante destro del mouse su **Log di SQL Server**e quindi scegliere **Configura**.  
  
2.  Nella finestra di dialogo **Configura log degli errori di SQL Server** , scegliere dalle opzioni seguenti.  
  
     **Limita il numero di file di log degli errori creati prima di essere riciclati**  
     Selezionare questa opzione per limitare il numero di log degli errori creati prima di essere riciclati. Ogni volta che viene avviata un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene creato un nuovo log degli errori. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mantiene backup dei sei log precedenti, a meno che non si selezioni questa opzione e non si specifichi un diverso numero massimo di log degli errori tramite l'opzione seguente.  
  
     **Numero massimo di file di log degli errori**  
     Consente di specificare il numero massimo di log degli errori creati prima di essere riciclati. Il valore predefinito è 6 che corrisponde al numero di log di backup precedenti mantenuti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prima che vengano riciclati.  
  
  
