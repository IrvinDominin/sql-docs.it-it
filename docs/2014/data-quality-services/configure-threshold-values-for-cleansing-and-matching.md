---
title: Configurare valori soglia per le attività di pulizia e di individuazione delle corrispondenze | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.admin.config.general.f1
helpviewer_keywords:
- cleansing,threshold value
- cleansing threshold values
- matching,threshold value
ms.assetid: d2305409-7115-45a4-8f60-1213c0a47368
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e69ad6e0cecc592bb25c2d07c48ccc52662538dc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48201437"
---
# <a name="configure-threshold-values-for-cleansing-and-matching"></a>Configurazione dei valori soglia per le attività di pulizia e di individuazione delle corrispondenze
  In questo argomento viene descritto come configurare valori soglia che verranno utilizzati durante le attività computerizzate di pulizia e di individuazione delle corrispondenze in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Per configurare i valori soglia è necessario disporre del ruolo dqs_administrator per il database DQS_MAIN.  
  
##  <a name="Configure"></a> Configurazione dei valori soglia  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Eseguire l'applicazione Data Quality Client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Nella schermata iniziale del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] fare clic su **Configurazione**.  
  
3.  Fare clic sulla scheda **Impostazioni generali** . Questa scheda consente di specificare valori soglia per le attività di pulizia e individuazione delle corrispondenze.  
  
4.  Per specificare valori soglia per l'attività di pulizia, specificare valori adatti nelle caselle seguenti nell'area **Pulizia interattiva** :  
  
    -   **Punteggio minimo per suggerimenti**: il punteggio minimo o livello di confidenza che verrà utilizzato in DQS per suggerire sostituzioni per un valore durante il processo di pulizia computerizzato. Immettere un valore nella notazione decimale del valore percentuale corrispondente. Ad esempio, digitare 0,75 per 75%. Questo valore deve essere minore o uguale al valore specificato nella casella **Punteggio minimo per correzioni automatiche** . Il valore predefinito è 0,7.  
  
    -   **Punteggio minimo per correzioni automatiche**: il punteggio minimo o livello di confidenza che verrà utilizzato in DQS per correggere automaticamente un valore durante il processo di pulizia computerizzato. Immettere un valore nella notazione decimale del valore percentuale corrispondente. Ad esempio, digitare 0,9 per 90%. Il valore predefinito è 0,8.  
  
5.  Per specificare il valore soglia per l'attività di individuazione delle corrispondenze, specificare un valore nella casella **Punteggio record minimo** nell'area **Corrispondenza** . Questo valore rappresenta il punteggio minimo per considerare un record come corrispondenza per un altro record. Il valore predefinito è 80.  
  
6.  Scegliere **Chiudi**.  
  
  
