---
title: Classi di sicurezza AMO | Documenti Microsoft
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Analysis Management Objects, security
- security [AMO]
- AMO, security
ms.assetid: e3d5012a-8121-40de-9244-1fc824228693
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 151642efa920091a95002f0dad8857986ed98861
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="amo-security-classes"></a>Classi di sicurezza AMO
  In questo argomento sono incluse le sezioni seguenti:  
  
-   [Oggetti Role e RoleMember](#RolesMembers)  
  
-   [Oggetti di autorizzazione](#Permissions)  
  
 Nella figura seguente viene illustrata la relazione delle classi descritte in questo argomento.  
  
 ![Classi di sicurezza in AMO descritte in questo argomento](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-securityclasses.gif "classi di sicurezza in AMO descritte in questo argomento")  
  
##  <a name="RolesMembers"></a>Oggetti Role e RoleMember  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.Role>, aggiungerlo alla raccolta di ruoli nel server, quindi aggiornare l'oggetto <xref:Microsoft.AnalysisServices.Role> nel server tramite il metodo Update. Prima che sia possibile utilizzare un oggetto <xref:Microsoft.AnalysisServices.Role>, è necessario aggiornarlo.  
  
 Per rimuovere un oggetto <xref:Microsoft.AnalysisServices.Role>, è necessario eliminarlo tramite il metodo Drop dell'oggetto <xref:Microsoft.AnalysisServices.Role>. Il metodo Remove disponibile nella raccolta dei ruoli impedisce solo la visualizzazione del ruolo nell'applicazione, ma non rimuove il ruolo dal server. Non è possibile eliminare un oggetto <xref:Microsoft.AnalysisServices.Role> se è presente un'autorizzazione associata all'oggetto stesso.  
  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.RoleMember>, aggiungere un utente alla raccolta di membri del ruolo, quindi aggiornare l'oggetto <xref:Microsoft.AnalysisServices.Role> nel server tramite il metodo Update. Solo agli amministratori del server e del database è consentita la creazione di ruoli. È necessario che un oggetto <xref:Microsoft.AnalysisServices.Role> sia aggiornato nel server prima che a uno qualsiasi dei relativi membri sia consentito utilizzare uno degli oggetti per cui sono state concesse le autorizzazioni all'utente.  
  
 Per rimuovere un oggetto <xref:Microsoft.AnalysisServices.RoleMember>, eliminarlo dalla raccolta tramite il metodo Remove della raccolta stessa, quindi aggiornare il ruolo tramite il metodo aggiorna.  
  
 Per ulteriori informazioni sui metodi e sulle proprietà disponibili per tali oggetti, vedere <xref:Microsoft.AnalysisServices.Role> e <xref:Microsoft.AnalysisServices.RoleMember> in <xref:Microsoft.AnalysisServices>.  
  
##  <a name="Permissions"></a>Oggetti di autorizzazione  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.Permission>, aggiungerlo alla raccolta di autorizzazioni dell'oggetto, quindi aggiornare l'oggetto <xref:Microsoft.AnalysisServices.Permission> nel server tramite il metodo Update.  
  
 Per rimuovere un oggetto <xref:Microsoft.AnalysisServices.Permission>, è necessario eliminarlo tramite il metodo Drop dell'oggetto. Il metodo Remove disponibile nella raccolta di autorizzazioni impedisce solo la visualizzazione delle autorizzazioni nell'applicazione, ma non rimuove l'oggetto <xref:Microsoft.AnalysisServices.Permission> dal server. Non è possibile eliminare un ruolo se è presente un'autorizzazione associata al ruolo stesso.  
  
 Per ulteriori informazioni sui metodi e sulle proprietà disponibili, vedere <xref:Microsoft.AnalysisServices.Permission> in <xref:Microsoft.AnalysisServices>.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices>   
 [Programmazione di oggetti di sicurezza AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-security-objects.md)   
 [Le autorizzazioni e diritti di accesso &#40; Analysis Services - dati multidimensionali &#41;](http://msdn.microsoft.com/library/59fa3573-f985-46cb-8042-7da71bd59a7b)   
 [Introduzione a classi AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [Architettura logica &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Gli oggetti di database &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
