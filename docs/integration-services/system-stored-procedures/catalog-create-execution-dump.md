---
title: catalog.create_execution_dump | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 91319b0b-5536-4ab4-a403-9559ed9dd177
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f13a1c0730b01280896b8c759aa401cf10ba875c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="catalogcreateexecutiondump"></a>catalog.create_execution_dump
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Comporta la sospensione di un pacchetto in esecuzione e la creazione di un file di dump. Il file viene archiviato nella cartella *\<unità>*:\Programmi\Microsoft SQL Server\130\Shared\ErrorDumps.  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
catalog.create_execution_dump [ @execution_id = ] execution_id  
  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @execution_id = ] *execution_id*  
 ID di esecuzione del pacchetto in esecuzione. *execution_id* è di tipo **bigint**.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene richiesta la creazione di un file di dump per il pacchetto in esecuzione con ID esecuzione 88.  
  
```sql
EXEC create_execution_dump @execution_id = 88  
```  
  
## <a name="return-codes"></a>Codici restituiti  
 0 (esito positivo)  
  
 Quando la stored procedure ha esito negativo viene generato un errore.  
  
## <a name="result-set"></a>Set di risultati  
 None  
  
## <a name="permissions"></a>Autorizzazioni  
 Per questa stored procedure è necessario che gli utenti siano membri del ruolo del database **ssis_admin**.  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte le condizioni che causano la mancata riuscita della stored procedure.  
  
-   È stato specificato un ID esecuzione non valido.  
  
-   Il pacchetto è già stato completato.  
  
-   È in corso la creazione di un file di dump nel pacchetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Generazione di file di dump per l'esecuzione dei pacchetti](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)  
  
  
