---
title: Wrapper di classe Java ADO | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 02/15/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class wrappers [ADO]
ms.assetid: 1fc09dc1-9e32-412e-9f43-b8eb8bb483ca
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b48b4753bd7ad94b1f8b8f17a6b3c5a211dbb740
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="ado-java-class-wrappers"></a>Wrapper di classe Java ADO
Questo codice dichiara un'istanza di ADO [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) wrapper della classe e la inizializza, tutte nella stessa riga di codice. Inoltre, vengono dichiarate le variabili per ognuno degli argomenti nel [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md) (metodo), in particolare per [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) e [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) (perché non supporta il linguaggio enumerato tipi). Apre e chiude il **Recordset** oggetto. L'impostazione di gruppi di risultati 1 su NULL semplicemente pianifica tale variabile deve essere rilasciato quando Java esegue il relativo rilascio sistematico e intermittente di oggetti inutilizzati.  
  
```  
public static void main( String args[])  
{  
   msado15._Recordset   Rs1 = new msado15.Recordset();  
   Variant Source     = new Variant( "SELECT * FROM Authors" );  
   Variant Connect    = new Variant( "DSN=AdoDemo;UID=admin;PWD=;" );  
   int     LockType   = msado15.CursorTypeEnum.adOpenForwardOnly;  
   int     CursorType = msado15.LockTypeEnum.adLockReadOnly;  
   int     Options    = -1;  
  
   Rs1.Open( Source, Connect, LockType,  CursorType, Options );  
   Rs1.Close();  
   Rs1 = null;  
  
   System.out.println( "Success!\n" );  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di Microsoft SDK per Java](../../../ado/guide/appendixes/using-the-microsoft-sdk-for-java.md)
