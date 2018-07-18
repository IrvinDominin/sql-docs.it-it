---
title: Append (metodo) (procedure ADOX) | Documenti Microsoft
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
apitype: COM
f1_keywords:
- Procedures::Append
- Procedures::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 38e3492c-c1e1-42e3-a71a-befdc90204db
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 83e3973bccfd0466ed7d912b4fc4d1c63b6da7a7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="append-method-adox-procedures"></a>Append (metodo) (ADOX procedure)
Aggiunge un nuovo [procedura](../../../ado/reference/adox-api/procedure-object-adox.md) dell'oggetto per il [procedure](../../../ado/reference/adox-api/procedures-collection-adox.md) insieme.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Procedures.Append Name, Command  
```  
  
#### <a name="parameters"></a>Parametri  
 *Nome*  
 Oggetto **stringa** valore che specifica il nome della procedura per creare e accodare.  
  
 *Command*  
 Un oggetto ADO [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto che rappresenta la procedura per creare e aggiungere.  
  
## <a name="remarks"></a>Osservazioni  
 Crea una nuova stored procedure nell'origine dati con il nome e gli attributi specificati nel **comando** oggetto.  
  
 Se il testo del comando specificato dall'utente rappresenta una vista piuttosto che una stored procedure, il comportamento è dipende dal provider in uso. **Aggiungere** avrà esito negativo se il provider non supporta i comandi di persistenza.  
  
> [!NOTE]
>  Quando si utilizza il Provider OLE DB per Microsoft Jet, la **procedure** raccolta **Append** metodo consente di specificare un **vista** piuttosto che un  **Procedura** nel *comando* parametro. Il **vista** verrà aggiunto all'origine dati e verrà aggiunto al **procedure** insieme. Dopo il **Append**, se il **procedure** e **viste** raccolte vengono aggiornate, il **visualizzazione** non sarà più possibile nel **Procedure** insieme e verranno visualizzati di **viste** insieme.  
  
## <a name="applies-to"></a>Si applica a  
 [Raccolta di oggetti Procedure (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure di esempio del metodo Append (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Append (metodo) (ADOX colonne)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append (metodo) (ADOX gruppi)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append (metodo) (ADOX indici)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append (metodo) (ADOX chiavi)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append (metodo) (ADOX tabelle)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append (metodo) (ADOX utenti)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Metodo Append (oggetti View ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
