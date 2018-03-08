---
title: Comandi con i comandi di calcolo con parametri | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data shaping [ADO], parameterized commands
- parameterized commands [ADO]
- APPEND clause [ADO]
- COMPUTE command [ADO]
ms.assetid: 732f624f-8900-4608-9815-194302d22e8b
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 18bfbc4a2e18e0232380edf157410fbd4eb3b12c
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="parameterized-commands-with-intervening-compute-commands"></a>I comandi con parametri con frapposti i comandi di calcolo
Un tipico comando APPEND shape con parametri contiene una clausola che crea un elemento padre **Recordset** con un comando di query e un'altra clausola che crea un elemento figlio **Recordset** con un comando di query con parametri: vale a dire un comando che include un parametro di segnaposto (un punto interrogativo, "?"). Il data shaping risultante **Recordset** ha due livelli, in cui l'elemento padre occupa il livello superiore e il figlio del livello inferiore.  
  
 La clausola che crea l'elemento figlio **Recordset** può ora essere un numero arbitrario di forma nidificata comandi COMPUTE, in cui il comando nidificato contiene la query con parametri. Il data shaping risultante **Recordset** dispone di più livelli, in cui l'elemento padre occupa il livello superiore, l'elemento figlio occupa il livello inferiore e un numero arbitrario di **Recordset**s generato per il comandi COMPUTE Shape occupano i livelli intermedi.  
  
 L'utilizzo tipico per questa funzionalità è possibile richiamare la funzione di aggregazione e le funzionalità di raggruppamento di shapeCOMPUTE i comandi per creare frapposti **Recordset** oggetti con informazioni analitiche relative figlio **Recordset** . Inoltre, poiché si tratta di un comando shape con parametri, ogni volta che una colonna a capitoli dell'elemento padre si accede, un nuovo elemento figlio **Recordset** possono essere recuperati. Poiché i livelli intermedi sono derivati dall'elemento figlio, vengono anche verrà ricalcolate.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di data shaping](../../../ado/guide/data/data-shaping-example.md)
