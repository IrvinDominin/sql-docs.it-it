---
title: Aggiungere utenti e gruppi, esempio di metodi ChangePassword (VC + +) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ChangePassword method [ADOX], VC++ example
- Groups Append method [ADOX], VC++ example
- Append method [ADOX], VC++ example
- Users Append method [ADOX], VC++ example
ms.assetid: 7e7067d0-6405-4c09-bff3-b1c2f2d783e0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d3f0929cc55fcf529e14ec17912f0a474f6e2257
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47659341"
---
# <a name="groups-and-users-append-changepassword-methods-example-vc"></a>Esempio dei metodi Append di Groups e Users e del metodo ChangePassword (VC++)
Questo esempio viene illustrato il [Append](../../../ado/reference/adox-api/append-method-adox-groups.md) metodo di [gruppi](../../../ado/reference/adox-api/groups-collection-adox.md), così come il [Append](../../../ado/reference/adox-api/append-method-adox-users.md) metodo [utenti](../../../ado/reference/adox-api/users-collection-adox.md) aggiungendo un nuovo [Gruppo](../../../ado/reference/adox-api/group-object-adox.md) e un nuovo [utente](../../../ado/reference/adox-api/user-object-adox.md) al sistema. Il nuovo **gruppo** viene aggiunto al **gruppi** raccolta del nuovo **utente**. Di conseguenza, il nuovo **utente** viene aggiunto per il **gruppo**. Inoltre, il [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) metodo viene utilizzato per specificare le **utente** password.  
  
> [!NOTE]
>  Se ci si connette a un provider dell'origine dati che supporta l'autenticazione di Windows, è necessario specificare **Trusted_Connection = yes** oppure **Integrated Security = SSPI** anziché un ID utente e password informazioni nella stringa di connessione.  
  
```  
// BeginGroupCpp.cpp  
// compile with: /EHsc  
#import "msadox.dll" no_namespace  
  
#include "iostream"  
using namespace std;  
  
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};  
  
int main() {  
   if (FAILED(::CoInitialize(NULL)) )  
      return -1;  
  
   HRESULT hr = S_OK;  
  
   // Define and initialize ADOX object pointers. These are in ADODB namespace.  
   _CatalogPtr m_pCatalog = NULL;  
   _UserPtr m_pUserNew = NULL;  
   _UserPtr m_pUser = NULL;  
   _GroupPtr m_pGroup = NULL;  
  
   // Define String Variables.  
   _bstr_t strCnn("Provider='Microsoft.JET.OLEDB.4.0';Data source = 'c:\\Northwind.mdb';jet oledb:system database='c:\\system.mdw'");  
  
   try {  
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof (Catalog)));  
      m_pCatalog->PutActiveConnection(strCnn);  
  
      // Create and append new group with a string.  
      m_pCatalog->Groups->Append("Accounting");  
  
      // Create and append new user with an object.  
      TESTHR(hr = m_pUserNew.CreateInstance(__uuidof(User)));  
      m_pUserNew->PutName("Pat Smith");  
      m_pUserNew->ChangePassword("", "Password1");  
      m_pCatalog->Users->Append(_variant_t((IDispatch *)m_pUserNew), "");  
  
      // Make the user Pat Smith a member of the Accounting group by creating and adding the  
      // appropriate Group object to the user's Groups collection. The same is accomplished if a User  
      // object representing Pat Smith is created and appended to the Accounting group Users collection  
      m_pUserNew->Groups->Append("Accounting");  
  
      // Enumerate all User objects in the catalog's Users collection.  
      long lUsrIndex;  
      long lGrpIndex;  
      _variant_t vIndex;  
      for ( lUsrIndex = 0 ; lUsrIndex < m_pCatalog->Users->Count ; lUsrIndex++ ) {  
         vIndex = lUsrIndex;  
         m_pUser = m_pCatalog->Users->GetItem(vIndex);  
         cout << "  " << m_pUser->Name << endl;  
         cout << "   Belongs to these groups:" << endl;  
  
         // Enumerate all Group objects in each User object's Groups collection.  
         if (m_pUser->Groups->Count != 0)  
            for ( lGrpIndex = 0 ; lGrpIndex < m_pUser->Groups->Count ; lGrpIndex++ ) {  
               vIndex = lGrpIndex;  
               m_pGroup = m_pUser->Groups->GetItem(vIndex);  
               cout << "     " << m_pGroup->Name << endl;  
            }  
         else  
            cout << "       [None]" << endl;  
      }  
  
      // Enumerate all Group objects in the default workspace's Groups collection.  
      for ( lGrpIndex = 0 ; lGrpIndex < m_pCatalog->Groups->Count ; lGrpIndex++ ) {  
         vIndex = lGrpIndex;  
         m_pGroup = m_pCatalog->Groups->GetItem(vIndex);  
         cout << "   " << m_pGroup->Name << endl;  
         cout << "    Has as its members:" << endl;  
  
         // Enumerate all User objects in each Group object's Users Collection.  
         if ( m_pGroup->Users->Count != 0)  
            for ( lUsrIndex = 0 ; lUsrIndex < m_pGroup->Users->Count ; lUsrIndex++ ) {  
               vIndex = lUsrIndex;  
               m_pUser = m_pGroup->Users->GetItem(vIndex);  
               cout << "    " << m_pUser->Name << endl;  
            }  
         else  
            cout << "      [None]" << endl;  
      }  
  
      // Delete new User and Group object because this is only a demonstration.  
      m_pCatalog->Users->Delete("Pat Smith");  
      m_pCatalog->Groups->Delete("Accounting");  
   }  
   catch(_com_error &e) {  
      // Notify the user of errors if any.  
      _bstr_t bstrSource(e.Source());  
      _bstr_t bstrDescription(e.Description());  
  
      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);  
   }  
   catch(...) {  
      cout << "Error occured in include files...." << endl;  
   }  
  
   ::CoUninitialize();  
}  
```
