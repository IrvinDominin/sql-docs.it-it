---
title: catalog.validate_package (database SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
helpviewer_keywords:
- validate_package stored procedure [Integration Services]
- catalog.validate_package stored procedure [Integration Services]
ms.assetid: 0dc03df1-b793-408f-af4c-c11188729abf
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 06fa7266cf88cacae049df1c9bf98a2979e3fa0a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47766489"
---
# <a name="catalogvalidatepackage-ssisdb-database"></a>catalog.validate_package (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Viene convalidato in modo asincrono un pacchetto nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```sql
catalog.validate_package [ @folder_name = ] folder_name  
    , [ @project_name = ] project_name  
    , [ @package_name = ] package_name  
    , [ @validation_id = ] validation_id OUTPUT  
 [  , [ @use32bitruntime = ] use32bitruntime ]  
 [  , [ @target_environment = ] target_environment ]  
 [  , [ @reference_id = ] reference_id ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @folder_name = ] *folder_name*  
 Nella della cartella in cui è contenuto il pacchetto. *folder_name* è di tipo **nvarchar(128)**.  
  
 [ @project_name = ] *project_name*  
 Nome del progetto in cui è contenuto il pacchetto. *project_name* è di tipo **nvarchar(128)**.  
  
 [ @package_name = ] *package_name*  
 Nome del pacchetto. *package_name* è di tipo **nvarchar(260)**.  
  
 [ @validation_id = ] *validation_id*  
 Viene restituito l'identificatore (ID) univoco della convalida. *validation_id* è di tipo **bigint**.  
  
 [ @use32bitruntime = ] *use32bitruntime*  
 Viene indicato se il runtime a 32 bit deve essere utilizzato per eseguire il pacchetto in un sistema operativo a 64 bit. Usare il valore `1` per eseguire il pacchetto con il runtime a 32 bit quando in esecuzione in un sistema operativo a 64 bit. Utilizzare il valore pari a `0` per eseguire il pacchetto con il runtime a 64 bit quando in esecuzione in un sistema operativo a 64 bit. Questo parametro è facoltativo. *use32bitruntime* è di tipo **bit**.  
  
 [ @environment_scope = ] *environment_scope*  
 Vengono indicati i riferimenti all'ambiente considerati dalla convalida. Quando il valore è `A`, tutti i riferimenti all'ambiente associati al progetto sono inclusi nella convalida. Quando il valore è `S`, è incluso solo un singolo riferimento all'ambiente. Quando il valore è `D`, non è incluso alcun riferimento all'ambiente e ogni parametro deve disporre di un valore predefinito letterale per passare la convalida. Questo parametro è facoltativo. Per impostazione predefinita, viene usato il carattere `D`. *environment_scope* è di tipo **Char(1)**.  
  
 [ @reference_id = ] *reference_id*  
 ID univoco del riferimento all'ambiente. Questo parametro è richiesto solo quando un singolo riferimento all'ambiente è incluso nella convalida, quando *environment_scope* è di tipo `S`. *reference_id* è di tipo **bigint**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 None  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ sul progetto e, se applicabile, autorizzazioni READ su ambienti a cui si fa riferimento  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Nome del progetto o del pacchetto non valido  
  
-   Utente senza autorizzazioni appropriate.  
  
-   Uno o più ambienti utilizzati come riferimento inclusi nella convalida in cui non sono contenute variabili di riferimento  
  
-   Convalida del pacchetto non completata  
  
-   Ambiente a cui viene fatto riferimento non disponibile  
  
-   Impossibile trovare variabili utilizzate come riferimento negli ambienti a cui viene fatto riferimento inclusi nella convalida  
  
-   Riferimento alla variabili effettuato nei parametri del pacchetto, ma nessuna inclusione di ambienti di riferimento nella convalida.  
  
## <a name="remarks"></a>Remarks  
 La convalida consente di identificare i problemi che possono impedire la corretta esecuzione del pacchetto. Usare la vista [catalog.validations](../../integration-services/system-views/catalog-validations-ssisdb-database.md) o [catalog.operations](../../integration-services/system-views/catalog-operations-ssisdb-database.md) per monitorare lo stato della convalida.  
  
  
