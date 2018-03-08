---
title: Impostazioni (conversione) (AccessToSQL) del progetto | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-access
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- conversion, options described
- Project Settings dialog box, Conversion
ms.assetid: bcebc635-c638-4ddb-924c-b9ccfef86388
caps.latest.revision: 
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ec31bf02ccdeedd4356d0a85c85d7d33041d5bde
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="project-settings-conversion-accesstosql"></a>Impostazioni del progetto (conversione) (AccessToSQL)
Le impostazioni di progetto di conversione consentono di configurare la modalità di conversione di oggetti da oggetti di database di Access da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o gli oggetti di database di SQL Azure.  
  
Il riquadro di conversione è disponibile nel **impostazioni progetto** e **impostazioni di progetto predefinite** finestre di dialogo.  
  
-   Utilizzare il **impostazioni progetto** la finestra di dialogo per impostare le opzioni di configurazione per il progetto corrente. Per accedere alle impostazioni di conversione, nel **strumenti** dal menu **impostazioni progetto**, fare clic su **generale** nella parte inferiore del riquadro sinistro, quindi scegliere **conversione**.  
  
-   Utilizzare il **impostazioni di progetto predefinite** la finestra di dialogo per impostare le opzioni di configurazione per tutti i progetti. Per accedere alle impostazioni di conversione, nel **strumenti** dal menu **impostazioni di progetto predefinite**, selezionare il tipo di progetto di migrazione per i quali impostazioni sono necessarie per essere visualizzati o modificati da **versione di destinazione della migrazione** elenco a discesa, fare clic su **generale** nella parte inferiore del riquadro sinistro, quindi scegliere **conversione**.  
  
## <a name="options"></a>Opzioni  
**Aggiungere la chiave primaria**  
Crea una nuova chiave primaria di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o una tabella di SQL Azure, se una tabella di accesso non dispone di alcuna chiave primaria o un indice univoco.  
  
-   **Modalità predefinita**: False  
  
-   **Modalità ottimistica**: False  
  
-   **Modalità**: True  
  
Quando si è connessi a SQL Azure, è per impostazione predefinita True. **Aggiungere colonne timestamp**  
Specifica se SSMA deve creare un valore di timestamp, se necessario.  
  
-   **Modalità predefinita**: SSMA consente di decidere  
  
-   **Modalità ottimistica**: mai  
  
-   **Modalità**: SSMA consente di decidere  
  
**Includere un report di valutazione di dati con i report di valutazione di conversione**  
Include una valutazione dei dati del report di valutazione.  
  
-   **Modalità predefinita**: True  
  
-   **Modalità ottimistica**: False  
  
-   **Modalità**: True  
  
**Tipo di messaggio quando una chiave primaria include colonne che ammettono valori null**  
Specifica il tipo di messaggio (avviso, errore o Nothing) contenente SSMA nel riquadro di Output quando trova le chiavi primarie con colonne che ammettono valori null.  
  
-   **Modalità predefinita**: avviso  
  
-   **Modalità ottimistica**: nessun messaggio  
  
-   **Modalità**: errore  
  
**Tipo di messaggio quando le colonne chiave esterna sono di dimensioni diverse**  
Specifica il tipo di messaggio (avviso, errore o Nothing) contenente SSMA nel riquadro di Output quando viene trovata una chiave esterna di testo non corretta.  
  
-   **Modalità predefinita**: avviso  
  
-   **Modalità ottimistica**: nessun messaggio  
  
-   **Modalità**: errore  
  
**Tipo di messaggio quando le colonne di dati memo siano indicizzate**  
Specifica il tipo di messaggio (avviso, errore o Nothing) contenente SSMA nel riquadro di Output quando rileva un indice che contiene un **memo** colonna.  
  
-   **Modalità predefinita**: avviso  
  
-   **Modalità ottimistica**: nessun messaggio  
  
-   **Modalità**: errore  
  
**Avvisa quando una query complessa viene utilizzato un carattere jolly (\&#42;)**  
Quando viene visualizzato un avviso nel riquadro di Output ed elenco errori un nome di colonna in un'istruzione SELECT è un carattere jolly (*).  
  
-   **Modalità predefinita**: True  
  
-   **Modalità ottimistica**: False  
  
-   **Modalità**: True  
  
**Avvisa quando viene modificato il nome di identificatore**  
Visualizza un messaggio nel rapporto di valutazione e nel riquadro di Output quando viene modificato un nome di identificatore di oggetto da SSMA.  
  
-   **Modalità predefinita**: True  
  
-   **Modalità ottimistica**: False  
  
-   **Modalità**: True  
  
**Avvisa se l'identificatore racchiuso tra virgolette**  
Visualizza un messaggio nel rapporto di valutazione e nel riquadro di Output quando racchiuso tra virgolette il nome di un identificatore di oggetto da SSMA. È necessario racchiudere tra virgolette gli identificatori, quando il nome è una parola chiave o contiene caratteri speciali.  
  
-   **Modalità predefinita**: True  
  
-   **Modalità ottimistica**: False  
  
-   **Modalità**: True  
  
## <a name="see-also"></a>Vedere anche  
[Reference(Access) dell'interfaccia utente](http://msdn.microsoft.com/en-us/af24c303-4a41-449b-9c86-d6558a97e839)  
  
