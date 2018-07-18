---
title: Append (metodo) (ADOX chiavi) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Keys::Append
- Keys::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 215a5391-f422-42ec-99ea-4e6fbb5d3d64
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9eaef312977613409453dfa1d876674d6b95c927
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35284820"
---
# <a name="append-method-adox-keys"></a>Append (metodo) (ADOX chiavi)
Aggiunge un nuovo [chiave](../../../ado/reference/adox-api/key-object-adox.md) dell'oggetto per il [chiavi](../../../ado/reference/adox-api/keys-collection-adox.md) insieme.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Keys.Append Key [,KeyType] [,Column] [,RelatedTable] [,RelatedColumn]  
```  
  
#### <a name="parameters"></a>Parametri  
 *Key*  
 Il **chiave** oggetto da accodare o il nome della chiave da creare e accodare.  
  
 *Elemento KeyType.*  
 Facoltativo. Oggetto **lungo** valore che specifica il tipo di chiave. Il *chiave* parametro corrisponde al [tipo](../../../ado/reference/adox-api/type-property-key-adox.md) proprietà di un **chiave** oggetto.  
  
 *Colonna*  
 Facoltativo. Oggetto **stringa** valore che specifica il nome della colonna da indicizzare. Il *colonne* parametro corrisponde al valore del [nome](../../../ado/reference/adox-api/name-property-adox.md) proprietà di un [colonna](../../../ado/reference/adox-api/column-object-adox.md) oggetto.  
  
 *RelatedTable*  
 Facoltativo. Oggetto **stringa** valore che specifica il nome della tabella correlata. Il *RelatedTable* parametro corrisponde al valore del **nome** proprietà di un [tabella](../../../ado/reference/adox-api/table-object-adox.md) oggetto.  
  
 *RelatedColumn*  
 Facoltativo. Oggetto **stringa** valore che specifica il nome della colonna correlata per una chiave esterna. Il *RelatedColumn* parametro corrisponde al valore del **nome** proprietà di un [colonna](../../../ado/reference/adox-api/column-object-adox.md) oggetto.  
  
## <a name="remarks"></a>Remarks  
 Il *colonne* parametro può accettare il nome di una colonna o una matrice di nomi di colonna.  
  
## <a name="applies-to"></a>Si applica a  
 [Raccolta di oggetti Key (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Chiavi Aggiungi metodo, tipo di chiave, RelatedColumn, RelatedTable e UpdateRule proprietà esempio (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Append (metodo) (ADOX colonne)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append (metodo) (ADOX gruppi)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append (metodo) (ADOX indici)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append (metodo) (ADOX procedure)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append (metodo) (ADOX tabelle)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append (metodo) (ADOX utenti)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Metodo Append (oggetti View ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
