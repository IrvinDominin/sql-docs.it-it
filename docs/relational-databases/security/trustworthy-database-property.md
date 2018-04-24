---
title: Proprietà di database TRUSTWORTHY | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: security
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TRUSTWORTHY database property
ms.assetid: 64b2a53d-4416-4a19-acc0-664a61b45348
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0a2a364b8d01d5a56c1d28464084ca26149de8d8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="trustworthy-database-property"></a>Proprietà di database TRUSTWORTHY
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La proprietà di database TRUSTWORTHY consente di indicare se l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] considera attendibile il database e il relativo contenuto. Per impostazione predefinita, questa impostazione ha valore OFF, ma è possibile impostarla su ON tramite l'istruzione ALTER DATABASE. Ad esempio, `ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;`.  
  
> [!NOTE]  
>  Per impostare questa opzione è necessario essere un membro del ruolo predefinito **sysadmin** del server.  
  
 Questa proprietà può essere utilizzata per limitare i rischi che possono derivare dal collegamento a un database contenente uno degli oggetti seguenti:  
  
-   Assembly dannosi con un'impostazione di autorizzazione EXTERNAL_ACCESS o UNSAFE. Per altre informazioni, vedere [Sicurezza per l'integrazione con CLR](../../relational-databases/clr-integration/security/clr-integration-security.md).  
  
-   Moduli dannosi definiti in modo da essere eseguiti con un account utente con privilegi elevati. Per altre informazioni, vedere [Clausola EXECUTE AS &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-clause-transact-sql.md).  
  
 Entrambe le situazioni richiedono un livello di privilegi specifico e vengono evitate grazie a meccanismi appropriati quando tali componenti vengono utilizzati nel contesto di un database già collegato a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se però il database è offline, un utente che ha accesso al file di database è potenzialmente in grado di collegarlo a un'istanza arbitraria di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e aggiungervi contenuto dannoso. Quando i database vengono scollegati e collegati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sui dati e sui file di log vengono impostate determinate autorizzazioni che limitano l'accesso ai file di database.  
  
 Poiché un database che viene collegato a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non può essere considerato immediatamente attendibile, non può accedere a risorse esterne al proprio ambito fino a quando non verrà esplicitamente contrassegnato come attendibile. Sono inoltre previsti ulteriori requisiti per l'esecuzione dei moduli progettati per accedere a risorse esterne al database e degli assembly con impostazione di autorizzazione EXTERNAL_ACCESS e UNSAFE.  
  
## <a name="related-content"></a>Contenuto correlato  
 [Centro di sicurezza per il motore di database di SQL Server e il database SQL di Azure](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
  
