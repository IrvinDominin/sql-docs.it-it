---
title: la procedura sp_monitor (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_monitor_TSQL
- sp_monitor
dev_langs:
- TSQL
helpviewer_keywords:
- sp_monitor
ms.assetid: cb628496-2f9b-40e4-b018-d0831c4cb018
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5312413386dae9915b9ac6649b4210541d45b1db
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47644429"
---
# <a name="spmonitor-transact-sql"></a>sp_monitor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza le statistiche sulle [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_monitor  
```  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Description|  
|-----------------|-----------------|  
|**last_run**|Tempo **sp_monitor** data dell'ultima esecuzione.|  
|**current_run**|Tempo **sp_monitor** è in esecuzione.|  
|**secondi**|Numero di secondi trascorsi a partire **sp_monitor** è stata eseguita.|  
|**cpu_busy**|Numero di secondi di attività della CPU del server per l'elaborazione di operazioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**io_busy**|Numero di secondi trascorsi per l'esecuzione di operazioni di input e output in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Inattività**|Numero di secondi durante i quali [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è rimasto inattivo.|  
|**packets_received**|Numero di pacchetti di input letti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**packets_sent**|Numero di pacchetti di output scritti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**PACKET_ERRORS**|Numero di errori rilevati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durante la lettura e la scrittura di pacchetti.|  
|**total_read**|Numero di letture eseguite da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**total_write**|Numero di scritture eseguite da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**total_errors**|Numero di errori rilevati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durante la lettura e la scrittura.|  
|**Connessioni**|Numero di accessi o tentativi di accesso a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="remarks"></a>Note  
 Tramite una serie di funzioni, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene tenuto traccia della quantità di operazioni eseguite. L'esecuzione **sp_monitor** consente di visualizzare i valori correnti restituiti da queste funzioni e viene illustrato quanto essi sono stati modificati dall'ultima volta la routine è stata eseguita.  
  
 Per ogni colonna, la statistica è stampata in forma *numero*(*numero*)-*numero*% o *numero*(*numero*). Il primo *numero* si riferisce al numero di secondi (per **cpu_busy**, **io_busy**, e **inattività**) oppure il numero totale (per gli altri le variabili) poiché [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è stato riavviato. Il *numero* tra parentesi indica il numero di secondi o il numero totale dall'ultima volta **sp_monitor** è stata eseguita. La percentuale è la percentuale di tempo trascorso dal **sp_monitor** data dell'ultima esecuzione. Ad esempio, se il report illustra **cpu_busy** 4250 (215)-68%, la CPU è stata occupata per 4250 secondi dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verso l'alto, 215 secondi dall'ultimo avvio **sp_monitor** stato ultima esecuzione e il 68% del Totale tempo trascorso dal **sp_monitor** data dell'ultima esecuzione.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituite informazioni relative all'attività di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
USE master  
EXEC sp_monitor  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
||||  
|-|-|-|  
|**last_run**|**current_run**|**secondi**|  
|1998-03-29 11.55|1998-04-04 14.22|561|  
  
||||  
|-|-|-|  
|**cpu_busy**|**io_busy**|**Inattività**|  
|190(0)-0%|187(0)-0%|148(556)-99%|  
  
||||  
|-|-|-|  
|**packets_received**|**packets_sent**|**PACKET_ERRORS**|  
|16(1)|20(2)|0(0)|  
  
|||||  
|-|-|-|-|  
|**total_read**|**total_write**|**total_errors**|**Connessioni**|  
|141(0)|54920(127)|0(0)|4(0)|  
  
## <a name="see-also"></a>Vedere anche  
 [sp_who &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
