---
title: Ridistribuzione di ADOMD.NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ADOMD.NET, redistributing
- redistributing ADOMD.NET
ms.assetid: f8db3c99-0243-4b92-b486-0d8786c264f4
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6fde698740a417076f7fe139250765b9610e91b5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37245611"
---
# <a name="redistributing-adomdnet"></a>Ridistribuzione di ADOMD.NET
  Quando si scrivono applicazioni che utilizzano ADOMD.NET, è necessario ridistribuire la versione appropriata di ADOMD.NET insieme all'applicazione. Per ridistribuire ADOMD.NET, includere il programma di installazione di ADOMD.NET nel programma di installazione dell'applicazione.  
  
 Il programma di installazione di ADOMD.NET, nonché la versione più recente di ADOMD.NET, sono disponibili nell'Area download Microsoft come parte di SQL Server Feature Pack.  
  
 Il programma di installazione ADOMD.NET installa i file ADOMD.NET in \< *unità di sistema*>: \Program Files\Microsoft.NET\ADOMD.NET\\*numero di versione*.  
  
 Dopo avere incluso il programma di installazione di ADOMD.NET, avviarlo dal programma di installazione dell'applicazione e installare ADOMD.NET. A seconda dell'ambiente, potrebbe inoltre essere necessario verificare che gli assembly correlati siano considerati attendibili da SQL Server.  
  
 Per ulteriori informazioni:  
  
 [Feature Pack per Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkId=389949)  
  
 [Microsoft Connect: Dipendenze di ADOMD.NET](http://go.microsoft.com/fwlink/?LinkId=389950)  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di Client ADOMD.NET](../../multidimensional-models-adomd-net-client/adomd-net-client-programming.md)   
 [Programmazione di server ADOMD.NET](../../multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
  
