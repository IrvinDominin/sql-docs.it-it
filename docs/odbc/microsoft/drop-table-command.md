---
title: Comando tabella DROP | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- drop table command [ODBC]
ms.assetid: bc50459b-8861-4889-84a9-129ae9065aa8
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bd9798d5394f4291b0ff77abba55cb7c780aa4f1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="drop-table-command"></a>TRASCINARE il comando di tabella
Rimuove una tabella dal database specificato con l'origine dati e la elimina dal disco.  
  
 Il Driver ODBC di Visual FoxPro supporta la sintassi del linguaggio Visual FoxPro native per questo comando. Per informazioni specifiche del driver, vedere la sezione Osservazioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP TABLE TableName | FileName | ?  
```  
  
## <a name="settings"></a>Impostazioni  
 *TableName*  
 Specifica la tabella da rimuovere dal database specificato con l'origine dati ed eliminare dal disco.  
  
 *FileName*  
 Specifica una tabella disponibile da eliminare dal disco.  
  
 ?  
 Consente di visualizzare la finestra di dialogo Rimuovi da cui è possibile scegliere una tabella per rimuovere dal database specificato con l'origine dati e per eliminare dal disco.  
  
## <a name="remarks"></a>Osservazioni  
 Quando viene eseguita l'istruzione DROP TABLE, vengono rimossi anche tutti indici primari, i valori predefiniti e regole di convalida associate alla tabella. DROP TABLE influisce inoltre su altre tabelle nel database specificato con l'origine dati, se tali tabelle disporre di regole o le relazioni associate alla tabella da rimuovere. Le regole e le relazioni non sono più valide quando la tabella verrà rimossa dal database.  
  
## <a name="driver-remarks"></a>Sezione Osservazioni di driver  
 Quando l'applicazione invia l'istruzione ODBC SQL DROP TABLE all'origine dati, il Driver ODBC di Visual FoxPro converte il comando al comando Visual FoxProDROP tabella utilizzando la sintassi illustrata nella tabella seguente.  
  
|Sintassi ODBC|Origine dati|Sintassi di Visual FoxPro|  
|-----------------|-----------------|--------------------------|  
|DROP TABLE *nome-tabella di base*|Database (file DBC)|Rimuovi tabella *TableName* eliminare|  
||Directory di tabelle disponibile (file con estensione dbf)|CANCELLARE *dbfName*<br /><br /> CANCELLARE *cdxName*<br /><br /> CANCELLARE *fptName*|
