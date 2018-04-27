---
title: Distribuzioni multilingue e globali (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: mds
ms.service: ''
ms.component: install-windows
ms.reviewer: ''
ms.suite: sql
ms.technology:
- setup-install
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3d485f8-867c-4aa2-a90d-f38fda192534
caps.latest.revision: 8
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6d5694035db52205d17a482a5ac8b8a79144d163
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="multi-lingual-and-global-deployments-master-data-services"></a>Distribuzioni multilingue e globali (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] supporta la distribuzione di componenti e strumenti in tutte le lingue supportate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [Versioni in lingua locale di SQL Server](../../sql-server/install/local-language-versions-in-sql-server.md).  
  
## <a name="how-languages-are-used"></a>Modalità di utilizzo delle lingue  
 Nella tabella seguente viene descritto il supporto per i componenti e gli strumenti di [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .  
  
|Componente o strumento|Description|  
|-----------------------|-----------------|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Installazione|Selezionare il programma di installazione in lingua inglese quando si desidera che l'applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] sia disponibile e supportata in lingue diverse dalla lingua di installazione. Per ulteriori informazioni, vedere la descrizione relativa a [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] riportata di seguito.|  
|[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]|La lingua di [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] viene determinata dal programma di installazione. Ad esempio, se si sceglie Italiano per la lingua di installazione, [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] sarà disponibile in italiano nel computer.|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]|Quando si esegue l'installazione in inglese, l'applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] è disponibile e supportata in tutte le lingue dell'applicazione. [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] può essere visualizzato in qualsiasi lingua dell'applicazione e può accettare l'input specifico delle impostazioni locali basato sulle preferenze di lingua del browser client. Se le preferenze per la lingua vengono configurate per una lingua dell'applicazione non supportata, [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] verrà impostato sulla lingua inglese.<br /><br /> Quando si esegue l'installazione in una lingua diversa dall'inglese, vengono incluse le risorse per tutte le altre lingue dell'applicazione [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , sebbene l'utilizzo da parte dei client in una lingua diversa dalla lingua di installazione selezionata non sia uno scenario supportato. Se si tenta di accedere a [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] in una lingua diversa da quella di installazione, è possibile che si verifichino problemi con la visualizzazione e l'input di dati nell'applicazione.|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database|Le informazioni nel database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] non sono specifiche delle impostazioni locali. In questo modo [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] è in grado di stabilire la modalità di visualizzazione delle informazioni, ad esempio date e i numeri, nel formato determinato dalle preferenze per la lingua del browser client.|  
  
## <a name="see-also"></a>Vedere anche  
 [Installazione di Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)  
  
  
