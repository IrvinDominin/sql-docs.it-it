---
title: I componenti di SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], components
- components [SQL Server Native Client]
- SQLNCLI, about SQL Server Native Client
ms.assetid: 65f932d5-daa1-4eff-b6df-ee633fcf2a7c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 329ffa78471ead02b1431a41d898cfc43ca65684
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48141041"
---
# <a name="components-of-sql-server-native-client"></a>Componenti di SQL Server Native Client
  In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client sono inclusi i componenti seguenti:  
  
|Componente|Description|  
|---------------|-----------------|  
|sqlncli11.dll|File della libreria di collegamento dinamico (DLL) che contiene tutte le funzionalità di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Sono inclusi il provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client e il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|sqlnclir11.rll|File di risorse associato per la libreria di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|s10ch_sqlncli.chm|File della Guida della Creazione guidata origine dati in cui viene illustrato come creare un'origine dati [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzando il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client o il provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|sqlncli.h|File di intestazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client che contiene tutte le nuove definizioni necessarie per utilizzare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Questo file di intestazione sostituisce entrambi i file di intestazione, odbcss.h e sqloledb.h. **Nota:** è possibile fare riferimento a SQLNCLI. h e Odbcss. h nello stesso programma, ma è possibile fare riferimento a SQLNCLI. h e SQLOLEDB. h nello stesso programma, purché venga definito prima SQLOLEDB. h.|  
|sqlncli11.lib|Il file di libreria necessario per chiamare direttamente le **bcp** le funzioni di utilità che fanno parte di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client. **Nota:** se si fa riferimento al file sqlncli11.lib nel codice di programmazione, è necessario assicurarsi che il file sqlncli11.dll si sia nel percorso di sistema e nel percorso di sistema di utenti che utilizzano l'applicazione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni con SQL Server Native Client](building-applications-with-sql-server-native-client.md)  
  
  
