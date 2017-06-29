---
title: Librerie di classi di elemento di Report personalizzato | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom report items, RDL
- RDL [Reporting Services], custom report items
ms.assetid: f18c5d8f-1d6b-4f0b-8657-c14896c2ce0d
caps.latest.revision: 27
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: f216228c01e835e88cd9d4c7d7d4190648a386db
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="custom-report-item-class-libraries"></a>Librerie di classi dell'elemento del report personalizzato
  Elementi del report personalizzati di usare le classi dal **Microsoft.ReportDesigner** dello spazio dei nomi. Le classi utilizzate per implementare un elemento del report personalizzato possono essere suddivise in due categorie principali: le classi univoche progettate per supportare l'infrastruttura dell'elemento del report personalizzato e le classi wrapper gestite che incapsulano la funzionalità degli elementi RDL (Report Definition Language) rilevanti. Per un esempio di codice su come usare queste classi, vedere [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="custom-report-item-infrastructure-classes"></a>Classi di infrastruttura dell'elemento del report personalizzato  
 Le classi riportate di seguito vengono utilizzate per implementare un elemento del report personalizzato.  
  
> [!NOTE]  
>  Nelle tabelle seguenti non vengono forniti elenchi completi, ma solo le proprietà e i metodi utilizzati più di frequente per ciascuna classe.  
  
### <a name="microsoftreportdesignercustomreportitemdesigner"></a>Microsoft.ReportDesigner.CustomReportItemDesigner  
 È la classe principale dell'elemento del report personalizzato. La classe principale dell'implementazione dell'elemento del report personalizzato deve ereditare da questa classe.  
  
#### <a name="public-properties"></a>Proprietà pubbliche  
  
|||  
|-|-|  
|**Nome**|Nome dell'elemento del report personalizzato.|  
|**Tipo**|Tipo di elemento del report personalizzato.|  
|**CustomData**|Oggetto <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> che incapsula le proprietà dei dati dell'elemento del report personalizzato specificate in fase di progettazione.|  
|**CustomProperties**|Raccolta di proprietà personalizzate per l'elemento del report personalizzato.|  
|**Altezza**|Altezza del controllo dell'elemento del report personalizzato.|  
|**Larghezza**|Larghezza del controllo dell'elemento del report personalizzato.|  
|**Report**|Contenitore per le proprietà a livello di report, ad esempio l'elenco dei set di dati nel report.|  
|**AltReportItem**|Oggetto elemento del report alternativo, da utilizzare se il controllo di runtime di un elemento del report personalizzato non è supportato.|  
|**Stile**|Proprietà di stile per l'elemento del report personalizzato.|  
|**Area di controllo**|Finestra dell'area di controllo utilizzata per la modifica interattiva del controllo.|  
|**Sito**|Il **ISite** del componente.|  
|**Insieme DesignerVerbCollection**|Matrice di verbi personalizzati per il menu di scelta rapida del controllo.|  
  
#### <a name="public-methods"></a>Metodi pubblici  
  
|||  
|-|-|  
|**BeginEdit**|Attiva la modifica interattiva per il controllo.|  
|**DoDefaultAction**|Viene chiamato quando si fa doppio clic o si preme Invio sul controllo.|  
|**EndEdit**|Disattiva la modifica interattiva per il controllo.|  
|**GetService**|Restituisce un oggetto che rappresenta un servizio.|  
|**InitializeNewComponent**|Viene chiamato quando si crea un nuovo elemento del report personalizzato.|  
|**Invalidare**|Ridisegna l'intera superficie del controllo.|  
|**OnDragEnter**<br /><br /> **OnDragDrop**|Viene chiamato quando si trascina un oggetto sul controllo.|  
|**OnPaint**|Chiamato in risposta al **Paint** evento.|  
  
### <a name="microsoftreportdesignercustomreportitemattribute"></a>Microsoft.ReportDesigner.CustomReportItemAttribute  
 Attributo utilizzato per identificare il tipo di elemento del report personalizzato. Il nome deve corrispondere al valore del \< **nome**> attributo del **ReportItem** elemento nel file di configurazione di progettazione Report.  
  
#### <a name="public-methods"></a>Metodi pubblici  
  
|||  
|-|-|  
|**CustomReportItemAttribute**|Crea l'oggetto CustomReportItemAttribute.|  
  
### <a name="microsoftreportdesignerlocalizednameattribute"></a>Microsoft.ReportDesigner.LocalizedNameAttribute  
 Attributo utilizzato per specificare il nome visualizzato da utilizzare per la finestra di progettazione dell'elemento del report personalizzato.  
  
#### <a name="public-methods"></a>Metodi pubblici  
  
|||  
|-|-|  
|**LocalizedNameAttribute**|Crea l'oggetto LocalizedNameAttribute.|  
  
### <a name="microsoftreportdesigneradornment"></a>Microsoft.ReportDesigner.Adornment  
 Il **dell'area di controllo** classe viene utilizzata dal componente in fase di progettazione dell'elemento di report personalizzato per fornire aree esterne al rettangolo principale dell'area di progettazione. Tali aree possono gestire eventi dell'interfaccia utente, quali clic del mouse e operazioni di trascinamento della selezione.  
  
#### <a name="public-methods"></a>Metodi pubblici  
  
|||  
|-|-|  
|**OnShow**|Chiamato quando il **dell'area di controllo** è attivato.|  
|**OnHide**|Chiamato quando il **dell'area di controllo** viene disattivato.|  
|**Disegno**|Chiamato in risposta al **Paint** evento.|  
|**OnDragEnter**<br /><br /> **OnDragOver**<br /><br /> **OnDragLeave**<br /><br /> **OnDragDrop**|Chiamata eseguita quando un oggetto viene trascinato il **dell'area di controllo**.|  
  
### <a name="microsoftreportdesigneradornerservice"></a>Microsoft.ReportDesigner.AdornerService  
 Questa classe viene utilizzata per fornire una raccolta di servizi visualizzati utilizzati dall'elemento del report personalizzato per supportare **dell'area di controllo** oggetti per il componente in fase di progettazione di elemento del report personalizzato.  
  
#### <a name="public-properties"></a>Proprietà pubbliche  
  
|||  
|-|-|  
|**AdornerWindowBounds**|Limiti della finestra Adorner.|  
|**AdornerWindowRegion**|Area della finestra Adorner.|  
|**AdornerWindowGraphics**|Contesto grafico per la finestra Adorner.|  
  
#### <a name="public-methods"></a>Metodi pubblici  
  
|||  
|-|-|  
|**ComponentRectInDesignerFrame**|Restituisce i limiti del componente convertito nelle coordinate della cornice della finestra di progettazione.|  
|**InvalidateAdorner**|Invalida la finestra Adorner.|  
|**PointToAdorner**|Restituisce un punto nelle coordinate dello schermo convertito nelle coordinate della finestra Adorner.|  
  
### <a name="microsoftreportdesignerexpressioneditor"></a>Microsoft.ReportDesigner.ExpressionEditor  
 Questa classe può essere utilizzata da un controllo della fase di progettazione dell'elemento del report personalizzato per richiamare l'Editor espressioni.  
  
#### <a name="public-methods"></a>Metodi pubblici  
  
|||  
|-|-|  
|**EditValue**|Richiama l'Editor espressioni, inizializzato con il valore dell'oggetto specificato.|  
  
### <a name="microsoftreportdesignerifieldsdataobject"></a>Microsoft.ReportDesigner.IFieldsDataObject  
 Questa classe è una raccolta di campi di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e viene utilizzata per supportare eventi di trascinamento della selezione nell'ambiente di progettazione. Eredita da **IReportItemDataObject**.  
  
#### <a name="public-properties"></a>Proprietà pubbliche  
  
|||  
|-|-|  
|**DataSetName**|Nome del set di dati contenente i campi da eliminare.|  
|**Campi**|La raccolta di campi (**Microsoft.ReportDesigner.Field**) da eliminare.|  
  
## <a name="see-also"></a>Vedere anche  
 [Report Definition Language &#40; SSRS &#41;](../../reporting-services/reports/report-definition-language-ssrs.md)   
 [Creazione di un componente di Run-Time di elemento di Report personalizzato](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [Creazione di un componente in fase di progettazione dell'elemento del Report personalizzato](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)  
  
  