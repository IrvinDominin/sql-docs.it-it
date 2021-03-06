---
title: Converti in finestra di dialogo del modello di distribuzione di pacchetto | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.bids.converttolegacydeployment.f1
ms.assetid: 9e60a34a-10f7-48d1-966f-b3ff236ab4b7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 17b3dae4dd2087fcae152718b9333d1b3afb52c8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140141"
---
# <a name="convert-to-package-deployment-model-dialog-box"></a>Finestra di dialogo Converti in modello di distribuzione di pacchetti
  Con il comando **Converti nel modello di distribuzione del pacchetto** è possibile convertire un pacchetto nel modello di distribuzione del pacchetto dopo aver verificato la compatibilità del progetto e di ogni relativo pacchetto con questo modello. Se in un pacchetto vengono utilizzate funzionalità univoche per il modello di distribuzione del progetto, ad esempio parametri, il pacchetto non può essere convertito.  
  
## <a name="task-list"></a>Elenco attività  
 Per la conversione di un pacchetto nel modello di distribuzione del pacchetto sono necessari due passaggi.  
  
1.  Quando si seleziona il comando **Converti nel modello di distribuzione del pacchetto** dal menu **Progetto** viene verificata la compatibilità del progetto e di ogni relativo pacchetto con questo modello. I risultati vengono visualizzati nella tabella **Risultati** .  
  
     Se la verifica di compatibilità del progetto o di un pacchetto non viene completata correttamente, per ottenere ulteriori informazioni fare clic su **Non riuscito** nella colonna **Risultato** . Fare clic su **Salva report** per salvare una copia di queste informazioni in un file di testo.  
  
2.  Se il progetto e tutti i pacchetti superano la verifica di compatibilità, fare clic su **OK** per convertire il pacchetto.  
  
> [!NOTE]  
>  Per convertire un progetto nel modello di distribuzione del progetto usare la **Conversione guidata progetto di Integration Services**. Per altre informazioni, vedere [Integration Services Project Conversion Wizard](../../2014/integration-services/integration-services-project-conversion-wizard.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di progetti e pacchetti](packages/deploy-integration-services-ssis-projects-and-packages.md)   
 [Distribuzione del pacchetto &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md)   
 [Conversione guidata progetto di Integration Services](../../2014/integration-services/integration-services-project-conversion-wizard.md)  
  
  
