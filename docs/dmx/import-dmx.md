---
title: IMPORTAZIONE (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4987701deb466148253c8418c88683d2dbfbc16b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38061025"
---
# <a name="import-dmx"></a>IMPORT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Carica nel server un modello o una struttura di data mining da un file con estensione abf (Analysis Services Backup File).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IMPORT FROM <filename>  
```  
  
## <a name="arguments"></a>Argomenti  
 *nome del file*  
 Stringa contenente il nome e il percorso del file da importare.  
  
## <a name="remarks"></a>Note  
 Se non è specificato alcun oggetto, verrà caricato tutto il contenuto del file con estensione dmb. Se il file con estensione dmb include un database che non esiste sul server, il database verrà creato.  
  
 Per esportare o importare oggetti è necessario essere un amministratore del server o del database.  
  
## <a name="import-from-file-example"></a>Esempio di importazione da file  
 Nell'esempio seguente viene importato nel server corrente l'intero contenuto del file contenente la struttura e il modello di associazione.  
  
```  
IMPORT FROM 'C:\TEMP\Association_NEW.dmb'  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Le estensioni di Data Mining di dati &#40;DMX&#41; istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)   
 [Le estensioni di Data Mining di dati &#40;DMX&#41; istruzioni di manipolazione dei dati](../dmx/dmx-statements-data-manipulation.md)   
 [Le estensioni di Data Mining di dati &#40;DMX&#41; riferimento alle istruzioni](../dmx/data-mining-extensions-dmx-statements.md)   
 [ESPORTARE &AMP;#40;DMX&AMP;#41;](../dmx/export-dmx.md)   
 [Esportare e importare gli oggetti di data mining](../analysis-services/data-mining/export-and-import-data-mining-objects.md)  
  
  
