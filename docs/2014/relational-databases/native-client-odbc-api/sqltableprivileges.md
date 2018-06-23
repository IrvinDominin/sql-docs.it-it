---
title: SQLTablePrivileges | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLTablePrivileges function
ms.assetid: 8cce22d5-28b1-4b50-a5bc-1de03e0ffd6b
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1b0459196645627dddcde96442742e2b6f02fd4c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054750"
---
# <a name="sqltableprivileges"></a>SQLTablePrivileges
  **SQLTablePrivileges** può essere eseguito su un cursore statico. Un tentativo di eseguire **SQLTablePrivileges** su un cursore aggiornabile (dinamico o basati su keyset) restituirà SQL_SUCCESS_WITH_INFO che indica il tipo di cursore è stato modificato.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client supporta la segnalazione di informazioni relative alle tabelle sui server collegati mediante l'accettazione di un nome composto da due parti per il *CatalogName* parametro: *linked_server_name*.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLTablePrivileges] (http://go.microsoft.com/fwlink/?LinkId=59373\)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  