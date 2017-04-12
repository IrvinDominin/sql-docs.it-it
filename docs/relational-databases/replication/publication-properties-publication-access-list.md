---
title: "Propriet&#224; pubblicazione, Elenco accesso pubblicazione | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.pubproperties.publicationaccesslist.f1"
ms.assetid: 9587bb9e-c66c-4e70-8171-09b943ec2d50
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Propriet&#224; pubblicazione, Elenco accesso pubblicazione
  Il **elenco accesso pubblicazione** pagina la **Proprietà pubblicazione** la finestra di dialogo consente di aggiungere e rimuovere gli account di accesso, account e gruppi dall'elenco di accesso (PAL). L'elenco di accesso alla pubblicazione costituisce il principale sistema di sicurezza del server di pubblicazione. Quando si crea una pubblicazione, la replica crea un elenco di accesso alla pubblicazione per la pubblicazione creata. L'elenco di accesso alla pubblicazione opera in modo analogo all'elenco di controllo di accesso di [!INCLUDE[msCoName](../../includes/msconame-md.md)] e include un elenco di account di accesso, account e gruppi ai quali viene consentito l'accesso alla pubblicazione.  
  
 Quando un Sottoscrittore si connette al server di pubblicazione o al server di distribuzione e richiede l'accesso alla pubblicazione, l'account di accesso del Sottoscrittore viene confrontato con le informazioni di autenticazione contenute nell'elenco di accesso alla pubblicazione. Ciò garantisce un maggior livello di sicurezza del server di pubblicazione, impedendo che gli account di accesso del server di pubblicazione e del server di distribuzione vengano utilizzati da uno strumento client per apportare modifiche direttamente nel server di pubblicazione. Per ulteriori informazioni, vedere [proteggere il server di pubblicazione](../../relational-databases/replication/security/secure-the-publisher.md).  
  
## Opzioni  
 **Aggiungi**  
 Consente di aggiungere una nuova voce all'elenco. È possibile aggiungere solo gli account di accesso, gli account o i nomi dei gruppi già definiti sia nel server di pubblicazione sia nel server di distribuzione. Tali account di accesso, account e nomi di gruppi vengono definiti in entrambi i server nei casi in cui si utilizzino account di dominio o siano stati creati account locali in entrambi i server.  
  
 **Rimuovi**  
 Consente di rimuovere la voce selezionata dall'elenco.  
  
 **Rimuovi tutto**  
 Consente di rimuovere tutte le voci dall'elenco.  
  
## Vedere anche  
 [Creazione di una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)   
 [Visualizzazione e modifica delle proprietà della pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Pubblicazione di dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  