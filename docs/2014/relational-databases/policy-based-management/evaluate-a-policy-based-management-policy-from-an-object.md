---
title: Valutare i criteri della gestione basata su criteri da un oggetto | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: b9e9d646-4894-4dee-a02a-0c71a8dc020e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e62aa591b3fb1f0b22f3dd829701bb5732d31a5e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48152133"
---
# <a name="evaluate-a-policy-based-management-policy-from-an-object"></a>Valutare i criteri della gestione basata su criteri da un oggetto
  In questo argomento verrà descritto come valutare i criteri da un'istanza del server, un database o un oggetto di database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Security](#Security)  
  
-   **Per valutare i criteri da un oggetto tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   La modalità di esecuzione è definita come parte dei criteri e non può essere modificata nella finestra di dialogo **Valuta criteri** .  
  
-   Nella finestra di dialogo **Valuta criteri** vengono visualizzati solo i criteri appropriati per l'oggetto di database.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È necessaria l'appartenenza al ruolo PolicyAdministratorRole nel database msdb.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-evaluate-a-policy-from-an-object"></a>Per valutare i criteri da un oggetto  
  
1.  In Esplora oggetti fare clic con il pulsante destro del mouse su un'istanza del server, un database o un oggetto di database, scegliere **Criteri**, quindi selezionare **Valuta**.  
  
2.  Nella finestra di dialogo **Valuta criteri** selezionare uno o più criteri e fare clic su **Valuta** per eseguire i criteri in modalità di valutazione. Verrà generato un report sulla conformità per il set di destinazioni, ma [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non verrà riconfigurato, né verrà applicata la conformità successiva. Per destinazioni non conformi ai criteri selezionati e in cui sono incluse proprietà che possono essere riconfigurate dalla gestione basata su criteri, è possibile applicare la conformità ai criteri facendo clic su **Applica**. Per ulteriori informazioni sulle opzioni disponibili nella finestra di dialogo **Valuta criteri** , vedere [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md), [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md)e [Results Detailed View Dialog Box](results-detailed-view-dialog-box.md).  
  
3.  Al termine, fare clic su **Chiudi**.  
  
  
