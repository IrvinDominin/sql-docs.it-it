---
title: Installare e disinstallare il componente di origine OData | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 0a3ae788-e8c8-4a4d-bb15-34c673abcd17
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 67bb3b093d63564c4eaae0144add029e569281f1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48068111"
---
# <a name="install-and-uninstall-odata-source-component"></a>Installare e disinstallare il componente di origine OData
  In questo argomento vengono fornite le istruzioni per installare il componente di origine OData nel computer o per eseguirne la rimozione.  
  
## <a name="installation"></a>Installazione  
 Per il componente di origine OData devono essere installati nel computer i componenti prerequisiti riportati di seguito.  
  
-   SQL Server Data Tools (per la progettazione di pacchetti)  
  
-   SQL Server Integration Services (per l'esecuzione di pacchetti esternamente a Visual Studio)  
  
 Per installare il componente di origine OData, scaricare [Feature Pack di SQL Server 2014](http://go.microsoft.com/fwlink/p/?LinkId=391999) ed eseguire uno dei seguenti file MSI.  
  
-   ODataSourceForSQLServer2014-amd64.msi per piattaforme a 64 bit  
  
-   ODataSourceForSQLServer2014-x86.msi per piattaforme a 32 bit  
  
> [!IMPORTANT]  
>  Il programma di installazione a 64 bit viene installato sia nella versione a 32 bit sia in quella a 64 bit del componente di origine OData. È sufficiente eseguire il programma di installazione a 32 bit se si utilizza un sistema operativo a 32 bit.  
  
## <a name="uninstallation"></a>Disinstallazione  
 Il componente origine OData può essere disinstallato dal **programmi e funzionalità** menu. Trovare il **Microsoft SQL Server SSIS OData Source Component (x64)** voce e fare clic su **Disinstalla**.  
  
  
