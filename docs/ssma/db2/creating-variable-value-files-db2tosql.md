---
title: Creazione di file di valore della variabile (DB2ToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-db2
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 122f3fbe-46a0-40df-ac3b-d43bf33d96ba
caps.latest.revision: "5"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 34edb3b225984442a97480a15648744baa8f796e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="creating-variable-value-files-db2tosql"></a>Creazione di file di valore della variabile (DB2ToSQL)
File valore variabile è un file XML che include i valori dei parametri dei comandi ad esempio, il nome del server di origine o di destinazione che cambiano spesso dalla migrazione di un server a un altro. Quando si verifica un numero elevato di migrazioni di database, verranno creati e a cui fa riferimento in un file di script master con più file di variabile per archiviare il valore di ogni server di origine di **– v** passare alla riga di comando. Ciò consente di mantenere i valori statici, in alcuni file di script con i valori delle variabili in più file di variabile.  
  
> [!NOTE]  
> 1.  I nomi delle variabili sono preceduti e seguiti da un simbolo di dollaro $. Se le variabili non vengono assegnate un valore nel file del valore della variabile, si verificherà un errore durante l'analisi del file script risultante in bloccare il processo di esecuzione della console.  
> 2.  The escape character for **$** is **$$**. Se il valore di un valore statico o variabile di un parametro contiene  **$**  simbolo (dollaro), quindi  **$$**  deve essere specificata di considerarlo come un carattere anziché una variabile.  
> 3.  Per motivi di manutenzione, le variabili possono essere dichiarate all'interno di `‘variable-group’` le variabili definite elementi per la separazione logica dell'utente.  Utilizzo di questo elemento non è obbligatorio.  
  
**Esempi:**  
  
**Esempio 1:**  
  
```  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="ProjectSpecs">  
  
    <variable name="$project_folder$" value="<project-folder>"/>  
  
    <variable name="$project_name$" value="<project-name>"/>  
  
    <variable name="$project_overwrite$" value="<true/false>"/>  
  
    <variable name="$project_type$" value="<project-type>"/>  
  
  </variable-group>  
  
</variables>  
```  
**Esempio 2:**  
  
```  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetServerName$" value="<server-name>"/>  
  
      <variable name="$TargetDB$" value="<database-name>"/>  
  
      <variable name="$TargetUserName$" value="<user-name>"/>  
  
      <variable name="$TargetPassword$" value="<password>"/>  
  
      <variable name="$TrustedConnection$" value="<true/false>"/>  
  
    </variable-group>  
  
    <variable-group name="SqlServerObjectParams">  
  
      <variable name="$ObjectName1$" value="<object-name>"/>  
  
      <variable name="$ObjectName2$" value="<object-name>"/>  
  
    </variable-group>  
  
  </variable-group>  
  
</variables>  
```  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo nella console di gestione è [creazione DB2ToSQL i file di connessione del Server &#40; &#41;](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Creazione dei file di connessione del server](http://msdn.microsoft.com/en-us/002f129e-0868-48ad-a4b4-c68b5007e12e)  
  
