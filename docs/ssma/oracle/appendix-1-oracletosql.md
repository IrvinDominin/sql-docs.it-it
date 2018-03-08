---
title: Appendice - 1 (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e01f8be5-ce68-4c9f-bd13-d65e73a16470
caps.latest.revision: "15"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 8e415cb8fddf1a2c37fa44f38ff23a2c5c64c568
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="appendix---1-oracletosql"></a>Appendice - 1 (OracleToSQL)
Anteprima della Console di SSMA opzioni riga di comando:  
  
|SL. No.|Opzione|Obbligatorio?|Passare l'argomento|Valori consentiti|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s/script|Sì|scriptfile|Nome del file XML valido.<br /><br />File di definizione di Script di console.|  
|2|variabile o - v|no|variablevaluefile|Nome del file XML valido.<br /><br />Se le variabili vengono utilizzate nel file di script, è necessario specificare questo file.|  
|3|-c/serverconnection|no|serverconnectionfile|Nome del file XML valido.<br /><br />Questo file contiene informazioni sulla connessione server.|  
|4|-x / xmloutput|no|xmloutputfile|Questa opzione indica l'output della console in formato XML. Se questa opzione non è specificata, l'output predefinito è in formato testo.<br /><br />Se xmloutputfile non viene specificato, l'output XML viene indirizzato alla `STDOUT`.<br /><br />Xmloutputfile è il nome del file in cui viene scritto l'output della console in formato XML.|  
|5|-l o di log|no|logfile|Nome file valido.|  
|6|e-/ projectenvironment|no|projectenvironmentfolder|Nome di cartella valido contenente i file dell'ambiente di progetto SSMA.|  
|7|-p/securepassword|no|-/ Aggiunge {< server_id > [,... n] &#124; tutti} – c &#124; serverconnection < file di connessione server > [-v &#124; variabile < variabile-valore-file >] [-o/sovrascrivere]<br /><br />o Gestione configurazione<br /><br />-/ Aggiunge {< server_id > [,... n] &#124; tutti} – s &#124; lo script < file di script > [-v &#124; variabile < variabile-valore-file >] [-o/sovrascrivere]<br /><br />– r/Rimuovi {< server_id > [,... n] &#124; tutti}<br /><br />-l/elenco<br /><br />e – / esportazione {< id-server > [,... n] &#124; tutti} < password crittografate - file ><br /><br />-i / importazione {< id-server > [,... n] &#124; tutti} < crittografati password-file >|Se specificato, è necessario non combinare questa opzione con le altre opzioni.<br /><br />ID del server: specificato un ID univoco per un server {stringa}<br /><br />file di connessione server: file di definizione del server (serverconnectionfile o scriptfile).<br /><br />file di variabile-valore: è un file di definizione della variabile e usato nel file di connessione server.<br /><br />file di password crittografata: è un file di password server crittografato con una specificata dall'utente-passphrase.|  
|8|-?|no|Non applicabile|Non applicabile|  
  
## <a name="see-also"></a>Vedere anche  
[L'esecuzione la Console SSMA (Oracle)](http://msdn.microsoft.com/en-us/7228ccba-c69f-4b4c-8664-01a2750183c5)  
  
