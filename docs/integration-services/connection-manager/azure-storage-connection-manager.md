---
title: Gestione connessione dell'archiviazione di Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpstorageconn.f1
- sql14.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 31440d6479353467d687467466f9c838a49d5252
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47724149"
---
# <a name="azure-storage-connection-manager"></a>Gestione connessione dell'archiviazione di Azure
  Il componente **Gestione connessione dell'archiviazione di Azure** consente di connettere un pacchetto SSIS a un account di archiviazione di Azure usando i valori specificati per le proprietà: Nome dell'account di archiviazione e Chiave dell'account.  
   
 **Gestione connessione dell'archiviazione di Azure** è un componente del [Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md). 
  
1.  Nella finestra di dialogo **Aggiungi gestione connessione SSIS** selezionare **Sottoscrizione di Azure**, quindi fare clic su **Aggiungi**.  
  
2.  Nella finestra di dialogo Editor gestione connessione di archiviazione di Azure, scegliere **Usa account Azure** per connettersi a un servizio di archiviazione di Azure con Internet o scegliere **Usa account per sviluppatore locale** per connettersi al servizio locale ospitato dall'emulatore di archiviazione di Azure.  
  
3.  Se si seleziona l'opzione **Usa account Azure** , eseguire queste operazioni:  
  
    1.  Specificare i valori per i campi **Nome dell'account di archiviazione** e **Chiave dell'account** . Questi valori vengono archiviati come dati sensibili nel pacchetto SSIS.  
  
    2.  Selezionare **Usa HTTPS** per usare HTTPS anziché HTTP per connettersi al servizio di archiviazione di Azure.  
  
4.  Scegliere **OK** per chiudere la finestra di dialogo.  
  
5.  È possibile visualizzare le proprietà del componente Gestione connessione create nella finestra **Proprietà** .  
  
  
