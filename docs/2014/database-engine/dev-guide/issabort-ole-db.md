---
title: ISSAbort (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- ISSAbort interface
ms.assetid: 7c4df482-4a83-4da0-802b-3637b507693a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a4b3e43dca5a18a991733492eeeffc4f49d14ef8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48181241"
---
# <a name="issabort-ole-db"></a>ISSAbort (OLE DB)
  Il **ISSAbort** interfaccia, esposta nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client, fornisce il [issabort:: Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md) metodo che viene utilizzato per annullare il set di righe corrente oltre a qualsiasi comando in batch con il comando che ha inizialmente generato il set di righe e non ha ancora completato l'esecuzione.  
  
 **ISSAbort** è un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interfaccia di specifica del provider Native Client disponibile mediante **QueryInterface** sul **IMultipleResults** oggetto restituito da  **ICommand:: Execute** oppure **IOpenRowset:: OPENROWSET**.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Metodo|Description|  
|------------|-----------------|  
|[Issabort:: Abort &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)|Annulla il set di righe corrente oltre a qualsiasi comando eseguito in batch associato al comando corrente.|  
  
## <a name="see-also"></a>Vedere anche  
 [Le interfacce &#40;OLE DB&#41;](../../../2014/database-engine/dev-guide/interfaces-ole-db.md)  
  
  
