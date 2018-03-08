---
title: Progetto Settings(Synchronization) (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e223fb7d-05ec-4fa5-8973-d845c33a23dd
caps.latest.revision: "5"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 030b6346a174d83234216e9c779b01026abe7b07
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="project-settingssynchronization-oracletosql"></a>Progetto Settings(Synchronization) (OracleToSQL)
La pagina di sincronizzazione del **impostazioni progetto** la finestra di dialogo contiene le impostazioni che consentono di personalizzare come SSMA carica e gli aggiornamenti del database in oggetti, ad esempio tabelle e stored procedure, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Le opzioni di azioni predefinite specificano le impostazioni predefinite per l'aggiornamento di oggetti dal database Oracle e per la sincronizzazione degli oggetti con il database di SQL Server. Per ulteriori informazioni, vedere [aggiornamento dal Database - Oracle](../../ssma/oracle/refresh-from-database-oracletosql.md).  
  
È possibile accedere a due diverse pagine di sincronizzazione che contengono le stesse impostazioni:  
  
-   Per specificare impostazioni per tutti i progetti futuri di SSMA, il **strumenti** menu, fare clic su **impostazioni di progetto predefinite**e quindi fare clic su **sincronizzazione** nella parte inferiore del riquadro a sinistra.  
  
-   Per specificare le impostazioni per il progetto corrente, il **strumenti** menu, fare clic su **impostazioni progetto**e quindi fare clic su **sincronizzazione** nella parte inferiore del riquadro a sinistra.  
  
## <a name="miscellaneous-options"></a>Opzioni varie  
**Tentativi**  
Specifica il numero di tentativi di SSMA è necessario apportare durante il caricamento di oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Gli oggetti che non vengono caricati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] nel tentativo corrente verrà ritentata finché SSMA raggiunge il numero massimo di tentativi durante il processo di sincronizzazione corrente. È impostato un valore predefinito **2**  
  
## <a name="synchronization-for-oracle-options"></a>Sincronizzazione per le opzioni di Oracle  
**Azione di modifica di oggetti locali e remoti**  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando la definizione dell'oggetto cambia in SSMA e nel server di database. È impostato un valore predefinito **aggiornamento dal database**.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  
**Azione di modifica di un oggetto locale**  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando l'oggetto viene modificato in SSMA. È impostato un valore predefinito **Skip**.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  
**Azione di modifica di un oggetto remoto**  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando gli oggetti modificati nel server di database. È impostato un valore predefinito **aggiornamento dal database**.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  
**Azione quando i metadati dell'oggetto locale sono mancanti**  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando mancano i metadati locali. È impostato un valore predefinito **aggiornamento dal database**.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  
## <a name="synchronization-for-sql-server-options"></a>Sincronizzazione per opzioni di SQL Server  
**Azione di modifica di oggetti locali e remoti**  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando la definizione dell'oggetto cambia in SSMA e nel server di database. È impostato un valore predefinito **scrittura al database**.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **scrivere nel Database**, SSMA aggiornerà gli oggetti del database in base al contenuto dei metadati SSMA quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  
**Azione di modifica di un oggetto locale**  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando l'oggetto viene modificato in SSMA. È impostato un valore predefinito **scrittura al database**.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **scrivere nel Database**, SSMA aggiornerà l'oggetto nel database in base al contenuto dei metadati SSMA quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  
**Azione di modifica di un oggetto remoto**  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando gli oggetti modificati nel server di database.  È impostato un valore predefinito **aggiornamento dal database**.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **scrivere nel Database**, SSMA aggiornerà l'oggetto nel database in base al contenuto dei metadati SSMA quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  
**Azione quando i metadati dell'oggetto locale sono mancanti**  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando mancano i metadati locali. È impostato un valore predefinito **aggiornamento dal database**.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA consente di selezionare il **aggiornamento dal Database** opzione quando la condizione è soddisfatta.  
  
-   Se si seleziona **scrivere nel Database**, SSMA eliminerà l'oggetto dal database quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  
