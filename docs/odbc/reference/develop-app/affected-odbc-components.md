---
title: Componenti ODBC interessati | Documenti Microsoft
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
- upgrading applications [ODBC], affected components
- application upgrades [ODBC], affected components
- compatibility [ODBC], affected components
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], affected components
ms.assetid: 71fa6ea4-007c-4c2b-b5af-2cec6ea79b58
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cb58971a193a210f927d1b0a38f2be671b749468
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="affected-odbc-components"></a>Componenti ODBC interessati
Compatibilità con le versioni precedenti viene descritto come applicazioni, gestione Driver e i driver sono interessati dall'introduzione di una nuova versione di gestione Driver. Questo influisce sulle applicazioni e driver quando uno o entrambi gli elementi rimangono nella versione precedente. Vi sono, pertanto, tre tipi di compatibilità con le versioni precedenti per prendere in considerazione, come illustrato nella tabella seguente.  
  
|Tipo|Versione di data mining|Versione dell'applicazione|Versione del driver|  
|----------|-------------------|----------------------------|-----------------------|  
|Compatibilità di gestione Driver|3*. x*|2.*x*|2.*x*|  
|Compatibilità con le versioni precedenti del Driver [1]|3*. x*|2.*x*|3.*x*|  
|Compatibilità con le versioni precedenti dell'applicazione|3.*x*|3.*x*|2.*x*|  
  
 [1] la compatibilità con le versioni precedenti del driver viene trattata principalmente in appendice g: Driver le linee guida per la compatibilità con le versioni precedenti.  
  
> [!NOTE]  
>  Un'applicazione conforme agli standard, ad esempio, un'applicazione che è stato scritto in conformità con gli standard Open Group o ISO CLI, sarà sicuramente funzionante con un'applicazione ODBC 3*x* driver tramite ODBC 3*x*Gestione driver. Si presuppone che la funzionalità che utilizza l'applicazione è disponibile nel driver. Si presuppone inoltre che sia stata compilata l'applicazione conforme agli standard con ODBC 3*x* file di intestazione.
