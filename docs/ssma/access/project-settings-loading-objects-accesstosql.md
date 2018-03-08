---
title: Impostazioni (caricamento di oggetti) del progetto (AccessToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-access
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 9ec1c1e8-a3e1-4e81-bf49-631f87daa209
caps.latest.revision: "4"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: da86fe46153ede299a41a2b4e308f1b5b51f6947
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="project-settings-loading-objects-accesstosql"></a>Impostazioni (caricamento di oggetti) del progetto (AccessToSQL)
Le impostazioni di progetto durante il caricamento di oggetti consentono di configurare come oggetti di database di Access vengono sincronizzati con gli oggetti di database di SQL Server.  
  
Le azioni predefinite specificano le impostazioni predefinite per l'aggiornamento di oggetti dal database di Access e per la sincronizzazione degli oggetti con il database di SQL Server. Per ulteriori informazioni, vedere [Aggiorna da Database &#40; AccessToSQL &#41;](../../ssma/access/refresh-from-database-accesstosql.md)  
  
È possibile accedere a due diverse pagine di sincronizzazione che contengono le stesse impostazioni:  
  
-   Per specificare impostazioni per tutti i progetti futuri di SSMA, il **strumenti** menu, fare clic su **DefaultProject impostazioni**e quindi fare clic su **durante il caricamento di oggetti** nella parte inferiore del riquadro a sinistra.  
  
-   Per specificare le impostazioni per il progetto corrente, il **strumenti** menu, fare clic su **impostazioni progetto**e quindi fare clic su **durante il caricamento di oggetti** nella parte inferiore del riquadro a sinistra.  
  
## <a name="options"></a>Opzioni  
  
##### <a name="misc"></a>Varie  
  
##### <a name="attempts"></a>Tentativi  
Fornisce le informazioni sul numero di passaggi di rendere gli oggetti da caricare in SQL Server. Caricamento degli oggetti in SQL Server viene in genere eseguito in più passaggi. Gli oggetti che non riescono a caricare il primo passaggio, ad esempio le chiavi esterne, potrebbero caricare correttamente il passaggio successivo.  
  
Per impostazione predefinita il valore è 2.  
  
## <a name="synchronization-for-sql-server"></a>Sincronizzazione per SQL Server  
  
##### <a name="default-action-on-local-and-remote-object-change"></a>Azione predefinita in locale e remoto Modifica oggetto  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando la definizione dell'oggetto cambia in SSMA e nel server di database.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **scrivere nel Database**, SSMA aggiornerà gli oggetti del database in base al contenuto dei metadati SSMA quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  
##### <a name="default-action-on-local-object-change"></a>Operazione predefinita sulla modifica di un oggetto locale  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando l'oggetto viene modificato in SSMA.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **scrivere nel Database**, SSMA aggiornerà l'oggetto nel database in base al contenuto dei metadati SSMA quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  
##### <a name="default-action-on-remote-object-change"></a>Operazione predefinita sulla modifica di un oggetto remoto  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando gli oggetti modificati nel server di database.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **scrivere nel Database**, SSMA aggiornerà l'oggetto nel database in base al contenuto dei metadati SSMA quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  
##### <a name="default-action-when-local-object-metadata-is-missing"></a>Azione predefinita quando i metadati dell'oggetto locale sono mancanti  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando mancano i metadati locali.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA consente di selezionare l'aggiornamento dall'opzione di Database quando viene soddisfatta la condizione.  
  
-   Se si seleziona **scrivere nel Database**, SSMA eliminerà l'oggetto dal database quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  
