---
title: Analizza in Excel | Documenti Microsoft
ms.custom: 
ms.date: 02/21/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f17b4df-eea2-48c7-a1f2-a3fb7748c15f
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bd537debaa43c89c2d09295f12598a9bfe9927b3
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="analyze-in-excel"></a>Analizza in Excel
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
La funzionalità analizza in Excel, in SSDT, consente agli autori di modelli tabulari di analizzare rapidamente i progetti di modello durante lo sviluppo. La caratteristica Analizza in Excel consente di aprire Microsoft Excel, di creare una connessione dell'origine dati al database dell'area di lavoro modello e di aggiungere automaticamente una tabella pivot al foglio di lavoro. Gli oggetti del database dell'area di lavoro (tabelle, colonne e misure) sono inclusi come campi nel relativo elenco della tabella pivot. Gli oggetti e i dati possono essere quindi visualizzati all'interno del contesto dell'utente effettivo o del ruolo e della prospettiva.  
  
 In questo articolo si presuppone che si ha già familiarità con Microsoft Excel, tabelle e grafici pivot. Per ulteriori informazioni sull'utilizzo di Excel, vedere la relativa Guida.  
  
##  <a name="bkmk_benefits"></a> Vantaggi  
 La caratteristica Analizza in Excel consente agli autori di modelli di verificare l'efficacia di un progetto di modello utilizzando l'applicazione per l'analisi dei dati comuni, ovvero Microsoft Excel. Per utilizzare la funzionalità analizza in Excel, è necessario che Microsoft Office 2003 o versione successiva nello stesso computer come SSDT.  
  
 La caratteristica Analizza in Excel consente di aprire Excel e di creare una nuova cartella di lavoro (con estensione xls). In seguito, viene creata una connessione dati dalla cartella di lavoro al database dell'area di lavoro modello, viene aggiunta una tabella pivot vuota al foglio di lavoro e i metadati dell'oggetto modello vengono popolati nell'elenco di campi della tabella pivot. Successivamente, è possibile aggiungere i dati e i relativi filtri visualizzabili alla tabella pivot.  
  
 Se si utilizza la caratteristica Analizza in Excel, per impostazione predefinita, l'account utente che ha attualmente effettuato l'accesso è l'utente effettivo. Questo account è in genere un amministratore senza restrizioni di visualizzazione relativamente agli oggetti o ai dati del modello. Tuttavia, è possibile specificare un nome utente o un ruolo effettivo diverso. In questo modo, l'utente può sfogliare un progetto di modello in Excel all'interno del contesto di un utente o ruolo specifico. La specificazione dell'utente effettivo prevede le opzioni seguenti:  
  
 **Utente di Windows corrente**  
 Viene utilizzato l'account utente con cui è stato effettuato l'accesso.  
  
 **Altro utente di Windows**  
 Viene utilizzato un nome utente di Windows specificato piuttosto che l'utente che ha effettuato l'accesso. L'utilizzo di un utente di Windows diverso non richiede una password. Gli oggetti e i dati possono essere visualizzati solo in Excel all'interno del contesto del nome utente effettivo. Non è possibile apportare alcuna modifica agli oggetti o ai dati del modello in Excel.  
  
 **Ruolo**  
 Un ruolo viene utilizzato per definire le autorizzazioni utente sui metadati e dati dell'oggetto. I ruoli vengono generalmente definiti per un utente di Windows o un gruppo di utenti di Windows particolare. In alcuni ruoli possono essere inclusi ulteriori filtri a livello di riga definiti in una formula DAX. Se si utilizza la caratteristica Analizza in Excel, è possibile selezionare facoltativamente un ruolo da utilizzare. Le viste dei metadati e dei dati dell'oggetto saranno limitate dall'autorizzazione e dai filtri definiti per il ruolo. Per ulteriori informazioni, vedere [creare e gestire ruoli](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md).  
  
 Oltre all'utente o al ruolo effettivo, è possibile specificare una prospettiva. Le prospettive consentono agli autori di modelli di definire viste di oggetti e dati del modello in scenari aziendali particolari. Per impostazione predefinita, non viene utilizzata alcuna prospettiva. Per utilizzare una prospettiva con analizza in Excel, le prospettive devono essere già definite tramite la finestra di dialogo prospettive in SSDT. Se viene specificata una prospettiva, nell'elenco di campi della tabella pivot saranno contenuti solo gli oggetti selezionati nella prospettiva. Per ulteriori informazioni, vedere [crea e Gestisci prospettive](../../analysis-services/tabular-models/create-and-manage-perspectives-ssas-tabular.md).  
  
##  <a name="bkmk_rt"></a> Related tasks  
  
|**Argomento**|**Description**|  
|---------------|---------------------|  
|[Analizzare un modello tabulare in Excel](../../analysis-services/tabular-models/analyze-a-tabular-model-in-excel-ssas-tabular.md)|In questo articolo viene descritto come utilizzare l'analizza nella funzionalità di Excel in Progettazione modelli per aprire Excel, creare una connessione all'origine dati al database dell'area di lavoro modello e aggiungere una tabella pivot al foglio di lavoro.|  
  
## <a name="see-also"></a>Vedere anche  
 [Analizzare un modello tabulare in Excel](../../analysis-services/tabular-models/analyze-a-tabular-model-in-excel-ssas-tabular.md)   
 [Ruoli](../../analysis-services/tabular-models/roles-ssas-tabular.md)   
 [Prospettive](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)  
  
  
