---
title: Copia della tabella remota - Parallel Data Warehouse | Documenti Microsoft
description: Utilizzo di copia della tabella remota in Analitica piattaforma Parallel Data Warehouse di System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 5ed517a471368e4192ad7393a92274424d37f975
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
ms.locfileid: "31538721"
---
# <a name="remote-table-copy"></a>Copia della tabella remota
Viene descritto come utilizzare la funzionalità di copia della tabella remota per copiare le tabelle dal database di SQL Server PDW ai database remoti di SMP SQL Server (non accessorio). Utilizzare tabella remota copy rende possibili scenari di hub e spoke per SQL Server PDW.  
  
## <a name="BasicsPDE"></a>Comprendere copia della tabella remota di SQL Server PDW  
Copia della tabella remota è una funzionalità di SQL Server PDW che consente scenari di Hub e Spoke, copiando i risultati di un'istruzione SQL SELECT in una tabella in un database SMP. La copia della tabella remota è stata avviata con il [CREATE REMOTE TABLE AS SELECT](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md) istruzione.  
  
## <a name="BasicsPrerequisites"></a>Requisiti per l'utilizzo di copia della tabella remota  
È possibile utilizzare le tabelle di copia per copiare la tabella remota da SQL Server PDW a un database di SQL Server quando vengono soddisfatte queste condizioni:  
  
-   Il database di destinazione deve essere un'istanza di Microsoft® SQL Server® che è in esecuzione in un sistema Microsoft Windows® che è possibile connettersi al dispositivo di SQL Server PDW ma non risiede su un server all'interno del dispositivo. Il Server SQL remoto può essere connesso a SQL Server PDW, utilizzare la rete InfiniBand o tramite rete Ethernet.  
  
-   I dati da copiare devono essere selezionabili utilizzando un singolo SQL Server PDW valido [selezionare](../t-sql/queries/select-transact-sql.md) istruzione.  
  
-   Il server di destinazione deve essere un server non appliance. Impossibile copiare i dati direttamente da un dispositivo a un altro utilizzando le istruzioni riportate in questo argomento.  
  
-   Il server di destinazione deve essere accessibile a tutti i nodi nella rete Infiniband del dispositivo.  
  
## <a name="ConfigureRemote"></a>Configurare una copia della tabella remota  
Per utilizzare una copia della tabella remota, è necessario acquistare e configurare un server Windows, configurare SQL Server in Windows server e configurare SQL Server PDW. Utilizzare i collegamenti seguenti per eseguire questi passaggi di configurazione di tre.  
  
1.  [Configurare un sistema di Windows esterno per la ricezione di copie di tabella remota utilizzando InfiniBand](configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband.md)  
  
2.  [Configurare un Server SQL SMP esterni per ricevono una copia di tabella remota](configure-an-external-smp-sql-server-to-receive-remote-table-copies.md)  
  
3.  [Configurare SQL Server PDW per copie tabella remota](configure-sql-server-pdw-for-remote-table-copies.md)  
  
## <a name="PerformRemote"></a>Eseguire una copia della tabella remota  
Per eseguire una copia della tabella remota, utilizzare il [CREATE REMOTE TABLE AS SELECT](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md) istruzione SQL. Esempi sono inclusi con l'argomento di CREATE REMOTE TABLE.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
