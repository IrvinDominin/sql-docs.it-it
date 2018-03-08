---
title: Aggregazioni CLR definite dall'utente | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- aggregate functions [CLR integration]
- custom aggregates [CLR integration]
- calculations [CLR integration]
- user-defined functions [CLR integration]
ms.assetid: bad9b7e8-5967-4afa-8dc8-6d840faf9372
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7a21a1ef44ac6898740b75daf5b087e76415d904
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="clr-user-defined-aggregates"></a>Aggregazioni CLR definite dall'utente
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Le funzioni di aggregazione eseguono un calcolo su un set di valori e restituiscono un singolo valore. Tradizionalmente, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è supportato solo funzioni di aggregazione predefinite, ad esempio **somma** o **MAX**, che operano su un set di valori scalari di input e generare una singola funzione di aggregazione valore da tale set. L'integrazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con il CLR [!INCLUDE[msCoName](../../includes/msconame-md.md)] di .NET Framework consente ora agli sviluppatori di creare funzioni di aggregazione personalizzate in codice gestito e di rendere accessibili queste funzioni a [!INCLUDE[tsql](../../includes/tsql-md.md)] o all'altro codice gestito.  
  
 Nella tabella seguente vengono elencati gli argomenti disponibili in questa sezione.  
  
 [Requisiti per aggregazioni CLR definite dall'utente](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates-requirements.md)  
 Viene fornita una panoramica dei requisiti per l'implementazione di funzioni di aggregazione CLR definite dall'utente.  
  
 [Richiamo di funzioni di aggregazione definita dall'utente CLR](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregate-invoking-functions.md)  
 Viene illustrato come richiamare aggregazioni definite dall'utente.  
  
  
