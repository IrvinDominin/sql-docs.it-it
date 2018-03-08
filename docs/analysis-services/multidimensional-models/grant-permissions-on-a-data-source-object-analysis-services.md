---
title: Concedere le autorizzazioni per un oggetto di origine dati (Analysis Services) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.asvs.roledesignerdialog.datasources.f1
helpviewer_keywords:
- read/write permissions
- user access rights [Analysis Services], data sources
- security [Analysis Services], data sources
- connection strings [Analysis Services]
- data sources [Analysis Services], security
ms.assetid: b4e302d3-c93b-4383-aa4a-37d15c129830
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f7cd02446a61b7ff1c8d9fdaa2803c30ee81a6e0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="grant-permissions-on-a-data-source-object-analysis-services"></a>Concedere le autorizzazioni per un oggetto origine dati (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]In genere, la maggior parte degli utenti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] non richiedono l'accesso alle origini dati sottostanti un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] progetto. Gli utenti in genere eseguono query solo sui dati inclusi in un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . In un contesto di data mining, tuttavia, ad esempio per l'esecuzione di stime basate su un modello di data mining, un utente deve unire in join i dati risultanti di un modello di data mining e i dati specificati dall'utente. Per connettersi all'origine dati contenente i dati specificati dall'utente, l'utente usa una query DMX (Data Mining Extensions) che include le clausole [OPENQUERY &#40;DMX&#41;](../../dmx/source-data-query-openquery.md) e [OPENROWSET &#40;DMX&#41;](../../dmx/source-data-query-openrowset.md).  
  
 Per eseguire una query DMX per la connessione a un'origine dei dati, l'utente deve poter accedere all'oggetto origine dei dati nel database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Per impostazione predefinita, solo gli amministratori del server o del database possono accedere agli oggetti origine dati. Ciò significa che un utente non può accedere a un oggetto origine dati a meno che un amministratore non conceda le autorizzazioni.  
  
> [!IMPORTANT]  
>  Per motivi di sicurezza, l'invio di query DMX tramite una stringa di connessione aperta nella clausola OPENROWSET è disabilitato.  
  
## <a name="set-read-permissions-to-a-data-source"></a>Impostare le autorizzazioni di Lettura per un'origine dati  
 A un ruolo del database è possibile non concedere alcuna autorizzazione di accesso per un oggetto origine dei dati oppure concedere autorizzazioni di lettura.  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]connettersi all'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], espandere il nodo **Ruoli** relativo al database appropriato in Esplora oggetti, quindi fare clic su un ruolo del database o creare un nuovo ruolo del database.  
  
2.  Nel riquadro **Accesso all'origine dati** individuare l'oggetto origine dati nell'elenco **Origine dati** , quindi selezionare **Lettura** nell'elenco **Accesso** relativo all'origine dati. Se questa opzione non è disponibile, verificare se nel riquadro **Generale** è selezionato Controllo completo. Il Controllo completo fornisce già l'autorizzazione e nell'origine dati non è possibile sostituire le autorizzazioni.  
  
## <a name="working-with-the-connection-string-used-by-a-data-source-object"></a>Stringa di connessione usata da un oggetto origine dei dati  
 L'oggetto origine dei dati include la stringa di connessione usata per eseguire la connessione all'origine dei dati sottostante. Tale stringa di connessione consente di specificare uno degli elementi seguenti:  
  
-   **Specificare un nome utente e una password**  
  
     Se tramite la stringa di connessione usata da un oggetto origine dei dati vengono specificati un nome utente e una password, è possibile creare più oggetti origine dei dati, ognuno dei quali con account utente diversi. La creazione di più oggetti origine dei dati consente agli utenti di accedere a oggetti origine dei dati specifici impedendo l'accesso ad altri oggetti origine dei dati. Questi altri oggetti origine dei dati possono essere usati da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stesso per elaborare oggetti, ad esempio cubi e modelli di data mining.  
  
-   **Specificare l'autenticazione Windows**  
  
     Se tramite la stringa di connessione usata da un oggetto origine dei dati viene specificata l'autenticazione di Windows, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] deve essere in grado di rappresentare il client. Se l'origine dei dati è presente in un computer remoto, i due computer devono essere ritenuti attendibili per la rappresentazione tramite l'autenticazione Kerberos, altrimenti la query ha in genere esito negativo. Per altre informazioni, vedere [Configurare Analysis Services per la delega vincolata Kerberos](../../analysis-services/instances/configure-analysis-services-for-kerberos-constrained-delegation.md) .  
  
     Se il client non consente la rappresentazione, tramite la proprietà Impersonation Level in OLE DB e altri componenti client, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] proverà a stabilire una connessione anonima all'origine dati sottostante. Le connessioni anonime alle origini dati remote raramente riescono poiché la maggior parte delle origini dati non accetta connessioni anonime.  
  
## <a name="see-also"></a>Vedere anche  
 [Origini dati nei modelli multidimensionali](../../analysis-services/multidimensional-models/data-sources-in-multidimensional-models.md)   
 [Proprietà della stringa di connessione &#40; Analysis Services &#41;](../../analysis-services/instances/connection-string-properties-analysis-services.md)   
 [Metodologie di autenticazione supportate da Analysis Services](../../analysis-services/instances/authentication-methodologies-supported-by-analysis-services.md)   
 [Concedere l'accesso personalizzato alla dimensione dei dati &#40; Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)   
 [Concedere le autorizzazioni per un cubo o un modello &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)   
 [Concedere l'accesso personalizzato ai dati delle celle &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)  
  
  
