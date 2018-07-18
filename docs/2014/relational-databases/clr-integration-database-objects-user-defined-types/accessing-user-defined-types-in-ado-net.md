---
title: Accesso ai tipi definiti dall'utente in ADO.NET | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- UDTs [CLR integration], ADO.NET
- user-defined types [CLR integration], ADO.NET
ms.assetid: 4b0d876c-8066-490e-8e18-327c0e942b19
caps.latest.revision: 12
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 6b48d45874824f166dc1b3843eda0e1052fddfd6
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37354663"
---
# <a name="accessing-user-defined-types-in-adonet"></a>Accesso ai tipi definiti dall'utente in ADO .NET
  Tipi definiti dall'utente (UDT) vengono scritti utilizzando uno dei linguaggi supportati dal [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework common language runtime (CLR) che producono codice verificabile. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# e [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. I tipi definiti dall'utente consentono l'archiviazione di oggetti e strutture di dati personalizzate in un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. I dati vengono esposti come membri pubblici di una classe o struttura .NET mentre i comportamenti vengono definiti dai metodi della classe o della struttura. Un tipo definito dall'utente può essere utilizzato come definizione di colonna di una tabella, come una variabile in un [!INCLUDE[tsql](../../includes/tsql-md.md)] batch, o come argomento di un [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure o funzione.  
  
 In ADO.NET il provider `System.Data.SqlClient` espone i tipi definiti dall'utente nei modi seguenti:  
  
-   Mediante `System.Data.SqlClient.SqlDataReader` come oggetto.  
  
-   Mediante `SqlDataReader` come byte non elaborati.  
  
-   Come parametro di un oggetto `System.Data.SqlClient.SqlParameter`.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Recupero di dati UDT](accessing-user-defined-types-retrieving-udt-data.md)  
 Viene illustrato come recuperare i dati dei tipi definiti dall'utente e come specificare i parametri.  
  
 [Aggiornamento di colonne con tipo definito dall'utente con DataAdapter](accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 Viene illustrato come utilizzare i tipi definiti dall'utente in `DataSets` e come aggiornarli utilizzando `DataAdapters`.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi definiti dall'utente per CLR](clr-user-defined-types.md)  
  
  
