---
title: La parola chiave NEW, la funzione di calcolo e funzioni di aggregazione | Documenti Microsoft
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
helpviewer_keywords:
- data shaping [ADO], functions
- CALC function [ADO]
- NEW keyword [ADO]
- aggregate functions [ADO]
ms.assetid: 0590b466-2a36-49a2-868e-028ef5e49394
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c3b7e33486bc8a5cc283a101893aec4287062c2f
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="aggregate-functions-the-calc-function-and-the-new-keyword"></a>Funzioni di aggregazione, la funzione di calcolo e la parola chiave NEW
Il data shaping supporta le funzioni seguenti. Il nome assegnato al capitolo contenente la colonna da utilizzare è il *alias capitolo*.  
  
 Un alias di capitolo può essere completo, costituito da ogni nome di colonna per il capitolo contenente il *-nome della colonna,* tutti separati da punti. Se, ad esempio, il capitolo padre Cap1 contiene un capitolo figlio Cap2, che include una colonna amount, amt, quindi il nome completo sarebbe chap1.chap2.amt.  
  
|Funzioni di aggregazione|Description|  
|-------------------------|-----------------|  
|SUM (*alias capitolo*. *nome della colonna*)|Calcola la somma di tutti i valori nella colonna specificata.|  
|AVG (*alias capitolo*. *nome della colonna*)|Calcola la media di tutti i valori nella colonna specificata.|  
|MAX (*alias capitolo*. *nome della colonna*)|Calcola il valore massimo nella colonna specificata.|  
|MIN (*alias capitolo*. *nome della colonna*)|Calcola il valore minimo nella colonna specificata.|  
|CONTEGGIO (*alias capitolo*[. *nome della colonna*])|Conta il numero di righe nell'alias specificato. Se viene specificata una colonna, solo le righe per cui tale colonna è non Null sono inclusi nel conteggio.|  
|STDEV(*chapter-alias*.*column-name*)|Calcola la deviazione standard della colonna specificata.|  
|QUALSIASI (*alias capitolo*. *nome della colonna*)|Valore della colonna specificata. UNO contiene un valore stimabile solo quando il valore della colonna è uguale per tutte le righe nel capitolo.<br /><br /> **Nota** se la colonna non contiene lo stesso valore per tutte le righe nel capitolo, il comando forma arbitrariamente restituisce uno dei valori per il valore della funzione qualsiasi.|  
  
|Espressione calcolata|Description|  
|---------------------------|-----------------|  
|CALC (*espressione*)|Calcola un'espressione arbitraria, ma solo per la riga del **Recordset** contenente la funzione di calcolo. Qualsiasi espressione che utilizza queste [Visual Basic, Applications Edition (VBA) funzioni](../../../ado/guide/data/visual-basic-for-applications-functions.md) è consentita.|  
  
|NUOVA parola chiave|Description|  
|-----------------|-----------------|  
|NUOVO *-tipo di campo* [(*larghezza* &#124; *scala* &#124; *precisione* &#124; *errore* [, *scala* &#124; *errore*])]|Aggiunge una colonna vuota per il tipo specificato di **Recordset**.|  
  
 Il *-tipo di campo* passato con la parola chiave NEW può essere uno dei seguenti tipi di dati.  
  
|Tipi di dati OLE DB|Equivalenti di tipi di dati ADO|  
|-----------------------|-----------------------------------|  
|DBTYPE_BSTR|adBSTR|  
|DBTYPE_BOOL|adBoolean|  
|DBTYPE_DECIMAL|adDecimal|  
|DBTYPE_UI1|adUnsignedTinyInt|  
|DBTYPE_I1|adTinyInt|  
|DBTYPE_UI2|adUnsignedSmallInt|  
|DBTYPE_UI4|adUnsignedInt|  
|DBTYPE_I8|adBigInt|  
|DBTYPE_UI8|adUnsignedBigInt|  
|DBTYPE_GUID|adGuid|  
|DBTYPE_BYTES|adLongVarBinary adBinary, AdVarBinary,|  
|DBTYPE_STR|adChar, adVarChar, adLongVarChar|  
|DBTYPE_WSTR|adWChar, adVarWChar, adLongVarWChar|  
|DBTYPE_NUMERIC|adNumeric|  
|DBTYPE_DBDATE|adDBDate|  
|DBTYPE_DBTIME|adDBTime|  
|DBTYPE_DBTIMESTAMP|adDBTimeStamp|  
|DBTYPE_VARNUMERIC|adVarNumeric|  
|DBTYPE_FILETIME|adFileTime|  
|DBTYPE_ERROR|adError|  
  
 Quando il nuovo campo è di tipo decimal (in OLE DB DBTYPE_DECIMAL, o adDecimal in ADO), è necessario specificare i valori di precisione e scala.  
  
## <a name="see-also"></a>Vedere anche  
 [Data Shaping di esempio](../../../ado/guide/data/data-shaping-example.md)   
 [Grammatica formale forma](../../../ado/guide/data/formal-shape-grammar.md)   
 [Comandi Shape in generale](../../../ado/guide/data/shape-commands-in-general.md)
