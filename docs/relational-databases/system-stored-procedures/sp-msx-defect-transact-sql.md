---
title: sp_msx_defect (Transact-SQL) | Microsoft Docs
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
- sp_msx_defect
- sp_msx_defect_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_msx_defect
ms.assetid: 0dfd963a-3bc5-4b58-94f7-aec976da2883
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cf63da8bfb0ac882e3d3949a91b848ba689985a6
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="spmsxdefect-transact-sql"></a>sp_msx_defect (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Esclude il server corrente dalle operazioni multiserver.  
  
> [!CAUTION]  
>  **sp_msx_defect** modifica il Registro di sistema. La modifica manuale del Registro di sistema non è un'operazione consigliata, in quanto modifiche inadeguate o non corrette possono causare gravi problemi di configurazione nel sistema. La modifica del Registro di sistema tramite l'editor corrispondente deve essere pertanto eseguita esclusivamente da utenti esperti. Per ulteriori informazioni, vedere la documentazione di Microsoft Windows.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_msx_defect [@forced_defection =] forced_defection  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@forced_defection =**] *forced_defection*  
 Specifica se utilizzare o meno l'esclusione forzata Master SQLServerAgent viene definitivamente perduto a seguito di un danno irreversibile **msdb** database oppure su no **msdb** backup del database. *forced_defection*è **bit**, il valore predefinito è **0**, che indica che l'esclusione forzata non viene devono essere eseguiti. Il valore **1** Forza esclusione.  
  
 Dopo l'esclusione forzata eseguendo **sp_msx_defect**, un membro del **sysadmin** ruolo predefinito del server SQLServerAgent Master deve eseguire il comando seguente per completare l'operazione:  
  
```  
EXECUTE msdb.dbo.sp_delete_targetserver @server_name = 'tsx-server', @post_defection =  0;  
```  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Quando **sp_msx_defect** completato correttamente, viene restituito un messaggio.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per eseguire questa stored procedure, è necessario che gli utenti siano membri del ruolo predefinito del server **sysadmin** .  
  
## <a name="see-also"></a>Vedere anche  
 [sp_msx_enlist &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
