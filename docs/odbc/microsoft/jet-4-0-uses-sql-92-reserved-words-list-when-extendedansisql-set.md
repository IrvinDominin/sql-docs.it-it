---
title: Elenco di parole riservate di Jet 4.0 utilizza SQL-92 quando ExtendedAnsiSQL_Set | Documenti Microsoft
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
- extendedANSISQL [ODBC], reserved words
ms.assetid: 7645187e-7777-4c07-9686-0a80d5c5834d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 07924c05cf566925785cb94bcf0e9ce6192c3a1a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="jet-40-uses-sql-92-reserved-words-list-when-extendedansisqlset"></a>Elenco di parole riservate di Jet 4.0 utilizza SQL-92 quando ExtendedAnsiSQL_Set
Quando viene attivato il flag ExtendedAnsiSQL, Jet 4.0 utilizza l'elenco di parole riservate SQL-92. Tentativo di utilizzare un SQL-92 (parola riservata) con un nome di oggetto non racchiusi tra virgolette determinerà un errore di sintassi. Quando il flag ExtendedAnsiSQL è disattivato, è possono utilizzare le nuove parole riservate come nomi di oggetto come prima.
