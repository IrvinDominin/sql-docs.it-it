---
title: "Esempio di proprietà di oggetti errore (VC + +) | Documenti Microsoft"
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
- Number property [ADO], VC++ example
- HelpContext property [ADO], VC++ example
- NativeError property [ADO], VC++ example
- SQLState property [ADO], VC++ example
- Source property [ADO], VC++ example
- HelpFile property [ADO], VC++ example
- Description property [ADO], VC++ example
ms.assetid: 5321fc0f-cd0c-4e2a-a5bc-0008fba86b59
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3533027fc963e5f509a7db14dd22caeec9d4499a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="description-helpcontext-helpfile-nativeerror-number-source-and-sqlstate-properties-example-vc"></a>Esempio di proprietà SQLState (VC + +), HelpContext, HelpFile, NativeError, numero, origine e descrizione
In questo esempio genera un errore intercettato e visualizza il [descrizione](../../../ado/reference/ado-api/description-property.md), [HelpContext](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md), [HelpFile](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md), [NativeError](../../../ado/reference/ado-api/nativeerror-property-ado.md), [ Numero](../../../ado/reference/ado-api/number-property-ado.md), [origine](../../../ado/reference/ado-api/source-property-ado-error.md), e [SQLState](../../../ado/reference/ado-api/sqlstate-property.md) le proprietà dell'oggetto risultante [errore](../../../ado/reference/ado-api/error-object.md) oggetto.  
  
```  
// BeginDescriptionCpp.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
// Function declarations  
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};  
void DescriptionX();  
void PrintProviderError(_ConnectionPtr pConnection);  
void PrintComError(_com_error &e);  
  
int main() {  
   if (FAILED(::CoInitialize(NULL)))  
      return -1;  
  
   DescriptionX();  
   ::CoUninitialize();  
}  
  
void DescriptionX() {  
   // Define ADO object pointers. Initialize pointers on define. These are in the ADODB::  namespace  
   _ConnectionPtr pConnection = NULL;  
   ErrorPtr errorLoop = NULL;  
  
   // Define Other Variables  
   HRESULT hr = S_OK;  
  
   try {  
      // Intentionally trigger an error.  open connection  
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));  
  
      if (FAILED(hr = pConnection->Open("Nothing", "", "", adConnectUnspecified))) {  
         _com_issue_error(hr);  
         exit(1);  
      }  
  
      // Cleanup object before exit.  
      pConnection->Close();  
   }  
   catch(_com_error) {  
      // Pass a connection pointer.  
      PrintProviderError(pConnection);  
   }  
}  
  
void PrintProviderError(_ConnectionPtr pConnection) {  
   // Define Other Variables  
   HRESULT hr = S_OK;  
   _bstr_t strError;  
   ErrorPtr pErr = NULL;  
  
   try {  
      // Enumerate Errors collection and display properties of each Error object.  
      long nCount = pConnection->Errors->Count;  
  
      // Collection ranges from 0 to nCount - 1.  
      for ( long i = 0 ; i < nCount ; i++ ) {  
         pErr = pConnection->Errors->GetItem(i);  
         printf("Error #%d\n", pErr->Number);  
         printf(" %s\n", (LPCSTR)pErr->Description);  
         printf(" (Source: %s)\n", (LPCSTR)pErr->Source);  
         printf(" (SQL State: %s)\n", (LPCSTR)pErr->SQLState);  
         printf(" (NativeError: %d)\n", (LPCSTR)pErr->NativeError);  
  
         if ((LPCSTR)pErr->GetHelpFile() == NULL)  
            printf("\tNo Help file available\n");  
         else {  
            printf("\t(HelpFile: %s\n)" ,pErr->HelpFile);  
            printf("\t(HelpContext: %s\n)" , pErr->HelpContext);  
         }  
      }  
   }  
  
   catch(_com_error &e) {  
      // Notify the user of errors if any.  
      PrintComError(e);  
   }  
}  
  
void PrintComError(_com_error &e) {  
   // Notify the user of errors if any.  
   _bstr_t bstrSource(e.Source());  
   _bstr_t bstrDescription(e.Description());  
  
   // Print Com errors.  
   printf("Error\n");  
   printf("\tCode = %08lx\n", e.Error());  
   printf("\tCode meaning = %s", e.ErrorMessage());  
   printf("\tSource = %s\n", (LPCSTR) bstrSource);  
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà Description](../../../ado/reference/ado-api/description-property.md)   
 [Oggetto Error](../../../ado/reference/ado-api/error-object.md)   
 [Proprietà HelpContext, HelpFile](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Proprietà HelpContext, HelpFile](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Proprietà NativeError (ADO)](../../../ado/reference/ado-api/nativeerror-property-ado.md)   
 [Proprietà Number (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Proprietà Source (errore ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)   
 [Proprietà SQLState](../../../ado/reference/ado-api/sqlstate-property.md)
