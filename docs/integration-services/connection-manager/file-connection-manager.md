---
title: "Gestione connessione file | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "cartelle [Integration Services], connessioni"
  - "file [Integration Services], connessioni"
  - "file [Integration Services]"
  - "gestioni connessioni [Integration Services], File"
  - "connessioni [Integration Services], file"
  - "gestione connessione file"
ms.assetid: 019078bc-44ee-4975-9169-0f9a89e3f3be
caps.latest.revision: 50
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 50
---
# Gestione connessione file
  Una gestione connessione file consente a un pacchetto di fare riferimento a un file o a una cartella esistente oppure di creare un file o una cartella in fase di esecuzione. Ad esempio, è possibile fare riferimento a un file di Excel. Le informazioni presenti nei file vengono utilizzate da alcuni componenti di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per effettuare le operazioni. L'attività Esegui SQL può ad esempio fare riferimento a un file che contiene le istruzioni SQL eseguite dall'attività. In altri componenti le operazioni vengono effettuate nei file. Ad esempio, tramite l'attività File System è possibile fare riferimento a un file per copiarlo in una nuova posizione.  
  
## Tipi di utilizzo per la gestione connessione file  
 Tramite la proprietà **FileUsageType** della gestione connessione file viene specificata la modalità di utilizzo della connessione file. La gestione connessione file può creare un file o una cartella oppure utilizzare un file o una cartella esistente.  
  
 Nella tabella seguente vengono elencati i possibili valori di **FileUsageType**.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**0**|La gestione connessione file utilizza un file esistente.|  
|**1**|La gestione connessione file crea un file.|  
|**2**|La gestione connessione file utilizza una cartella esistente.|  
|**3**|La gestione connessione file crea una cartella.|  
  
## Connessioni a più file o cartelle  
 La gestione connessione file può fare riferimento solo a un file o a una cartella. Per fare riferimento a più file o cartelle, al posto di una gestione connessione file utilizzare una gestione connessione per più file. Per altre informazioni, vedere [Multiple Files Connection Manager](../../integration-services/connection-manager/multiple-files-connection-manager.md).  
  
## Configurazione della gestione connessione file  
 Quando si aggiunge una gestione connessione file a un pacchetto, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crea una gestione connessione che in fase di esecuzione verrà risolta in una connessione file, imposta le proprietà della connessione file e la aggiunge alla raccolta **Connections** del pacchetto.  
  
 La proprietà **ConnectionManagerType** della gestione connessione viene impostata su **FILE**.  
  
 Per configurare una gestione connessione file, procedere nel modo seguente:  
  
-   Specificare il tipo di utilizzo.  
  
-   Specificare un file o una cartella.  
  
 È possibile impostare la proprietà ConnectionString per la gestione connessione file specificando un'espressione nella finestra Proprietà di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Tuttavia, per evitare un errore di convalida quando si usa un'espressione per specificare il file o la cartella, aggiungere il percorso di un file o di una cartella in **Editor gestione connessione file** per **File/Cartella**.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , vedere [Editor gestione connessione file](../../integration-services/connection-manager/file-connection-manager-editor.md).  
  
 Per informazioni sulla configurazione di una gestione connessione a livello di programmazione, vedere <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> e [Aggiunta di connessioni a livello di programmazione](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
  