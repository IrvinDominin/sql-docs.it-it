---
title: SQLTransact (Driver Access) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLTransact
- SQLTransact function [ODBC], Access Driver
ms.assetid: 892b79c7-9e20-4d1f-bc60-d4b25694ca25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0cb17ed043a6b533b007769b9cbb28652d06e6f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47719613"
---
# <a name="sqltransact-access-driver"></a>SQLTransact (driver Access)
> [!NOTE]  
>  In questo argomento vengono fornite informazioni di accesso specifici del Driver. Per informazioni generali su questa funzione, vedere l'argomento appropriato nel [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Quando viene usato il driver Microsoft Access, SQL_COMMIT e SQL_ROLLBACK sono supportati per il *fType* argomento nella chiamata a **SQLTransact**.  
  
 Se si verifica un errore durante il processo di commit, i database interessato può essere corretti tramite l'opzione di Database di ripristino nell'installazione driver Microsoft Access, oppure tramite la parola chiave REPAIR_DB nel **SQLConfigDataSource** funzione.
