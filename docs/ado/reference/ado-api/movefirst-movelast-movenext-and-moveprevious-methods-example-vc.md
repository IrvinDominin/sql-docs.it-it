---
title: Spostare il puntatore del Record di esempio di Recordset (VC + +) | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MoveLast method [ADO], VC++ example
- MoveNext method [ADO], VC++ example
- MovePrevious method [ADO], VC++ example
- MoveFirst method [ADO], VC++ example
ms.assetid: 7f8aea7b-9183-4b29-8ac0-a393ed2e8bd5
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b1456959d265b260969b0f0e7e9754338ed2b773
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="movefirst-movelast-movenext-and-moveprevious-methods-example-vc"></a>MoveFirst, MoveLast, MoveNext e MovePrevious metodi esempio (VC + +)
Questo esempio viene utilizzato il [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), e [MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) metodi per spostare il puntatore del record di un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) in base al comando specificato. La funzione MoveAny è necessaria per eseguire questo esempio.  
  
## <a name="example"></a>Esempio  
  
```  
// MoveFirstMoveLastMoveNextSample.cpp  
// compile with: /EHsc  
#include <ole2.h>  
#include <stdio.h>  
  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
// Function declarations  
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };  
void MoveFirstX();  
void MoveAny(int intChoice, _RecordsetPtr pRstTemp);  
void PrintProviderError(_ConnectionPtr pConnection);  
void PrintComError(_com_error &e);  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL)) )  
      return -1;  
  
   MoveFirstX();  
   ::CoUninitialize();  
}  
  
void MoveFirstX() {  
   HRESULT hr = S_OK;  
   _RecordsetPtr pRstAuthors = NULL;  
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");  
   _bstr_t strMessage("UPDATE Titles SET Type = "  
      "'psychology' WHERE Type = 'self_help'");  
   int intCommand = 0;  
  
   // Temporary string variable for type conversion for printing.  
   _bstr_t  bstrFName;  
   _bstr_t  bstrLName;  
  
   try {  
      // Open recordset from Authors table.  
      TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset)));  
      pRstAuthors->CursorType = adOpenStatic;  
  
      // Use client cursor to enable AbsolutePosition property.  
      pRstAuthors->CursorLocation = adUseClient;  
      pRstAuthors->Open("Authors", strCnn, adOpenStatic, adLockBatchOptimistic, adCmdTable);  
  
      // Show current record information and get user's method choice.  
      while (true) {   // Continuous loop.  
         // Convert variant string to convertable string type.  
         bstrFName = pRstAuthors->Fields->Item["au_fName"]->Value;  
         bstrLName = pRstAuthors->Fields->Item["au_lName"]->Value;  
  
         printf("Name: %s %s\n Record %d of %d\n\n",  
            (LPCSTR) bstrFName,  
            (LPCSTR) bstrLName,  
            pRstAuthors->AbsolutePosition,  
            pRstAuthors->RecordCount);  
         printf("[1 - MoveFirst, 2 - MoveLast, \n");  
         printf(" 3 - MoveNext, 4 - MovePrevious, 5 - Quit]\n");  
  
         scanf_s("%d", &intCommand);  
  
         if ((intCommand < 1) || (intCommand > 4))  
            break;   // Out of range entry exits program loop.  
  
         // Call method based on user's input.  
         MoveAny(intCommand, pRstAuthors);  
      }  
   }  
   catch (_com_error &e) {  
      // Notify the user of errors if any.  
      // Pass a connection pointer accessed from the Recordset.  
      _variant_t vtConnect = pRstAuthors->GetActiveConnection();  
  
      // GetActiveConnection returns connect string if connection  
      // is not open, else returns Connection object.  
      switch(vtConnect.vt) {  
         case VT_BSTR:  
            PrintComError(e);  
            break;  
         case VT_DISPATCH:  
            PrintProviderError(vtConnect);  
            break;  
         default:  
            printf("Errors occured.");  
            break;  
      }  
   }  
  
   // Clean up objects before exit.  
   if (pRstAuthors)  
      if (pRstAuthors->State == adStateOpen)  
         pRstAuthors->Close();  
}  
  
void MoveAny(int intChoice, _RecordsetPtr pRstTemp) {  
   // Use specified method, trapping for BOF and EOF  
   try {  
      switch(intChoice) {  
         case 1:  
            pRstTemp->MoveFirst();  
            break;  
         case 2:  
            pRstTemp->MoveLast();  
            break;  
         case 3:  
            pRstTemp->MoveNext();  
            if (pRstTemp->EndOfFile) {  
               printf("\nAlready at end of recordset!\n");  
               pRstTemp->MoveLast();  
            }    // End If  
            break;  
         case 4:  
            pRstTemp->MovePrevious();  
            if (pRstTemp->BOF) {  
               printf("\nAlready at beginning of recordset!\n");  
               pRstTemp->MoveFirst();  
            }  
            break;  
         default:  
            ;  
      }  
   }  
  
   catch(_com_error &e) {  
      // Notify the user of errors if any.  
      // Pass a connection pointer accessed from the Recordset.  
      _variant_t vtConnect = pRstTemp->GetActiveConnection();  
  
      // GetActiveConnection returns connect string if connection  
      // is not open, else returns Connection object.  
      switch(vtConnect.vt)  {  
         case VT_BSTR:  
            PrintComError(e);  
            break;  
         case VT_DISPATCH:  
            PrintProviderError(vtConnect);  
            break;  
         default:  
            printf("Errors occured.");  
            break;  
      }  
   }  
}  
  
void PrintProviderError(_ConnectionPtr pConnection) {  
   // Print Provider Errors from Connection object.  
  
   // pErr is a record object in the Connection's Error collection.  
   ErrorPtr pErr = NULL;  
  
   if ( (pConnection->Errors->Count) > 0) {  
      long nCount = pConnection->Errors->Count;  
      // Collection ranges from 0 to nCount - 1.  
      for ( long i = 0 ; i < nCount ; i++) {  
         pErr = pConnection->Errors->GetItem(i);  
         printf("\t Error number: %x\t%s", pErr->Number, pErr->Description);  
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
  
 Input  
  
```  
5  
```  
  
## <a name="see-also"></a>Vedere anche  
 [MoveFirst, MoveLast, MoveNext e MovePrevious metodi (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
