---
title: Moduli e prologhi (XQuery) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- XQuery, prolog
- prolog
ms.assetid: 0f17b4a4-6234-41d4-a996-6db4e27bff7e
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 09599ba6001a1d73786f7cc98767957fdcabf436
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="modules-and-prologs-xquery"></a>Moduli e prologhi (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [Prologo XQuery](../xquery/modules-and-prologs-xquery-prolog.md) è una serie di dichiarazioni dello spazio dei nomi. Se si dichiara lo spazio dei nomi nel prologo, è possibile specificare l'associazione di un prefisso a uno spazio dei nomi e utilizzare il prefisso nel corpo della query.  
  
## <a name="implementation-limitations"></a>Limitazioni di implementazione  
 Le specifiche di XQuery seguenti non sono supportate in questa implementazione:  
  
-   Dichiarazione del modulo (`version`)  
  
-   Dichiarazione del modulo (`module namespace`)  
  
-   Xmpspacedeclaration (`xmlspace`)  
  
-   Dichiarazione delle regole di confronto predefinite (`declare default collation`)  
  
-   Dichiarazione dell'URI di base (`declare base-uri`)  
  
-   Dichiarazione della costruzione (`declare construction`)  
  
-   Dichiarazione dell'ordinamento predefinito (`declare ordering`)  
  
-   Importazione di schema (`import schema namespace`)  
  
-   Importazione di modulo (`import module`)  
  
-   Dichiarazione di variabile nel prologo (`declare variable`)  
  
-   Dichiarazione di funzione (`declare function`)  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Prologo XQuery](../xquery/modules-and-prologs-xquery-prolog.md)  
 Descrive il prologo di una query XQuery.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento al linguaggio XQuery &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)  
  
  
