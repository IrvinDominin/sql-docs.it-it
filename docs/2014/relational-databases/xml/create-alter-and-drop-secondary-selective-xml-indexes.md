---
title: Creare, modificare o eliminare indici XML selettivi secondari | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 45128105-833b-40a9-9cc9-1ae03ac0b52b
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e1b85ab8b80a8c488c768ace365ca1a3478a609e
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43889227"
---
# <a name="create-alter-and-drop-secondary-selective-xml-indexes"></a>Creare, modificare o eliminare indici XML selettivi secondari
  Viene descritto come creare un nuovo indice XML selettivo secondario oppure modificarne o eliminarne uno esistente.  
  
##  <a name="create"></a> Creazione di un indice XML selettivo secondario  
  
### <a name="how-to-create-a-secondary-selective-xml-index"></a>Procedura: Creare un indice XML selettivo secondario  
 **Creare un indice XML selettivo secondario tramite Transact-SQL**  
 Creare un indice XML selettivo secondario chiamando l'istruzione CREATE XML INDEX. Per altre informazioni, vedere [CREATE XML INDEX &#40;indici XML selettivi&#41;] (~ / t-sql/statements/create-xml-index-selective-xml-indexes.  
  
 **Esempio**  
  
 Nell'esempio seguente viene creato un indice XML selettivo secondario nel percorso `'pathabc'`. Il percorso dell'indice viene identificato dal nome fornito al momento della creazione con l'istruzione CREATE SELECTIVE XML INDEX. Per altre informazioni, vedere [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).  
  
```tsql  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
  
##  <a name="alter"></a> Modifica di un indice XML selettivo secondario  
 L'istruzione ALTER non è supportata per gli indici XML selettivi secondari. Per modificare un indice XML selettivo secondario, eliminare l'indice esistente e ricrearlo.  
  
### <a name="how-to-alter-a-secondary-selective-xml-index"></a>Procedura: Modificare un indice XML selettivo secondario  
 **Modificare un indice XML selettivo secondario tramite Transact-SQL**  
 1.  Eliminare l'indice XML selettivo secondario esistente chiamando l'istruzione DROP INDEX. Per altre informazioni, vedere [DROP INDEX &#40;indici XML selettivi&#41;](../indexes/indexes.md).  
  
2.  Ricreare l'indice con le opzioni desiderate chiamando l'istruzione CREATE XML INDEX. Per altre informazioni, vedere [CREATE XML INDEX &#40;indici XML selettivi&#41;] (~ / t-sql/statements/create-xml-index-selective-xml-indexes.  
  
 **Esempio**  
  
 Nell'esempio seguente viene modificato un indice XML selettivo secondario eliminandolo e ricreandolo.  
  
```tsql  
DROP INDEX filt_sxi_index_c  
  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
  
##  <a name="drop"></a> Eliminazione di un indice XML selettivo secondario  
  
### <a name="how-to-drop-a-secondary-selective-xml-index"></a>Procedura: Eliminare un indice XML selettivo secondario  
 **Eliminare un indice XML selettivo secondario tramite Transact-SQL**  
 Eliminare un indice XML selettivo secondario chiamando l'istruzione DROP INDEX. Per altre informazioni, vedere [DROP INDEX &#40;indici XML selettivi&#41;](../indexes/indexes.md).  
  
 **Esempio**  
  
 Nell'esempio seguente viene illustrata un'istruzione DROP INDEX.  
  
```tsql  
DROP INDEX ssxi_index  
ON tbl  
```  
  
  
## <a name="see-also"></a>Vedere anche  
 [Indici XML selettivi &#40;SXI&#41;](selective-xml-indexes-sxi.md)  
  
  
