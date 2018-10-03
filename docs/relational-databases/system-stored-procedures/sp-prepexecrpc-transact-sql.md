---
title: sp_prepexecrpc (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepexecrpc
- sp_cursor_prepexecrpc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_prepexecrpc
ms.assetid: 35d686f2-ef31-4eaa-baa9-9cef5d6c87c2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: aced26fc44c40e28fafc9bb8bcc7d9a44a01959f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837898"
---
# <a name="spprepexecrpc-transact-sql"></a>sp_prepexecrpc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Prepara ed esegue una chiamata della stored procedure con parametri specificata utilizzando un identificatore RPC. sp_prepexecrpc viene richiamata specificando ID = 14 in un pacchetto del flusso TDS.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_prepexecrpc handle OUTPUT, RPCCall  
    [ , bound_param ] [ ,...n]]  
```  
  
## <a name="arguments"></a>Argomenti  
 *handle*  
 Identificatore dell'handle preparato generato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *gestire* è un parametro obbligatorio con un **int** valore restituito.  
  
 *RPCCall*  
 Definisce la chiamata della stored procedure mediante la sintassi canonica ODBC. *RPCCall* è un parametro obbligatorio che richiede un **ntext** valore di stringa di input.  
  
 *bound_param*  
 Indica l'utilizzo facoltativo di parametri aggiuntivi. *bound_param* richiede un valore di input di qualsiasi tipo di dati per definire i parametri aggiuntivi in uso.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
