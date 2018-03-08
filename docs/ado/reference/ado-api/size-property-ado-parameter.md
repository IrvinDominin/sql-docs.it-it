---
title: "Proprietà (parametro ADO) Size | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Parameter::Size
helpviewer_keywords:
- Size property [ADO Parameter]
ms.assetid: e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1959316966e284ab1f7880d6afcaa4820c009556
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="size-property-ado-parameter"></a>Proprietà Size (parametro ADO)
Indica la dimensione massima, in byte o caratteri, di un [parametro](../../../ado/reference/ado-api/parameter-object.md) oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **lungo** valore che indica le dimensioni massime in byte o caratteri di un valore in un **parametro** oggetto.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **dimensioni** proprietà per determinare le dimensioni massime per i valori scritti o leggere il [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà di un **parametro** oggetto.  
  
 Se si specifica un tipo di dati a lunghezza variabile per un **parametro** oggetto (ad esempio, qualsiasi **stringa** digitare, ad esempio **adVarChar**), è necessario impostare l'oggetto  **Dimensioni** proprietà prima di aggiungerlo al [parametri](../../../ado/reference/ado-api/parameters-collection-ado.md) raccolta; in caso contrario, si verifica un errore.  
  
 Se è già stato accodato la **parametro** dell'oggetto per il **parametri** raccolta di un [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto e si modifica il tipo a un tipo di dati a lunghezza variabile, è necessario impostare il **parametro** dell'oggetto **dimensioni** proprietà prima di eseguire il **comando** oggetto; in caso contrario, si verifica un errore.  
  
 Se si utilizza il [aggiornamento](../../../ado/reference/ado-api/refresh-method-ado.md) per ottenere informazioni sui parametri da e il provider restituisce uno o più tipi di dati a lunghezza variabile **parametro** gli oggetti ADO potrebbe allocare memoria per i parametri di base alle relative dimensioni massime possibili, che potrebbe causare un errore durante l'esecuzione. Per evitare un errore, è necessario impostare in modo esplicito il **dimensioni** proprietà per tali parametri prima di eseguire il comando.  
  
 Il **dimensioni** proprietà è di lettura/scrittura.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Parameter](../../../ado/reference/ado-api/parameter-object.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà direzione (VB), CommandText, CommandTimeout, CommandType, dimensioni e ActiveConnection](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Esempio di proprietà direzione (VC + +), CommandText, CommandTimeout, CommandType, dimensioni e ActiveConnection](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, dimensioni e direzione proprietà esempio (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Proprietà Size (flusso ADO)](../../../ado/reference/ado-api/size-property-ado-stream.md)
