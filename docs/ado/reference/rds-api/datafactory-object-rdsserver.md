---
title: Oggetto DataFactory (RDSServer) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- DataFactory object [ADO]
ms.assetid: e75240c2-b749-471e-b6ea-98cae232efbe
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: db11cc8488b2ca2d3083ca95ac124cbe15b5313c
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="datafactory-object-rdsserver"></a>Oggetto DataFactory (RDSServer)
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Questo oggetto business sul lato server per impostazione predefinita implementa metodi che forniscono accesso ai dati di lettura/scrittura per le applicazioni sul lato client alle origini dati specificato.  
  
 Il **RDSServer** oggetto è stato progettato come un oggetto di automazione sul lato server che riceve le richieste client. In un'implementazione di Internet, si trova in un server Web e viene creata un'istanza dal componente ADISAPI. Il **RDSServer** oggetto consente di lettura e accesso in scrittura ai dati specificati origini, ma non contiene qualsiasi logica delle regole di convalida o di business.  
  
 Se si utilizza un metodo che è disponibile in entrambe le **RDSServer** e [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetti, Remote Data Service utilizza la **RDS. DataControl** versione per impostazione predefinita. Il valore predefinito presuppone uno scenario di programmazione di base, in cui il **RDSServer** funge da oggetto business generico sul lato server.  
  
 Se si desidera che l'applicazione Web per gestire l'elaborazione sul lato server specifici dell'attività, è possibile sostituire il **RDSServer** con un oggetto di business personalizzata.  
  
 È possibile creare gli oggetti business sul lato server che chiamano il **RDSServer** metodi, ad esempio [Query](../../../ado/reference/rds-api/query-method-rds.md) e [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md). Ciò risulta utile se si desidera aggiungere funzionalità a oggetti di business, ma possono sfruttare le tecnologie esistenti Remote Data Service.  
  
 Il **DataFactory** oggetto non è sicuro per gli script da eseguire sul lato client.  
  
 L'ID di classe per il **RDSServer** oggetto è 9381D8F5-11-0288 D 0-9501-00AA00B911A5.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi dell'oggetto DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di oggetto DataFactory, metodo Query e metodo CreateObject (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)


