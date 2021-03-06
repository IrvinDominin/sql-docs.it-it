---
title: sp_addserver (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addserver
- sp_addserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addserver
- renaming servers
- machine names [SQL Server]
- computer names
ms.assetid: 160a6b29-5e80-44ab-80ec-77d4280f627c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d18fa2ca30559ee31ed5caeaddf361f0895986d9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47685524"
---
# <a name="spaddserver-transact-sql"></a>sp_addserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Definisce il nome dell'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Quando il computer che ospita [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene rinominato, usare **sp_addserver** per indicare all'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] del nome del nuovo computer. Questa routine deve essere eseguita in tutte le istanze del [!INCLUDE[ssDE](../../includes/ssde-md.md)] ospitate nel computer. Il nome dell'istanza di [!INCLUDE[ssDE](../../includes/ssde-md.md)] non può essere modificato. Per modificare il nome di un'istanza denominata, installare una nuova istanza con il nome desiderato, scollegare i file di database dall'istanza precedente, collegare i database alla nuova istanza ed eliminare l'istanza precedente. In alternativa, è possibile creare un nome alias del client nel computer client, reindirizzando la connessione a una combinazione diversa di server e nome di istanza o **server:port** senza modificare il nome dell'istanza nel computer server.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addserver [ @server = ] 'server' ,  
     [ @local = ] 'local'   
     [ , [ @duplicate_ok = ] 'duplicate_OK' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@server =** ] **'***server***'**  
 Nome del server. I nomi di server devono essere univoci e conformi alle regole per i nomi di computer di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Gli spazi non sono consentiti. *server* è di tipo **sysname**e non prevede alcun valore predefinito.  
  
 Quando più istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono installati in un computer a un'istanza agisce come se fosse in un server separato. Specificare un'istanza denominata tramite un riferimento a *server* come *nomeserver\nomeistanza*.  
  
 [  **@local =** ] **'LOCAL'**  
 Specifica che il server viene aggiunto come server locale. **@local** viene **varchar (10)**, con un valore predefinito è NULL. Che specifica **@local** come **locale** definisce **@server** come nome del server locale e le cause di @@SERVERNAME funzione per restituire il valore dei *server*.  
  
 Durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] questa variabile viene impostata sul nome del computer. Per impostazione predefinita, il nome del computer è consente agli utenti di connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] senza richiedere un'ulteriore configurazione.  
  
 La definizione locale diventa effettiva solo dopo il riavvio del [!INCLUDE[ssDE](../../includes/ssde-md.md)]. È possibile definire un solo server locale in ogni istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 [  **@duplicate_ok =** ] **'duplicate_OK'**  
 Specifica se è consentito utilizzare un nome di server duplicato. **@duplicate_OK** viene **varchar(13)**, con un valore predefinito è NULL. **@duplicate_OK** può avere solo il valore **duplicate_OK** o NULL. Se **duplicate_OK** specificato e il nome del server da aggiungere già esiste, viene generato alcun errore. Se non si utilizzano parametri denominati, **@local** deve essere specificato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Note  
 Per impostare o deselezionare le opzioni server, usare **sp_serveroption**.  
  
 **sp_addserver** non può essere utilizzata in una transazione definita dall'utente.  
  
 Usando **sp_addserver** per aggiungere un server remoto non è più disponibile. Usare [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) in alternativa.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo predefinito del server **setupadmin** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente il [!INCLUDE[ssDE](../../includes/ssde-md.md)] voce per il nome del computer che ospita [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a `ACCOUNTS`.  
  
```  
sp_addserver 'ACCOUNTS', 'local';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Rinominare un Computer che ospita un'istanza autonoma di SQL Server](../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_dropserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Stored procedure di sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  
