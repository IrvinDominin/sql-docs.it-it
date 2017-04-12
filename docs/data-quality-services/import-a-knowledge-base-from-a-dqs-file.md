---
title: "Importazione di una Knowledge Base da un file DQS | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b9786fe-9e80-429a-afcb-dc3b3dd6f0b0
caps.latest.revision: 17
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 17
---
# Importazione di una Knowledge Base da un file DQS
  In questo argomento viene descritto come importare un'intera Knowledge Base da un file di dati con estensione DQS in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Creare il file di dati esportando una knowledge base esistente dall'interno di [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] applicazione (vedere [esportare una Knowledge Base in un File DQS](../data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)).  
  
 L'utilizzo di un file di dati DQS per l'esportazione del contenuto di una Knowledge Base e la successiva reimportazione del contenuto in un'altra Knowledge Base nello stesso [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] , o su un [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] diverso, semplifica il processo di generazione delle informazioni e consente di risparmiare tempo e impegno. La procedura permette di condividere una Knowledge Base e le relative informazioni con altri utenti, consentendo in tal modo anche ad essi un notevole risparmio di tempo. Il file DQS conterrà tutte le informazioni della Knowledge Base, compresi domini e i criteri di corrispondenza, tranne le informazioni sui dati di riferimento collegati. Verranno importati sia i dati pubblicati che quelli non pubblicati.  
  
 I file di dati DQS sono crittografati, pertanto non è possibile visualizzarne il contenuto.  
  
 Quando si importa una Knowledge Base, è possibile utilizzare lo stesso nome, a meno che il nome della Knowledge Base già esista nell'applicazione client, nel qual caso sarà necessario modificarlo.  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
 Per importare una Knowledge Base da un file DQS, è necessario avere già esportato la Knowledge Base nel file DQS.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Per importare una Knowledge Base da un file DQS è necessario disporre del ruolo dqs_kb_editor o dqs_administrator nel database DQS_MAIN.  
  
##  <a name="Import"></a> Importazione di una Knowledge Base da un file DQS  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Eseguire l'applicazione Client Data Quality](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Nella schermata iniziale del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] fare clic su **Nuova Knowledge Base**.  
  
3.  Immettere un nome per la Knowledge Base.  
  
4.  Fare clic sulla freccia in giù per **Crea Knowledge Base da**, quindi selezionare **Importa da file DQS**.  
  
5.  Per **Seleziona il file di dati**, fare clic su **Sfoglia**.  
  
6.  Nella finestra di dialogo **Importa da file di dati** spostarsi nella cartella contenente il file DQS da importare, quindi fare clic sul nome del file. Fare clic su **Apri**.  
  
7.  Verificare che la Knowledge Base e i domini corretti vengano visualizzati nell'elenco dei **Domini** .  
  
8.  Selezionare l'attività che si desidera eseguire, quindi fare clic su **Crea**.  
  
9. Nella finestra di dialogo **Importa Knowledge Base** verificare che la riga dello stato indichi che l'importazione è stata completata. Scegliere **OK**.  
  
10. Completare l'individuazione delle informazioni, la gestione del dominio o l'attività dei criteri di corrispondenza richieste, quindi fare clic su **Fine**.  
  
11. Fare clic su **Pubblica** per pubblicare le informazioni nella Knowledge Base o **No** per non pubblicarle.  
  
12. Se si è scelto di pubblicare la Knowledge Base, fare clic su **OK**.  
  
13. Nella pagina iniziale di Data Quality Services, verificare che la Knowledge Base sia elencata in **Knowledge Base recenti**.  
  
##  <a name="FollowUp"></a> Completamento: Dopo avere importato una Knowledge Base da un file DQS  
 Dopo avere importato una Knowledge Base da un file DQS, è possibile aggiungervi informazioni o utilizzarla per progetti di pulizia o di individuazione delle corrispondenze, a seconda del suo contenuto. Per ulteriori informazioni, vedere [eseguire l'individuazione delle informazioni](../data-quality-services/perform-knowledge-discovery.md), [gestione di un dominio](../data-quality-services/managing-a-domain.md), [la gestione di un dominio composito](../data-quality-services/managing-a-composite-domain.md), [creare un criterio di corrispondenza](../data-quality-services/create-a-matching-policy.md), [la pulizia dei dati](../data-quality-services/data-cleansing.md), o [corrispondenza dei dati](../data-quality-services/data-matching.md).  
  
  