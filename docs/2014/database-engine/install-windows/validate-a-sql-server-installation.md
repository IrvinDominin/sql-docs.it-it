---
title: Convalidare un'installazione di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- validating installations [SQL Server]
ms.assetid: 1689af50-d2b8-4aa6-8f27-cc7127157fc8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e2a71d127ad565690f78dbbbf8eeffaa13194b2a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178561"
---
# <a name="validate-a-sql-server-installation"></a>Convalidare un'installazione di SQL Server
  Il report sull'individuazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può essere utilizzato per verificare la versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e le caratteristiche di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installate nel computer. Il **Installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] report sull'individuazione delle funzionalità** consente di visualizzare un report di tutti i [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], e [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] prodotti e funzionalità che vengono installati nel server locale. Il report sull'individuazione delle funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è disponibile nella pagina **Strumenti** del Centro installazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Per eseguire il report sull'individuazione delle funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :**  
  
 Avviare Centro installazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] facendo clic sul pulsante **Start**, scegliendo **Tutti i programmi**, quindi **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\<nome versione>**, **Strumenti di configurazione** e quindi facendo clic su **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Centro installazione**. Per eseguire il report sull'individuazione delle funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], fare clic su **Strumenti** nell'area di navigazione a sinistra di **Centro installazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**, quindi fare clic su **Report sull'individuazione delle funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installate**.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] report sull'individuazione viene salvato in % ProgramFiles %\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< ultima sessione di installazione\>.  
  
 Tale report può essere generato anche tramite la riga di comando. Eseguire "Setup.exe /Action = RunDiscovery" da un prompt dei comandi, se si aggiunge "/ q" alla riga di comando precedente non viene visualizzata alcuna interfaccia utente, ma il report verrà comunque creato in % ProgramFiles %\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< ultima sessione di installazione\>.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e leggere i file di log del programma di installazione di SQL Server](view-and-read-sql-server-setup-log-files.md)  
  
  
