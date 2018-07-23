---
title: Impostare Progettazione diagrammi di database (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.InstallSqlDiagramSupport
helpviewer_keywords:
- Database Diagram Designer
- database diagrams [SQL Server], Database Diagram Designer
- diagrams [SQL Server], Database Diagram Designer
ms.assetid: 927321ee-b459-4f5b-9719-4a7a95639143
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 54714f5d4c1cd0db5c9117e3812107caf039676e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37997663"
---
# <a name="set-up-database-diagram-designer-visual-database-tools"></a>Impostazione di Progettazione diagrammi di database (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Per usare Progettazione diagrammi di database, è necessario che un membro del ruolo **proprietario_database** ne effettui preventivamente la configurazione per il controllo dell'accesso ai diagrammi.  
  
### <a name="to-set-up-database-diagramming"></a>Per impostare i diagrammi di database  
  
1.  In Esplora oggetti espandere un nodo di database.  
  
2.  Espandere il nodo dei diagrammi di database al di sotto della connessione al database.  
  
3.  Quando viene chiesto se si intende configurare i diagrammi di database, scegliere **Sì** .  
  
    > [!NOTE]  
    > Nel database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] verranno create la tabella del diagramma di database, le stored procedure di sistema e una funzione di sistema.  
  
4.  Tramite Visual Studio verranno creati i seguenti oggetti nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]:  
  
    1.  Tabella sysdiagrams  
  
    2.  Stored procedure sp_alterdiagram  
  
    3.  Stored procedure sp_creatediagram  
  
    4.  Stored procedure sp_dropdiagram  
  
    5.  Stored procedure sp_renamediagram  
  
    6.  Funzione fn_diagramobjects  
  
    7.  Stored procedure sp_helpdiagrams  
  
    8.  Stored procedure sp_helpdiagramsdefinition  
  
    9. Stored procedure sp_upgraddiagrams  
  
## <a name="see-also"></a>Vedere anche  
[Informazioni sulla proprietà dei diagrammi di database &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/understand-database-diagram-ownership-visual-database-tools.md)  
[Aggiornamento di diagrammi di database delle precedenti edizioni &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/upgrade-database-diagrams-from-previous-editions-visual-database-tools.md)  
[ALTER AUTHORIZATION (Transact-SQL)](http://msdn.microsoft.com/en-us/8c805ae2-91ed-4133-96f6-9835c908f373)  
  
