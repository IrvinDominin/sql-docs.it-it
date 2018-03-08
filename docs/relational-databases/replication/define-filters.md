---
title: Definisci filtri | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.replconflictviewer.definefilters.f1
helpviewer_keywords: Define Filters dialog box
ms.assetid: 1fa71d22-ce5a-4aae-ba05-4d755842aeac
caps.latest.revision: "18"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d8165cea64c9057b30f316cd6fee6117f3de0f97
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="define-filters"></a>Definisci filtri
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] La finestra di dialogo **Definisci filtri** consente di definire i filtri da applicare ai conflitti dei dati per visualizzare un subset dei conflitti nella griglia. Per definire un filtro, scegliere un operatore nell'elenco a discesa **Operatore** e quindi digitare un valore. Ad esempio, per visualizzare soltanto i conflitti in cui la riga in conflitto ignorata è il server **ReplTest1**, selezionare l'operatore **Uguale a** nell'elenco a discesa **Operatore** e immettere **ReplTest1** nella prima colonna **Valore** .  
  
## <a name="options"></a>Opzioni  
 **Operatore**  
 Consente di selezionare un operatore per il filtro, ad esempio **Minore o uguale a**.  
  
 **Value**  
 Consente di digitare un valore per il filtro. Per la maggior parte degli operatori è necessario specificare soltanto un valore nella prima colonna **Valore** , tuttavia, gli operatori **Compreso tra** e **Non compreso tra** richiedono un valore in entrambe le colonne **Valore** .  
  
 **Clear**  
 Fare clic su questo pulsante per cancellare tutti i filtri definiti in precedenza.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzatore conflitti di replica Microsoft &#40;replica di tipo merge&#41;](../../relational-databases/replication/microsoft-replication-conflict-viewer-merge-replication.md)   
 [Visualizzatore conflitti di replica Microsoft &#40;replica di tipo transazionale&#41;](../../relational-databases/replication/microsoft-replication-conflict-viewer-transactional-replication.md)  
  
  
