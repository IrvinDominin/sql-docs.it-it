---
title: sp_copysnapshot (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_copysnapshot
- sp_copysnapshot_TSQL
helpviewer_keywords:
- sp_copysnapshot
ms.assetid: a012a32f-6f26-45bf-8046-b51cd7fec455
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: d21d69faf204e2d6c26f7af2d5fac1bc2e9371eb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32988046"
---
# <a name="spcopysnapshot-transact-sql"></a>sp_copysnapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Copia la cartella snapshot della pubblicazione specificata nella cartella indicata nel **@destination_folder**. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione. Risulta utile per la copia di uno snapshot su supporti rimovibili, quali un CD-ROM.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_copysnapshot [ @publication = ] 'publication', [ @destination_folder = ] 'destination_folder' ]  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db = ] 'subscriber_db' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione di cui si desidera copiare la cartella snapshot. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@destination_folder=**] **'***destination_folder***'**  
 Nome della cartella in cui si desidera copiare il contenuto della cartella snapshot della pubblicazione. *destination_folder*viene **nvarchar(255**, non prevede alcun valore predefinito. Il *destination_folder* può essere un percorso alternativo, ad esempio in un altro server, un'unità di rete o su un supporto rimovibile (ad esempio un CD-ROM o un disco rimovibile).  
  
 [  **@subscriber=**] **'***sottoscrittore***'**  
 Nome del Sottoscrittore. *Sottoscrittore* è di tipo sysname, con un valore predefinito è NULL.  
  
 [  **@subscriber_db=**] **'***subscriber_db***'**  
 Nome del database di sottoscrizione. *subscriber_db* è di tipo sysname, con un valore predefinito è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_copysnapshot** viene utilizzata in tutti i tipi di replica. I sottoscrittori che eseguono [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versione 7.0 e versioni precedenti non è possibile utilizzare la posizione dello snapshot alternativo.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_copysnapshot**.  
  
## <a name="see-also"></a>Vedere anche  
 [Posizioni alternative della cartella snapshot](../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
