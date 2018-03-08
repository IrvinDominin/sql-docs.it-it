---
title: Implementazione della compressione Unicode | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: compression
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-data-compression
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode data compression
- compression [SQL Server], Unicode data
ms.assetid: 44e69e60-9b35-43fe-b9c7-8cf34eaea62a
caps.latest.revision: "7"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1cc9061265e845b5d7a655e73e28386769e1451b
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="unicode-compression-implementation"></a>Implementazione della compressione Unicode
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usa un'implementazione dell'algoritmo SCSU (Standard Compression Scheme for Unicode) per comprimere i valori Unicode archiviati in oggetti compressi di riga o pagina. Per questi oggetti compressi, la compressione Unicode è automatica per le colonne **nchar(n)** e **nvarchar(n)** . [!INCLUDE[ssDE](../../includes/ssde-md.md)] archivia i dati Unicode come 2 byte, indipendentemente dalle impostazioni locali. Questa funzionalità è nota come codifica UCS-2. Per alcune impostazioni locali, l'implementazione della compressione SCSU in SQL Server consente di risparmiare fino al 50 percento di spazio di archiviazione.  
  
## <a name="supported-data-types"></a>Tipi di dati supportati  
 La compressione Unicode supporta i tipi di dati a lunghezza fissa **nchar(n)** e **nvarchar(n)** . I valori di dati archiviati all'esterno di righe o in colonne **nvarchar(max)** non sono compressi.  
  
> [!NOTE]  
>  La compressione Unicode non è supportata per i dati **nvarchar(max)** anche se archiviati nella riga. Questo tipo di dati, tuttavia, può ancora trarre vantaggio dalla compressione pagina.  
  
## <a name="upgrading-from-earlier-versions-of-sql-server"></a>Aggiornamento da versioni precedenti di SQL Server  
 Quando un database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene aggiornato a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], le modifiche legate alla compressione Unicode non vengono apportate ad alcun oggetto di database, compresso o meno. Una volta aggiornato il database, gli effetti sugli oggetti sono i seguenti:  
  
-   Se l'oggetto non è compresso, non viene apportata alcuna modifica e l'oggetto continua a funzionare come in precedenza.  
  
-   Gli oggetti sui quali è stata applicata la compressione di riga o di pagina continuano a funzionare come in precedenza. I dati non compressi restano in formato non compresso finché non viene aggiornato il loro valore.  
  
-   Le nuove righe inserite in una tabella sulla quale sia stata applicata la compressione di riga o di pagina vengono compresse utilizzando la compressione Unicode.  
  
    > [!NOTE]  
    >  Per sfruttare a pieno i vantaggi della compressione Unicode, l'oggetto deve essere ricompilato con la compressione di pagina o di riga.  
  
## <a name="how-unicode-compression-affects-data-storage"></a>Influenza della compressione Unicode sull'archiviazione dei dati  
 Quando un indice viene creato o ricompilato, oppure quando un valore viene modificato in una tabella compressa con compressione di riga o di pagina, l'indice o il valore interessato viene archiviato compresso solo se la sua dimensione compressa è inferiore alla dimensione corrente. Ciò impedisce che le dimensioni delle righe in una tabella o in un indice aumentino a causa della compressione Unicode.  
  
 Lo spazio di archiviazione risparmiato grazie alla compressione dipende dalle caratteristiche dei dati che si stanno comprimendo e dalle impostazioni locali dei dati. La seguente tabella elenca i risparmi possibili in termini di spazio per diverse impostazioni locali.  
  
|Impostazioni locali|Percentuale di compressione|  
|------------|-------------------------|  
|Inglese|50%|  
|Tedesco|50%|  
|Hindi|50%|  
|Turco|48%|  
|Vietnamita|39%|  
|Giapponese|15%|  
  
## <a name="see-also"></a>Vedere anche  
 [Compressione dei dati](../../relational-databases/data-compression/data-compression.md)   
 [sp_estimate_data_compression_savings &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md)   
 [Implementazione della compressione di pagina](../../relational-databases/data-compression/page-compression-implementation.md)   
 [sys.dm_db_persisted_sku_features &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-persisted-sku-features-transact-sql.md)  
  
  
