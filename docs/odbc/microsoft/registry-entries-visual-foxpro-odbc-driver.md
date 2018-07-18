---
title: Le voci del Registro di sistema (Driver ODBC di Visual FoxPro) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- registry keys [ODBC]
- Visual FoxPro ODBC driver [ODBC], registry entries
- keys [ODBC]
- FoxPro ODBC driver [ODBC], registry entries
ms.assetid: 1a63d92d-ca3a-46ae-911f-6788292c801e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2a8a742aeb4f2290ef7f76410d689e15afec5c6d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32903526"
---
# <a name="registry-entries-visual-foxpro-odbc-driver"></a>Voci del Registro di sistema (Driver ODBC di Visual FoxPro)
Quando si installa il Driver ODBC di Visual FoxPro, il programma di installazione aggiorna il Registro di sistema nella chiave del Registro di sistema HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCInst.ini, per aggiungere una nuova chiave denominata driver per Microsoft Visual FoxPro. In tale chiave, vengono aggiunti i valori descritti nella tabella seguente.  
  
|Nome del valore|Tipo valore|Value|  
|----------------|----------------|-----------|  
|APILevel|REG_SZ|"1"|  
|ConnectFunctions|REG_SZ|"YYN"|  
|Driver|REG_SZ|Percorso di sistema per il file vfpodbc|  
|DriverODBCVer|REG_SZ|"02.50"|  
|FileExtns|REG_SZ|"*.dbf,\*.cdx,\*.fpt"|  
|FileUsage|REG_SZ|"1"|  
|Installazione|REG_SZ|Percorso di sistema per il file vfpodbc|  
|SQLLevel|REG_SZ|"0"|  
  
 Il programma di installazione aggiunge anche la chiave "Visual FoxPro Files", che rappresenta il driver di Visual FoxPro predefinito, alla chiave HKEY_CURRENT_USER\SOFTWARE\ODBC\Odbc.ini del sistema. In questa chiave, il programma di installazione aggiunge i valori descritti nella tabella seguente.  
  
|Nome del valore|Tipo valore|Value|  
|----------------|----------------|-----------|  
|Driver|REG_SZ|Percorso di sistema per il file vfpodbc|  
  
 Ogni volta che si aggiunge un'origine dati ODBC Visual FoxPro alla configurazione di ODBC, viene aggiunta una nuova chiave per tale nome origine dati. I valori per l'origine dati corrispondono ai valori impostati il **installazione ODBC Visual FoxPro** la finestra di dialogo, come indicato nella tabella seguente.  
  
|Nome del valore (parola chiave)|Tipo valore|Value|  
|----------------------------|----------------|-----------|  
|Fascicola|REG_SQ|Sequenza di confronto supportate|  
|Description|REG_SZ|Descrizione dell'origine dati utente|  
|Driver||Percorso di sistema per il file vfpodbc|  
|Exclusive||Sì o No|  
|BackgroundFetch||Sì o No|  
|SourceDB|REG_SZ|Percorso. File DBC|  
|SourceType|REG_SZ|"DBC" o "DBF"|  
  
 Non è necessario accedere direttamente; queste informazioni qualsiasi amministrazione del Registro di sistema viene gestita dall'amministratore ODBC quando si aggiungere, modificare o eliminare un'origine dati.  
  
 È possibile utilizzare alcune di queste parole chiave e i valori come parametri in di [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) funzione API ODBC.
