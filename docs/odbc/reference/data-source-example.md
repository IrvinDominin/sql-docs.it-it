---
title: Esempio di origine dati | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], examples
ms.assetid: cbf15f32-0550-4c74-8088-8f7ac3855469
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2162e6eb6add9e710ac9bf7d0adc36a87e5d2b43
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="data-source-example"></a>Esempio di origine dati
Nei computer che eseguono Microsoft® Windows NT® Server e Windows 2000 Server, Microsoft Windows NT Workstation/Windows 2000 Professional o Microsoft Windows® 95/98, dati del computer, informazioni di origine vengono archiviate nel Registro di sistema. A seconda del Registro di sistema chiave vengono archiviate le informazioni in, l'origine dati è noto come un *origine dati utente* o *origine dati di sistema*. Le origini dati utente vengono archiviate nella chiave HKEY_CURRENT_USER e sono disponibili solo per l'utente corrente. Origini dati di sistema vengono archiviate nella chiave HKEY_LOCAL_MACHINE e possono essere utilizzate da più di un utente in un unico computer. Possono inoltre essere utilizzati dai servizi a livello di sistema, che possono accedere all'origine dati anche se nessun utente è connesso al computer. Per ulteriori informazioni sull'utente e origini dati di sistema, vedere [SQLManageDataSources](../../odbc/reference/syntax/sqlmanagedatasources.md).  
  
 Si supponga che un utente dispone di tre origini di dati utente: personale e l'inventario, che utilizzano un DBMS Oracle; e retribuzioni, che utilizza un sistema DBMS di Microsoft SQL Server. I valori del Registro di sistema per le origini dati potrebbero essere:  
  
```  
HKEY_CURRENT_USER  
SOFTWARE  
          ODBC  
               Odbc.ini  
                    ODBC Data Sources  
                    Personnel : REG_SZ : Oracle  
                    Inventory : REG_SZ : Oracle  
                    Payroll : REG_SZ : SQL Server  
```  
  
 e i valori del Registro di sistema per l'origine di dati del libro paga potrebbero essere:  
  
```  
HKEY_CURRENT_USER  
     SOFTWARE  
          ODBC  
               Odbc.ini  
                    Payroll  
                         Driver : REG_SZ : C:\WINDOWS\SYSTEM\Sqlsrvr.dll  
                         Description : REG_SZ : Payroll database  
                         Server : REG_SZ : PYRLL1  
                         FastConnectOption : REG_SZ : No                          UseProcForPrepare : REG_SZ : Yes  
                         OEMTOANSI : REG_SZ : No  
                         LastUser : REG_SZ : smithjo  
                         Database : REG_SZ : Payroll  
                         Language : REG_SZ :  
```
