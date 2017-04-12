---
title: "Mapping dei tipi di dati per i server di pubblicazione Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pubblicazione Oracle [replica di SQL Server], mapping dei tipi di dati"
  - "tipi di dati [replica di SQL Server], pubblicazione Oracle"
  - "mapping di tipi di dati [replica di SQL Server]"
ms.assetid: 6da0e4f4-f252-4b7e-ba60-d2e912aa278e
caps.latest.revision: 47
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 47
---
# Mapping dei tipi di dati per i server di pubblicazione Oracle
  Tipi di dati Oracle e [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipi di dati non sempre corrispondono esattamente. Se possibile, durante la pubblicazione di una tabella Oracle viene selezionato automaticamente il tipo di dati corrispondente. Nei casi in cui il mapping di un singolo tipo di dati non risulti chiaro, vengono forniti mapping di tipi di dati alternativi. Per informazioni sulla selezione di mapping alternativi, vedere la sezione "Specifica di mapping di tipi di dati alternativi" più avanti in questo argomento.  
  
 Nella tabella seguente viene illustrato il mapping predefinito tra i tipi di dati Oracle e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] quando i dati del server di pubblicazione Oracle vengono spostati nel server di distribuzione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La colonna Alternativi indica se sono disponibili mapping alternativi.  
  
|Tipo di dati Oracle|Tipo di dati di SQL Server|Alternativi|  
|----------------------|--------------------------|------------------|  
|BFILE|VARBINARY(MAX)|Sì|  
|BLOB|VARBINARY(MAX)|Sì|  
|CHAR([1-2000])|CHAR([1-2000])|Sì|  
|CLOB|VARCHAR(MAX)|Sì|  
|DATE|DATETIME|Sì|  
|FLOAT|FLOAT|No|  
|FLOAT([1-53])|FLOAT([1-53])|No|  
|FLOAT([54-126])|FLOAT|No|  
|INT|NUMERIC(38)|Sì|  
|INTERVAL|DATETIME|Sì|  
|LONG|VARCHAR(MAX)|Sì|  
|LONG RAW|IMAGE|Sì|  
|NCHAR([1-1000])|NCHAR([1-1000])|No|  
|NCLOB|NVARCHAR(MAX)|Sì|  
|NUMBER|FLOAT|Sì|  
|NUMBER([1-38])|NUMERIC([1-38])|No|  
|NUMBER([0-38],[1-38])|NUMERIC([0-38],[1-38])|Sì|  
|NVARCHAR2([1-2000])|NVARCHAR([1-2000])|No|  
|RAW([1-2000])|VARBINARY([1-2000])|No|  
|REAL|FLOAT|No|  
|ROWID|CHAR(18)|No|  
|TIMESTAMP|DATETIME|Sì|  
|TIMESTAMP(0-7)|DATETIME|Sì|  
|TIMESTAMP(8-9)|DATETIME|Sì|  
|TIMESTAMP(0-7) WITH TIME ZONE|VARCHAR(37)|Sì|  
|TIMESTAMP(8-9) WITH TIME ZONE|VARCHAR(37)|No|  
|TIMESTAMP(0-7) WITH LOCAL TIME ZONE|VARCHAR(37)|Sì|  
|TIMESTAMP(8-9) WITH LOCAL TIME ZONE|VARCHAR(37)|No|  
|UROWID|CHAR(18)|No|  
|VARCHAR2([1-4000])|VARCHAR([1-4000])|Sì|  
  
## Considerazioni sul mapping dei tipi di dati  
 Durante la replica di dati da un database Oracle, è opportuno considerare i problemi relativi ai tipi di dati riportati di seguito.  
  
### Tipi di dati non supportati  
 I tipi di dati seguenti non sono supportati e pertanto non è possibile replicare le colonne che li contengono:  
  
-   Tipi di oggetti  
  
-   Tipi XML  
  
-   Matrici con dimensione variabile  
  
-   Tabelle nidificate  
  
-   Colonne che utilizzano REF  
  
### Tipo di dati DATE  
 Le date in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sono comprese nell'intervallo dal 1753 D.C. al 9999 D.C., mentre le date in Oracle sono comprese nell'intervallo dal 4712 A.C. al 4712 A.C. Se una colonna di tipo DATE contiene valori non compresi nell'intervallo di SQL Server, selezionare il tipo di dati alternativo per la colonna, ovvero VARCHAR(19).  
  
### Tipi FLOAT e NUMBER  
 La scala e la precisione specificate durante il mapping dei tipi di dati FLOAT e NUMBER dipende dalla scala e dalla precisione specificate per la colonna che utilizza il tipo di dati nel database Oracle. La precisione è il numero di cifre in un numero. La scala è il numero di cifre a destra della virgola decimale in un numero. Il numero 123,45, ad esempio, ha una precisione di 5 e una scala di 2.  
  
 In Oracle è possibile definire i numeri con una scala maggiore della precisione, ad esempio NUMBER(4,5), mentre in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] la precisione deve essere uguale o maggiore della scala. Per garantire che i dati non vengano troncati, se la scala è maggiore della precisione nel server di pubblicazione Oracle, la precisione viene impostata su un valore uguale a quello della scala quando si esegue il mapping del tipo di dati. Il mapping di NUMBER(4,5) sarebbe NUMERIC(5,5).  
  
> [!NOTE]  
>  Se non si specifica una scala e una precisione per NUMBER, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengono automaticamente utilizzate la scala massima (8) e la precisione massima (38). Per migliorare le prestazioni e le operazioni di archiviazione durante la replica dei dati, è consigliabile impostare una scala e una precisione specifiche in Oracle.  
  
### Tipi di oggetti di grandi dimensioni  
 Oracle supporta fino a 4 GB, mentre SQL Server supporta fino a 2 GB. I dati replicati superiori a 2 GB vengono troncati.  
  
 Se una tabella Oracle include una colonna BFILE, i dati della colonna vengono archiviati nel file system. All'account utente di amministrazione della replica deve essere concesso l'accesso alla directory in cui sono archiviati i dati mediante la sintassi seguente:  
  
 `GRANT READ ON DIRECTORY <directory_name> TO <replication_administrative_user_schema>`  
  
 Per ulteriori informazioni sui tipi di oggetti di grandi dimensioni, vedere la sezione "Considerazioni per oggetti di grandi dimensioni" in [Considerazioni sulla progettazione e limitazioni per server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/design-considerations-and-limitations-for-oracle-publishers.md).  
  
## Specifica di mapping di tipi di dati alternativi  
 Generalmente, è consigliabile utilizzare il mapping del tipo di dati predefinito, ma per molti tipi di dati Oracle è possibile selezionarne uno da un set di mapping alternativi, anziché utilizzare quello predefinito. È possibile specificare mapping alternativi in due modi:  
  
-   Mediante l'override del mapping predefinito per ogni singolo articolo, utilizzando le stored procedure o la Creazione guidata nuova pubblicazione.  
  
-   Mediante una modifica globale del mapping predefinito per tutti gli articoli futuri utilizzando stored procedure (i mapping predefiniti non vengono modificati per gli articoli esistenti).  
  
 Per specificare i mapping dei tipi di dati alternativi, vedere [specificare mapping di tipi di dati per un server di pubblicazione Oracle](../../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md).  
  
## Vedere anche  
 [Configurazione di un server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Considerazioni e limitazioni relative alla progettazione dei server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/design-considerations-and-limitations-for-oracle-publishers.md)   
 [Panoramica della pubblicazione Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  