---
title: Supporto del tipo di dati timestamp in FOR XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- timestamp data type
ms.assetid: 4e1920e1-e7a4-4069-965e-3f6039a6099e
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2411dca6acb605e5a543f8bc89982b6783f9f70a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37240141"
---
# <a name="for-xml-support-for-the-timestamp-data-type"></a>Supporto del tipo di dati timestamp in FOR XML
  Nella trasformazione FOR XML, i valori di tipo **timestamp** vengono considerati come dati **varbinary(8)** e sono sempre codificati con Base64. Lo schema XSD o XDR, se necessario, rappresenta questo tipo di dati.  
  
```  
drop table t  
go  
create table t  
(c1 int,  
 c2 timestamp)  
go  
  
insert t values(1, null)  
go  
select * from t  
for xml auto, xmldata  
go  
```  
  
 Risultato:  
  
```  
<Schema name="Schema1"   
        xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:datatypes">  
  <ElementType name="t" content="empty" model="closed">  
    <AttributeType name="c1" dt:type="i4" />  
    <AttributeType name="c2" dt:type="bin.base64" />  
    <attribute type="c1" />  
    <attribute type="c2" />  
  </ElementType>  
</Schema>  
<t xmlns="x-schema:#Schema1" c1="1" c2="AAAAAAAAH04=" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di FOR XML per vari tipi di dati di SQL Server](for-xml-support-for-various-sql-server-data-types.md)  
  
  
