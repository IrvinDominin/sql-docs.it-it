---
title: CERT_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CERT_ID
- CERT_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- identification numbers [SQL Server], certificates
- CERT_ID function
- IDs [SQL Server], certificates
- certificates [SQL Server], IDs
ms.assetid: 59cc06f5-272e-4936-8afe-afba7aba8eea
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1b424d7c19f668d17dbe899804c2ef3002775a27
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47708599"
---
# <a name="certid-transact-sql"></a>CERT_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Questa funzione restituisce il valore ID di un certificato.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
Cert_ID ( 'cert_name' )  
```  
  
## <a name="arguments"></a>Argomenti  
**'** *cert_name* **'**  

Nome di un certificato nel database.
  
## <a name="return-types"></a>Tipi restituiti
 **int**  
  
## <a name="remarks"></a>Remarks  
I nomi di certificato sono visualizzati nella vista del catalogo [sys.certificates](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md).
  
## <a name="permissions"></a>Permissions  
Richiede le autorizzazioni appropriate per il certificato ed è necessario che al chiamante non sia stata negata l'autorizzazione VIEW DEFINITION per il certificato. Vedere [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md#permissions) per altre informazioni sulle autorizzazioni per i certificati.
  
## <a name="examples"></a>Esempi  
In questo esempio viene restituito l'ID di un certificato denominato `ABerglundCert3`.
  
```sql
SELECT Cert_ID('ABerglundCert3');  
GO  
```  
  
## <a name="see-also"></a>Vedere anche
[sys.certificates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)  
[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
[Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)
  
  
