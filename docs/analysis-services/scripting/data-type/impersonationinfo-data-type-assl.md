---
title: Il tipo di dati ImpersonationInfo (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ImpersonationInfo Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: ImpersonationInfo data type
ms.assetid: 8a6b55fe-1f02-4519-bdc2-4553b576b2f3
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f651898ff723f55b4d3c32ad31f462144d28946c
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="impersonationinfo-data-type-assl"></a>Tipo di dati ImpersonationInfo (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Definisce un tipo di dati primitivo che rappresenta le informazioni utilizzate per rappresentare un utente.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ImpersonationInfo>  
   <ImpersonationMode>...</ImpersonationMode>  
   <Account>...</Account>  
   <Password>   </Password>  
   <ImpersonationInfoSecurity>...</ImpersonationInfoSecurity>  
</ImpersonationInfo>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati di base|None|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[Account](../../../analysis-services/scripting/properties/account-element-impersonationinfo-assl.md), [ImpersonationInfoSecurity](../../../analysis-services/scripting/properties/impersonationinfosecurity-element-assl.md), [ImpersonationMode](../../../analysis-services/scripting/properties/impersonationmode-element-assl.md), [Password](../../../analysis-services/scripting/properties/password-element-assl.md)|  
|Elementi derivati|[DataSourceImpersonationInfo](../../../analysis-services/scripting/properties/datasourceimpersonationinfo-element-assl.md), [ImpersonationInfo](../../../analysis-services/scripting/properties/impersonationinfo-element-assl.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Analysis Services Scripting Language tipi di dati XML &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
