---
title: Comando BLOCKSIZE SET | Documenti Microsoft
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
- set blocksize command [ODBC]
ms.assetid: 0c11580f-37f5-4a8e-99be-9fb9c44bb433
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 85b9df4f40c68d68ea28a4bfad006105e4a98d7b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32901816"
---
# <a name="set-blocksize-command"></a>Comando BLOCKSIZE SET
Specifica la modalità di allocazione di spazio su disco per l'archiviazione dei campi di dati memo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET BLOCKSIZE TO nBytes  
```  
  
## <a name="arguments"></a>Argomenti  
 *nBytes*  
 Specifica la dimensione del blocco in cui è allocato spazio su disco per i campi di dati memo. Se *nBytes* è 0, spazio su disco viene allocato in byte singoli (blocchi di 1 byte). Se *nBytes* è un numero intero compreso tra 1 e 32, spazio su disco viene allocato in blocchi di *nBytes* byte moltiplicato per 512. Se *nBytes* è maggiore di 32, viene allocato spazio su disco in blocchi di *nBytes* byte. Se si specifica un valore di dimensione blocco maggiore di 32, è possibile risparmiare spazio su disco considerevole.  
  
## <a name="remarks"></a>Osservazioni  
 Il valore predefinito per impostare BLOCKSIZE è 64. Per reimpostare la dimensione del blocco su un valore diverso dopo aver creato il file, impostarla su un nuovo valore e quindi utilizzare copia per creare una nuova tabella. La nuova tabella include la dimensione del blocco specificato.
