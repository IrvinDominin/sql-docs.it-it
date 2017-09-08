---
title: DROP ASSEMBLY (Transact-SQL) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 05/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP ASSEMBLY
- DROP_ASSEMBLY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- removing assemblies
- DROP ASSEMBLY statement
- deleting assemblies
- assemblies [CLR integration], removing
- dropping assemblies
- WITH NO DEPENDENTS option
ms.assetid: 452d181a-a8e6-44a3-975d-29966d01b18d
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c38654a3ce90b4e1605cfdbe1db7a49ddac8b6b1
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-assembly-transact-sql"></a>DROP ASSEMBLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove un assembly e tutti i relativi file associati dal database corrente. Gli assembly vengono creati utilizzando [CREATE ASSEMBLY](../../t-sql/statements/create-assembly-transact-sql.md) e modificati tramite [ALTER ASSEMBLY](../../t-sql/statements/alter-assembly-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
DROP ASSEMBLY [ IF EXISTS ] assembly_name [ ,...n ]  
[ WITH NO DEPENDENTS ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *SE ESISTE*  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Elimina in modo condizionale l'assembly solo se esiste già.  
  
 *nome_assembly*  
 Nome dell'assembly da eliminare.  
  
 WITH NO DEPENDENTS  
 Se specificato, Elimina solo *nome_assembly* e nessuno degli assembly dipendenti che fanno riferimento all'assembly. Se omesso, DROP ASSEMBLY Elimina *nome_assembly* e tutti gli assembly dipendenti.  
  
## <a name="remarks"></a>Osservazioni  
 L'eliminazione di un assembly comporta la rimozione di un assembly e di tutti i relativi file associati, ad esempio file del codice sorgente o di debug, dal database.  
  
 Se WITH NO DEPENDENTS viene omesso, DROP ASSEMBLY Elimina *nome_assembly* e tutti gli assembly dipendenti. Se il tentativo di eliminare gli assembly dipendenti ha esito negativo, DROP ASSEMBLY restituisce un errore.  
  
 DROP ASSEMBLY restituisce un errore se all'assembly viene fatto riferimento da un altro assembly esistente nel database oppure se viene utilizzato da funzioni CLR (Common Language Runtime), procedure, trigger, tipi definiti dall'utente o funzioni di aggregazione nel database corrente.  
  
 DROP ASSEMBLY non interferisce con il codice che fa riferimento all'assembly in esecuzione. Tuttavia, dopo l'esecuzione di DROP ASSEMBLY qualsiasi tentativo di richiamare l'assembly avrà esito negativo.  
  
## <a name="permissions"></a>Permissions  
 È necessario essere il proprietario dell'assembly oppure è richiesta l'autorizzazione CONTROL per l'assembly.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente si presuppone che l'assembly `HelloWorld` sia già stato creato nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
DROP ASSEMBLY Helloworld ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREAZIONE di ASSEMBLY &#40; Transact-SQL &#41;](../../t-sql/statements/create-assembly-transact-sql.md)   
 [ALTER ASSEMBLY &#40; Transact-SQL &#41;](../../t-sql/statements/alter-assembly-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [Recupero di informazioni sugli assembly](../../relational-databases/clr-integration/assemblies-getting-information.md)  
  
  
