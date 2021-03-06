---
title: Conformità di interfaccia di livello 1 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- level 1 interface conformance levels [ODBC]
ms.assetid: ee3f5c08-0583-4f3b-8354-ef71b6086a7e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f2071ec7d7c9a31a9da8982b583ef7618700db5e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47649319"
---
# <a name="level-1-interface-conformance"></a>Conformità di interfaccia di livello 1
Il livello di conformità di interfaccia di livello 1 include le funzionalità a livello di base dell'interfaccia della conformità oltre a funzionalità aggiuntive, ad esempio le transazioni, in genere disponibili in un DBMS relazionale OLTP. Un driver conforme allo standard dell'interfaccia di livello 1 consente all'applicazione di eseguire le operazioni seguenti, oltre alle funzionalità del livello di conformità di interfaccia Core:  
  
|||  
|-|-|  
|101|Specificare lo schema del database, tabelle e viste (con due parti di denominazione). (Per altre informazioni, vedere la denominazione in tre parti funzionalità 201 nel [conformità di interfaccia di livello 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)|  
|102|Richiamare true esecuzione asincrona delle funzioni ODBC, dove applicabile funzioni ODBC sono tutte sincrone o tutte asincrone in una determinata connessione.|  
|103|Utilizzare i cursori scorrevoli e ottenere in tal modo l'accesso a un set di risultati nei metodi diverso da quello forward-only, chiamando **SQLFetchScroll** con il *FetchOrientation* argomento diverso da SQL_FETCH_NEXT. (Il SQL_FETCH_BOOKMARK *FetchOrientation* è in funzione 204 [conformità di interfaccia di livello 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)|  
|104|Ottenere le chiavi primarie delle tabelle, chiamando **SQLPrimaryKeys**.|  
|105|Utilizzare le stored procedure, tramite la sequenza di escape ODBC per le chiamate di procedure ed eseguire query del dizionario dei dati riguardanti le stored procedure, chiamando **SQLProcedureColumns** e **SQLProcedures**. (Il processo mediante il quale le procedure vengono create e archiviate nell'origine dati è all'esterno dell'ambito di questo documento).|  
|106|Connettersi a un'origine dati passando in modo interattivo i server disponibili, chiamando **SQLBrowseConnect**.|  
|107|Usare le funzioni ODBC invece delle istruzioni SQL per eseguire determinate operazioni di database: **SQLSetPos** con SQL_POSITION e SQL_REFRESH.|  
|108|Ottenere l'accesso al contenuto di più set di risultati generato da batch e stored procedure, chiamando **SQLMoreResults**.|  
|109|Consente di delimitare le transazioni che si estende su più funzioni ODBC, con true atomicità e la possibilità di specificare SQL_ROLLBACK nel **SQLEndTran**.|
