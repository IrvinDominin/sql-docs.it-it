---
title: MSSQLSERVER_8710 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 8710 (Database Engine error)
ms.assetid: 78b9f9da-5489-4be0-94df-f065d86ed18c
caps.latest.revision: 8
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: c46591374fc32ba20f4eb20c48bec171c76d9ac7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069169"
---
# <a name="mssqlserver8710"></a>MSSQLSERVER_8710
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|MSSQLSERVER|  
|ID evento|8710|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|QUERY2_CUBE_ILLEGAL_AGG_FUNC|  
|Testo del messaggio|Le funzioni di aggregazione utilizzate con query CUBE, ROLLUP o GROUPING SET devono supportare l'unione di aggregazioni secondarie. Per risolvere il problema, rimuovere la funzione di aggregazione o scrivere la query utilizzando UNION ALL nelle clausole GROUP BY.|  
  
## <a name="explanation"></a>Spiegazione  
 Una funzione di aggregazione è stata utilizzata con CUBE, ROLLUP o GROUPING SETS che non forniscono un metodo per unire aggregazioni secondarie.  
  
## <a name="user-action"></a>Azione dell'utente  
 Per risolvere il problema, rimuovere la funzione di aggregazione o scrivere la query utilizzando UNION ALL nelle clausole GROUP BY.  
  
  