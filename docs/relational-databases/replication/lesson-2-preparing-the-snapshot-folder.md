---
title: "Lezione 2: Preparazione della cartella snapshot | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "replica [SQL Server], esercitazioni"
ms.assetid: f286cde9-c0d0-43ef-b7ba-53c3cbb8906c
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Lezione 2: Preparazione della cartella snapshot
In questa lezione verrà configurata la cartella snapshot utilizzata per la creazione e l'archiviazione dello snapshot di pubblicazione.  
  
### Per creare una condivisione per la cartella snapshot e assegnare le autorizzazioni  
  
1.  In Esplora risorse passare alla cartella di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il percorso predefinito è C:\Programmi\Microsoft SQL Server\MSSQL.X\MSSQL\Data.  
  
2.  Creare una nuova cartella denominata **repldata**.  
  
3.  Fare clic con il pulsante destro del mouse sulla cartella e scegliere **Proprietà**.  
  
4.  Nella scheda **Condivisione** della finestra di dialogo **Proprietà di repldata** fare clic su **Condividi**.  
  
5.  Nella finestra di dialogo **Condivisione file** fare clic su **Condividi** e quindi su **Chiudi**.  
  
6.  Nella scheda **Sicurezza** fare clic su **Modifica**.  
  
7.  Nella finestra di dialogo **Autorizzazioni** fare clic su **Aggiungi**. Nella casella di testo **Seleziona utenti, computer, account del servizio o gruppi** digitare il nome dell'account dell'agente snapshot creato nella lezione 1 nel formato \<*Nome_Macchina>***\repl_snapshot**, dove \<*Nome_Macchina>* è il nome del server di pubblicazione. Fare clic su **Controlla nomi** e quindi su **OK**.  
  
8.  Ripetere il passaggio precedente per aggiungere le autorizzazioni per l'agente di distribuzione nel formato \<*Nome_Macchina>***\repl_distribution** e per l'agente di merge nel formato \<*Nome_Macchina>***\repl_merge**.  
  
9. Verificare che siano state concesse le autorizzazioni seguenti:  
  
    -   repl_snapshot - Controllo completo  
  
    -   repl_distribution - Lettura  
  
    -   repl_merge - Lettura  
  
10. Fare clic su **OK** per chiudere la finestra di dialogo **Proprietà di repldata** e creare la condivisione repldata.  
  
## Passaggi successivi  
In questo modo è stata configurata la condivisione per la cartella snapshot. Il passaggio successivo consiste nella configurazione della distribuzione. Vedere [Lezione 3: Configurazione della distribuzione](../../relational-databases/replication/lesson-3-configuring-distribution.md).  
  
## Vedere anche  
[Sicurezza della cartella snapshot](../../relational-databases/replication/security/secure-the-snapshot-folder.md)  
  
  
  