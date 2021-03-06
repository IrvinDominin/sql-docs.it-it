---
title: Gestione dei ruoli pacchetto a livello di programmazione (servizio SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, roles
- roles [Integration Services]
- packages [Integration Services], roles
ms.assetid: 2e0ca0d5-d4f5-421d-b17d-a48b37b923e5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 70e2be6eb03685b0f1c7165b4ace41c79304f74e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48047932"
---
# <a name="managing-package-roles-programmatically-ssis-service"></a>Gestione dei ruoli pacchetto a livello di programmazione (servizio SSIS)
  Quando si utilizzano i pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] a livello di programmazione, può essere necessario determinare quali ruoli possono essere applicati ai pacchetti oppure determinare o impostare i ruoli applicati a un singolo pacchetto. La classe <xref:Microsoft.SqlServer.Dts.Runtime.Application> dello spazio dei nomi <xref:Microsoft.SqlServer.Dts.Runtime> fornisce un'ampia varietà di metodi e classi per soddisfare questi requisiti.  
  
 I ruoli si applicano solo ai pacchetti archiviati nel database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb**. Per altre informazioni sui ruoli pacchetto, vedere [Ruoli Integration Services &#40;servizio SSIS&#41;](../security/integration-services-roles-ssis-service.md).  
  
 Tutti i metodi descritti in questo argomento richiedono un riferimento all'assembly `Microsoft.SqlServer.ManagedDTS`. Dopo aver aggiunto il riferimento in un nuovo progetto, importare lo spazio dei nomi <xref:Microsoft.SqlServer.Dts.Runtime> con un'istruzione `using` o `Imports`.  
  
> [!IMPORTANT]  
>  I metodi della classe <xref:Microsoft.SqlServer.Dts.Runtime.Application> per l'utilizzo dell'archivio pacchetti SSIS supportano solo ".", localhost o il nome del server locale. Non è possibile utilizzare "(local)".  
  
## <a name="determining-which-roles-are-available"></a>Verifica dei ruoli disponibili  
 Per determinare quali ruoli sono disponibili per i pacchetti archiviati in un determinato server, chiamare il metodo <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerRoles%2A> della classe <xref:Microsoft.SqlServer.Dts.Runtime.Application>.  
  
## <a name="determining-which-roles-are-assigned"></a>Verifica dei ruoli assegnati  
 Per determinare quali ruoli sono già stati assegnati a un determinato pacchetto, chiamare il metodo <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageRoles%2A>. Per assegnare ruoli a un pacchetto, chiamare il metodo <xref:Microsoft.SqlServer.Dts.Runtime.Application.SetPackageRoles%2A>.  
  
![Icona di Integration Services (piccola)](../media/dts-16.gif "icona di Integration Services (piccola)")**rimangono fino a Date con Integration Services** <br /> Per i download, gli articoli, gli esempi e i video Microsoft più recenti, oltre alle soluzioni selezionate dalla community, visitare la pagina [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sul sito MSDN:<br /><br /> [Visita la pagina di Integration Services su MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Per ricevere notifica automatica su questi aggiornamenti, sottoscrivere i feed RSS disponibili nella pagina.  
  
## <a name="see-also"></a>Vedere anche  
 [Ruoli Integration Services &#40;servizio SSIS&#41;](../security/integration-services-roles-ssis-service.md)  
  
  
