---
title: Oggetto del modello (TMSL) | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6f60b0998dd344cdc3151da1a1c8920495b36917
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="model-object-tmsl"></a>Oggetto del modello (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Definisce un modello tabulare. È disponibile un modello per ogni database e un solo database che può essere specificato in qualsiasi comando specificato. Un oggetto di Database è l'oggetto padre.  
  
 Le definizioni di modello sono troppo grandi per riprodurre la sintassi intera in un argomento. Per questo motivo, una le parti principali di evidenziazione della sintassi parziale può trovarsi sotto, con collegamenti agli oggetti figlio.  
  
 Ad esempio il modo migliore per comprendere una definizione del modello consiste nell'iniziare con un modello tabulare che si conosce bene. Utilizzare il **Visualizza codice** opzione in SQL Server Data Tools per visualizzare la relativa definizione. È necessario installare un editor di JSON in modo che è possibile visualizzare il codice. È possibile ottenere un editor di JSON in Visual Studio [download Community edition](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) o altra edizione di Visual Studio.  
  
> [!NOTE]  
>  In qualsiasi script, è possibile fare riferimento un solo database al momento. Per qualsiasi oggetto diverso dal database stesso, la proprietà del Database è facoltativa se si specifica il modello. È presente un mapping uno a uno tra un modello e un Database che può essere usato per dedurre il nome del Database se viene fornito in modo non esplicito.   
> Analogamente, è possibile lasciare il modello, impostandone le proprietà nel Database.  
  
## <a name="object-definition"></a>Definizione dell'oggetto  
 Tutti gli oggetti hanno un set comune di proprietà, inclusi nome, tipo, descrizione, una raccolta di proprietà e le annotazioni. **Modello** oggetti hanno anche le proprietà seguenti.  
  
 storageLocation  
 Percorso su disco in cui inserire il modello.  
  
 proprietà defaultMode  
 Il metodo predefinito per rendere disponibili i dati nella partizione.  
  
 defaultDataView  
 Per i modelli in modalità DirectQuery, questa proprietà determina le partizioni vengono utilizzate per eseguire query sul modello.  I valori validi includono completa e esempio.  
  
 lingua  
 Le impostazioni cultura da utilizzare per la formattazione.  
  
 collation  
 La sequenza di regole di confronto. Vedere [scenari di globalizzazione per Analysis Services](../../analysis-services/globalization-scenarios-for-analysis-services.md) per ulteriori informazioni.  
  
 tables  
 L'insieme completo di tabelle del modello, incluse le partizioni, colonne, misure, indicatori KPI e annotazioni. Vedere [oggetto tabelle &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md) per informazioni dettagliate.  
  
 relazioni  
 Specifica la relazione tra ogni coppia di tabelle, incluse le proprietà che impostano la direzione del filtro e sicurezza. Vedere [oggetto relazioni &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/relationships-object-tmsl.md) per informazioni dettagliate.  
  
 origini dati  
 Una o più connessioni a database esterni che forniscono dati al modello o utilizzato per passano attraverso le query. Vedere [origini dati oggetto &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md) per informazioni dettagliate.  
  
 ruoli  
 Oggetti associati a un database l'autorizzazione, gli account dei membri e, facoltativamente, i filtri di sicurezza in DAX per il controllo di accesso personalizzati.  
  
## <a name="usage"></a>Utilizzo  
 **Modello** oggetti contengono un modello intero. È necessario specificare un modello e/o il relativo oggetto di Database padre nella maggior parte dei comandi.  
  
 Durante la creazione, la sostituzione o modifica di un oggetto modello, specificare tutte le proprietà di sola lettura della definizione dell'oggetto. Omissione di una proprietà di lettura / scrittura è considerata un'operazione di eliminazione.  
  
## <a name="partial-syntax"></a>Sintassi parziale  
 Poiché questa definizione di oggetto è elevata, sono elencate solo le proprietà di primo livello. Vedere [le definizioni degli oggetti in Tabular Model Scripting Language &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/tmsl-reference-tabular-objects.md) per un elenco di oggetti figlio.  
  
```  
    "model": {  
      "description": "Model object of a Tabular database",  
      "type": "object",  
      "properties": {  
          "name": {  },  
          "description": {  },  
         "storageLocation": {  },  
         "defaultMode":  {  },  
         "defaultDataView": {  },  
         "culture": {  },  
         "collation": {  },  
         "annotations": {  },  
         "tables": {  },  
         "relationships": {  },  
         "dataSources": {  },  
         "perspectives": {  },  
            "cultures": {  },  
         "roles": {  }  
    }  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento a Tabular Model Scripting Language &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Livello di compatibilità per i modelli tabulari in Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
