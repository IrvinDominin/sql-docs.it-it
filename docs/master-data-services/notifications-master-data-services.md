---
title: Notifiche (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- notifications [Master Data Services]
- notifications [Master Data Services], about notifications
- e-mail [Master Data Services]
- e-mail [Master Data Services], about e-mail notifications
ms.assetid: d7ad32d5-9fe5-48fd-8c61-0b00c0aff082
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 7b973d967645b51aafe7e4314b339c5966fa7141
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47671589"
---
# <a name="notifications-master-data-services"></a>Notifiche (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] può essere configurato in modo da inviare una notifica tramite posta elettronica quando la convalida delle regole di business non riesce oppure quando lo stato di una versione di modello o di un insieme di modifiche cambia.  
  
## <a name="how-notifications-are-sent"></a>Modalità di invio delle notifiche  
 È possibile configurare notifiche in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. La configurazione delle notifiche attiva l'invio di messaggi di posta elettronica tramite il componente Posta elettronica database nell'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] che ospita il database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Per altre informazioni su Posta elettronica database, vedere la sezione [Oggetti di configurazione di Posta elettronica database](../relational-databases/database-mail/database-mail-configuration-objects.md) nella documentazione online di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
## <a name="when-notifications-are-sent"></a>Quando vengono inviate le notifiche  
 Dopo la configurazione delle notifiche, è possibile inviare notifiche automatiche tramite posta elettronica nelle due istanze seguenti.  
  
|Istanza|Descrizione|  
|--------------|-----------------|  
|La convalida dei dati tramite regole business ha esito negativo|È necessario configurare singole regole business per l'invio di posta elettronica quando la convalida tramite regole business di un valore di attributo ha esito negativo. La notifica contiene le informazioni seguenti.<br /><br /> Modello<br /><br /> Versione<br /><br /> Entità<br /><br /> Codice membro<br /><br /> Regola di business non riuscita<br /><br /> Collegamento al membro per il quale il valore dell'attributo causa l'errore della regola business<br /><br /> Ora di invio della notifica<br /><br /> Per altre informazioni, vedere [Configurare le regole di business per l'invio di notifiche &#40;Master Data Services&#41;](../master-data-services/configure-business-rules-to-send-notifications-master-data-services.md).|  
|Lo stato della versione di un modello viene modificato|Ogni volta che lo stato della versione di un modello viene modificato, vengono inviate automaticamente notifiche agli utenti configurati come amministratori del modello. La notifica contiene le informazioni seguenti.<br /><br /> Modello<br /><br /> Versione<br /><br /> Stato precedente e nuovo della versione<br /><br /> Ora di invio della notifica<br /><br /> Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).|  
|Modifiche dello stato dell'insieme di modifiche|Ogni volta che viene modificato lo stato di un insieme di modifiche per un'entità che richiede l'approvazione, gli amministratori dell'entità e/o i proprietari dell'insieme di modifiche ricevono automaticamente una notifica. La notifica contiene le informazioni seguenti.<br /><br /> Modello<br /><br /> Versione<br /><br /> Nome dell'insieme di modifiche<br /><br /> Stato precedente<br /><br /> Nuovo stato<br /><br /> Collegamento per applicare l'insieme di modifiche per visualizzare e modificare le modifiche in sospeso.<br /><br /> Per altre informazioni, vedere [Insiemi di modifiche &#40;Master Data Services&#41;](../master-data-services/changesets-master-data-services.md)|  
  
## <a name="system-settings"></a>Impostazioni sistema  
 Alcune impostazioni di [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] hanno effetto sulle notifiche. È possibile regolare tali impostazioni in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] o direttamente nella tabella Impostazioni sistema del database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Per altre informazioni, vedere [Impostazioni di sistema &#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md).  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Configurare [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] per inviare notifiche di posta elettronica.|[Configurare notifiche di posta elettronica &#40;Master Data Services&#41;](../master-data-services/configure-email-notifications-master-data-services.md)|  
|Configurare [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] per inviare notifiche quando i valori dell'attributo vengono modificati.|[Configurare le regole di business per l'invio di notifiche &#40;Master Data Services&#41;](../master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)|  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   [Regole business &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
-   [Versioni &#40;Master Data Services&#41;](../master-data-services/versions-master-data-services.md)  
  
-   [Risoluzione dei problemi relativi alle notifiche di posta elettronica (Master Data Services)](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx)  
  
  
