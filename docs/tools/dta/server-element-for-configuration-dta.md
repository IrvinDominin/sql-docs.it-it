---
title: Elemento server per Configuration (DTA) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: dta
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: Server element
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
caps.latest.revision: "13"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4df65dc3db8f8c23aa0fd012ee834020839d1ce9
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="server-element-for-configuration-dta"></a>Elemento Server per Configuration (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Contiene le informazioni di identificazione per il server in cui si desidera Ottimizzazione guidata motore Database per valutare la configurazione del ipotetica (specificato da di **configurazione** elemento).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Configuration>  
    <Server>  
...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuno|  
|**Valore predefinito**|Nessuno|  
|**Occorrenza**|Richiesto una volta per l'elemento **Configuration** .|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento Configuration &#40; DTA &#41;](../../tools/dta/configuration-element-dta.md)|  
|**Elementi figlio**|[Elemento Name per Server &#40; DTA &#41;](../../tools/dta/name-element-for-server-dta.md)<br /><br /> [Elemento database per Configuration &#40; DTA &#41;](../../tools/dta/database-element-for-configuration-dta.md)|  
  
## <a name="remarks"></a>Osservazioni  
 È possibile specificare solo un elemento **Server** per l'elemento **Configuration** . Questo elemento appartiene al Name **ServerTypecomplexType** nell' [XML Schema dell'ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?linkid=43100). Non si deve confondere questo elemento **Server** con l'elemento figlio di **DTAInput**. Per altre informazioni, vedere [Elemento Server &#40;DTA&#41;](../../tools/dta/server-element-dta.md).  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo, vedere [Esempio di file di input XML con configurazione specificata dall'utente &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
