---
title: Connetti ad Archiviazione di Microsoft Azure (Ripristino) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql13.swb.restore.connectstorage.f1
ms.assetid: c0b7d7c8-b878-4b7f-8120-d0c6917b583f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7be978540b673578fb9ca401f25dfab053f4f7e3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47854175"
---
# <a name="connect-to-microsoft-azure-storage-restore"></a>Connetti ad Archiviazione di Microsoft Azure (Ripristino)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La finestra di dialogo consente di specificare la connessione alle informazioni sull'account del servizio di archiviazione Windows Azure per recuperare l'archiviazione di file nell'account di archiviazione di Windows Azure. Dopo avere specificato le informazioni necessarie, fare clic su **Connetti** per stabilire la connessione al servizio di archiviazione Microsoft Azure.  
  
## <a name="windows-azure-storage-account"></a>Account di archiviazione di Windows Azure  
 **Account di archiviazione**  
 Selezionare, digitare o incollare il nome dell'account di archiviazione di Windows Azure da utilizzare. Nella casella di riepilogo sono elencati gli account utilizzati in precedenza.  
  
 **Chiave dell'account**  
 Specificare la chiave di accesso dell'account di archiviazione di Windows Azure.  
  
 Casella di controllo**Usa endpoint sicuri (HTTPS)**   
 Selezionare questa opzione per stabilire una connessione protetta al servizio di archiviazione Windows Azure (consigliato).  
  
 Casella di controllo**Salva chiave account**   
 Selezionare questa casella di controllo se si desidera memorizzare in SQL Server la chiave di accesso per l'account di archiviazione.  
  
### <a name="sql-credential"></a>Credenziali SQL  
 **Selezionare credenziali esistenti**  
 Selezionare le credenziali SQL esistenti corrispondenti alle informazioni sulla chiave account e sull'account di archiviazione.  
  
 **Crea nuove credenziali**  
 Selezionare questa opzione per creare nuove credenziali utilizzando le informazioni sulla chiave account e sull'account di archiviazione. Specificare il nome delle nuove credenziali nel campo **Nome credenziali** .  
  
  
