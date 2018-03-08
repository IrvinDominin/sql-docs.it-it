---
title: L'installazione di SSMA per Client di MySQL (MySQLToSQL) | Documenti Microsoft
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
helpviewer_keywords: Installing client,Licensing
ms.assetid: ede3128c-370d-45a5-a815-3d94eecaea30
caps.latest.revision: "22"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 20e2b46e1b020865359431a4999e097c20e14da1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="installing-ssma-for-mysql-client-mysqltosql"></a>L'installazione di SSMA per Client di MySQL (MySQLToSQL)
SSMA per client di MySQL è costituito da file di programma eseguono le attività seguenti:  
  
-   Connettersi a un database MySQL.  
  
-   Connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.  
  
-   Convertire gli oggetti di database MySQL per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o gli oggetti di SQL Azure.  
  
-   Caricare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.  
  
-   La migrazione dei dati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.  
  
In questo argomento fornisce i prerequisiti di installazione e le istruzioni per l'installazione di SSMA per client di MySQL.  
  
## <a name="prerequisites"></a>Prerequisites  
SSMA per MySQL è progettato per funzionare con MySQL 4.1 o versioni successive e tutte le edizioni di SQL Server 2005, SQL Server 2008, SQL Server 2012, SQL Server 2014, SQL Server 2016 e database SQL di Azure.  
  
Prima di installare SSMA, assicurarsi che il computer soddisfi i requisiti seguenti:  
  
-   Windows 7 o versioni successive o Windows Server 2008 o versioni successive.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3.1 o versione successiva.  
  
-   Il [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] versione 4.0 o versione successiva. Il [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] è disponibile nel supporto del prodotto SQL Server versione 4.0. È anche possibile ottenere dal [Centro per sviluppatori di .NET Framework](http://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   MySQL 5.1 provider ODBC e la connettività ai database di MySQL che si desidera eseguire la migrazione. È possibile installare MySQL dal sito Web di MySQL. Per informazioni sulla connettività, vedere [connessione a MySQL &#40; MySQLToSQL &#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
-   Per l'accesso e autorizzazioni sufficienti nel computer che ospita l'istanza di destinazione di SQL Server in cui si desidera migrare gli oggetti di database e i dati. Per ulteriori informazioni, vedere [connessione a SQL Server &#40; MySQLToSQL &#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
-   In caso di progetti di SQL Azure, accesso e autorizzazioni sufficienti per l'istanza di database SQL di Azure in cui si desidera migrare gli oggetti dati e di database. Per ulteriori informazioni, vedere [la connessione al database SQL di Azure &#40; MySQLToSQL &#41; ](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md).  
  
-   4 GB di RAM consigliato.  
  
## <a name="installing-ssma-for-mysql-client"></a>L'installazione di SSMA per Client di MySQL  
SSMA è un download Web. Per scaricare la versione più recente, vedere il [pagina di download di SQL Server Migration Assistant](http://aka.ms/ssmaformysql).  
  
Dopo aver scaricato la versione più recente, è necessario estrarre i file di installazione prima di poter installare SSMA.  
  
**Per installare il client SSMA**  
  
1.  Fare doppio clic su SSMA per MySQL  *n* . Install.exe, in cui  *n*  è il numero di build.  
  
2.  Nella pagina di benvenuto fare clic su **Avanti**.  
  
    Se non si dispone di installati i prerequisiti, verrà visualizzato un messaggio che indica che è necessario innanzitutto installare i componenti necessari. Assicurarsi di aver installato tutti i prerequisiti prima di eseguire nuovamente il programma di installazione.  
  
3.  Leggere il contratto di licenza. Se si accetta, selezionare **accetto i termini del contratto di licenza**, quindi fare clic su **Avanti**.  
  
4.  Nella pagina Selezione tipo di installazione, fare clic su **tipica**.  
  
5.  Fare clic su **Installa**.  
  
> [!IMPORTANT]  
> 1.  Prima di installare la nuova versione disinstallare tutte le versioni precedenti di SSMA per MySQL.  
  
Il percorso di installazione predefinito è C:\Program Files\Microsoft SQL Server Migration Assistant per MySQL.  
  
In computer Windows a 64 bit il prodotto sia installato in C:\Microsoft SQL Server Migration Assistant per MySQL.  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database MySQL a SQL Server: database SQL di Azure &#40; MySQLToSql &#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
