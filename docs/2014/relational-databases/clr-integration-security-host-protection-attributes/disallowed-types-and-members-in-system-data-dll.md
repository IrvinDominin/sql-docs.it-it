---
title: Non consentito di tipi e membri in System | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: ee5f55e9-fbef-401a-be18-a2e5873c8720
caps.latest.revision: 17
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 728de68145c4deb7b259c7b59687e29e960c822a
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37353973"
---
# <a name="disallowed-types-and-members-in-systemdatadll"></a>Tipi e membri non consentiti in System.Data.dll
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] programmazione dell'integrazione (CLR) comuni del linguaggio non consente l'utilizzo di un tipo o membro che dispone di un `HostProtectionAttribute` che specifica una `System.Security.Permissions.HostProtectionResource` con un valore di enumerazione `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, **SharedState**, `Synchronization`, o `UI`. Nella tabella seguente sono elencati i membri e i tipi dell'assembly System.Data.dll i cui valori degli attributi di protezione host non sono consentiti.  
  
> [!NOTE]  
>  Questo elenco è stato generato dagli assembly supportati. Per altre informazioni, vedere [librerie di .NET Framework supportate](../clr-integration/database-objects/supported-net-framework-libraries.md).  
  
|Tipo o membro|Valori dell'attributo di protezione host|  
|--------------------|--------------------|  
|System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery()|ExternalThreading|  
|System.Data.SqlClient.SqlCommand.BeginExecuteReader()|ExternalThreading|  
|System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency..ctor()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency.Start()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency.Stop()|ExternalThreading|  
|System.Data.TypedDataSetGenerator|SharedState, Synchronization|  
|System.Xml.XmlDataDocument|Synchronization|  
  
## <a name="see-also"></a>Vedere anche  
 [Attributi di protezione host e programmazione dell'integrazione con CLR](host-protection-attributes-and-clr-integration-programming.md)   
 [Tipi non consentiti e i membri in VisualBasic](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)   
 [Tipi non consentiti e i membri in mscorlib. dll](disallowed-types-and-members-in-mscorlib-dll.md)   
 [Tipi non consentiti e i membri in System. dll](disallowed-types-and-members-in-system-dll.md)   
 [Tipi e membri non consentiti in System.Core.dll](disallowed-types-and-members-in-system-core-dll.md)  
  
  
