---
title: Limitazioni di sicurezza per SQL Server in Linux | Documenti Microsoft
description: Questo articolo descrive SQL Server sulle restrizioni di Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/30/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.workload: Inactive
ms.openlocfilehash: 54e7518c24cb75e5f41f8fc6a4c5a159093ca66a
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2018
---
# <a name="security-limitations-for-sql-server-on-linux"></a>Limitazioni di sicurezza per SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server in Linux attualmente presenta le limitazioni seguenti:

* Viene fornito un criterio password standard. MUST_CHANGE è l'unica opzione che è possibile configurare.  
* Extensible Key Management non è supportata. 
* Utilizzo di chiavi archiviate nell'insieme di credenziali chiave di Azure non è supportato.
* SQL Server genera il proprio certificato autofirmato per crittografia delle connessioni. SQL Server può essere configurato per l'utilizzo di un utente fornito un certificato per TLS. 

Per ulteriori informazioni sulle funzionalità di sicurezza disponibili in SQL Server, vedere il [centro di sicurezza per il motore di Database di SQL Server e Database SQL di Azure](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## <a name="next-steps"></a>Passaggi successivi

Per le attività di sicurezza comuni, vedere [iniziare con la funzionalità di sicurezza di SQL Server in Linux](sql-server-linux-security-get-started.md). Per uno script modificare il protocollo TCP numero di porta, le directory di SQL Server e configurare i flag di traccia o regole di confronto, vedere [configurare SQL Server in Linux con mssql conf](sql-server-linux-configure-mssql-conf.md).
