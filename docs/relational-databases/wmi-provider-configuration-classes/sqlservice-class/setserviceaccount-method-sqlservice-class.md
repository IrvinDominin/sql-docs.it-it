---
title: Metodo SetServiceAccount (classe SqlService) | Documenti Microsoft
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
- SetServiceAccount Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetServiceAccount method
ms.assetid: d5782892-e9d8-4d48-92af-b3afe9610f84
caps.latest.revision: 
author: JennieHubbard
ms.author: jhubbard
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1bdcb3f6789baf009165a74bcf3d82630fa868fd
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="setserviceaccount-method-sqlservice-class"></a>Metodo SetServiceAccount (classe SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
Tenta di modificare il nome utente e la password con cui è in esecuzione l'istanza del servizio.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.SetServiceAccount(ServiceStartName , ServiceStartPassword)  
```  
  
## <a name="parts"></a>Parti  
 *oggetto*  
 Oggetto della [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) che rappresenta il servizio.  
  
#### <a name="parameters"></a>Parametri  
 *ServiceStartName*  
 Valore string che specifica il nome dell'account con cui è in esecuzione il servizio. A seconda del tipo di servizio, il nome dell'account potrebbe essere nel formato NomeDominio\NomeUtente. Durante l'esecuzione il processo del servizio viene registrato utilizzando uno di due formati:  
  
-   Se l'account appartiene al dominio predefinito, è possibile specificare \Nomeutente.  
  
-   Se si specifica NULL, il servizio verrà connesso come il **LocalSystem** account.  
  
 Per i driver del kernel o a livello di sistema, *StartName* contiene il nome dell'oggetto driver, \FileSystem\Rdr o \Driver\Xns, che utilizza il sistema dei / o per caricare il driver di dispositivo. Se viene specificato NULL, il driver viene eseguito con un nome dell'oggetto predefinito creato dal sistema I/O in base sul nome del servizio, ad esempio DWDOM\Admin.  
  
 *ServiceStartPassword*  
 Valore stringa che specifica la password per il nome dell'account nel *StartName* parametro. Specificare NULL se non si modifica la password. Specificare una stringa vuota se il servizio non dispone di password.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore **uint32** che è 0 se il servizio è stato modificato correttamente 0 1 se la richiesta non è supportata. Qualsiasi altro numero indica un errore.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio e arresto di servizi](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
