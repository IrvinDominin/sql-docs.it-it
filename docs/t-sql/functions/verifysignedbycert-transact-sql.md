---
title: VERIFYSIGNEDBYCERT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VERIFYSIGNEDBYCERT
- VERIFYSIGNEDBYCERT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- digitally signed data for changes [SQL Server]
- verifying digitally signed data for changes
- testing digitally signed data for changes
- checking digitally signed data for changes
- VERIFYSIGNEDBYCERT
- signatures [SQL Server]
- digital signatures [SQL Server]
ms.assetid: 4e041f33-60c4-4190-91c7-220d51dd6c8f
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6267b5ca34c3e69af9611c2cdb4a607a7d539f00
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="verifysignedbycert-transact-sql"></a>VERIFYSIGNEDBYCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Verifica se i dati con firma digitale sono stati modificati dopo la firma.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
VerifySignedByCert( Cert_ID , signed_data , signature )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Cert_ID*  
 ID di un certificato nel database. *Cert_ID* è **int**.  
  
 *signed_data*  
 È una variabile di tipo **nvarchar**, **char**, **varchar**, o **nchar** che contiene dati che sono stati firmati con un certificato.  
  
 *firma*  
 Firma allegata ai dati firmati. *firma* è **varbinary**.  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
 Restituisce 1 se i dati firmati risultano invariati; in caso contrario, restituisce 0.  
  
## <a name="remarks"></a>Osservazioni  
 **VerifySignedBycert** decrittografa la firma dei dati utilizzando la chiave pubblica del certificato specificato e confronta il valore decrittografato con un nuovo hash MD5 calcolato dei dati. Se i valori corrispondono, viene confermata la validità della firma.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW DEFINITION per il certificato.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-verifying-that-signed-data-has-not-been-tampered-with"></a>A. Verifica che i dati firmati non siano stati alterati  
 Nell'esempio seguente viene verificato se le informazioni incluse in `Signed_Data` sono state modificate dopo la firma tramite il certificato denominato `Shipping04`. La firma viene archiviata in `DataSignature`. Il certificato `Shipping04` viene passato a `Cert_ID`, che restituisce l'ID del certificato nel database. Se `VerifySignedByCert` restituisce 1, la firma è corretta. Se invece `VerifySignedByCert` restituisce 0, i dati in `Signed_Data` non corrispondono ai dati utilizzati per generare `DataSignature`. In questo caso, i dati in `Signed_Data` sono stati modificati dopo la firma oppure la firma di `Signed_Data` è stata eseguita con un certificato diverso.  
  
```  
SELECT Data, VerifySignedByCert( Cert_Id( 'Shipping04' ),  
    Signed_Data, DataSignature ) AS IsSignatureValid  
FROM [AdventureWorks2012].[SignedData04]   
WHERE Description = N'data signed by certificate ''Shipping04''';  
GO  
```  
  
### <a name="b-returning-only-records-that-have-a-valid-signature"></a>B. Restituzione solo dei record che dispongono di una firma valida  
 La query restituisce solo i record che non hanno subito modifiche dopo essere stati firmati utilizzando il certificato `Shipping04`.  
  
```  
SELECT Data FROM [AdventureWorks2012].[SignedData04]   
WHERE VerifySignedByCert( Cert_Id( 'Shipping04' ), Data,   
    DataSignature ) = 1   
AND Description = N'data signed by certificate ''Shipping04''';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CERT_ID &#40; Transact-SQL &#41;](../../t-sql/functions/cert-id-transact-sql.md)   
 [SIGNBYCERT &#40; Transact-SQL &#41;](../../t-sql/functions/signbycert-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [Istruzione ALTER CERTIFICATE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [DROP CERTIFICATE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
