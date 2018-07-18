---
title: Installazione dei componenti ODBC | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC]
- installing ODBC components [ODBC], about installing
- ODBC [ODBC], component installation
ms.assetid: b7e48e9c-8912-4003-b4ef-30aa44de06a7
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2cf4bec202249de89178e5618cdaa5f2770778fc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="installing-odbc-components"></a>Installazione dei componenti ODBC
> [!NOTE]  
>  A partire da Windows XP e Windows Server 2003, ODBC è incluso nel sistema operativo Windows. Solo nelle versioni precedenti di Windows è necessario installare ODBC in modo esplicito.  
  
 In questa sezione viene descritto come componenti ODBC vengono installati e rimossi. Dato che gli sviluppatori di driver installati sempre un componente ODBC (i relativi driver), è necessario leggere questa sezione. Gli sviluppatori di applicazioni è necessario leggere questa sezione solo se si spedirà componenti ODBC con le rispettive applicazioni. Componenti ODBC includono gestione Driver, driver, funzioni di conversione, il programma di installazione DLL, la libreria di cursori e tutti i file correlati. Ai fini di questa sezione, le applicazioni ODBC non sono considerate componenti ODBC.  
  
> [!NOTE]  
>  In questa sezione è specifica per le piattaforme Microsoft Windows. La modalità di installazione dei componenti ODBC su altre piattaforme è specifica della piattaforma.  
  
 Componenti ODBC vengono installati e rimossi in modo da singoli componenti, non un singolo file dal file. Ad esempio, se una funzione di conversione costituito il convertitore di se stesso e un numero di file di dati, questi file vengono installati e rimossi come un gruppo. non devono essere installati e rimossi in una file dal file base. Il motivo consiste nel verificare che siano completi solo componenti presenti nel sistema.  
  
 Ai fini dell'installazione e rimozione di componenti, le operazioni seguenti vengono definiti componenti ODBC:  
  
-   **Componenti di base.** Gestione Driver, libreria di cursori, programma di installazione DLL e qualsiasi altro correlati file costituiscono i componenti di base e devono essere installati e rimosso come gruppo.  
  
-   **Driver.** Ogni driver è un componente separato.  
  
-   **Funzioni di conversione.** Ogni funzione di conversione è un componente separato.  
  
 Con il supporto di Unicode in ODBC 3.5 e versioni successive, è necessario assegnare presi in considerazione l'utilizzo di componenti OLE DB con ODBC. Specifica Unicode specifiche all'interno di ODBC 3.0 è stata scritta la versione 1.1 del Provider OLE DB per ODBC. Poiché queste specifiche modificato in ODBC 3.5, è necessario disporre di versione 1.5 o versioni successive del provider quando si utilizza ODBC 3.5 e versioni successive. In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Componenti di installazione](../../../odbc/reference/install/installation-components.md)  
  
-   [Conteggio utilizzi](../../../odbc/reference/install/usage-counting.md)
