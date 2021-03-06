---
title: Eseguire il backup elemento (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4e00a4991226779a91e16806dbe15973d946ec69
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38007151"
---
# <a name="backup-element-xmla"></a>Elemento Backup (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Esegue il backup di un database di Analysis Services in un file di backup.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Backup>  
      <Object>...</Object>  
      <File>...</File>  
      <Security>...</Security>  
      <ApplyCompression>...</ApplyCompression>  
      <AllowOverwrite>...</AllowOverwrite>  
      <Password>...</Password>  
      <BackupRemotePartitions>...</BackupRemotePartitions>  
      <Locations>...</Locations>  
   </Backup>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[AllowOverwrite](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md), [ApplyCompression](../../../analysis-services/xmla/xml-elements-properties/applycompression-element-xmla.md), [BackupRemotePartitions](../../../analysis-services/xmla/xml-elements-properties/backupremotepartitions-element-xmla.md), [File](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md), [posizioni](../../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md), [ Oggetto](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), [Password](../../../analysis-services/xmla/xml-elements-properties/password-element-xmla.md), [sicurezza](../../../analysis-services/xmla/xml-elements-properties/security-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Il **Backup** comando esegue il backup di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database specificato nella [oggetto](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) elemento in un file di backup e facoltativamente esegue il backup di partizioni remote nei file di backup remoti. Se il **oggetti** elemento fa riferimento a un oggetto diverso da un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] del database, si verifica un errore.  
  
 Il tipo di informazioni delle quali il comando **Backup** esegue il backup dipende dalla modalità di archiviazione utilizzata dagli oggetti nel database. Nella tabella seguente sono identificate le informazioni delle quali viene eseguito il backup in base alla modalità di archiviazione utilizzata.  
  
|Modalità di archiviazione|Informazioni delle quali viene eseguito il backup|  
|------------------|-----------------------------------|  
|OLAP multidimensionale (MOLAP)|Dati di origine, aggregazioni e metadati|  
|OLAP ibrido (HOLAP)|Aggregazioni e metadati|  
|OLAP relazionale (ROLAP)|Metadati|  
  
 Durante un **Backup** comando, viene inserito un blocco condiviso nel [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database indicato con il **oggetto** elemento. Il blocco condiviso viene rilasciato dopo il completamento del comando **Backup** .  
  
 Più **Backup** comandi possono essere eseguiti in parallelo, se i comandi sono inclusi nel [parallele](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md) raccolta di un [Batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) comando. La raccolta **Parallel** consente il backup di un database in più file di backup contemporaneamente.  
  
 Per altre informazioni sul backup e ripristino di database, vedere [backup, ripristino e sincronizzazione di database &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
> [!IMPORTANT]  
>  Per ogni file di backup, l'utente che esegue il comando di backup deve disporre delle autorizzazioni per scrivere nel percorso di backup specificato per ogni file. Inoltre, l'utente deve avere uno dei ruoli seguenti: deve essere un membro di un ruolo del server per l'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] oppure un membro di un ruolo del database con autorizzazioni Controllo completo (amministratore) sul database di cui eseguire il backup.  
  
## <a name="see-also"></a>Vedere anche
 [Elemento Restore &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Elemento Synchronize &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [I comandi &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
