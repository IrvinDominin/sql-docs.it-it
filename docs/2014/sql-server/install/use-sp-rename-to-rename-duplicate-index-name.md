---
title: Utilizzare sp_rename per rinominare il nome di indice duplicati | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- table names [SQL Server]
- duplicate table names
- index names [SQL Server]
- sp_rename
- duplicate index names
ms.assetid: ee66c7a5-eb6d-4fcf-970c-ab099d78c8d9
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 641dbb6e33f7b39a7542fdd43a940c487a4b21d9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48093041"
---
# <a name="use-sprename-to-rename-duplicate-index-name"></a>Utilizzare sp_rename per rinominare gli indici duplicati
  Sono stati rilevati nomi di indici di tabella o di vista duplicati. Rinominare gli indici prima di eseguire l'aggiornamento.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Azione correttiva  
  
1.  Individuare gli indici duplicati eseguendo la query seguente:  
  
    ```  
    SELECT DISTINCT OBJECT_NAME(o.id), name  
    FROM sysindexes as o  
    WHERE EXISTS   
        (SELECT name FROM sysindexes  as i  
          WHERE i.id = o.id  
          AND i.name = o.name and i.indid < o.indid);  
    ```  
  
2.  Uso **sp_rename** per cambiare uno dei nomi di indice. Poiché i nomi di indice sono uguali, non è possibile determinare quale indice verrà rinominato. Questa operazione consente quindi di differenziare gli indici.  
  
    ```  
    EXEC sp_rename N'table_name.index_name', N'new_index_name', N'INDEX'  
    ```  
  
3.  Per verificare quale indice è stato rinominato eseguire la query seguente, che restituisce tutti gli indici, inclusi i nomi delle colonne chiave sulla tabella o vista specificata:  
  
    ```  
    SELECT i.name AS IndexName, c.name AS ColumnName, ik.colid, ik.keyno  
    FROM sysindexes i  
    JOIN sysindexkeys ik ON i.id = ik.id and i.indid = ik.indid   
    JOIN syscolumns c ON c.id = ik.id and ik.colid = c.colid  
    WHERE i.id = OBJECT_ID('table_or_view_name')  
    ```  
  
4.  Se necessario, utilizzare **sp_rename** nuovamente per correggere i nomi di indice.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Preparazione aggiornamento a SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
