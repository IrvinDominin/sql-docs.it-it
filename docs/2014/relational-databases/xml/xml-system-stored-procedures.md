---
title: Stored procedure XML di sistema | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- system stored procedures [SQL Server], XML
- sp_xml_removedocument
- OPENXML statement, system stored procedures
- sp_xml_preparedocument
- XML [SQL Server], system stored procedures
ms.assetid: e60c7f85-6823-4d28-93d6-b053d08cc830
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7f84fbd7435a092abc326f8bb253e5d8565618fc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218137"
---
# <a name="xml-system-stored-procedures"></a>Stored procedure XML di sistema
  In SQL Server sono disponibili le stored procedure di sistema seguenti, utilizzate insieme all'istruzione OPENXML:  
  
-   [sp_xml_preparedocument &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql)  
  
-   [sp_xml_removedocument &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql)  
  
 Per scrivere le query tramite l'istruzione OPENXML, è prima necessario creare una rappresentazione interna del documento XML chiamando la stored procedure **sp_xml_preparedocument**. La stored procedure restituisce un handle per la rappresentazione interna del documento XML. Tale handle viene quindi passato a OPENXML, che restituisce viste di set di righe del documento basate su query XPath. In particolare, vengono restituiti un modello di riga e uno o più modelli di colonna.  
  
> [!NOTE]  
>  L'handle del documento restituito dalla stored procedure **sp_xml_preparedocument** è valido per l'intera durata della sessione.  
  
 È possibile rimuovere la rappresentazione interna del documento XML dalla memoria chiamando la stored procedure di sistema **sp_xml_removedocument** .  
  
## <a name="see-also"></a>Vedere anche  
 [OPENXML &#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql)   
 [OPENXML &#40;SQL Server&#41;](../xml/openxml-sql-server.md)  
  
  
