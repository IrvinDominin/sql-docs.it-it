---
title: "Esempio di proprietà StayInSync (VC + +) | Documenti Microsoft"
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
dev_langs:
- C++
helpviewer_keywords:
- StayInSync property [ADO], VC++ example
ms.assetid: 3a5db5f0-094b-46e1-939b-d9fa9417a406
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b668da2e9a4c2104d8b4e7c31091d7eeddf9d244
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="stayinsync-property-example-vc"></a>Esempio di proprietà StayInSync (VC + +)
Questo esempio viene illustrato come la [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md) proprietà semplifica l'accesso alle righe in un modello gerarchico [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 Il ciclo esterno viene visualizzato il nome e cognome, stato e identificazione di ogni autore. L'oggetto aggiunto **Recordset** per ogni riga viene recuperato dal [campi](../../../ado/reference/ado-api/fields-collection-ado.md) insieme e assegnata automaticamente agli **rstTitleAuthor** dal **StayInSync**  proprietà ogni volta che l'elemento padre **Recordset** passa a una nuova riga. Il ciclo interno visualizza quattro campi da ogni riga del Recordset accodato.  
  
```  
// BeginStayInSyncCpp.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
#include <ole2.h>  
#include <stdio.h>  
#include <conio.h>  
  
// Function declarations  
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };  
void StayInSyncX();  
void PrintProviderError(_ConnectionPtr pConnection);  
void PrintComError(_com_error &e);  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL)) )  
      return -1 ;  
  
   StayInSyncX();  
   ::CoUninitialize();  
}  
  
void StayInSyncX() {  
   HRESULT  hr = S_OK;  
  
   // Define string variables.  
   _bstr_t strCnn("Provider='MSDataShape'; Data Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");  
  
   // Define ADO object pointers.  Initialize pointers on define.  
   // These are in the ADODB::  namespace.  
   _ConnectionPtr pConnection = NULL;  
   _RecordsetPtr pRst = NULL;  
   _RecordsetPtr pRstTitleAuthor = NULL;  
  
   try {  
      TESTHR(pRstTitleAuthor.CreateInstance(__uuidof(Recordset)));  
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));  
      TESTHR(pRst.CreateInstance(__uuidof(Recordset)));  
  
      // Open connection.  
      pConnection->Open (strCnn, "", "", adConnectUnspecified);  
      pRst->PutStayInSync(true);  
  
      // Open recordset with names from Author & titleauthor table.  
      pRst->Open("SHAPE  {select * from authors} "   
         "APPEND ({select * from titleauthor}"  
         "RELATE au_id TO au_id) AS chapTitleAuthor",  
         _variant_t((IDispatch*)pConnection, true), adOpenStatic, adLockReadOnly, adCmdText);  
  
      pRstTitleAuthor = pRst->GetFields()->GetItem("chapTitleAuthor")->Value;  
      while (!(pRst->EndOfFile)) {      
         printf("\n%s  %s  %s    %s\n", (LPCSTR)(_bstr_t)pRst->  
            Fields->GetItem("au_fname")->Value,  
            (LPCSTR)(_bstr_t)pRst->Fields->GetItem("au_lname")->Value,  
            (LPCSTR)(_bstr_t)pRst->Fields->GetItem("state")->Value,   
            (LPCSTR)(_bstr_t)pRst->Fields->GetItem("au_id")->Value);  
  
         _variant_t vIndex;  
         while ( !(pRstTitleAuthor->EndOfFile) ) {  
            vIndex = (short) 0;  
            printf("%s    ",(LPCSTR)(_bstr_t)pRstTitleAuthor->Fields->Item[&vIndex]->Value);  
            vIndex = (short) 1;  
            printf("%s    ",(LPCSTR)(_bstr_t)pRstTitleAuthor->Fields->Item[&vIndex]->Value);  
            vIndex = (short) 2;  
            printf("%s    ",(LPCSTR)(_bstr_t)pRstTitleAuthor->Fields->Item[&vIndex]->Value);  
            vIndex = (short) 3;  
            printf("%s\n",(LPCSTR)(_bstr_t)pRstTitleAuthor->Fields->Item[&vIndex]->Value);  
  
            pRstTitleAuthor->MoveNext();  
         }  
         pRst->MoveNext();  
      }  
   }  
   catch(_com_error &e) {  
      // Notify user of errors, if any.  Pass connection pointer accessed from the Recordset.  
      PrintProviderError(pConnection);  
      PrintComError(e);     
   }  
  
   // Clean up objects before exit.  
   if (pRst)  
      if (pRst->State == adStateOpen)  
         pRst->Close();  
   if (pConnection)  
      if (pConnection->State == adStateOpen)  
         pConnection->Close();  
}  
  
void PrintProviderError(_ConnectionPtr pConnection) {  
   // Print Provider Errors from Connection object.  
   // pErr is a record object in the Connection's Error collection.  
   ErrorPtr pErr = NULL;  
  
   if ( (pConnection->Errors->Count) > 0) {  
      long nCount = pConnection->Errors->Count;  
      // Collection ranges from 0 to nCount -1.  
      for ( long i = 0 ; i < nCount ; i++ ) {  
         pErr = pConnection->Errors->GetItem(i);  
         printf("Error number: %x\t%s\n", pErr->Number, (LPCSTR) pErr->Description);  
      }  
   }  
}  
  
void PrintComError(_com_error &e) {  
   _bstr_t bstrSource(e.Source());  
   _bstr_t bstrDescription(e.Description());  
  
   // Print Com errors.    
   printf("Error\n");  
   printf("\tCode = %08lx\n", e.Error());  
   printf("\tCode meaning = %s\n", e.ErrorMessage());  
   printf("\tSource = %s\n", (LPCSTR) bstrSource);  
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta di campi (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Proprietà StayInSync](../../../ado/reference/ado-api/stayinsync-property.md)
