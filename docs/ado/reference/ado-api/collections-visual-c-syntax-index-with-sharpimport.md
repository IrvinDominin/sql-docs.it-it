---
title: 'Raccolte (indice sintassi Visual C++ con #import) | Documenti Microsoft'
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
dev_langs:
- C++
helpviewer_keywords:
- 'syntax indexes [ADO], ADO for Visual C++ syntax with #import'
- 'collections [ADO], ADO for Visual C++ syntax with #import'
- 'ADO for Visual C++ syntax with #import [ADO]'
- '#import [ADO]'
ms.assetid: 36fbca8e-1884-44b5-806b-d15e30f42fe6
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 488f5dcc74f6b5b1d1ea89c794511a96dc3dea81
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="collections-visual-c-syntax-index-with-import"></a>Raccolte (indice sintassi Visual C++ con #import)
È utile per gli insiemi ereditano determinati metodi e proprietà comuni.  
  
 Ereditano tutte le raccolte di **conteggio** proprietà e **aggiornare** (metodo) e tutte le raccolte di aggiungono il **elemento** proprietà. Il **errori** insieme aggiunge il **deselezionare** metodo. Il **parametri** raccolta eredita le **Append** e **eliminare** metodi, mentre il **campi** insieme aggiunge il **Append**, **eliminare**, e **aggiornamento** metodi.  
  
## <a name="properties-collection"></a>Raccolta delle proprietà  
  
### <a name="methods"></a>Metodi  
  
```  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>Proprietà  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="errors-collection"></a>Raccolta di errori  
  
### <a name="methods"></a>Metodi  
  
```  
HRESULT Clear( );  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>Proprietà  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="parameters-collection"></a>Raccolta Parameters  
  
### <a name="methods"></a>Metodi  
  
```  
HRESULT Append( IDispatch * Object );  
HRESULT Delete( const _variant_t & Index );  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>Proprietà  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="fields-collection"></a>Raccolta Fields  
  
### <a name="methods"></a>Metodi  
  
```  
HRESULT Append( _bstr_t Name, enum DataTypeEnum Type, long DefinedSize, enum FieldAttributeEnum Attrib, const _variant_t & FieldValue = vtMissing );  
HRESULT Delete( const _variant_t & Index );  
HRESULT Refresh( );  
HRESULT Update( );  
```  
  
### <a name="properties"></a>Proprietà  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta di errori (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Raccolta di campi (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Raccolta di parametri (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
