---
title: Destinazione SQL Server Compact Edition | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.sqlservercompactdest.f1
helpviewer_keywords:
- destinations [Integration Services], SQL Server Compact
- SQL Server Compact, destination
- inserting data
ms.assetid: 697742ba-cc14-414d-8187-1845ad0dd99b
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ff9b88f90db3348f07eb768ed3d50c7dc7e5a7dd
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="sql-server-compact-edition-destination"></a>Destinazione SQL Server Compact Edition
  La destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact consente di scrivere dati in database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
> [!NOTE]  
>  In un computer a 64 bit è necessario eseguire pacchetti che si connettono a origini dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact in modalità a 32 bit. Il provider [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact usato in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per la connessione a origini dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact è disponibile solo nella versione a 32 bit.  
  
 Per configurare la destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, è necessario specificare il nome della tabella in cui la destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact inserisce i dati. Il TableName è contenuto nella proprietà personalizzata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] della destinazione Compact.  
  
 Per connettersi a un'origine dati, questa destinazione usa una gestione connessione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact che specifica il provider OLE DB da usare. Per altre informazioni, vedere [Configurazione della gestione connessione SQL Server Compact Edition](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md).  
  
 La destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact include la proprietà personalizzata TableName, che può essere aggiornata da un'espressione di proprietà al caricamento del pacchetto. Per altre informazioni, vedere [Espressioni di Integration Services &#40;SSIS&#41;](../../integration-services/expressions/integration-services-ssis-expressions.md), [Utilizzo delle espressioni di proprietà nei pacchetti](../../integration-services/expressions/use-property-expressions-in-packages.md) e [Proprietà personalizzate della destinazione SQL Server Compact Edition](../../integration-services/data-flow/sql-server-compact-edition-destination-custom-properties.md).  
  
 La destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact prevede un solo input e non supporta un output degli errori.  
  
## <a name="configuration-of-the-sql-server-compact-edition-destination"></a>Configurazione della destinazione SQL Server Compact Edition  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Nella finestra di dialogo **Editor avanzato** sono disponibili le proprietà che è possibile impostare a livello di codice. Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Proprietà personalizzate della destinazione SQL Server](../../integration-services/data-flow/sql-server-destination-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Per altre informazioni su come impostare le proprietà del componente, vedere [Impostazione delle proprietà di un componente del flusso di dati](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Flusso di dati](../../integration-services/data-flow/data-flow.md)  
  
  
