---
title: SQLColAttributes (Driver ODBC di Visual FoxPro) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLColAttribute function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: d403dfa0-c26d-47d4-91d9-2f29aa387399
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8cef195281e4793af925174eb0e13ed6a5ff8667
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlcolattributes-visual-foxpro-odbc-driver"></a>SQLColAttributes (Driver ODBC di Visual FoxPro)
> [!NOTE]  
>  In questo argomento contiene informazioni specifiche del Driver ODBC Visual FoxPro. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Supporto: completo  
  
 Conformità di API ODBC: Il livello di base  
  
 Restituisce informazioni sul descrittore per una colonna in un set di risultati. Informazioni del descrittore viene restituite come una stringa di caratteri, un dipendente dal descrittore di valore a 32 bit o un valore intero.  
  
> [!NOTE]  
>  **SQLColAttributes** non può essere utilizzata per restituire informazioni sulla colonna segnalibro (colonna 0).  
  
 Il Driver ODBC di Visual FoxPro supporta tutti *fDescType* valori. Nella tabella seguente include i commenti sull'implementazione del driver dei valori selezionati.  
  
|*fDescType*|Commento|  
|-----------------|-------------|  
|SQL_COLUMN_AUTO_INCREMENT|Restituisce FALSE: Visual FoxPro non dispone di alcun campo contatore.|  
|SQL_COLUMN_CASE_SENSITIVE|Restituisce sempre TRUE se il tipo di colonna è di carattere.|  
|SQL_COLUMN_LABEL|Restituisce il nome della colonna, viene restituito anche dalla SQL_COLUMN_NAME.|  
|SQL_COLUMN_MONEY|Restituisce TRUE se il tipo di colonna è valuta (rappresentato da una "Y" del linguaggio Visual FoxPro).|  
|SQL_COLUMN_OWNER_NAME|Restituisce sempre una stringa vuota.|  
|SQL_COLUMN_QUALIFIER_NAME|Restituisce sempre una stringa vuota.|  
|SQL_COLUMN_SEARCHABLE|Restituisce SQL_UNSEARCHABLE per le colonne di tipo generale; Queste colonne non possono essere utilizzate in una clausola WHERE.<br /><br /> Restituisce SQL_SEARCHABLE per le colonne di tipo carattere o Memo con NOCPTRANS non è impostata; Queste colonne possono essere utilizzate in una clausola WHERE con qualsiasi operatore di confronto.<br /><br /> Restituisce SQL_ALL_EXCEPT_LIKE per tutti gli altri tipi di colonna; Queste colonne possono essere utilizzate in una clausola WHERE con tutti gli operatori di confronto, ad eccezione di tipo.|  
|SQL_COLUMN_TABLE_NAME|Restituisce sempre una stringa vuota.|  
  
 Per ulteriori informazioni, vedere [SQLColAttributes](../../odbc/reference/syntax/sqlcolattributes-function.md) nel *riferimento per programmatori ODBC*.
