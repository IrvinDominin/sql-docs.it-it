---
title: Domande frequenti sul driver JDBC | Microsoft Docs
ms.custom: ''
ms.date: 07/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cbc0e397-ecf2-4494-87b2-a492609bceae
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2f0197ed97f8d03784cd89d2bede5a4e7744e80f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47613419"
---
# <a name="frequently-asked-questions-faq-for-jdbc-driver"></a>Domande frequenti sul driver JDBC

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Questa pagina offre le risposte alle domande frequenti su Microsoft JDBC Driver per SQL Server.

## <a name="frequently-asked-questions"></a>Domande frequenti

**Come contribuire a migliorare il Driver JDBC?**  
Il Driver JDBC è open source e il codice sorgente è reperibile sul [GitHub](https://github.com/microsoft/mssql-jdbc). È possibile migliorare il driver di archiviazione problemi che contribuiscono alla base di codice.

**Quali versioni di SQL Server e Java sono supportate dal driver?**  
Vedere la pagina [Matrice di supporto di Microsoft JDBC Driver per SQL Server](../../connect/jdbc/microsoft-jdbc-driver-for-sql-server-support-matrix.md) per altri dettagli.

**Che cos'è la differenza tra i pacchetti di driver JDBC disponibili nel Microsoft Download Center e il driver JDBC disponibile su GitHub?**  
File del driver JDBC disponibili nel repository di GitHub per Microsoft JDBC driver sono il nucleo del driver JDBC e sono in base alla licenza open source elencata nel repository. I pacchetti driver nel Microsoft Download Center includono librerie aggiuntive per l'autenticazione integrata di Windows e abilitare le transazioni XA con il driver JDBC. Tali librerie aggiuntive sono sotto la licenza inclusa con il pacchetto scaricabile.

**Quali informazioni sono necessarie prima di aggiornare il driver?**  
 Microsoft JDBC Driver 7.0 supporta 4.3 specifiche (parzialmente) e JDBC 4.2 e include due librerie di classi JAR nel pacchetto di installazione, come indicato di seguito:

| JAR                        | Specifica JDBC            | Versione JDK |
| -------------------------- | ----------------------------- | ----------- |
| mssql-jdbc-7.0.0.jre10.jar | JDBC 4.3 (parzialmente) e 4.2 | JDK 10.0    |
| mssql-jdbc-7.0.0.jre8.jar  | JDBC 4.2                      | JDK 8.0     |

Microsoft JDBC Driver 6.4 supporta JDBC 4.1, 4.2 e 4.3 (parzialmente) specifiche e include tre librerie di classi JAR nel pacchetto di installazione, come indicato di seguito:

| JAR                       | Specifica JDBC                 | Versione JDK |
| ------------------------- | ---------------------------------- | ----------- |
| mssql-jdbc-6.4.0.jre9.jar | JDBC 4.3 (parzialmente), 4.2 e 4.1 | JDK 9.0     |
| mssql-jdbc-6.4.0.jre8.jar | JDBC 4.2 e 4.1                  | JDK 8.0     |
| mssql-jdbc-6.4.0.jre7.jar | JDBC 4.1                           | JDK 7.0     |

Microsoft JDBC Driver 6.2 supporta le specifiche JDBC 4.2, 4.1 e 4.0 e include due librerie di classi JAR nel pacchetto di installazione, come indicato di seguito:

| JAR                       | Specifica JDBC     | Versione JDK |
| ------------------------- | ---------------------- | ----------- |
| MSSQL-jdbc-6.2.2.jre8.jar | JDBC 4.2, 4.1 e 4.0 | JDK 8.0     |
| MSSQL-jdbc-6.2.2.jre7.jar | JDBC 4.1 e 4.0       | JDK 7.0     |

Microsoft JDBC driver 6.0 e 4.2 per SQL Server supporta le specifiche JDBC 4.0, 4.1 e 4.2 e includono due librerie di classi JAR nel pacchetto di installazione, come indicato di seguito:

| JAR           | Specifica JDBC     | Versione JDK |
| ------------- | ---------------------- | ----------- |
| sqljdbc42.jar | JDBC 4.2, 4.1 e 4.0 | JDK 8.0     |
| sqljdbc41.jar | JDBC 4.1 e 4.0       | JDK 7.0     |

Microsoft JDBC Driver 4.1 per SQL Server supporta la specifica JDBC 4.0 e include una libreria di classi JAR nel pacchetto di installazione, come indicato di seguito:

| JAR           | Specifica JDBC | Versione JDK     |
| ------------- | ------------------ | --------------- |
| sqljdbc41.jar | JDBC 4.0           | JDK 7.0 e 6.0 |

**È necessario modificare in qualche modo il codice dell'applicazione per usare il driver più recente con la versione di SQL Server esistente?**  
In generale, il driver è progettato per essere compatibile con le versioni precedenti in modo che non sia necessario modificare le applicazioni esistenti quando si aggiorna il driver. Nel caso in cui una nuova versione del driver introduca una modifica di rilievo, il [note sulla versione per il Driver JDBC](../../connect/jdbc/release-notes-for-the-jdbc-driver.md) sezione fornisce tutti i dettagli necessari su tale modifica e dell'impatto sulle applicazioni esistenti. Inoltre, è possibile esaminare le note sulla versione incluse con il driver per un elenco dei bug corretti in tale versione e per i problemi noti.

**Quanto costa il driver?**  
Microsoft JDBC Driver per SQL Server è disponibile gratuitamente.

**È possibile ridistribuire il driver?**
Il driver JDBC 4.1, 4.2, 6.0, 6.2, 6.4 e 7.0 sono ridistribuibili. Esaminare la clausola "Codice distribuibile" nei contratti di licenza.

**È possibile usare il driver per accedere a Microsoft SQL Server da un computer Linux?**
Sì. È possibile usare il driver per accedere a SQL Server da Unix, Linux e altre piattaforme non Windows. Per altre informazioni, vedere [Microsoft JDBC Driver per SQL Server Support Matrix](../../connect/jdbc/microsoft-jdbc-driver-for-sql-server-support-matrix.md).

**Il driver supporta la crittografia Secure Sockets Layer (SSL)?**
A partire dalla versione 1.2, il driver supporta la crittografia Secure Sockets Layer (SSL). Per altre informazioni, vedere[Uso della crittografia SSL](../../connect/jdbc/using-ssl-encryption.md).

**Quali tipi di autenticazione supporta Microsoft JDBC Driver per SQL Server?**  
La tabella seguente elenca le opzioni di autenticazione disponibili. L'autenticazione Kerberos Java pura è disponibile a partire dalla versione 4.0 del driver.

|             |                                       |
| ----------- | ------------------------------------- |
| Piattaforma    | Autenticazione                        |
| Non Windows | Kerberos Java pura                    |
| Non Windows | SQL Server                            |
| Non Windows | Autenticazione di Azure Active Directory |
| Windows     | Kerberos Java pura                    |
| Windows     | SQL Server                            |
| Windows     | Kerberos con backup NTLM             |
| Windows     | NTLM                                  |
| Windows     | Autenticazione di Azure Active Directory |

**Il driver supporta gli indirizzi del protocollo IPv6?**  
Sì. Il driver supporta l'uso di indirizzi IPv6. Usare la raccolta di proprietà di connessione e la proprietà di stringa di connessione serverName. Per altre informazioni, vedere [Costruzione dell'URL di connessione](../../connect/jdbc/building-the-connection-url.md).

**Che cos'è il buffering adattivo?**  
Il buffer adattivo è stato introdotto a partire da Microsoft SQL Server 2005 JDBC Driver versione 1.2. È progettato per recuperare qualsiasi tipo di dati con valori di grandi dimensioni senza l'overhead dei cursori server. La funzionalità di buffering adattivo di Microsoft SQL Server JDBC Driver fornisce una proprietà della stringa di connessione responseBuffering che può essere impostata su "adattiva" o "completa". Nella versione 1.2 la modalità di buffering predefinita è "full" e l'applicazione deve impostare la modalità di buffering adattivo in modo esplicito. A partire da JDBC Driver versione 2.0 il comportamento predefinito è "adattivo". Per ottenere il comportamento di buffering adattivo, l'applicazione non deve quindi richiederlo in modo esplicito. Per altre informazioni, vedere [Uso del buffering adattivo](../../connect/jdbc/using-adaptive-buffering.md) e il post di blob [What is adaptive response buffering and why should I use it?](http://go.microsoft.com/fwlink/?LinkId=111575) (Che cos'è il buffering con risposta adattativa e perché è consigliabile usarlo?).

**Il driver supporta il pool di connessioni?**  
Il driver fornisce il supporto per il pool di connessioni Java Platform, Enterprise Edition 5 (Java EE 5). Il driver implementa le interfacce JDBC 3.0 necessarie per consentire al driver di partecipare a qualsiasi implementazione di pool di connessioni offerta dai fornitori di server applicazioni middleware. Il driver partecipa alle connessioni in pool in questi ambienti. Per altre informazioni, vedere [Uso del pool di connessioni](../../connect/jdbc/using-connection-pooling.md). Il driver non fornisce una propria implementazione di pool, ma si basa su server applicazioni Java di terze parti.

**È disponibile il supporto per il driver?**  
Sono disponibili diverse opzioni di supporto. È possibile pubblicare una domanda o inviare al nostro [repository GitHub](https://github.com/microsoft/mssql-jdbc) che viene monitorato da Microsoft. [Forum](http://go.microsoft.com/fwlink/?LinkID=246673) monitorate da Microsoft, MVP e community. È anche possibile contattare il Supporto tecnico Microsoft. Il team di sviluppo potrebbe richiedere di riprodurre il problema all'esterno di eventuali server applicazioni di terze parti. Se il problema non può essere riprodotto all'esterno dell'ambiente contenitore Java che lo ospita, sarà necessario coinvolgere le terze parti interessate per consentire al team di continuare a offrire assistenza. Il team potrebbe essere anche richiesto di riprodurre il problema in un sistema operativo, ad esempio Windows, in modo che il problema può essere più supportato.

**Il driver è certificato per l'uso con server applicazioni di terze parti?**
Il driver è stato testato nei principali server applicazioni, inclusi IBM WebSphere e SAP NetWeaver.

**Come si abilita la traccia?**  
Il driver supporta l'utilizzo della traccia (o registrazione) per semplificare la risoluzione dei problemi relativi all'utilizzo del driver JDBC nell'applicazione. Per abilitare l'utilizzo della traccia JAR sul lato client, il driver JDBC usa le API di registrazione in java.util.logging. Per altre informazioni, vedere [Creazione di tracce](../../connect/jdbc/tracing-driver-operation.md). Per informazioni sulla traccia XA sul lato server, vedere la pagina relativa alla [traccia di accesso ai dati in SQL Server](http://go.microsoft.com/fwlink/?LinkId=248705).

**Da dove è possibile scaricare le versioni precedenti del driver, ad esempio SQL Server 2000 JDBC Driver, 2005 Driver oppure le versioni del driver 1.0, 1.1 o 1.2?**  
Queste versioni del driver non sono disponibili per il download perché non sono più supportate. Il supporto per la connettività Java è in continuo miglioramento, pertanto è consigliabile usare sempre la versione più recente del driver Microsoft JDBC.

**Si sta usando JRE 1.4. Quali sono i driver compatibili?**  
I clienti che usano prodotti SAP e richiedono il supporto di JRE 1.4 possono contattare [SAPService Marketplace](http://service.sap.com/) per ottenere Microsoft JDBC Driver 1.2.

**Il driver può comunicare usando gli algoritmi FIPS convalidati?**  
Microsoft JDBC Driver non contiene algoritmi di crittografia. Se un cliente usa algoritmi del sistema operativo, dell'applicazione e JVM considerati accettabili da FIPS (Federal Information Processing Standard) e configura il driver per l'uso di tali algoritmi, il driver usa solo gli algoritmi designati per la comunicazione.

## <a name="see-also"></a>Vedere anche

[Panoramica del driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)
