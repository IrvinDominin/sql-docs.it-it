---
title: ALTER COLUMN ENCRYPTION KEY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 10/28/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER COLUMN ENCRYPTION
- ALTER_COLUMN_ENCRYPTION_TSQL
- ALTER COLUMN ENCRYPTION KEY
- ALTER_COLUMN_ENCRYPTION_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- column encryption key, alter
- ALTER COLUMN ENCRYPTION KEY statement
ms.assetid: c79a220d-e178-4091-a330-c924cc0f0ae0
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a6bc70a7cafdbf69549435b44099b903cfc60327
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="alter-column-encryption-key-transact-sql"></a>ALTER COLUMN ENCRYPTION KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Modifica una chiave di crittografia di colonna in un database, aggiunta o eliminazione di un valore crittografato. Una CEK può avere fino a due valori che consente la rotazione della chiave master della colonna corrispondente. Una CEK viene utilizzata per la crittografia di colonne mediante il [Always Encrypted &#40; motore di Database &#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md) funzionalità. Prima di aggiungere un valore CEK, è necessario definire la chiave master della colonna utilizzata per crittografare il valore utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [CREATE MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md) istruzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
ALTER COLUMN ENCRYPTION KEY key_name   
    [ ADD | DROP ] VALUE   
    (  
        COLUMN_MASTER_KEY = column_master_key_name   
        [, ALGORITHM = 'algorithm_name' , ENCRYPTED_VALUE =  varbinary_literal ]   
    ) [;]  
```  
  
## <a name="arguments"></a>Argomenti  
 *key_name*  
 La chiave di crittografia di colonna che si sta modificando.  
  
 *column_master_key_name*  
 Specifica il nome della chiave master colonna (CMK) utilizzata per crittografare la chiave di crittografia di colonna (CEK).  
  
 *nome_algoritmo*  
 Nome dell'algoritmo di crittografia utilizzato per crittografare il valore. L'algoritmo per i provider di sistema deve essere **RSA_OAEP**. Questo argomento non valido durante l'eliminazione di un valore di chiave di crittografia di colonna.  
  
 *varbinary_literal*  
 Il BLOB del CEK crittografato con lo schema specificato chiave di crittografia. . Questo argomento non valido durante l'eliminazione di un valore di chiave di crittografia di colonna.  
  
> [!WARNING]  
>  Non passare mai in testo normale valori CEK in questa istruzione. In questo modo includerà il vantaggio di questa funzionalità.  
  
## <a name="remarks"></a>Osservazioni  
 In genere, una chiave di crittografia di colonna viene creata con un solo valore crittografato. Quando una chiave master della colonna deve essere ruotato (la colonna chiave master esigenze correnti da sostituire con la nuova chiave master di colonna), è possibile aggiungere un nuovo valore della chiave di crittografia della colonna, crittografata con la nuova chiave master della colonna. In questo modo sarà possibile verificare applicazioni client possono accedere ai dati crittografati con la chiave di crittografia di colonna, mentre la nuova chiave master della colonna reso disponibile alle applicazioni client. Un Always Encrypted abilitato driver in un'applicazione client che non ha accesso alla nuova chiave master, sarà possibile utilizzare il valore chiave crittografia della colonna crittografato con la vecchia chiave master di colonna per accedere a dati sensibili. Gli algoritmi di crittografia, supporta Always Encrypted, richiedono il valore di testo normale di 256 bit. Un valore crittografato dovrebbe essere generato utilizzando un provider dell'archivio chiavi che incapsula l'archivio chiavi contenente la chiave master della colonna.  
  
 Utilizzare [Columns &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md), [column_encryption_keys &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md) e [column_encryption_key_values &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md) per visualizzare informazioni sulle chiavi di crittografia di colonna.  
  
## <a name="permissions"></a>Permissions  
 Richiede **ALTER ANY COLUMN ENCRYPTION KEY** autorizzazione per il database.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-adding-a-column-encryption-key-value"></a>A. Aggiunta di un valore di chiave di crittografia di colonna  
 L'esempio seguente modifica una chiave di crittografia di colonna denominata `MyCEK`.  
  
```  
ALTER COLUMN ENCRYPTION KEY MyCEK  
ADD VALUE  
(  
    COLUMN_MASTER_KEY = MyCMK2,   
    ALGORITHM = 'RSA_OAEP',   
    ENCRYPTED_VALUE = 0x016E000001630075007200720065006E00740075007300650072002F006D0079002F0064006500650063006200660034006100340031003000380034006200350033003200360066003200630062006200350030003600380065003900620061003000320030003600610037003800310066001DDA6134C3B73A90D349C8905782DD819B428162CF5B051639BA46EC69A7C8C8F81591A92C395711493B25DCBCCC57836E5B9F17A0713E840721D098F3F8E023ABCDFE2F6D8CC4339FC8F88630ED9EBADA5CA8EEAFA84164C1095B12AE161EABC1DF778C07F07D413AF1ED900F578FC00894BEE705EAC60F4A5090BBE09885D2EFE1C915F7B4C581D9CE3FDAB78ACF4829F85752E9FC985DEB8773889EE4A1945BD554724803A6F5DC0A2CD5EFE001ABED8D61E8449E4FAA9E4DD392DA8D292ECC6EB149E843E395CDE0F98D04940A28C4B05F747149B34A0BAEC04FFF3E304C84AF1FF81225E615B5F94E334378A0A888EF88F4E79F66CB377E3C21964AACB5049C08435FE84EEEF39D20A665C17E04898914A85B3DE23D56575EBC682D154F4F15C37723E04974DB370180A9A579BC84F6BC9B5E7C223E5CBEE721E57EE07EFDCC0A3257BBEBF9ADFFB00DBF7EF682EC1C4C47451438F90B4CF8DA709940F72CFDC91C6EB4E37B4ED7E2385B1FF71B28A1D2669FBEB18EA89F9D391D2FDDEA0ED362E6A591AC64EF4AE31CA8766C259ECB77D01A7F5C36B8418F91C1BEADDD4491C80F0016B66421B4B788C55127135DA2FA625FB7FD195FB40D90A6C67328602ECAF3EC4F5894BFD84A99EB4753BE0D22E0D4DE6A0ADFEDC80EB1B556749B4A8AD00E73B329C95827AB91C0256347E85E3C5FD6726D0E1FE82C925D3DF4A9  
);  
GO  
  
```  
  
### <a name="b-dropping-a-column-encryption-key-value"></a>B. Eliminazione di un valore di chiave di crittografia di colonna  
 L'esempio seguente modifica una chiave di crittografia di colonna denominata `MyCEK` mediante il rilascio di un valore.  
  
```  
ALTER COLUMN ENCRYPTION KEY MyCEK  
DROP VALUE  
(  
    COLUMN_MASTER_KEY = MyCMK  
);  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [DROP COLUMN ENCRYPTION KEY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
 [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Always Encrypted &#40;Motore di database&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [sys.column_encryption_keys  &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md)   
 [sys.column_encryption_key_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
