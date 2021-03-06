---
title: Gestione connessione OData | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 3caa4372-aff3-4c0f-9ecd-97870948b8d0
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ac0ffe016e2c88a381b230a26c58be2f6b2087a3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48136631"
---
# <a name="odata-connection-manager"></a>Gestione connessione OData
  Con la gestione connessione OData è possibile connettere un pacchetto a un'origine OData. Tramite un componente di origine OData viene eseguita la connessione a un'origine OData mediante una gestione connessione OData e vengono utilizzati i dati del servizio. Visualizzare [origine OData](../data-flow/odata-source.md)sezione per informazioni dettagliate, incluse le istruzioni di installazione per questi componenti.  
  
## <a name="adding-connection-manager-to-an-ssis-package"></a>Aggiunta di gestione connessione a un pacchetto SSIS  
 È possibile aggiungere una nuova gestione connessione OData a un pacchetto SSIS nelle tre modalità seguenti:  
  
-   Fare clic sul pulsante **Nuovo** in **Editor origine OData**  
  
-   Fare doppio clic su **gestioni connessioni** cartella le **Esplora soluzioni** e fare clic su **nuova gestione connessione**. Selezionare **ODATA** per **Tipo gestione connessione**.  
  
-   Fare doppio clic nella **gestioni connessioni** riquadro nella parte inferiore del pacchetto della finestra di progettazione e seleziona **nuova connessione...** . Selezionare **ODATA** per **Tipo gestione connessione**.  
  
## <a name="connection-manager-authentication"></a>Autenticazione di gestione connessione  
 La gestione connessione OData supporta due modalità di autenticazione.  
  
-   Autenticazione di Windows  
  
-   Autenticazione di base (nome utente/password)  
  
 Per l'accesso anonimo, selezionare l'opzione Autenticazione di Windows.  
  
### <a name="specifying-and-securing-credentials"></a>Specifica e protezione delle credenziali  
 Se il servizio OData richiede l'autenticazione di base, è possibile specificare un nome utente e una password di [Editor gestione connessione OData](../odata-connection-manager-editor.md). I valori immessi nell'editor sono persistenti nel pacchetto. Il valore della password è crittografato in base al livello di protezione del pacchetto.  
  
 È possibile esternalizzare/impostare i parametri dei valori del nome utente e della password in più modalità. Le due modalità principali per eseguire questa operazione in [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] consistono nell'utilizzo dei parametri oppure nell'impostare le proprietà di gestione connessione direttamente quando si esegue il pacchetto mediante SQL Server Management Studio.  
  
## <a name="odata-connection-manager-properties"></a>Proprietà di gestione connessione OData  
 Nell'elenco seguente vengono descritte alcune delle proprietà di gestione connessione OData che è possibile modificare.  
  
|||  
|-|-|  
|Proprietà|Description|  
|URL|URL del documento di servizio.|  
|UserName|Nome utente da utilizzare per l'autenticazione di base.|  
|Password|Password da utilizzare per l'autenticazione di base.|  
|ConnectionString|Riflette altre proprietà della gestione connessione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Editor gestione connessione OData](../odata-connection-manager-editor.md)  
  
  
