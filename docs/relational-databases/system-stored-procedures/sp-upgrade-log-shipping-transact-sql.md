---
title: sp_upgrade_log_shipping (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_upgrade_log_shipping
- sp_upgrade_log_shipping_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_upgrade_log_shipping
ms.assetid: ee01092f-9caf-4e88-888b-ec7b84223705
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1dfadccae2d5bd647c7c7b8081430aedaea9d0dd
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="spupgradelogshipping-transact-sql"></a>sp_upgrade_log_shipping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La stored procedure sp_upgrade_log_shipping viene richiamata automaticamente per aggiornare i metadati specifici del log shipping.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_upgrade_log_shipping  
```  
  
## <a name="arguments"></a>Argomenti  
 Nessuno  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Questa stored procedure viene richiamata automaticamente durante l'aggiornamento di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per eseguire l'aggiornamento dei metadati specifici per il log shipping. Non è necessario eseguire questa procedura in modo esplicito, a meno che non si verifichino problemi a livello dei metadati durante l'aggiornamento.  
  
 La stored procedure sp_upgrade_log_shipping deve essere eseguita dal database master nel server primario, secondario o di monitoraggio.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul Log Shipping &#40; SQL Server &#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
