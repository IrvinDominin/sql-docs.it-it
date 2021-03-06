---
title: Assistente compilazione nativa | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
f1_keywords:
- sql12.swb.nativecompilationwizard.f1
- swb.nativecompilationwizard.f1
ms.assetid: d3898a47-2985-4a08-bc70-fd8331a01b7b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 36a6a30ffbf5a0991e2b55ba655549454516e82d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48147101"
---
# <a name="native-compilation-advisor"></a>Assistente compilazione nativa
  Lo strumento dei report sulle prestazioni delle transazioni (vedere [Determinare se una tabella o una stored procedure deve essere trasferita a OLTP in memoria](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)) indica quali stored procedure interpretate nel database trarranno vantaggio se trasferite per utilizzare la compilazione nativa. Una volta identificata la stored procedure da trasferire per l'utilizzo nella compilazione nativa, è possibile utilizzare l'Assistente compilazione nativa per facilitare la migrazione della stored procedure interpretata alla compilazione nativa. Per altre informazioni sulle stored procedure compilate in modo nativo, vedere [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md).  
  
 Connettersi innanzitutto all'istanza contenente la stored procedure interpretata. È possibile connettersi all'istanza di [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] . Tuttavia, se si desidera effettuare la migrazione con il supporto dell'Assistente compilazione nativa, è necessario connettersi a un'istanza di [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] in cui la funzionalità OLTP in memoria sia abilitata. Per ulteriori informazioni sui requisiti di OLTP in memoria, vedere [Requirements for Using Memory-Optimized Tables](memory-optimized-tables.md).  
  
 Per informazioni sulle metodologie di migrazione, vedere la pagina relativa a [OLTP in memoria: considerazioni sulla migrazione e sui modelli di carico di lavoro comuni](http://msdn.microsoft.com/library/dn673538.aspx).  
  
## <a name="walkthrough-using-the-native-compilation-advisor"></a>Procedura dettagliata per l'utilizzo dell'Assistente compilazione nativa  
 In **Esplora oggetti**fare clic con il pulsante destro del mouse sulla stored procedure che si desidera convertire, quindi selezionare **Assistente compilazione nativa**. Verrà visualizzata la pagina introduttiva di **Assistente compilazione nativa stored procedure**. Fare clic su **Avanti** per continuare.  
  
### <a name="stored-procedure-validation"></a>Convalida stored procedure  
 In questa pagina verrà indicato se la stored procedure utilizza dei costrutti che non sono compatibili con la compilazione nativa. Fare clic su **Avanti** per vedere i dettagli. Se sono presenti costrutti che non sono compatibili con la compilazione nativa, fare clic su **Avanti** per vedere i dettagli.  
  
### <a name="stored-procedure-validation-result"></a>Risultati di convalida stored procedure  
 I dettagli su eventuali costrutti non compatibili con la compilazione nativa saranno visualizzati nella pagina **Risultati di convalida stored procedure** . È possibile generare un report (facendo clic su **Genera report**), uscire da **Assistente compilazione nativa**e aggiornare il codice in modo che risulti compatibile con la compilazione nativa.  
  
## <a name="code-sample"></a>Codice di esempio  
 Nell'esempio seguente viene mostrata una stored procedure interpretata e la stored procedure equivalente per la compilazione nativa. Nell'esempio viene supposto l'utilizzo di una directory denominata c:\data.  
  
```tsql  
CREATE DATABASE Demo  
ON  
PRIMARY(NAME = [Demo_data],  
FILENAME = 'C:\DATA\Demo_data.mdf', size=500MB)  
, FILEGROUP [Demo_fg] CONTAINS MEMORY_OPTIMIZED_DATA(  
NAME = [Demo_dir],  
FILENAME = 'C:\DATA\Demo_dir')  
LOG ON (name = [Demo_log], Filename='C:\DATA\Demo_log.ldf', size=500MB)  
COLLATE Latin1_General_100_BIN2;  
GO  
USE Demo;  
GO  
  
CREATE TABLE [dbo].[SalesOrders]  
(  
     [order_id] [int] NOT NULL,  
     [order_date] [datetime] NOT NULL,  
     [order_status] [tinyint] NOT NULL  
  
CONSTRAINT [PK_SalesOrders] PRIMARY KEY NONCLUSTERED HASH   
(  
     [order_id]  
)WITH ( BUCKET_COUNT = 2097152)  
)WITH ( MEMORY_OPTIMIZED = ON )  
  
go  
  
CREATE PROCEDURE [dbo].[InsertOrder] @id INT, @date DATETIME2, @status TINYINT  
AS   
BEGIN   
  
  INSERT dbo.SalesOrders VALUES (@id, @date, @status)  
  
END  
  
go  
  
CREATE PROCEDURE [dbo].[InsertOrderXTP] @id INT, @date DATETIME2, @status TINYINT  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS   
BEGIN ATOMIC WITH   
(    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
     LANGUAGE = N'us_english')  
  
  INSERT dbo.SalesOrders VALUES (@id, @date, @status)  
  
END  
go  
  
select * from SalesOrders  
go  
exec dbo.InsertOrder @id= 10, @date = '1956-01-01 12:00:00', @status = 1 ;  
exec dbo.InsertOrderXTP @id= 11, @date = '1956-01-01 12:01:00', @status = 2 ;  
select * from SalesOrders  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Migrazione a OLTP in memoria](migrating-to-in-memory-oltp.md)  
  
  
