---
title: 'Procedura: Distribuire un elemento del report personalizzato | Microsoft Docs'
ms.custom: 
ms.date: 03/18/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: custom-report-items
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: custom report items, deploying
ms.assetid: 80e97b0d-e355-4240-aebd-08cbc84089ed
caps.latest.revision: "26"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: cbbd9a7fc05e7149dcb03eab3ed3c522500b7e0a
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="how-to-deploy-a-custom-report-item"></a>Procedura: Distribuzione di un elemento del report personalizzato
  Per distribuire un elemento del report personalizzato in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], è necessario modificare i file di configurazione del server di report e copiare gli assembly del componente runtime e della fase di progettazione nelle cartelle appropriate dell'applicazione sia per Progettazione report sia per il server di report.  
  
### <a name="to-deploy-a-custom-report-item"></a>Per distribuire un elemento del report personalizzato  
  
1.  Modificare il file Rsreportdesigner.config per configurare i componenti runtime e della modalità progettazione del report personalizzato da utilizzare nella finestra di progettazione. Si noti che **ReportItemName** deve corrispondere all'attributo **CustomReportItemAttribute** usato nella classe **CustomReportItemDesigner**. Ad esempio  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    <ReportItemDesigner>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsDesigner, PolygonsDesigner" />  
    </ReportItemDesigner>  
    <ReportItemConverter>  
       <Converter Source="Chart" Target="Polygons" Type="PolygonsCRI.PolygonsConverter, PolygonsDesigner" />  
    </ReportItemConverter>  
    ```  
  
2.  Modificare il file Rsreportserver.config per registrare il componente runtime dell'elemento del report personalizzato. Ad esempio  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    ```  
  
3.  Modificare il file Rsssrvpolicy.config per aggiungere **CodeGroup** che concede le autorizzazioni appropriate all'elemento del report personalizzato. Ad esempio  
  
    ```  
    <CodeGroup   
       class="UnionCodeGroup"   
       version="1"   
       PermissionSetName="FullTrust"  
       Description="This code group grants MyCustomReportItem.dll FullTrust permission. ">  
       <IMembershipCondition   
          class="UrlMembershipCondition"  
          version="1"  
       Url="C:\Program Files\Microsoft SQL Server\ MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin\MyCustomReportItem.dll" />  
    </CodeGroup>  
    ```  
  
4.  Copiare la DLL del componente runtime dell'elemento del report personalizzato nelle directory %Programmi%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies e \Programmi\Microsoft SQL Server\MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin.  
  
5.  Copiare la DLL del componente della modalità progettazione dell'elemento del report personalizzato nella directory %Programmi %\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.  
  
## <a name="see-also"></a>Vedere anche  
 [File di configurazione di Reporting Services](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Librerie di classi dell'elemento del report personalizzato](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)  
  
  
