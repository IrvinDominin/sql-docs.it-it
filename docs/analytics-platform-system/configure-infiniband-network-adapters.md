---
title: Configurare InfiniBand - Analitica Platform System | Documenti Microsoft
description: Viene descritto come configurare le schede di rete InfiniBand in un server non strumento client per connettersi al nodo di controllo in Parallel Data Warehouse (PDW). Utilizzare queste istruzioni per la connettività di base e per la disponibilità elevata, in modo che il caricamento, i processi di backup e altri si connettono automaticamente alla rete InfiniBand attiva.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 8e67d63e7bb4bded0bd19e5db4a0b7faddb80977
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
ms.locfileid: "31539021"
---
# <a name="configure-infiniband-network-adapters-for-analytics-platform-system"></a>Configurare le schede di rete InfiniBand per Analitica Platform System
Viene descritto come configurare le schede di rete InfiniBand in un server non strumento client per connettersi al nodo di controllo in Parallel Data Warehouse (PDW). Utilizzare queste istruzioni per la connettività di base e per la disponibilità elevata, in modo che il caricamento, i processi di backup e altri si connettono automaticamente alla rete InfiniBand attiva.  
  
## <a name="Basics"></a>Descrizione  
Queste istruzioni viene illustrato come trovare e impostare quindi InfiniBand IP corretti, indirizzi e subnet mask sul server collegato InfiniBand. Viene inoltre illustrato come impostare il server da utilizzare lo strumento di APS DNS in modo che si risolve la connessione alla rete InfiniBand attiva.  
  
Per la disponibilità elevata, punti di accesso dispone di due reti InfiniBand, uno attivo e uno passivo. Ogni rete InfiniBand dispone di un indirizzo IP diverso per il nodo di controllo. Se la rete InfiniBand active diventa inattiva, la rete InfiniBand passiva diventa rete attiva. Quando ciò si verifica uno script o un processo si connette automaticamente alla rete InfiniBand active senza modificare i parametri dello script.  
  
In particolare, in questo articolo è:  
  
1.  Trovare gli indirizzi IP InfiniBand del DNS APS server (appliance_domain AD01 e appliance_domain *-AD02). A tale scopo è possibile accedere con il server AD01 e AD02 e ottenere gli indirizzi IP per ogni rete InfiniBand. Gli indirizzi IP InfiniBand nel nodo Active Directory sono gli indirizzi IP del DNS.  
  
2.  Configurare ogni scheda di rete per l'utilizzo di un indirizzo IP disponibile nelle reti InfiniBand punti di accesso.  
  
    1.  Se si dispone di due schede di rete InfiniBand, si configura una scheda con un indirizzo IP disponibile nella rete InfiniBand primo che viene chiamato TeamIB1, mentre l'altra con un indirizzo IP disponibile nella rete InfiniBand secondo cui viene chiamata TeamIB2. Indirizzo IP di utilizzare il TeamIB1 appliance_domain AD01 come server DNS preferito e TeamIB1 appliance_domain AD02 indirizzo IP del server DNS alternativo per la scheda di rete TeamIB1. Indirizzo IP di utilizzare il TeamIB2 appliance_domain AD01 come server DNS preferito e TeamIB2 appliance_domain AD02 indirizzo IP del server DNS alternativo per TeamIB2 scheda di rete.  
  
    2.  Se si dispone di una sola scheda di rete InfiniBand, configurare l'adapter con un indirizzo IP disponibile da una delle reti InfiniBand. Quindi configurare il valore desiderato e i server DNS alternativi in questa scheda utilizzando TeamIB1 appliance_domain AD01 e AD02 appliance_domain TeamIB1 o TeamIB2 appliance_domain AD01 e AD02 appliance_domain TeamIB2 a seconda del valore è nella stessa rete rispettivamente come l'adapter configurato come il valore desiderato e i server DNS alternativi.  
  
3.  Configurare la scheda di rete InfiniBand per utilizzare i server DNS di APS per risolvere la connessione alla rete InfiniBand attiva.  
  
    1.  Per configurare questa opzione che è usare le impostazioni avanzate TCP/IP per aggiungere il suffisso DNS del dominio accessorio all'inizio dell'elenco dei suffissi DNS sul server client. Questo è solo necessario configurare su una delle schede di rete; l'impostazione si applica a entrambe le schede.  
  
Dopo aver configurato le schede di rete InfiniBand, i processi client possono connettersi al nodo di controllo nella rete InfiniBand tramite `PDW_region-SQLCTL01` per l'indirizzo del server. Il server aggiunge il suffisso DNS di sistema della piattaforma Analitica, o è possibile immettere l'indirizzo completo, ovvero `PDW_region-SQLCTL01.appliance_domain.pdw.local`.  
  
Ad esempio, se il nome dell'area PDW è MyPDW e il nome del dispositivo è MyAPS, la specifica del server dwloader per il caricamento dei dati è uno dei valori seguenti:  
  
-   `dwloader –S MYPDW-SQLCTL01.MyAPS.pdw.local`  
  
-   `dwloader –S MYPDW-SQLCTL01`  
  
## <a name="BeforeBegin"></a>Prima di iniziare  
  
### <a name="requirements"></a>Requisiti  
È necessario un account di dominio accessorio APS per accedere al nodo AD01. Ad esempio, F12345 * \administrator.  
  
È necessario un account di Windows nel server che dispone dell'autorizzazione per configurare le schede di rete client.  
  
### <a name="prerequisites"></a>Prerequisiti  
Queste istruzioni presuppongono il server di client è già stato centralizzato in remoto e connesso alla rete InfiniBand accessorio. Per su rack e i cavi di istruzioni, vedere [acquisire e configurare un Server durante il caricamento](acquire-and-configure-loading-server.md).  
  
### <a name="general-remarks"></a>Osservazioni generali  
Tramite SQLCTL01, Analitica piattaforma del sistema DNS si connette server client al nodo di controllo utilizzando la rete InfiniBand attive. Questo vale solo per connettere; Se la rete InfiniBand diventa inattiva durante un backup o il carico, è necessario riavviare il processo.  
  
Per soddisfare i requisiti aziendali specifici, è possibile aggiungere anche il server del client al gruppo di lavoro non accessorio o dominio Windows.  
  
## <a name="Sec1"></a>Passaggio 1: Ottenere il dispositivo le impostazioni di rete InfiniBand  
*Per ottenere le impostazioni di rete InfiniBand di dispositivo*  
  
1.  Accedere al dispositivo AD01 nodo utilizzando l'account appliance_domain\Administrator.  
  
2.  Nel nodo AD01 del dispositivo, aprire il pannello di controllo, selezionare rete, Internet, selezionare la rete e condivisione Center *, quindi Modifica impostazioni scheda.  
  
3.  Nella finestra connessioni di rete, fare clic su IB1 Team e selezionare proprietà.  
  
    ![Connessioni InfiniBand nel nodo di gestione](media/network-teamib.png "connessioni InfiniBand nel nodo di gestione")  
  
4.  Dalla finestra Proprietà protocollo Internet versione 4 (TCP/IPv4), annotare i valori per il **indirizzo IP** e **Subnet mask**.  L'indirizzo IP del ***appliance_domain *-AD01** nodo è l'indirizzo IP del server DNS di sistema di piattaforma Analitica.  
  
5.  Ripetere i passaggi da 1 a 5 per l'adapter TeamIB1 su ***appliance_domain *-AD02** server.  
  
    ![Proprietà InfiniBand 1 nodo Gestione PDW](media/network-ip1-properties.png "proprietà InfiniBand 1 nodo Gestione PDW")  
  
6.  Fare clic su Annulla per chiudere la finestra.  
  
7.  Trovare un indirizzo IP inutilizzato nella rete TeamIB1 e prenderne nota.  
  
    Per trovare un indirizzo IP inutilizzato, aprire una finestra di comando e provare a eseguire il ping di indirizzi IP all'interno dell'intervallo di indirizzi per il dispositivo. In questo esempio, l'indirizzo IP della rete TeamIB1 è 172.16.14.30. Trovare un indirizzo IP che inizia con 172.16.14 non utilizzato. Ad esempio, dalla riga di comando immettere "ping 172.16.14.254". Se la richiesta di ping ha esito negativo, l'indirizzo IP è disponibile.  
  
8.  Eseguire la stessa operazione per TeamIB2. Nel * finestra connessioni di rete, fare clic su IB2 Team e selezionare proprietà.  
  
9. Dalla finestra Proprietà protocollo Internet versione 4 (TCP/IPv4), annotare i valori per l'indirizzo IP e Subnet mask per TeamIB2.  
  
10. Ripetere i passaggi da 8 a 9 per la scheda TeamIB2 appliance_domain AD02 server.  
  
    ![Proprietà per TeamIB2](media/network-ip2-properties.png "proprietà per TeamIB2")  
  
11. Trovare un indirizzo IP inutilizzato nella **TeamIB2** di rete e prenderne nota.  
  
    Per trovare un indirizzo IP inutilizzato, aprire una finestra di comando e provare a eseguire il ping di indirizzi IP all'interno dell'intervallo di indirizzi per il dispositivo. In questo esempio, l'indirizzo IP della rete TeamIB2 è 172.16.18.30. Trovare un indirizzo IP che inizia con 172.16.18 non utilizzato. Ad esempio, dalla riga di comando immettere "ping 172.16.18.254". Se la richiesta di ping ha esito negativo, l'indirizzo IP è disponibile.  
  
## <a name="Sec2"></a>Passaggio 2: Configurare le impostazioni della scheda di rete InfiniBand nel Server Client  

### <a name="notes"></a>Note  
  
-   La procedura mostra come registrare il server con i server DNS APS.  
  
-   Per soddisfare le proprie esigenze di rete, è possibile aggiungere anche il server del client al gruppo di lavoro non accessorio o dominio Windows.  
  
-   Il passaggio di istruzioni tramite la configurazione di due schede di rete in ogni server.  Se si dispone solo di una scheda di rete, selezionare una delle reti per configurare la scheda di rete e quindi aggiungere il secondo indirizzo IP DNS come server DNS alternativo.  
  
### <a name="to-configure-the-infiniband-network-adapter-settings-on-your-client-server"></a>Per configurare le impostazioni della scheda di rete InfiniBand nel server client  
  
1.  Accedere come amministratore di Windows per il caricamento, il backup o altri server client sul dispositivo rete InfiniBand.  
  
2.  Aprire il riquadro controllo * selezionare centro rete e condivisione e quindi scegliere Modifica impostazioni scheda.  
  
### <a name="to-configure-the-first-network-adapter"></a>Per configurare la prima scheda di rete  
  
1.  Nella finestra connessioni di rete, fare clic su uno degli slot di rete non identificata per l'Adapter Mellanox e selezionare proprietà.  
  
    ![Selezionare le reti InfiniBand](media/network-connections.png "selezionare le reti InfiniBand")  
  
2.  Nella finestra proprietà  
  
    1.  Nella scheda Generale, impostare l'indirizzo IP per l'indirizzo IP è considerato disponibile nel test di ping per TeamIB1. Per i valori di esempio usati in questo articolo, immettere 172.16.14.254.  
  
    2.  Impostare la subnet mask per la subnet mask che si è preso nota per TeamIB1.  
  
    3.  Impostare il server DNS preferito per l'indirizzo IP del TeamIB1 che si è preso nota in precedenza da appliance_domain *-AD01 nodo.  
  
    4.  Impostare il server DNS alternativo per l'indirizzo IP del TeamIB1 che si è preso nota in precedenza da appliance_domain *-AD02 nodo.  
  
        ![Proprietà dell'Adapter 1 rete InfiniBand](media/network-ib1-properties.png "SQL_Server_PDW_Network_IB1_properties")  
  
    5.  Fare clic su OK per applicare le modifiche.  
  
### <a name="to-configure-the-second-network-adapter"></a>Per configurare la seconda scheda di rete  
  
1.  Ignorare questa sezione se si dispone solo di una scheda di rete.  
  
2.  Nella finestra connessioni di rete, fare clic sul secondo slot di rete non identificata per l'Adapter Mellanox e selezionare proprietà.  
  
    ![Selezionare le reti InfiniBand](media/network-connections.png "selezionare le reti InfiniBand")  
  
3.  Nella finestra proprietà  
  
    1.  Nella scheda Generale, impostare l'indirizzo IP per l'indirizzo IP è considerato disponibile nel test di ping per TeamIB2. Per i valori di esempio usati in questo articolo, immettere 172.16.18.254.  
  
    2.  Impostare la subnet mask per la subnet mask che si è preso nota per TeamIB2.  
  
    3.  Impostare il server DNS preferito per l'indirizzo IP del TeamIB2 che si è preso nota in precedenza da appliance_domain *-AD01 nodo.  
  
    4.  Impostare il server DNS alternativo per l'indirizzo IP del TeamIB2 che si è preso nota in precedenza da appliance_domain *-AD02 nodo.  
  
        > [!NOTE]  
        > Se si dispone solo una scheda di rete, configurare i Preferiti e i server DNS alternativi utilizzando rispettivamente l'accessorio TeamIB1 AD01 e appliance AD02 TeamIB1 come i Preferiti e i server DNS alternativi oppure utilizzare lo strumento TeamIB2 AD01 e accessorio TeamIB2 AD02 come il valore desiderato e i server DNS alternativi a seconda che la macchina virtuale di Active Directory ha eseguito il failover.  
  
        ![Proprietà dell'Adapter 1 rete InfiniBand](media/network-ib1-properties.png "proprietà scheda di rete 1 InfiniBand")  
  
    5.  Fare clic su OK per applicare le modifiche.  
  
### <a name="to-configure-the-dns-suffix"></a>Per configurare il suffisso DNS  
  
1.  Nella finestra connessioni di rete, fare clic su uno degli slot di rete per la scheda Mellanox e selezionare proprietà.  
  
2.  Fare clic su Avanzate... .  
  
3.  Nella finestra Impostazioni TCP/IP avanzate, se l'operazione di Accodamento opzione questi suffissi DNS (in ordine) non è disattivata, chiamata la casella di controllo Aggiungi questi suffissi DNS (in ordine): selezionare il suffisso del dominio applicazione e fare clic su Aggiungi... Il suffisso di dominio del dispositivo `appliance_domain.local`  
  
4.  Se l'operazione di Accodamento questi DNS suffissi (in ordine): opzione è disattivata, è possibile aggiungere il dominio dei punti di accesso a questo server modificando la chiave del Registro di sistema HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows NT\DNSClient.  
  
    ![Impostazioni TCP/IP](media/network-tcpip.png "impostazioni TCP/IP")  
  
5.  Per la risoluzione degli indirizzi più veloce, è consigliabile spostare il suffisso accessorio nella parte superiore dell'elenco.  
  
6.  Fare clic su OK.  
  
7.  A questo punto, è possibile connettersi alla rete Infiniband accessorio utilizzando `PDW_region-SQLCTL01.appliance_domain.local`, o semplicemente `appliance_domain-SQLCTL01`. Se ci si connette con il nome completo e il suffisso DNS, è possibile stabilire la connessione più veloce.  
  
    Esempi per un'applicazione denominata MyAPS con un'area PDW MyPDW:  
  
    -   MyPDW-SQLCTL01.MyAPS.local  
  
    -   MyPDW-SQLCTL01  
  
## <a name="see-also"></a>Vedere anche  
[Acquisire e configurare un Server di caricamento ](acquire-and-configure-loading-server.md)  
  
