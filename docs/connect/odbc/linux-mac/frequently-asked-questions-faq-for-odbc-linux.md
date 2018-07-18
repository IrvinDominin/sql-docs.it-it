---
title: Domande frequenti (FAQ) per Linux ODBC e macOS | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 65bfd6d2-c83d-4528-a5e1-a85b125a4f4a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 17d25f6084e136736dbc4c8a8ff3cb019ce4692e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="frequently-asked-questions-faq-for-odbc-linux-and-macos"></a>Domande frequenti (FAQ) per Linux ODBC e macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Di seguito sono risposte a domande riguardanti il Driver ODBC per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] su Linux e macOS.
  
## <a name="frequently-asked-questions"></a>Domande frequenti

**Come funzionano le applicazioni ODBC esistenti in Linux o macOS con il driver?**  
Dovrebbe essere possibile compilare ed eseguire le applicazioni ODBC la compilazione e in esecuzione in Linux o Mac OS con altri driver. 
  
**Le funzionalità di [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] questa versione del supporto del driver?**

Il driver ODBC in Linux e macOS supporta tutte le funzionalità server in [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] ad eccezione del database locale. Per ulteriori informazioni su [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] le funzionalità supportate, vedere [linee guida di programmazione](../../../connect/odbc/linux-mac/programming-guidelines.md).  
  
**Il driver supporta l'autenticazione Kerberos?**  
Sì. Se si dispone di un'impostazione dell'ambiente Kerberos esistente, deve essere in grado di connettersi ai server tramite il `Trusted_Connection=Yes` opzione della stringa di connessione o DSN. Per ulteriori informazioni, vedere [Using Integrated Authentication](../../../connect/odbc/linux-mac/using-integrated-authentication.md).  
  
**Quale codifica Unicode deve essere usata un'applicazione?**  
UTF-8 per i dati SQL_CHAR e UTF-16 per i dati SQL_WCHAR.  

**Sono disponibili esempi ODBC che è possibile scaricare ed eseguire con il driver per sperimentare o valutarlo?**

Per un esempio, vedere l'articolo relativo all' [uso di esempi ODBC C++ di MSDN per il driver ODBC in Linux](http://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) . Questo vale anche per il driver ODBC macOS. 

**È il driver ODBC in Linux o open source di macOS?**

No, il driver ODBC in Linux e macOS non sono un prodotto open source.  

## <a name="see-also"></a>Vedere anche
[L'installazione di Microsoft ODBC Driver for SQL Server in Linux e macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
