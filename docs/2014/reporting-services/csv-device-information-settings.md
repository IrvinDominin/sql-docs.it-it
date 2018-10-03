---
title: Impostazioni relative alle informazioni sul dispositivo CSV | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- CSV [Reporting Services]
- device information settings [Reporting Services], CSV rendering
ms.assetid: f96f83a6-50bc-48ce-9fcd-fd9e1952d40a
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2dfb27e467dc762c6591c8b820cb71302eac99fe
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48116911"
---
# <a name="csv-device-information-settings"></a>Impostazioni relative alle informazioni sul dispositivo CSV
  Le impostazioni relative alle informazioni sul dispositivo per l'estensione per il rendering CSV consentono di modificare i delimitatori e i qualificatori e di specificare il tipo di gestione delle interruzioni di riga. È anche possibile specificare l'estensione di file, nonché la codifica e l'inclusione delle righe di intestazione nell'output. Poiché in genere i delimitatori sono caratteri speciali, è necessario codificarli in una sezione CDATA, se le impostazioni sono scritte in formato XML.  
  
 Nella tabella seguente sono elencate le impostazioni relative alle informazioni sul dispositivo per il rendering in formato testo.  
  
|Impostazione|valore|  
|-------------|-----------|  
|`Encoding`|Il nome IANA (Internet Assigned Numbers Authority) di una codifica dei caratteri supportata da .NET Framework. Il valore predefinito è `UTF-8`. Esempi di altri valori includono ASCII, UTF-7 e UTF-16.|  
|`ExcelMode`|Specifica che l'output di destinazione è destinato a Excel. Il valore predefinito è `true`.|  
|`FieldDelimiter`|Stringa di delimitazione da inserire nel risultato. Il valore predefinito è una virgola (,). Quando si passano queste informazioni sul dispositivo a un URL, è necessario codificarne il valore. Un carattere di tabulazione utilizzato come delimitatore corrisponde ad esempio a "%09".<br /><br /> È possibile modificare il delimitatore di campo predefinito impostandolo su qualsiasi carattere desiderato, incluso TAB, modificando le impostazioni relative alle informazioni sul dispositivo nel file di configurazione. Per usare TAB, aggiornare ad esempio l'impostazione FieldDelimiter impostandola su \<FieldDelimiter xml:space="preserve">[TAB]\</FieldDelimiter><br /><br /> Nell'esempio [TAB] è un carattere di tabulazione effettivo, pertanto nel file di configurazione viene visualizzato una spazio vuoto. L'attributo "xml:space" indica al parser che lo spazio vuoto deve essere mantenuto.|  
|`FileExtension`|Estensione di file per il risultato. Il valore predefinito è `.CSV`. Se si specifica sia `FileExtension` che `Extension`, `FileExtension` ha la precedenza.|  
|**NoHeader**|Indica se la riga di intestazione è esclusa dall'output. Il valore predefinito è `false`.|  
|`Qualifier`|Qualificatore da inserire prima e dopo i risultati che contengono il delimitatore di campo o di record. Se i risultati contengono il qualificatore, il qualificatore viene ripetuto. L'impostazione `Qualifier` deve essere diversa dalle impostazioni `FieldDelimiter` e `RecordDelimiter`. Il valore predefinito è costituito dalle virgolette (").|  
|`RecordDelimiter`|Delimitatore di record da inserire alla fine di ogni record. Il valore predefinito è \<cr>\<lf>.|  
|**SuppressLineBreaks**|Indica se le interruzioni di riga vengono rimosse dai dati inclusi nell'output. Il valore predefinito è `false`. Se il valore è `true`, il `FieldDelimiter`, `RecordDelimiter`, e `Qualifier` impostazioni non possono essere un carattere di spazio.|  
|`UseFormattedValues`|Indica se le stringhe formattate vengono inserite nell'output CSV. Il valore predefinito è `true` quando si `ExcelMode` viene `true`; in caso contrario è `false`.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Il passaggio di impostazioni informazioni dispositivo a estensioni per il Rendering](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personalizzare i parametri di estensione per il rendering in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Riferimento tecnico &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
