---
title: Domande frequenti per ODBC in Linux e macOS | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 65bfd6d2-c83d-4528-a5e1-a85b125a4f4a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 99b92271060cbe670b48058e988b104aa296474b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47731529"
---
# <a name="frequently-asked-questions-faq-for-odbc-linux-and-macos"></a>Domande frequenti per ODBC in Linux e macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Di seguito sono riportate le risposte a domande riguardanti il driver ODBC per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in Linux e macOS.
  
## <a name="frequently-asked-questions"></a>Domande frequenti

**Come funzionano le applicazioni ODBC esistenti in Linux o macOS con il driver?**  
Dovrebbe essere possibile compilare ed eseguire le applicazioni ODBC compilate ed eseguite in Linux o macOS con altri driver. 
  
**Quali funzionalità di [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] supporta questa versione del driver?**

Il driver ODBC in Linux e macOS supporta tutte le funzionalità server di [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ad eccezione del database locale. Per altre informazioni sulle funzionalità di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supportate, vedere [Linee guida per la programmazione](../../../connect/odbc/linux-mac/programming-guidelines.md).  
  
**Il driver supporta l'autenticazione Kerberos?**  
Sì. Se si dispone di una configurazione dell'ambiente Kerberos esistente, deve essere in grado di connettersi ai server tramite il `Trusted_Connection=Yes` opzione della stringa di connessione o DSN. Per altre informazioni, vedere [Uso dell'autenticazione integrata](../../../connect/odbc/linux-mac/using-integrated-authentication.md).  
  
**Quale codifica Unicode deve essere usata dall'applicazione?**  
UTF-8 per i dati SQL_CHAR e UTF-16 per i dati SQL_WCHAR.  

**Sono disponibili esempi ODBC che è possibile scaricare ed eseguire con il driver per provarlo o valutarlo?**

Per un esempio, vedere l'articolo relativo all' [uso di esempi ODBC C++ di MSDN per il driver ODBC in Linux](http://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) . Questo vale anche per il driver ODBC di macOS. 

**È il driver ODBC in Linux o macOS aprire origine?**

No, non i driver ODBC in Linux e macOS sono un prodotto open source.  

## <a name="see-also"></a>Vedere anche
[Installazione di Microsoft ODBC Driver for SQL Server in Linux e macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
