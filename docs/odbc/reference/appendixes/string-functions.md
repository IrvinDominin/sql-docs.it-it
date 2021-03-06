---
title: Funzioni stringa | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], string functions
- string functions [ODBC]
ms.assetid: 270f669e-8aab-4db0-95a4-f2b3c69538b3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0eeccf4e9c972592f8efecb622fc71f4f3c87a0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47720059"
---
# <a name="string-functions"></a>Funzioni per i valori stringa
La tabella seguente elenca le funzioni di manipolazione di stringa. Un'applicazione può determinare quali funzioni di stringa sono supportate da un driver chiamando **SQLGetInfo** con un *tipo di informazioni* di SQL_STRING_FUNCTIONS.  
  
## <a name="remarks"></a>Note  
 Gli argomenti indicati come *string_exp* può essere il nome di una colonna, una *valore letterale stringa di caratteri*, o il risultato di un'altra funzione scalare, dove il tipo di dati sottostante può essere rappresentato come SQL_CHAR, SQL _ VARCHAR o SQL_LONGVARCHAR.  
  
 Gli argomenti indicati come *character_exp* sono una stringa di caratteri a lunghezza variabile.  
  
 Gli argomenti indicati come *avviare*, *lunghezza*, o *count* può essere un *letterali numerici* o il risultato di un'altra funzione scalare, dove la tipo di dati sottostante può essere rappresentato come SQL_TINYINT, SQL_SMALLINT o SQL_INTEGER.  
  
 Le funzioni di stringa elencate di seguito sono basati su 1; vale a dire il primo carattere nella stringa è 1 carattere.  
  
 Le funzioni scalari stringa BIT_LENGTH CHAR_LENGTH, CHARACTER_LENGTH, funzione OCTET_LENGTH e posizione sono state aggiunte nella versione 3.0 di ODBC per la compatibilità con SQL-92.  
  
|Funzione|Description|  
|--------------|-----------------|  
|**ASCII (** *string_exp* **)** (1.0 ODBC)|Restituisce il codice ASCII del carattere più a sinistra della *string_exp* come integer.|  
|**Funzione BIT_LENGTH (** *string_exp* **)** (ODBC 3.0)|Restituisce la lunghezza in bit dell'espressione stringa.<br /><br /> Funziona solo per i tipi di dati stringa, pertanto verrà non implicitamente convert *string_exp* in una stringa ma restituisce le dimensioni di qualsiasi tipo di dati viene fornito (interna).|  
|**CHAR (** *codice* **)** (1.0 ODBC)|Restituisce il carattere dotato di ASCII di codice del valore specificato da *codice*. Il valore di *codice* deve essere compreso tra 0 e 255; in caso contrario, il valore restituito è dipende dall'origine dati.|  
|**CHAR_LENGTH (** *string_exp* **)** (ODBC 3.0)|Restituisce la lunghezza in caratteri dell'espressione stringa, se l'espressione di stringa è di un tipo di dati carattere. in caso contrario, restituisce la lunghezza in byte dell'espressione stringa (l'intero più piccolo non inferiore al numero di bit diviso per 8). (Questa funzione è lo stesso della funzione CHARACTER_LENGTH).|  
|**CHARACTER_LENGTH (** *string_exp* **)** (ODBC 3.0)|Restituisce la lunghezza in caratteri dell'espressione stringa, se l'espressione di stringa è di un tipo di dati carattere. in caso contrario, restituisce la lunghezza in byte dell'espressione stringa (l'intero più piccolo non inferiore al numero di bit diviso per 8). (Questa funzione è lo stesso della funzione CHAR_LENGTH).|  
|**CONCAT (** *string_exp1*,*string_exp2 e * * *)** (ODBC 1.0)|Restituisce una stringa di caratteri che rappresenta il risultato della concatenazione *string_exp2 e* al *string_exp1*. La stringa risultante dipende da DBMS. Ad esempio, se la colonna rappresentata dal *string_exp1* contiene un valore NULL, DB2, viene restituito NULL ma SQL Server restituisce la stringa non NULL.|  
|**DIFFERENZA (** *string_exp1*,*string_exp2 e * * *)** (ODBC 2.0)|Restituisce un valore integer che indica la differenza tra i valori restituiti dalla funzione SOUNDEX per *string_exp1* e *string_exp2 e*.|  
|**INSERT (** *string_exp1*, *start*, *lunghezza*, *string_exp2 e * * *)** (1.0 ODBC)|Restituisce il carattere stringa where *lunghezza* caratteri sono stati eliminati dal *string_exp1*, a partire da *avviare*e in cui *string_exp2 e* è stato inserito *string_exp,* iniziando *start*.|  
|**LCASE (** *string_exp* **)** (1.0 ODBC)|Restituisce una stringa uguale a quello in *string_exp*, con tutte le lettere convertite in caratteri minuscoli.|  
|**A sinistra (** *string_exp*, *count * * *)** (1.0 ODBC)|Restituisce il più a sinistra *conteggio* caratteri di *string_exp*.|  
|**LUNGHEZZA (** *string_exp* **)** (1.0 ODBC)|Restituisce il numero di caratteri *string_exp,* esclusi gli spazi vuoti finali.<br /><br /> **LUNGHEZZA** accetta solo le stringhe. Di conseguenza in modo implicito convertirà *string_exp* per una stringa e restituire la lunghezza di questa stringa (non le dimensioni interne del tipo di dati).|  
|**INDIVIDUARE (** *string_exp1*, *string_exp2 e*[, *avviare*]**)** (1.0 ODBC)|Restituisce la posizione iniziale della prima occorrenza di *string_exp1* entro *string_exp2 e*. La ricerca per la prima occorrenza di *string_exp1* inizia con la posizione del primo carattere nella *string_exp2 e* , a meno che l'argomento facoltativo *avviare*, viene specificato. Se *avviare* è specificato, la ricerca inizia con la posizione del carattere indicata dal valore di *avviare*. Posizione del primo carattere *string_exp2 e* è indicato dal valore 1. Se *string_exp1* non viene trovato all'interno *string_exp2 e*, viene restituito il valore 0.<br /><br /> Se un'applicazione può chiamare la funzione scalare di individuazione con il *string_exp1*, *string_exp2 e*, e *avviare* argomenti, il driver restituisce SQL_FN_STR_LOCATE quando  **SQLGetInfo** viene chiamato con un *opzione* di SQL_STRING_FUNCTIONS. Se l'applicazione può chiamare la funzione scalare INDIVIDUA solo con il *string_exp1* e *string_exp2 e* argomenti, il driver restituisce SQL_FN_STR_LOCATE_2 quando **SQLGetInfo**viene chiamato con un *opzione* di SQL_STRING_FUNCTIONS. I driver che supportano la chiamata alla funzione di individuazione con due o tre argomenti restituiscono SQL_FN_STR_LOCATE sia SQL_FN_STR_LOCATE_2.|  
|**LTRIM (** *string_exp* **)** (1.0 ODBC)|Restituisce i caratteri di *string_exp*, rimuoverli gli spazi vuoti iniziali.|  
|**Funzione OCTET_LENGTH (** *string_exp* **)** (ODBC 3.0)|Restituisce la lunghezza in byte dell'espressione stringa. Il risultato è il più piccolo numero integer non inferiore al numero di bit diviso per 8.<br /><br /> Funziona solo per i tipi di dati stringa, pertanto verrà non implicitamente convert *string_exp* in una stringa ma restituisce le dimensioni di qualsiasi tipo di dati viene fornito (interna).|  
|**POSIZIONE (** *character_exp* **India** *character_exp * * *)** (ODBC 3.0)|Restituisce la posizione della prima espressione di caratteri nella seconda espressione di caratteri. Il risultato è un valore numerico esatto con scala 0 e una precisione definita dall'implementazione.|  
|**Ripetere i (** *string_exp,* *count * * *)** (1.0 ODBC)|Restituisce una stringa di caratteri costituita *string_exp* ripetuto *conteggio* volte.|  
|**SOSTITUIRE (** *string_exp1*, *string_exp2 e*, *string_exp3 * * *)** (ODBC 1.0)|Ricerca *string_exp1* foroccurrences dei *string_exp2 e*e sostituire con *string_exp3*.|  
|**RIGHT (** *string_exp*, *count * * *)** (1.0 ODBC)|Restituisce il più a destra *conteggio* caratteri di *string_exp*.|  
|**RTRIM (** *string_exp* **)** (1.0 ODBC)|Restituisce i caratteri di *string_exp* rimossi gli spazi vuoti finali.|  
|**SOUNDEX (** *string_exp* **)** (ODBC 2.0)|Restituisce una stringa di caratteri dipende dall'origine dati che rappresenta il suono delle parole nei *string_exp*. Ad esempio, SQL Server restituisce un codice SOUNDEX di 4 cifre; Oracle restituisce una rappresentazione fonetica di ogni parola.|  
|**Lo spazio (** *conteggio* **)** (ODBC 2.0)|Restituisce una stringa di caratteri costituito *conteggio* spazi.|  
|**SUBSTRING (** *string_exp*, *start*, lunghezza **)** (1.0 ODBC)|Restituisce una stringa di caratteri che è derivata da *string_exp*, iniziando in corrispondenza della posizione di carattere specificata da *avviare* per *lunghezza* caratteri.|  
|**UCASE (** *string_exp* **)** (1.0 ODBC)|Restituisce una stringa uguale a quello in *string_exp*, con tutte le lettere minuscole caratteri convertiti in caratteri maiuscoli.|
