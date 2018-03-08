---
title: Finestra di dialogo Aggiungi tabella (Progettazione query e Progettazione viste) (Visual Database Tools) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdt.dlgbox.query.addtable
- vdtsql.chm:65565
ms.assetid: fce7adcc-4cf5-4a52-9203-11c13d1ecf08
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: edb2a1f1b761a3ed4a23bd57b783f030956329e0
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="add-table-dialog-box-query-and-view-designers-visual-database-tools"></a>Finestra di dialogo Aggiungi tabella (Progettazione query e Progettazione viste) (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Questa finestra di dialogo consente di aggiungere tabelle, viste, funzioni definite dall'utente o sinonimi a una query o a una vista.  
  
> [!NOTE]  
> Se la tabella viene pubblicata per la replica, è necessario apportare modifiche allo schema usando l'istruzione [ALTER TABLE](http://msdn.microsoft.com/en-us/f1745145-182d-4301-a334-18f799d361d1) di Transact-SQL oppure SMO (SQL Server Management Objects). Quando si apportano modifiche allo schema utilizzando Progettazione tabelle o Progettazione diagrammi di database, viene effettuato il tentativo di rimuovere e rigenerare la tabella. La modifica allo schema non riuscirà, poiché non è consentita la rimozione di oggetti pubblicati.  
  
## <a name="options"></a>Opzioni  
**Tabelle**  
Elenca le tabelle che è possibile aggiungere al riquadro **Diagramma** . Per aggiungere una tabella, selezionarla e fare clic su **Aggiungi**. Per aggiungere contemporaneamente più tabelle, selezionarle e fare clic su **Aggiungi**.  
  
**Viste**  
Elenca le viste che è possibile aggiungere al riquadro **Diagramma** . Per aggiungere una vista, selezionarla e fare clic su **Aggiungi**. Per aggiungere contemporaneamente più viste, selezionarle e fare clic su **Aggiungi**.  
  
**Funzioni**  
Elenca le funzioni definite dall'utente che è possibile aggiungere al riquadro **Diagramma** . Per aggiungere una funzione, selezionarla e fare clic su **Aggiungi**. Per aggiungere contemporaneamente più funzioni, selezionarle e fare clic su **Aggiungi**.  
  
**Sinonimi**  
Elenca i sinonimi che è possibile aggiungere al riquadro **Diagramma** . Per aggiungere un sinonimo, selezionarlo e fare clic su **Aggiungi**. Per aggiungere contemporaneamente più sinonimi, selezionarli e fare clic su **Aggiungi**.  
  
**Aggiorna**  
Aggiorna l'elenco includendo tutte le modifiche apportate al database da quando l'elenco è stato recuperato l'ultima volta.  
  
**Aggiungi**  
Aggiunge l'elemento o gli elementi selezionati.  
  
## <a name="see-also"></a>Vedere anche  
[Procedure per la progettazione di query e viste &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
