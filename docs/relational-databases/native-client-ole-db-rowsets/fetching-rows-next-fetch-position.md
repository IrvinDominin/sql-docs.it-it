---
title: Posizione del recupero successivo | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
ms.assetid: 9ef74b3f-c9c0-492f-9b93-d65738a61abd
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 6df5d3e025b16b58f105093ef64278d49f6daa78
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35694822"
---
# <a name="fetching-rows---next-fetch-position"></a>Recupero righe - posizione del recupero successiva
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider tiene traccia della posizione del recupero successivo in modo che una sequenza di chiamate per il **GetNextRows** metodo (senza salti, modifiche di direzione o intermedi le chiamate al  **FindNextRow**, **Seek**, oppure **esecuzione di RestartPosition** metodi) legge l'intero set di righe senza ignorare o ripetizione di una riga. Posizione del recupero successivo viene modificata chiamando **IRowset:: GetNextRows**, **IRowset:: RestartPosition**, o **IRowsetIndex:: Seek**, oppure chiamando **FindNextRow** con un valore null *pBookmark* valore. La chiamata **FindNextRow** con un valore diverso da null *pBookmark* valore non influisce sulla posizione del recupero successivo.  
  
## <a name="see-also"></a>Vedere anche  
 [Recupero di righe](../../relational-databases/native-client-ole-db-rowsets/fetching-rows.md)  
  
  
