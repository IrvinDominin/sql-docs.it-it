---
title: Append (metodo) (ADOX chiavi) | Documenti Microsoft
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
- Keys::Append
- Keys::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 215a5391-f422-42ec-99ea-4e6fbb5d3d64
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8d1f8938adf51ee1f38de29b85753095d55d7703
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
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
  
 *KeyType*  
 Facoltativa. Oggetto **lungo** valore che specifica il tipo di chiave. Il *chiave* parametro corrisponde al [tipo](../../../ado/reference/adox-api/type-property-key-adox.md) proprietà di un **chiave** oggetto.  
  
 *Colonna*  
 Facoltativa. Oggetto **stringa** valore che specifica il nome della colonna da indicizzare. Il *colonne* parametro corrisponde al valore del [nome](../../../ado/reference/adox-api/name-property-adox.md) proprietà di un [colonna](../../../ado/reference/adox-api/column-object-adox.md) oggetto.  
  
 *RelatedTable*  
 Facoltativa. Oggetto **stringa** valore che specifica il nome della tabella correlata. Il *RelatedTable* parametro corrisponde al valore del **nome** proprietà di un [tabella](../../../ado/reference/adox-api/table-object-adox.md) oggetto.  
  
 *RelatedColumn*  
 Facoltativa. Oggetto **stringa** valore che specifica il nome della colonna correlata per una chiave esterna. Il *RelatedColumn* parametro corrisponde al valore del **nome** proprietà di un [colonna](../../../ado/reference/adox-api/column-object-adox.md) oggetto.  
  
## <a name="remarks"></a>Osservazioni  
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
