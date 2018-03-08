---
title: Linee guida e limitazioni per i DiffGram in SQLXML | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2af871b240d318aaa027402a52a9c31498521b99
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>Linee guida e limitazioni per i Diffgram in SQLXML
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Quando si utilizzano Diffgram con SQLXML 4.0, tenere presenti le considerazioni seguenti:  
  
-   Tipi di oggetto binario di grandi dimensioni (BLOB) come **text/ntext** e le immagini non devono essere utilizzati nel  **\<diffgr: prima di >** blocco quando si utilizzano DiffGram, perché in questo caso verrà inclusi per l'utilizzo in controllo della concorrenza. Ciò può provocare problemi con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a causa delle limitazioni applicate al confronto per i tipi BLOB. Ad esempio, viene utilizzata la parola chiave LIKE nella clausola WHERE per il confronto tra le colonne di **testo** del tipo di dati; tuttavia, i confronti avrà esito negativo nel caso di tipi BLOB in cui le dimensioni dei dati sono maggiore di 8 KB.  
  
-   Caratteri speciali nel **ntext** dati possono provocare problemi con SQLXML 4.0 a causa delle limitazioni applicate al confronto per i tipi BLOB. Ad esempio, l'utilizzo di "[Serializable]" nel  **\<diffgr: prima di >** blocco di un DiffGram se utilizzato nel controllo della concorrenza di una colonna di **ntext** tipo avrà esito negativo con il seguente SQLOLEDB Descrizione dell'errore:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
