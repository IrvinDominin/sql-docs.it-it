---
title: "Supporto dello spazio dei nomi in modalità di PATH | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PATH FOR XML mode, namespace support
- namespaces [XML in SQL Server]
ms.assetid: 5f128ea2-0ceb-4b23-bce7-c8b3fd615466
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cc700d8b31d9348ca3411a6d399671dfde965b20
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="namespace-support-in-path-mode"></a>Supporto dello spazio dei nomi in modalità di PATH
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
In questa versione, il supporto dello spazio dei nomi in modalità PATH è disponibile utilizzando WITH NAMESPACES. Ad esempio, nella query seguente viene illustrata la sintassi WITH NAMESPACES per la dichiarazione di uno spazio dei nomi ("a:") che è possibile utilizzare nell'istruzione SELECT successiva:  
  
```  
WITH XMLNAMESPACES('a' as a)  
SELECT 1 as 'a:b'  
FOR XML PATH  
```  
  
## <a name="examples"></a>Esempi  
 In questi esempi viene illustrato l'utilizzo della modalità PATH nella generazione di codice XML da una query SELECT. Molte di queste query vengono specificate sui documenti XML di istruzioni per la produzione di biciclette archiviate nella colonna Instructions della tabella ProductModel.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzare la modalità PATH con FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
