---
title: Metodo ListInstalledSharePointVersions (WMI) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: wmi-provider-library-reference
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListInstalledSharePointVersions method
ms.assetid: 8f0a5e9f-23f1-41e5-9a90-dfec19ef1df7
caps.latest.revision: "13"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b37b8727d6349949093cff52f9b50f22cbb20046
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="configurationsetting-method---listinstalledsharepointversions"></a>Metodo di ConfigurationSetting - ListInstalledSharePointVersions
  Restituisce un set di token che rappresentano le versioni di Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]o [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installate nello stesso computer del server di report.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Sub ListInstalledSharePointVersions(ByRef VersionTokens() _  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void ListReportServersInDatabase (out string[] VersionTokens,   
    out Int32 Length, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parametri  
 *VersionTokens[]*  
 [out] Matrice che contiene i token che rappresentano la versione di un prodotto o di una tecnologia SharePoint compatibile con il server di report installato.  
  
 *Lunghezza*  
 [out] Lunghezza della matrice dei token di versione.  
  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Un valore pari a 0 indica l'esito positivo della chiamata al metodo. Un valore diverso da zero indica che si è verificato un errore.  
  
## <a name="remarks"></a>Remarks  
 Ogni token restituito rappresenta una versione di [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] o [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] compatibile con il server di report attualmente installato. Se una particolare versione di SharePoint è compatibile con le versioni di SharePoint precedenti, vengono restituiti token per ogni versione di SharePoint compatibile.  
  
 Di seguito è riportata una tabella dei token di SharePoint restituiti.  
  
|**Token di versione**|**Descrizione**|  
|------------------------|---------------------|  
|WSS_V2_Compatible|È installata una versione di [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]o [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] compatibile con [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 2.0.|  
|WSS_V3_Compatible|È installata una versione di [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]o [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] compatibile con [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3.0.|  
|WSS_V4_Compatible|È installata una versione di [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] o [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] compatibile con Office 14.|  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
