---
title: Generare uno schema XDR inline | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XDR schemas [SQL Server]
- inline XDR schema generation [SQL Server]
- XMLDATA option
- FOR XML clause, inline XDR schema generation
ms.assetid: 2a40d617-9724-4f7d-80a4-a85c702f14d0
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8d0c7e9c46b4b5ad42192cc4d524e2170a968620
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48088851"
---
# <a name="generate-an-inline-xdr-schema"></a>Generazione di uno schema XDR inline
  La direttiva **XMLDATA** in FOR XML restituisce uno schema XDR inline insieme al risultato della query. Lo schema XDR tuttavia non supporta tutti i nuovi tipi di dati e i miglioramenti introdotti in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. In alternativa, è possibile richiedere uno schema XSD inline usando [la direttiva XMLSCHEMA](generate-an-inline-xsd-schema.md).  
  
> [!IMPORTANT]  
>  La direttiva XMLDATA all'opzione FOR XML è deprecata. Utilizzare la generazione XSD in caso di modalità RAW e AUTO. Non sono disponibili sostituzioni per direttiva XMLDATA in modalità EXPLICIT. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Per il supporto dello schema XDR inline, notare inoltre quanto segue:  
  
-   Se il risultato della query FOR XML include colonne di tipo **xml** e viene richiesto uno schema XDR inline, sarà generato un errore. Gli schemi XDR inline non supportano infatti questi tipi.  
  
-   Verrà eseguito il mapping dei tipi **(n)varchar(max)** e **(n)varbinary(max)** rispettivamente a **(n)varchar(n)** e **varbinary(n)**.  
  
-   Se la modalità di compatibilità è impostata su 90 o superiore, i valori **timestamp** vengono considerati come dati **varbinary(8)** , trattati come dati binari e restituiti nel risultato nel modo seguente:  
  
    -   Se si specifica **binary base64** , viene usata la codifica Base64.  
  
    -   Se non si specifica **binary base64** , viene usata la codifica URL in modalità AUTO.  
  
  
