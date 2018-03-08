---
title: La grammatica SQL minima | Documenti Microsoft
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
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: 4f36d785-104f-4fec-93be-f201203bc7c7
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 130f434bfb0b41829d2c49782454fcf888af1e27
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sql-minimum-grammar"></a>Grammatica SQL minima
Questa sezione descrive la sintassi SQL minima che deve supportare un driver ODBC. La sintassi descritta in questa sezione è un subset della sintassi del livello di voce di SQL-92.  
  
 Un'applicazione può utilizzare qualsiasi della sintassi in questa sezione e verificare che eventuali driver conforme a ODBC supporta la sintassi. Per determinare se sono supportate le funzionalità aggiuntive di SQL-92 non in questa sezione, l'applicazione deve chiamare **SQLGetInfo** con il tipo di informazioni SQL_SQL_CONFORMANCE. Anche se il driver non è conforme a qualsiasi livello di conformità di SQL-92, un'applicazione può comunque utilizzare la sintassi descritta in questa sezione. Se un driver conforme a un livello di SQL-92, d'altra parte, supporta tutte le sintassi incluse in tale livello. Ciò include la sintassi in questa sezione perché la grammatica minima descritta di seguito è un subset puro di livello più basso conformità SQL-92. Dopo l'applicazione conosce il livello di SQL-92 supportato, è possibile determinare se una funzionalità di livello superiore supportata (se presente) chiamando **SQLGetInfo** con il tipo di informazioni singoli corrispondente a tale funzionalità.  
  
 I driver che funzionano solo con origini dati di sola lettura potrebbero non supportare le parti della grammatica inclusi in questa sezione che gestiscono la modifica dei dati. In un'applicazione può determinare se un'origine dati è di sola lettura chiamando **SQLGetInfo** con il tipo di informazioni SQL_DATA_SOURCE_READ_ONLY.  
  
## <a name="statement"></a>.  
 *istruzione create table* :: =  
  
 CREATE TABLE *nome-tabella di base*  
  
 (*-tipo di dati colonna identificatore* [*, tipo di dati colonna identificatore*]...)  
  
> [!IMPORTANT]  
>  Come un *-tipo di dati* in un *-istruzione create table*, le applicazioni devono utilizzare un tipo di dati dalla colonna TYPE_NAME del set di risultati restituito da **SQLGetTypeInfo**.  
  
 *la ricerca istruzione DELETE* :: =  
  
 DELETE FROM *-nome della tabella* [dove *condizione di ricerca*]  
  
 *istruzione DROP-tabella* :: =  
  
 DROP TABLE *nome-tabella di base*  
  
 *istruzione INSERT* :: =  
  
 INSERT INTO *-nome della tabella* [( *colonna identificatore* [, *colonna identificatore*]...)]      VALORI (*Inserisci valore*[, *Inserisci valore*]...)  
  
 *istruzioni SELECT* :: =  
  
 Selezionare [tutti &#124; DISTINCT] *elenco select*  
  
 DA *elenco di riferimento di tabella*  
  
 [In *condizione di ricerca*]  
  
 [*clausola order by*]  
  
 *istruzione* :: = *-istruzione create table*  
  
 &#124; *ricerca delete-istruzione*  
  
 &#124; *rilascio-tabella-istruzione*  
  
 &#124; *insert-istruzione*  
  
 &#124; *select-istruzione*  
  
 &#124; *ricerca update-istruzione*  
  
 *la ricerca Update-istruzione*  
  
 AGGIORNAMENTO *-nome della tabella*  
  
 IMPOSTARE *colonna identificatore* = {*espressione* &#124; NULL}  
  
 [, *colonna identificatore* = {*espressione* &#124; NULL}]...  
  
 [In *condizione di ricerca*]  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Elementi usati nelle istruzioni SQL](../../../odbc/reference/appendixes/elements-used-in-sql-statements.md)  
  
-   [Supporto dei tipi di dati](../../../odbc/reference/appendixes/data-type-support.md)  
  
-   [Tipi di dati parametro](../../../odbc/reference/appendixes/parameter-data-types.md)  
  
-   [Marcatori di parametro](../../../odbc/reference/appendixes/parameter-markers.md)
