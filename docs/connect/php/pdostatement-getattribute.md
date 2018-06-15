---
title: PDOStatement::getAttribute | Documenti Microsoft
ms.custom: ''
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 41d0cca3-8556-4573-bb90-8e9402d9379f
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e2c02170c88066ed30b99fb1fca46505b099752f
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35308510"
---
# <a name="pdostatementgetattribute"></a>PDOStatement::getAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Recupera il valore di un attributo PDOStatement predefinito o di un attributo personalizzato del driver.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
mixed PDOStatement::getAttribute( $attribute );  
```  
  
#### <a name="parameters"></a>Parametri  
$*attributo*: un numero intero, una delle PDO::ATTR_ * PDO::SQLSRV_ATTR_\* costanti. Sono supportati gli attributi che è possibile impostare con [pdostatement:: SetAttribute](../../connect/php/pdostatement-setattribute.md), PDO:: sqlsrv_attr_direct_query (per ulteriori informazioni, vedere [esecuzione di istruzioni diretta e preparata nel il Driver PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md)), PDO:: attr_cursor e PDO:: sqlsrv_attr_cursor_scroll_type (per ulteriori informazioni, vedere [tipi di cursore (Driver PDO_SQLSRV)](../../connect/php/cursor-types-pdo-sqlsrv-driver.md)).  
  
## <a name="return-value"></a>Valore restituito  
In caso di esito positivo, restituisce un valore misto per un attributo predefinito del PDO o per un attributo personalizzato del driver. In caso di errore, restituisce Null.  
  
## <a name="remarks"></a>Remarks  
Per un esempio, vedere [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md) .  
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
