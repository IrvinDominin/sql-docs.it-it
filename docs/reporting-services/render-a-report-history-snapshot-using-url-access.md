---
title: Eseguire il rendering degli snapshot della cronologia dei report tramite l'accesso con URL | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services], report history
- history snapshots [Reporting Services]
- historical data [Reporting Services]
- snapshots [Reporting Services], URL access
- snapshots [Reporting Services], rendering report history
ms.assetid: 3f87f82d-0e61-4492-9c4b-f5238c39e8cd
author: markingmyname
ms.author: maghan
ms.openlocfilehash: e13765e67b1e14cd676d371fdeb0a3f8e6a896fc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47795189"
---
# <a name="render-a-report-history-snapshot-using-url-access"></a>Eseguire il rendering degli snapshot della cronologia dei report tramite l'accesso con URL
  È possibile eseguire il rendering di un report in base allo snapshot della cronologia del report fornendo il parametro *rs:Snapshot* e impostandone il valore su un ID di snapshot valido. Il valore di questo parametro è nel formato AAAA-MM-GGTHH:MM:SS, in base allo standard ISO (International Organization for Standardization) 8601.  
  
 Se si omette questo parametro, il rendering del report viene eseguito in base alle impostazioni dell'opzione di esecuzione del report e gestione della cache del server di report. Per altre informazioni sull'esecuzione di report, vedere [Impostare proprietà di elaborazione dei report](../reporting-services/report-server/set-report-processing-properties.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un URL che consente di recuperare uno snapshot della cronologia del report:  
  
```  
http://myrshost/reportserver?/SampleReports/Company Sales&rs:Snapshot=2003-04-07T13:40:02  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso con URL &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)   
 [Riferimento ai parametri di accesso con URL](../reporting-services/url-access-parameter-reference.md)  
  
  
