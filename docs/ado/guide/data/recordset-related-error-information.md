---
title: Informazioni sugli errori Recordset | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset-related errors [ADO]
- errors [ADO], Recordset-related
ms.assetid: 7e103574-59ad-4790-b5f9-fa8d715e711e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2dab1996d2915757ba6e7834b5e41bd6eade41c6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="recordset-related-error-information"></a>Informazioni sugli errori di recordset
Durante l'elaborazione batch, il **stato** proprietà del **Recordset** oggetto fornisce informazioni relative ai singoli record nel **Recordset**. Prima di un aggiornamento in blocco, il **stato** proprietà del **Recordset** riflette le informazioni sui record aggiunti, modificati ed eliminati. Dopo aver **UpdateBatch** è stato chiamato, il **stato** proprietà indica l'esito positivo o negativo dell'operazione. Quando si sposta da un record a altro **Recordset**, il valore della **stato** le modifiche alle proprietà per descrivere lo stato del record corrente.
