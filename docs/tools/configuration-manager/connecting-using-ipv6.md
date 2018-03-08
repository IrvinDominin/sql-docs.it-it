---
title: Connessione con IPv6 | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Internet Protocol
- IPv4
- IPv6
ms.assetid: 2669098c-f5f1-43da-aec6-e91003ac89f6
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3270ffb9899b8d8e4663c7e0d1b4dc52b8d89049
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="connecting-using-ipv6"></a>Connessione con IPv6
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client supportano completamente sia protocollo Internet versione 4 (IPv4) e protocollo Internet versione 6 (IPv6). Quando Windows è configurato in modo da utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]per IPv6 i componenti riconoscono automaticamente l'esistenza di IPv6. Non è necessaria alcuna configurazione particolare di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Il supporto include, tra l'altro, le caratteristiche seguenti:  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] e gli altri componenti server possono restare in ascolto contemporaneamente sugli indirizzi IPv4 e IPv6. Quando si utilizza sia IPv4 che IPv6, è possibile utilizzare Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per configurare il [!INCLUDE[ssDE](../../includes/ssde-md.md)] in modo che resti in ascolto solo sugli indirizzi di IPv4 o solo sugli indirizzi di IPv6.  
  
-   Quando il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser in esecuzione su un computer che supporta sia IPv4 che IPv6 riceve una richiesta su un indirizzo IPv4, risponde con un indirizzo IPv4 e con la prima porta TCP IPv4 in elenco. Quando riceve una richiesta su un indirizzo IPv6, il servizio risponde con un indirizzo IPv6 e con la prima porta TCP IPv6 in elenco. Per evitare inconsistenze, è consigliabile che i listener IPv4 e IPv6 siano configurati in modo da restare in ascolto sulla stessa porta.  
  
-   Strumenti quali [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accettano sia i formati IPv4 che IPv6 per gli indirizzi IP. Nella maggior parte dei casi, la stringa di connessione non devono essere modificate se il \< *nome_computer*>\\<*instance_name*> viene specificato usando nome host del server o il nome di dominio completo (FQDN). Se nel computer server vengono utilizzati sia IPv4 che IPv6, il relativo nome host o FQDN verrà risolto in più indirizzi IP, tra cui almeno un indirizzo IPv4 e più indirizzi IPv6. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client tenta di stabilire connessioni utilizzando questi indirizzi IP nell'ordine ricevuti da TCP/IP e utilizza la prima connessione che ha esito positivo. Poiché l'ordine non può essere previsto da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, deve essere considerato come casuale. In presenza di indirizzi sia IPv4 che IPv6 vengono tentati prima gli indirizzi IPv4. Questa logica è trasparente agli utenti di ODBC, OLE DB o ADO.NET.  
  
    > [!NOTE]  
    >  Se il [!INCLUDE[ssDE](../../includes/ssde-md.md)] non è in ascolto su IPv4, prima che venga tentata la connessione sull'indirizzo IPv6 si dovrà attendere il timeout della connessione IPv4. Per evitare tale attesa, stabilire direttamente una connessione all'indirizzo IP di IPv6 o configurare un alias sul client con l'indirizzo IPv6.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione configurazione SQL Server](../../relational-databases/sql-server-configuration-manager.md)  
  
  
