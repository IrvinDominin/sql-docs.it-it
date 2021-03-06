---
title: Utilizzo di istruzioni con Stored procedure | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 0041f9e1-09b6-4487-b052-afd636c8e89a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d12b5d0940ea161e3650dc5126a10783c1afc3e6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47812849"
---
# <a name="using-statements-with-stored-procedures"></a>Utilizzo delle istruzioni con le stored procedure

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Una stored procedure è una procedura del database, simile alle procedure di altri linguaggi di programmazione, contenuta all'interno dello stesso database. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le stored procedure possono essere create usando [!INCLUDE[tsql](../../includes/tsql-md.md)] o Common Language Runtime (CLR) e uno dei linguaggi di programmazione di Visual Studio, ad esempio Visual Basic o C#. In genere, le stored procedure di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consentono di eseguire le operazioni seguenti:  
  
- Accettare parametri di input e restituire più valori sotto forma di parametri di output alla procedura o al batch che esegue la chiamata.  
  
- Includere istruzioni di programmazione che eseguono le operazioni nel database, tra cui la chiamata di altre procedure.  
  
- Restituire un valore di stato a una procedura o a un batch che esegue la chiamata per indicare l'esito positivo o negativo (e il motivo dell'esito negativo).  
  
> [!NOTE]  
> Per altre informazioni sulle stored procedure di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere "Informazioni sulle stored procedure" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Per gestire i dati in un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando una stored procedure, tramite [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] vengono fornite le classi [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) e [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). La classe da utilizzare dipende dall'eventuale richiesta della stored procedure dei parametri IN (input) o OUT (output). Se la stored procedure non richiede i parametri IN o OUT, è possibile usare la classe SQLServerStatement. Se la chiamata di stored procedure verrà eseguita più volte o vengono richiesti solo i parametri IN, è possibile usare la classe SQLServerPreparedStatement. Se la stored procedure richiede entrambi IN e i parametri OUT, è consigliabile usare la classe SQLServerCallableStatement. Solo quando la stored procedure richiede i parametri OUT sarà necessario l'overhead dell'utilizzo della classe SQLServerCallableStatement.  
  
> [!NOTE]  
> Inoltre le stored procedure possono restituire conteggi di aggiornamento e più set di risultati. Per altre informazioni, vedere [utilizzando una Stored Procedure con un conteggio di aggiornamento](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md) e [utilizzando più set di risultati](../../connect/jdbc/using-multiple-result-sets.md).  
  
Quando si chiama una stored procedure usando il driver JDBC, è necessario usare la sequenza di escape SQL `call` insieme al metodo [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) della classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). La sintassi completa della sequenza di escape `call` è la seguente:  
  
 `{[?=]call procedure-name[([parameter][,[parameter]]...)]}`  
  
> [!NOTE]  
> Per altre informazioni sul `call` e altri SQL sequenze di escape, vedere [usando le sequenze di Escape SQL](../../connect/jdbc/using-sql-escape-sequences.md).  
  
Negli argomenti di questa sezione vengono descritti i possibili modi per chiamare le stored procedure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando il driver JDBC e la sequenza di escape SQL `call`.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Descrizione|  
|-----------|-----------------|  
|[Uso di una stored procedure senza parametri](../../connect/jdbc/using-a-stored-procedure-with-no-parameters.md)|Viene descritto come utilizzare il driver JDBC per eseguire le stored procedure che non contengono parametri di input o di output.|  
|[Uso di una stored procedure con parametri di input](../../connect/jdbc/using-a-stored-procedure-with-input-parameters.md)|Viene descritto come utilizzare il driver JDBC per eseguire le stored procedure che contengono parametri di input.|  
|[Uso di una stored procedure con parametri di output](../../connect/jdbc/using-a-stored-procedure-with-output-parameters.md)|Viene descritto come utilizzare il driver JDBC per eseguire le stored procedure che contengono parametri di output.|  
|[Uso di una stored procedure con stato restituito](../../connect/jdbc/using-a-stored-procedure-with-a-return-status.md)|Viene descritto come utilizzare il driver JDBC per eseguire le stored procedure che contengono valori di stato restituito.|  
|[Uso di una stored procedure con un conteggio di aggiornamento](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md)|Viene descritto come utilizzare il driver JDBC per eseguire le stored procedure che restituiscono conteggi di aggiornamento.|  
  
## <a name="see-also"></a>Vedere anche

[Uso delle istruzioni con il driver JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
