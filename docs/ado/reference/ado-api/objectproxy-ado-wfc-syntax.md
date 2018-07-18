---
title: ObjectProxy (ADO - sintassi WFC) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ObjectProxy collection [ADO]
ms.assetid: f68f58bc-ad28-46cc-9fb3-099e1a678397
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0ce52d661b5fffe6f0263baa81808dc7d1e9fd3b
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35279660"
---
# <a name="objectproxy-ado---wfc-syntax"></a>ObjectProxy (ADO - sintassi WFC)
Un **ObjectProxy** oggetto rappresenta un server e viene restituito dal **createObject** metodo il [DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) oggetto. La classe ObjectProxy include un metodo, **chiamare**, che può richiamare un metodo nel server e restituire un oggetto risultante da tale chiamata.  
  
 **package com.ms.wfc.data**  
  
## <a name="methods"></a>Metodi  
  
### <a name="call-method-adowfc-syntax"></a>Metodo di chiamata (sintassi ADO/WFC)  
 Richiama un metodo sul server rappresentato dall'oggetto ObjectProxy. Facoltativamente, gli argomenti del metodo possono essere passati come una matrice di oggetti.  
  
#### <a name="syntax"></a>Sintassi  
  
```  
public Object ObjectProxy.( String method )  
public Object ObjectProxy.( String method, Object[] args)  
```  
  
#### <a name="returns"></a>Valori di codice restituiti  
 Object  
 Oggetto risultante dalla chiamata al metodo.  
  
#### <a name="parameters"></a>Parametri  
 *ObjectProxy*  
 Un **ObjectProxy** oggetto che rappresenta il server.  
  
 *Metodo*  
 Stringa contenente il nome del metodo da richiamare sul server.  
  
 *argomenti*  
 Facoltativo. Matrice di oggetti che rappresentano argomenti del metodo nel server. Tipi di dati Java vengono automaticamente convertiti in tipi di dati adatti per l'uso nel server.
