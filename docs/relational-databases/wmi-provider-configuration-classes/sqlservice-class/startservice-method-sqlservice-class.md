---
title: Metodo StartService (classe SqlService) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- StartService Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- StartService method
ms.assetid: 83dfb6bd-dbd5-45d8-aad2-a11926317f91
caps.latest.revision: 
author: JennieHubbard
ms.author: jhubbard
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3698bd4f7b9817cf4a6bde946946723f4accc0fb
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="startservice-method-sqlservice-class"></a>Metodo StartService (classe SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
Esegue un tentativo di avvio del servizio.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.StartService()  
```  
  
## <a name="parts"></a>Parti  
 *oggetto*  
 Oggetto della [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) che rappresenta il servizio.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore uint32 che specifica uno dei seguenti stati di avvio.  
  
 0  
 Esito positivo. La richiesta è stata accettata.  
  
 1  
 Non supportato. La richiesta non è supportata.  
  
 2  
 Accesso negato. L'utente non dispone dei diritti di accesso appropriati.  
  
 3  
 Servizi dipendenti in esecuzione. Impossibile arrestare il servizio perché altri servizi in esecuzione dipendono dal servizio.  
  
 4  
 Controllo servizio non valido. Il codice di controllo richiesto non è valido o non è accettabile per il servizio.  
  
 5  
 Il servizio non accetta il controllo. Impossibile inviare il codice di controllo richiesto al servizio perché lo stato del servizio (Win32_BaseService:State) è uguale a 0, 1 o 2.  
  
 6  
 Servizio non attivo. Il servizio non è stato avviato.  
  
 7  
 Timeout richiesta servizio. Il servizio non ha risposto in tempo utile alla richiesta di avvio.  
  
 8  
 Errore sconosciuto. Errore sconosciuto durante l'avvio del servizio.  
  
 9  
 Percorso non trovato. Impossibile trovare il percorso di directory del file eseguibile del servizio.  
  
 10  
 Servizio già in esecuzione. Il servizio è già in esecuzione.  
  
 11  
 Database del servizio bloccato. Il database a cui aggiungere il nuovo servizio è bloccato.  
  
 12  
 Dipendenza del servizio eliminata. Il servizio si basa su una dipendenza che è stata rimossa dal sistema.  
  
 13  
 Errore di dipendenza del servizio. Impossibile trovare un servizio dipendente necessario.  
  
 14  
 Servizio disabilitato. Il servizio è stato disabilitato dal sistema.  
  
 15  
 Errore di accesso del servizio. Il servizio non dispone delle credenziali di autenticazione corrette per l'esecuzione nel sistema.  
  
 16  
 Servizio contrassegnato per l'eliminazione. Il servizio verrà rimosso dal sistema.  
  
 17  
 Nessun thread disponibile per il servizio. Nessun thread di esecuzione per il servizio.  
  
 18  
 Stato: dipendenza circolare. All'avvio del servizio sono state rilevate dipendenze circolari.  
  
 19  
 Stato: nome duplicato. È presente un servizio in esecuzione con lo stesso nome.  
  
 20  
 Stato: nome non valido. Il nome del servizio contiene caratteri non validi.  
  
 21  
 Stato: parametro non valido. Sono stati passati parametri non validi al servizio.  
  
 22  
 Stato: account di servizio non valido. L'account utilizzato per l'esecuzione del servizio non è valido o non dispone delle autorizzazioni necessarie per eseguire il servizio.  
  
 23  
 Stato: servizio già esistente. Il servizio esiste già nel database dei servizi disponibili dal sistema.  
  
 24  
 Servizio già sospeso. Il servizio è attualmente sospeso nel sistema.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio e arresto di servizi](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
