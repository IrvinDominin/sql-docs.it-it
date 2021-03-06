---
title: 'PDO:: getavailabledrivers | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: eab561e6-1229-401a-9482-008c23f9a4e6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a48b35d805021f8dc165679719847c56e2b3fe36
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47646439"
---
# <a name="pdogetavailabledrivers"></a>PDO::getAvailableDrivers
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Restituisce una matrice dei driver PDO nell'installazione di PHP.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
array PDO::getAvailableDrivers ();  
```  
  
## <a name="return-value"></a>Valore restituito  
Una matrice con l'elenco dei driver PDO.  
  
## <a name="remarks"></a>Remarks  
Il nome del driver PDO usato in PDO::__construct per creare un'istanza PDO.  
  
PDO::getAvailableDrivers non deve essere implementata dai driver PHP. Per altre informazioni su questo metodo, vedere la documentazione di PHP.  
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
  
```  
<?php  
print_r(PDO::getAvailableDrivers());  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
