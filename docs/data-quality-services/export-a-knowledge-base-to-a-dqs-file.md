---
title: Esportare una Knowledge Base in un file DQS | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: data-quality-services
ms.service: 
ms.component: data-quality-services
ms.reviewer: 
ms.suite: sql
ms.technology: data-quality-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a324ead5-c8aa-4e26-abe3-ef415add00f8
caps.latest.revision: "19"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1b7bca78f2d4538b1b4769efd3d34ba21ae019e6
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="export-a-knowledge-base-to-a-dqs-file"></a>Esportazione di una Knowledge Base in un file DQS
  In questo argomento viene descritto come esportare un'intera Knowledge Base in un file di dati con estensione DQS in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). È possibile esportare un dominio o una Knowledge Base intera in un file di dati. Per informazioni sull'esportazione di un dominio, vedere [Esportare un dominio in un file DQS](../data-quality-services/export-a-domain-to-a-dqs-file.md).  
  
 L'esportazione di una Knowledge Base in un file con estensione DQS e la successiva importazione in un'altra Knowledge Base semplifica il processo di generazione delle informazioni e consente di risparmiare tempo e impegno. La procedura permette di condividere una Knowledge Base e le relative informazioni con altri utenti. Il file DQS conterrà tutte le informazioni della Knowledge Base, compresi domini e i criteri di corrispondenza, tranne le informazioni sui dati di riferimento collegati. È necessario collegare nuovamente i domini richiesti ai servizi dati di riferimento appropriati, se necessario, dopo avere importato il file DQS. Vengono esportati sia i dati pubblicati che quelli non pubblicati in una Knowledge Base.  
  
 Il file di dati DQS creato dal processo di esportazione viene crittografato, pertanto non è possibile visualizzarne i contenuti.  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
 Per esportare una Knowledge Base in un file di dati DQS, è necessario avere creato e aperto una Knowledge Base. Non è necessario disporre di un file DQS in cui esportare, in quanto verrà creato automaticamente.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Per esportare una Knowledge Base da un file DQS è necessario disporre del ruolo dqs_kb_editor o dqs_administrator nel database DQS_MAIN.  
  
##  <a name="Export"></a> Export a knowledge base to a .dqs file  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Eseguire l'applicazione Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Nella schermata iniziale del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] aprire una Knowledge Base nell'attività Gestione dominio.  
  
3.  Nella pagina Gestione dominio (con qualsiasi scheda selezionata), fare clic sull'icona **Esporta dati Knowledge Base** sopra l'elenco di domini, quindi fare clic su **Esporta Knowledge Base**. In alternativa, è possibile fare clic con il pulsante destro del mouse sull'elenco **Dominio** , selezionare **Esporta**, quindi fare clic su **Esporta Knowledge Base**.  
  
4.  Nella finestra di dialogo **Esporta in file di dati** spostarsi nella cartella in cui si vuole salvare il file, denominare il file o mantenere il nome della Knowledge Base, mantenere **File di dati DQS (\*.dqs)** in **Salva come** e fare clic su **Salva**.  
  
5.  Nella finestra di dialogo **Esporta Knowledge Base** verificare che la riga dello stato indichi che l'esportazione è stata completata. Fare clic su **OK**.  
  
##  <a name="FollowUp"></a> Completamento: Dopo avere esportato un dominio in un file DQS  
 Una volta esportata una Knowledge Base in un file DQS, è possibile importarla nello stesso [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] (con un nuovo nome) o in un [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]diverso.  
  
  
