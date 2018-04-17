---
title: È supportata la grammatica SQL ODBC (Driver ODBC di Visual FoxPro) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- native Visual FoxPro language syntax [ODBC]
- FoxPro ODBC driver [ODBC], SQL grammar
- SQL grammar [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], SQL grammar
- grammar support in Visual FoxPro ODBC driver [ODBC]
- Visual FoxPro ODBC driver [ODBC], native Visual FoxPro language syntax
- FoxPro ODBC driver [ODBC], native Visual FoxPro language syntax
ms.assetid: f41a38c2-e22e-4c65-a32e-9a6777435160
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: beabfae6f19f4d425a830489591e321373dfed95
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="supported-odbc-sql-grammar-visual-foxpro-odbc-driver"></a>Grammatica SQL ODBC supportate (Visual FoxPro ODBC Driver)
Il Driver ODBC Microsoft Visual FoxPro supporta le operazioni seguenti:  
  
-   Tutte le istruzioni SQL e le clausole nella grammatica SQL minima ODBC  
  
-   Un'istruzione SQL aggiuntiva dalla grammatica SQL di base ODBC  
  
 Nella tabella seguente sono elencati gli elementi supportati dal driver, dal livello di grammatica SQL ODBC.  
  
|Level|Elementi|Elemento|  
|-----------|--------------|----------|  
|Minimo|Data Definition Language (DDL)|CREATE TABLE e DROP TABLE|  
||Data Manipulation Language (DML)|Selezionare, inserire, aggiornare ed eliminare|  
||Espressioni|Semplice (ad esempio un > B + C)|  
||Tipi di dati|CHAR, VARCHAR o LONG VARCHAR|  
  
 Oltre la grammatica SQL ODBC supportata, il Driver ODBC di Visual FoxPro supporta la sintassi del linguaggio Visual FoxPro nativa completezza per i comandi di Visual FoxPro seguenti:  
  
 [ISTRUZIONE ALTER TABLE](../../odbc/microsoft/alter-table-sql-command.md)  
  
 [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md)  
  
 [DELETE](../../odbc/microsoft/delete-sql-command.md)  
  
 [ELIMINAZIONE DI TAG](../../odbc/microsoft/delete-tag-command.md)  
  
 [DROP TABLE](../../odbc/microsoft/drop-table-command.md)  
  
 [INDEX](../../odbc/microsoft/index-command.md)  
  
 [INSERT](../../odbc/microsoft/insert-sql-command.md)  
  
 [SELECT](../../odbc/microsoft/select-sql-command.md)  
  
 [UPDATE](../../odbc/microsoft/update-sql-command.md)
