---
title: Attività Esegui istruzione T-SQL | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.executetsqlstatementtask.f1
helpviewer_keywords:
- Transact-SQL statements, SSIS
- statements [Integration Services]
- Execute T-SQL Statement task [Integration Services]
ms.assetid: 7e9086ca-d27e-46c0-bfad-d61333ebd55e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fb90ba901620d1280b49fda959a958ae9c93a81f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47827125"
---
# <a name="execute-t-sql-statement-task"></a>Attività Esegui istruzione T-SQL
  L'attività Esegui istruzione T-SQL consente di eseguire istruzioni Transact-SQL. Per altre informazioni, vedere [Guida di riferimento a Transact-SQL &#40;Motore di database&#41;](../../t-sql/transact-sql-reference-database-engine.md) e [Query di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-queries.md).  
  
 Questa attività è simile all'attività Esegui SQL, ma supporta solo la versione Transact-SQL del linguaggio SQL e non può essere utilizzata per eseguire istruzioni su server che utilizzano altri sottolinguaggi del linguaggio SQL. Se è necessario eseguire query con parametri, salvare i risultati delle query nelle variabili oppure utilizzare espressioni di proprietà, è necessario utilizzare l'attività Esegui SQL anziché l'attività Esegui istruzione T-SQL. Per altre informazioni, vedere [Attività Esegui SQL](../../integration-services/control-flow/execute-sql-task.md).  
  
## <a name="configuration-of-the-execute-t-sql-task"></a>Configurazione dell'attività Esegui istruzione T-SQL  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Questa attività è disponibile nella sezione **Attività di manutenzione** della **casella degli strumenti** di Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Attività Esegui istruzione T-SQL &#40;Piano di manutenzione&#41;](../../relational-databases/maintenance-plans/execute-t-sql-statement-task-maintenance-plan.md)  
  
 Per altre informazioni sull'impostazione di queste proprietà in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Impostazione delle proprietà di un'attività o di un contenitore](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
## <a name="see-also"></a>Vedere anche  
 [Attività di Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Flusso di controllo](../../integration-services/control-flow/control-flow.md)   
 [MERGE nei pacchetti di Integration Services](../../integration-services/control-flow/merge-in-integration-services-packages.md)  
  
  
