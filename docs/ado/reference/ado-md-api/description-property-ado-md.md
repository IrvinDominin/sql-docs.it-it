---
title: "Proprietà Description (ADO MD) | Documenti Microsoft"
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
- Member::Description
- Level::Description
- CubeDef::Description
- Hierarchy::Description
- Description
- Dimension::Description
helpviewer_keywords:
- Description property [ADO MD]
ms.assetid: 6d626d35-0bf3-4f24-9934-ad9c9c91273a
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0f3052ab5b0ad05c1a792ff348e77ea0b32c7484
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="description-property-ado-md"></a>Proprietà Description (ADO MD)
Restituisce una descrizione di testo dell'oggetto corrente.  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce un **stringa** ed è di sola lettura.  
  
## <a name="remarks"></a>Osservazioni  
 Per [membro](../../../ado/reference/ado-md-api/member-object-ado-md.md) oggetti, **descrizione** si applica solo ai membri di misure e formule. **Descrizione** restituisce una stringa vuota ("") per tutti gli altri tipi di membri. Per ulteriori informazioni sui vari tipi di membri, vedere il [tipo](../../../ado/reference/ado-md-api/type-property-ado-md.md) proprietà.  
  
 Questa proprietà è supportata solo su **membro** gli oggetti che appartengono a un [livello](../../../ado/reference/ado-md-api/level-object-ado-md.md) oggetto. Si verifica un errore quando questa proprietà viene fatto riferimento dal **membro** oggetti appartenenti a un [posizione](../../../ado/reference/ado-md-api/position-object-ado-md.md) oggetto.  
  
## <a name="applies-to"></a>Si applica a  
  
||||  
|-|-|-|  
|[Oggetto CubeDef (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|[Oggetto Dimension (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|[Oggetto Hierarchy (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|  
|[Oggetto Level (ADO MD)](../../../ado/reference/ado-md-api/level-object-ado-md.md)|[Oggetto Member (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)||
