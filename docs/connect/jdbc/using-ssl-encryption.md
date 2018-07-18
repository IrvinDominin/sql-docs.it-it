---
title: Utilizzo della crittografia SSL | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8e566243-2f93-4b21-8065-3c8336649309
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5444946843576f87b6887d2bc9446d0a93d5106d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-ssl-encryption"></a>Utilizzo della crittografia SSL
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  La crittografia Secure Sockets Layer (SSL) consente la trasmissione dei dati crittografati attraverso la rete tra un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e un'applicazione client.  
  
 SSL (Secure Sockets Layer) è un protocollo che consente di stabilire un canale di comunicazione sicuro per impedire l'intercettazione di informazioni critiche o riservate attraverso la rete e altre comunicazioni Internet. SSL consente al client e al server di autenticare l'identità reciproca. Dopo che i partecipanti sono stati autenticati, SSL fornisce connessioni crittografate tra di essi per una trasmissione sicura dei messaggi.  
  
 Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fornisce un'infrastruttura per abilitare e disabilitare la crittografia in una particolare connessione in base all'utente di specificare le proprietà di connessione e le impostazioni di server e client. L'utente può specificare il percorso e la password dell'archivio certificati, un nome host da utilizzare per convalidare il certificato e quando crittografare il canale di comunicazione.  
  
 L'abilitazione della crittografia SSL contribuisce alla sicurezza del traffico di dati in rete tra le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e le applicazioni, ma comporta un rallentamento delle prestazioni.  
  
 Negli argomenti di questa sezione viene descritto come [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] versione supporta la crittografia SSL, tra cui nuove proprietà di connessione e come è possibile configurare l'archivio di scopi consentiti sul lato client.  
  
> [!NOTE]  
>  Il **hostNameInCertificate** proprietà di connessione è consigliabile convalidare un certificato SSL.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Informazioni sul supporto SSL](../../connect/jdbc/understanding-ssl-support.md)|Viene descritto come [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] supporta la crittografia SSL.|  
|[Connessione tramite la crittografia SSL](../../connect/jdbc/connecting-with-ssl-encryption.md)|Viene descritto come connettersi a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database utilizzando le nuove proprietà di connessione specifiche di SSL.|  
|[Configurazione del client per la crittografia SSL](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md)|Viene descritto come configurare l'archivio di attendibilità predefinito sul lato client e come importare un certificato privato nell'archivio di attendibilità del computer client.|  
  
## <a name="see-also"></a>Vedere anche  
 [Protezione delle applicazioni del driver JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
