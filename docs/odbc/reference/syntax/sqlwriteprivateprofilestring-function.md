---
title: Funzione SQLWritePrivateProfileString | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLWritePrivateProfileString
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLWritePrivateProfileString
helpviewer_keywords:
- SQLWritePrivateProfileString [ODBC]
ms.assetid: 526f36a4-92ed-4874-9725-82d27c0b86f9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aeff68aaa4e4901820054a9bf3079efc7d74cebc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818849"
---
# <a name="sqlwriteprivateprofilestring-function"></a>Funzione SQLWritePrivateProfileString
**Conformità**  
 Versione introdotta: ODBC 2.0  
  
 **Riepilogo**  
 **SQLWritePrivateProfileString** scrive un nome di valore e i dati per la sottochiave ODBC. ini delle informazioni di sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLWritePrivateProfileString(  
     LPCSTR     lpszSection,  
     LPCSTR     lpszEntry,  
     LPCSTR     lpszString,  
     LPCSTR     lpszFilename);  
```  
  
## <a name="arguments"></a>Argomenti  
 *lpszSection*  
 [Input] Punta a una stringa con terminazione null che contiene il nome della sezione in cui verrà copiata la stringa. Se la sezione non esiste, viene creato. Il nome della sezione è indipendente dal caso; la stringa può essere qualsiasi combinazione di lettere maiuscole e minuscole.  
  
 *lpszEntry*  
 [Input] Punta a una stringa con terminazione null che contiene il nome della chiave da associare a una stringa. Se la chiave non esiste nella sezione specificata, viene creato. Se questo argomento è NULL, l'intera sezione, incluse tutte le voci all'interno della sezione, viene eliminato.  
  
 *lpszString*  
 [Input] Punta a una stringa con terminazione null da scrivere nel file. Se questo argomento è NULL, la chiave a cui fa riferimento il *lpszEntry* argomento viene eliminato.  
  
 *lpszFilename*  
 [Output] Punta a una stringa con terminazione null che corrisponde al nome del file di inizializzazione.  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLWritePrivateProfileString** FALSO, restituisce un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* i valori che possono essere restituiti da **SQLInstallerError** e illustra ognuna nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_REQUEST_FAILED|Richiesta non è riuscita|Non è possibile scrivere le informazioni di sistema richiesta.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione non è stato possibile eseguire la funzione a causa della mancanza di memoria.|  
  
## <a name="comments"></a>Commenti  
 **SQLWritePrivateProfileString** viene fornito come un modo semplice per la porta driver e file DLL di installazione di driver di Microsoft® Windows® per Microsoft Windows/Windows 2000. Le chiamate a **WritePrivateProfileString** che scrivere una stringa di profilo nel file ini deve essere sostituita con chiamate al **SQLWritePrivateProfileString**. **SQLWritePrivateProfileString** chiama le funzioni nell'API Win32® per aggiungere il nome del valore specificato e i dati per la sottochiave ODBC. ini delle informazioni di sistema.  
  
 Una modalità di configurazione indica dove la voce ini Elenca i valori DSN è nelle informazioni di sistema. Se il DSN è un DSN utente (la variabile di stato è USERDSN_ONLY), la funzione scrive la voce ini in HKEY_CURRENT_USER. Se il DSN è un DSN di sistema (SYSTEMDSN_ONLY), la funzione scrive la voce ini in HKEY_LOCAL_MACHINE. Se la variabile di stato è BOTHDSN, viene eseguito un tentativo di HKEY_CURRENT_USER e, se ha esito negativo, HKEY_LOCAL_MACHINE viene usato.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Ottiene un valore di dalle informazioni di sistema|[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|
