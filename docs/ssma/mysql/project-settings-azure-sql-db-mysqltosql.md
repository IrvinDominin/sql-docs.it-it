---
title: Impostazioni (database SQL Azure) del progetto (MySQLToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-mysql
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
ms.assetid: 8c06420a-533b-4de0-948d-a0c6b368c544
caps.latest.revision: "10"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a71ecfe91f04e45382ac6ab9f1ec3aa18dd64d04
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="project-settings-azure-sql-db-mysqltosql"></a>Impostazioni (database SQL Azure) del progetto (MySQLToSQL)
Le impostazioni di progetto di SQL Azure consentono di configurare il suffisso del database di SQL Azure per essere aggiunto nella finestra di dialogo di connessione e consentire l'implementazione di meccanismo di heartbeat in connessione a SQL Azure.  
  
Il riquadro SQL Azure è disponibile nel **impostazioni progetto** e **impostazioni di progetto predefinite** finestre di dialogo.  
  
-   Utilizzare la finestra di dialogo Impostazioni di progetto per impostare le opzioni di configurazione per il progetto corrente. Per accedere alle impostazioni di SQL Azure, sul **strumenti** dal menu **impostazioni progetto**, fare clic su **generale** nella parte inferiore del riquadro sinistro, quindi scegliere **SQL Azure**.  
  
-   Utilizzare la finestra di dialogo Impostazioni di progetto predefinite per impostare le opzioni di configurazione per tutti i progetti. Per accedere alle impostazioni di SQL Azure, sul **strumenti** dal menu **DefaultProject impostazioni**, selezionare il tipo di progetto di migrazione come SQL Azure da **versione di destinazione della migrazione** elenco a discesa per accedere alle impostazioni nel riquadro SQL Azure, fare clic su **generale** nella parte inferiore del riquadro sinistro, quindi scegliere **SQL Azure**.  
  
## <a name="options"></a>Opzioni  
  
## <a name="connectivity"></a>Connettività  
**Intervallo heartbeat**  
  
Specifica un intervallo di tempo da utilizzare per il meccanismo di heartbeat per mantenere la connessione a SQL Azure attivo in ' minuti: formato secondi.  
  
**Il valore predefinito**: "4:45 '  
  
Il valore deve essere specificato in corso: formato degli ss (ad esempio, "4:45 ' o ' 0:50 ').  
  
**SQL Server Azure suffisso**  
  
Specifica il suffisso del server SQL Azure  
  
**Il valore predefinito**: 'database.windows.net'.  
  
