---
title: Metodo SetStartMode (classe SqlService) | Documenti Microsoft
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
- SetStartMode Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetStartMode method
ms.assetid: f6f198b4-f9a4-468c-8977-76462ef06e61
caps.latest.revision: 
author: JennieHubbard
ms.author: jhubbard
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 713513ec867a8d5dadf46a59a0721eea10d26919
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="setstartmode-method-sqlservice-class"></a>Metodo SetStartMode (classe SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
Modifica la modalità di avvio dell'istanza del servizio.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.SetStartMode(StartMode)  
```  
  
## <a name="parts"></a>Parti  
 *oggetto*  
 Oggetto della [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) che rappresenta il servizio.  
  
#### <a name="parameters"></a>Parametri  
 *StartMode*  
 Valore **uint32** che specifica la modalità di avvio dell'istanza del servizio.  
  
 I valori validi sono i seguenti:  
  
 Valore = 0. Boot: driver di dispositivo avviato dal caricatore del sistema operativo. Questo valore è valido solo per i servizi del driver.  
  
 Valore = 1. System: driver di dispositivo avviato dal metodo **IoInitSystem** . Questo valore è valido solo per i servizi del driver.  
  
 Valore = 2. Automatic: servizio da avviare automaticamente da Gestione controllo servizi durante l'avvio del sistema.  
  
 Valore = 3. Manual: servizio da avviare da Gestione computer quando un processo chiama il metodo **StartService** .  
  
 Valore = 4. Disabled: impossibile avviare il servizio.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore **uint32** che è 0 se il servizio è stato modificato correttamente 0 1 se la richiesta non è supportata. Qualsiasi altro numero indica un errore.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio e arresto di servizi](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
