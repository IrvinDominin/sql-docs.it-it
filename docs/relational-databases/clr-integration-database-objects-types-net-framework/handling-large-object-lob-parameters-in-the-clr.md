---
title: Gestione di parametri LOB (Large Object) in CLR | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: reference
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- large data, CLR integration
- LOB data [SQL Server], CLR integration
- SqlBytes data type
- SqlChars data type
ms.assetid: d07956f6-9543-4476-9426-536f95991150
caps.latest.revision: 20
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 659724653cb68750cf377e83fd00e7c72b92b99d
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35697162"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>Gestione di parametri di tipo LOB (Large Object) in CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Uso **SqlBytes** e **SqlChars** passare LOB (large object) di tipo binario (**varbinary (max)**) e LOB di tipo carattere (**nvarchar (max)**) i parametri, rispettivamente. Questi tipi consentono di eseguire il flusso dei valori LOB dal database alla routine CLR (Common Language Runtime) anziché copiare l'intero valore nello spazio gestito. **SqlBinary** e **SqlString** deve essere utilizzato solo per file binario di piccole dimensioni e i valori di stringa di caratteri.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati di SQL Server in .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
