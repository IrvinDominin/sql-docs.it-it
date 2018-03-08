---
title: Append (metodo) (ADOX utenti) | Documenti Microsoft
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
- Users::raw_Append
- Users::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: b80bc5d5-78ca-4f75-956b-2ac658029cc7
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 00652a3051d817c779fd45f546228163c72656fd
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="append-method-adox-users"></a>Append (metodo) (ADOX utenti)
Aggiunge un nuovo [utente](../../../ado/reference/adox-api/user-object-adox.md) dell'oggetto per il [utenti](../../../ado/reference/adox-api/users-collection-adox.md) insieme.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Users.Append User[,Password]  
```  
  
#### <a name="parameters"></a>Parametri  
 *Utente*  
 Oggetto **Variant** valore contenente il **utente** oggetto da accodare o il nome dell'utente per creare e aggiungere.  
  
 *Password*  
 Facoltativa. Oggetto **stringa** valore contenente la password per l'utente. Il *Password* parametro corrisponde al valore specificato per il [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) metodo di un **utente** oggetto.  
  
## <a name="remarks"></a>Osservazioni  
 Il **utenti** raccolta di un [catalogo](../../../ado/reference/adox-api/catalog-object-adox.md) rappresenta gli utenti del catalogo. Il **utenti** raccolta per un [gruppo](../../../ado/reference/adox-api/group-object-adox.md) rappresenta solo gli utenti appartenenti al gruppo specifico.  
  
 Se il provider non supporta la creazione di utenti, si verificherà un errore.  
  
> [!NOTE]
>  Prima di accodare un **utente** dell'oggetto per il **utenti** raccolta di un **gruppo** oggetto, un **utente** oggetto con lo stesso [nome ](../../../ado/reference/adox-api/name-property-adox.md) dell'oggetto da aggiungere deve già esistere nel **utenti** insieme il **catalogo**.  
  
## <a name="applies-to"></a>Si applica a  
 [Raccolta di oggetti User (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Utenti e gruppi, ChangePassword metodi esempio Append (VB)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)   
 [Append (metodo) (ADOX colonne)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append (metodo) (ADOX gruppi)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append (metodo) (ADOX indici)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append (metodo) (ADOX chiavi)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append (metodo) (ADOX procedure)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append (metodo) (ADOX tabelle)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Metodo Append (oggetti View ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
