---
title: catalog.rename_environment (database SSISDB) | Microsoft Docs
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
ms.assetid: c73d7452-31c5-4f4e-afcc-e9eca760c826
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 07839e0dbe6e15d096cb56c655b71d7bc56086be
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="catalogrenameenvironment-ssisdb-database"></a>catalog.rename_environment (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Viene rinominato un ambiente nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
catalog.rename_environment [ @folder_name = ] folder_name  
    , [ @environment_name = ] environment_name  
    , [ @new_environment_name= ] new_environment_name  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @folder_name = ] *folder_name*  
 Nome della cartella in cui è contenuto l'ambiente. *folder_name* è di tipo **nvarchar(128)**.  
  
 [ @environment_name = ] *environment_name*  
 Nome originale dell'ambiente. *environment_name* è di tipo **nvarchar(128)**.  
  
 [ @new_environment_name = ] *new_environment_name*  
 Nuovo nome dell'ambiente. *new_environment_name* è di tipo **nvarchar(128)**.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 None  
  
## <a name="permissions"></a>Autorizzazioni  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni MODIFY sull'ambiente  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Nome originale dell'ambiente non valido  
  
-   Nome nuovo già utilizzato in un ambiente esistente  
  
## <a name="remarks"></a>Remarks  
 I riferimenti all'ambiente dai progetti non vengono aggiornati automaticamente quando si rinomina l'ambiente, pertanto è necessario aggiornarli di conseguenza. Questa stored procedure verrà completata anche se i riferimenti all'ambiente vengono interrotti modificando il nome dell'ambiente. I riferimenti all'ambiente devono essere aggiornati dopo il completamento di questa stored procedure.  
  
> [!NOTE]  
>  Quando un riferimento all'ambiente non è valido, la convalida e l'esecuzione dei pacchetti corrispondenti in cui vengono utilizzati tali riferimenti non verranno completate.  
  
  
