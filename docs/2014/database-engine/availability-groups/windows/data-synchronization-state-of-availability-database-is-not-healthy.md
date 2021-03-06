---
title: Lo stato di sincronizzazione dei dati del database di disponibilità non è integro | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp3datasynchealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 4fd003e7-808e-4b0e-b28a-47d9f2616f06
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1aa901fe3230a76af3127af41630b075414d77a6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48096876"
---
# <a name="data-synchronization-state-of-availability-database-is-not-healthy"></a>Lo stato della sincronizzazione dei dati del database di disponibilità non è integro
    
## <a name="introduction"></a>Introduzione  
  
|||  
|-|-|  
|**Nome criteri**|Stato di sincronizzazione dei dati del database di disponibilità|  
|**Problema**|Lo stato di sincronizzazione dei dati del database di disponibilità non è integro.|  
|**Category**|**Avviso**|  
|**Facet**|Database di disponibilità|  
  
## <a name="description"></a>Description  
 Questi criteri consentono di eseguire il rollup dello stato di sincronizzazione dei dati di tutti i database di disponibilità, anche noti come "repliche di disponibilità", nella replica di disponibilità. I criteri sono in uno stato non integro se una qualsiasi replica del database non è nello stato di sincronizzazione dei dati previsto. Altrimenti, sono in uno stato integro.  
  
> [!NOTE]  
>  Per questa versione di [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], le informazioni sulle possibili cause e le soluzioni sono disponibili nella pagina relativa allo [stato di sincronizzazione non integro dei dati di alcuni database di disponibilità](http://go.microsoft.com/fwlink/p/?LinkId=220858) su TechNet Wiki.  
  
## <a name="possible-causes"></a>Possibili cause  
 Lo stato di sincronizzazione dei dati di questo database di disponibilità non è integro. In una replica di disponibilità con commit asincrono, ogni database di disponibilità deve trovarsi nello stato SINCRONIZZAZIONE IN CORSO. In una replica con commit sincrono, ogni database di disponibilità deve trovarsi nello stato SINCRONIZZATO.  
  
## <a name="possible-solution"></a>Possibile soluzione  
 Utilizzare i criteri della replica del database per trovare la replica del database con uno stato di sincronizzazione dei dati non integro e risolvere il relativo problema.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Usare il Dashboard Always On &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
