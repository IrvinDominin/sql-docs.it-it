---
title: "Novità di SSMA per Oracle (OracleToSQL) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 03/01/2018
ms.reviewer: 
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f305ebb6-7393-4a43-abb3-6332b739d690
caps.latest.revision: 
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 63bc96b49c351d9923c5e4d4ae59056c7911ae40
ms.sourcegitcommit: 6a5b80cac78fe5c2d2567a391daa335f9b4b3637
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/01/2018
---
# <a name="whats-new-in-ssma-for-oracle-oracletosql"></a>Novità di SSMA per Oracle (OracleToSQL)
Questo argomento elenca SSMA delle modifiche Oracle in ogni versione.  

## <a name="ssma-v77"></a>SSMA v7.7
La versione v7.7 di SSMA per Oracle sono incluse le modifiche seguenti:
- SSMA per Oracle è stata migliorata con le correzioni di destinazione che consentono di migliorare le metriche di qualità e la conversione.
- In base a grande richiesta, la versione a 32 bit di SSMA per Oracle è nuovo. Se confrontato con l'implementazione precedente (prima v7.4), sono disponibili due pacchetti di installazione, ma non possono essere installati side-by-side. Di conseguenza, è necessario scegliere la versione più appropriata in base ai componenti di connettività che è. È sempre preferibile usare la versione a 64 bit, se possibile.
- SQL Server 2017 è ora il supporto ufficiale con il pacchetto di estensione Oracle supportati anche in Linux (nuova opzione di installazione remota). Si noti che la funzionalità di estensione Pack è limitata durante l'installazione su Linux, il tester e funzionalità di migrazione dei dati lato server non sono supportate 
- SSMA per Oracle consente di eseguire la migrazione di viste materializzate come normali tabelle (può essere configurato tramite le impostazioni di **impostazioni progetto** -> **sincronizzazione**  ->  **Individuare le tabelle di supporto per le viste materializzate**).

> [!IMPORTANT]
> Con SSMA v7.4 e versioni successive, .net 4.5.2 è un prerequisito di installazione.

## <a name="ssma-v76"></a>SSMA v7.6
La versione v7.6 di SSMA per Oracle è stata migliorata con le correzioni di destinazione che consentono di migliorare le metriche di qualità e la conversione e con il supporto per SQL Server 2017 (anteprima pubblica). Supporto per SQL Server 2017 in Windows e Linux è disponibile in anteprima pubblica e non deve essere utilizzato per le migrazioni di produzione.

> [!IMPORTANT]
> Con SSMA v7.4 e versioni successive, .net 4.5.2 è un prerequisito di installazione e la versione a 32 bit dello strumento è stata interrotta.

## <a name="ssma-v75"></a>SSMA v7.5
La versione v7.5 di SSMA per Oracle sono incluse le modifiche seguenti:
- Migliorato con numerosi miglioramenti per garantire maggiore accessibilità per persone affette da disabilità.
- Aggiornato per migliorare la metrica della qualità e la conversione con correzioni di destinazione, ad esempio la gestione dei tipi di dati date e float durante la migrazione dei dati, in base ai suggerimenti dei clienti avanzata.

> [!IMPORTANT]
> .NET 4.5.2 è un prerequisito per l'installazione di SSMA v7.5. Inoltre, a partire da v7.4, la versione a 32 bit di SSMA è stata sospesa.

## <a name="ssma-v74"></a>SSMA v7.4
La versione v7.4 di SSMA per Oracle sono incluse le modifiche seguenti:

- SSMA per Oracle supporta ora Azure SQL Data Warehouse come piattaforma di destinazione per la migrazione.

    ![Finestra Nuovo progetto](../media/new-project.png)
  - Supporta le opzioni di archiviazione del Data Warehouse, come illustrato nella figura seguente:

    ![opzioni di archiviazione per data warehouse](../media/storage-options_red.png)
  - Supporta le opzioni di distribuzione di dati, come illustrato nella figura seguente:

    ![distribuzione dei dati per data warehouse](../media/data-distribution_red.png)

- Il **timeout Query** l'opzione è disponibile durante l'individuazione di oggetti dello schema all'origine e di destinazione.

    ![valore di timeout query](../media/query-timeout_red.png)

- La metrica della qualità e la conversione è stata migliorata con le correzioni di destinazione, in base ai suggerimenti dei clienti.

> [!IMPORTANT]
> .NET 4.5.2 è un prerequisito per l'installazione di SSMA v7.4. Inoltre, a partire da v7.4, la versione a 32 bit di SSMA è stata sospesa.

## <a name="ssma-v73"></a>SSMA v7.3
La versione v7.3 di SSMA per Oracle sono incluse le modifiche seguenti:
- Metrica qualità e la conversione migliorata con le correzioni di destinazione in base ai suggerimenti dei clienti.
- Framework di estendibilità SSMA esposta tramite gli elementi seguenti:
  - La funzionalità di esportazione per un progetto di SQL Server Data Tools (SSDT).
    -   È ora possibile esportare script dello schema da SSMA a un progetto SSDT. È possibile utilizzare gli script di schema per apportare ulteriori modifiche dello schema e distribuire il database.
![Comando progetto SSDT Salva con nome](../media/export-schema-scripts_red.png)
  - Librerie che possono essere utilizzate da SSMA per l'esecuzione di conversioni personalizzate.
    - È ora possibile creare codice in grado di gestire le conversioni di sintassi personalizzata e che non sono stati precedentemente gestite dal SSMA.
      - Le istruzioni su come costruire un convertitore personalizzato sono disponibili in questo post di blog [funzionalità di conversione della estensione SQL Server Migration Assistant](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/).
      - Progetto di esempio per la conversione possibile scaricare questo [post di blog](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/).


## <a name="ssma-v72"></a>SSMA v7.2
La versione di SSMA per Oracle di versione 7.2 contiene le seguenti modifiche:
- Metrica qualità e la conversione migliorata con le correzioni di destinazione in base ai suggerimenti dei clienti.
- Miglioramenti di telemetria per fornire una migliore punti dati per risolvere i problemi dei clienti e migliorare il tasso di conversione di SSMA.

## <a name="ssma-v71"></a>V 7.1 SSMA
La versione v 7.1 di SSMA per Oracle sono incluse le seguenti modifiche:
- 2017 di SQL Server in Windows e Linux CTP1 è una piattaforma di destinazione supportate per la migrazione. Questa funzionalità è disponibile in anteprima tecnica e consente lo spostamento di dati e lo schema per i server SQL di destinazione.
- SSMA supporta ora gli aggiornamenti automatici per scaricare la versione più recente di SSMA è disponibile.
- I file binari installabili SSMA ora vengono recapitati tramite file di pacchetto di Windows installer (MSI).

**Risorse**

[Estensione delle funzionalità di SQL Server Migration Assistant conversione](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)

[Valutare e migrare i dati da piattaforme di dati non Microsoft per SQL Server *(con un esempio di Oracle)*](https://blogs.msdn.microsoft.com/datamigration/2016/11/16/sql-server-migration-assistant-how-to-assess-and-migrate-databases-from-non-microsoft-data-platforms-to-sql-server/) 

## <a name="may-2016"></a>Maggio 2016  
La versione di maggio 2016 di SSMA per Oracle sono incluse le seguenti modifiche:  

-   Aggiunta del supporto per SQL Server 2016.
-   Aggiunta conversione delle tabelle di archiviazione di Oracle flashback alle tabelle temporali di SQL Server.
-   Aggiunta la conversione del criterio VPD Oracle convertire in oggetti Criteri di SQL Server (protezione di livello di riga per Oracle).
-   Ora di una riduzione del carico iniziale per Oracle.
-   Resolver e il parser migliorate.
-   Rimuovere il controllo di programma di installazione per .net 2.0.
-   Aggiornato estensione dipendenza del Pack da .net 3.5 per .net 4.0.
-   Fisso "Salva"progetto "progetto aperto" comandi e per la Console di SSMA.
-   Comando predefinito "securepassword" per la Console di SSMA.
-   Fissa il conteggio di oggetti per il caricamento iniziale.
-   Correzione di conversione dei tipi di dati carattere per Oracle.
-   Correzione del bug nelle impostazioni globali.
  
## <a name="march-2016"></a>Marzo 2016  
La versione di anteprima di marzo 2016 di SSMA per Oracle sono incluse le seguenti modifiche:  
  
-   Aggiunta del supporto per la migrazione a SQL Server 2016.  
-   Aggiunta del supporto per la migrazione sicurezza Oracle a livello di riga (con alcune limitazioni).  
-   Aggiunto il supporto per la migrazione di tabelle Oracle in memoria all'archivio di colonna di SQL Server.  
  
## <a name="january-2016"></a>Gennaio 2016  
Il mese di gennaio 2014 manutenzione versione di SSMA per Oracle sono incluse le seguenti modifiche:  
  
-   Aggiunta del supporto per gli indici cluster.  
-   Correzione di query di schema Oracle lente (RFC 5076207).  
-   Fisso connettersi ad Azure da console.  
-   Aggiunta Log menu Visualizza per SSMA (RFC 5706203). 
-   Aggiunta di telemetria.  
  
## <a name="july-2014"></a>Luglio 2014  
La versione di luglio 2014 di SSMA per Oracle sono incluse le seguenti modifiche:  
  
-   Aggiunta del supporto per database SQL di Azure.  
-   Funzionalità di estensione pack spostato nello schema per il supporto di database SQL di Azure.  
-   Aggiunta del supporto per le viste materializzate Oracle.  
-   Tabelle con ottimizzazione aggiunto il supporto per la memoria di SQL Server 2014.  
-   Miglioramenti delle prestazioni inclusi testato per i database con più di 10k oggetti.  
-   Aggiunti miglioramenti dell'interfaccia utente per la gestione con un numero elevato di oggetti.  
-   Aggiungere l'evidenziazione degli schemi LOB "noti".  
-   Inclusi i miglioramenti di velocità di conversione.  
-   Aggiunta del supporto per la visualizzazione oggetto conta nell'interfaccia utente.  
-   Dimensioni del report ridotta da più di 25%.
-   Messaggi di errore migliorati per i costrutti non analizzati.  
  
## <a name="april-2014"></a>Aprile 2014  
La versione di aprile 2014 di SSMA per Oracle sono incluse le seguenti modifiche:  
  
-   Aggiunta del supporto di Microsoft SQL Server 2014.  
-   Aggiunta del supporto di ottimizzazione di Oracle 12 e query.  
-   Bug risolti sulla conversione in Azure.  
-   Bug risolti per le pagine del report invisibile in Internet Explorer 10.  
  
## <a name="january-2012"></a>Gennaio 2012  
La versione di gennaio 2012 di SSMA per Oracle sono incluse le seguenti modifiche:  
  
-   Aggiunta del supporto per i parametri di input RowType e RecordType automaticamente impostati su NULL.  
  
## <a name="july-2011"></a>Luglio 2011  
La versione di luglio 2011 di SSMA per Oracle sono incluse le seguenti modifiche:  
  
-   Aggiunto il supporto per la conversione della sequenza di Oracle da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] generatore di sequenza "Denali".  
-   Una migliore segnalazione errori durante la migrazione dei dati.  
-   Conversione miglioramento dell'istruzione di utilizzo di parole riservate.  
-   Migliorate conversione implicita del valore di data in una funzione.  
  
## <a name="april-2011"></a>Aprile 2011  
La versione di aprile 2011 di SSMA per Oracle sono incluse le seguenti modifiche:  
  
-   Singolo prodotto "SSMA per Oracle", che supporta [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] "Denali".  
-   Aggiunto il supporto per la connessione e la migrazione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] "Denali".  
-   Modulo di migrazione avanzata dei dati sul lato client, che supporta la migrazione parallela dei dati.  
-   Prestazioni migrazione di dati migliorate con semplici e di massa registrato i modelli di recupero.  
-   Aggiunta del supporto per la compatibilità con le versioni precedenti dei progetti creati con versioni precedenti di SSMA (v 4.0 e v 4.2).  
-   Aggiunta la possibilità di installare SSMA per Oracle v 5.0 prodotto affiancata (SxS) con le versioni precedenti di SSMA (v 4.0 e v 4.2).  
-   Aggiunta del supporto per i tipi definiti dall'utente (include sottotipo, VARRAY, tabella nidificata, tabella oggetti e visualizzazione di oggetti) e relativo utilizzo in blocchi PL/SQL con messaggi di errore speciale di reporting.  

## <a name="july-2010"></a>Luglio 2010  
La versione di luglio 2010 di SSMA per Oracle sono incluse le seguenti modifiche:  
  
-   Aggiunta del supporto per la migrazione a SQL Server 2008 R2.  
-   Aggiungere una nuova applicazione Console di SSMA per l'esecuzione della riga di comando.  
-   Aggiunta del supporto per la migrazione dei dati tramite motori di migrazione dei dati sul lato Client e lato Server.  
-   Aggiunta del supporto per l'istruzione "SELECT personalizzata" nella migrazione dei dati.  
-   Aggiunta del supporto per la migrazione da Oracle 11g R2.  
  
## <a name="june-2008"></a>Giugno 2008  
La versione di giugno 2008 di SSMA per Oracle sono incluse le seguenti modifiche:  
  
-   Aggiunti miglioramenti per il Report di valutazione, tra cui informazioni aggiuntive per sinonimi, origine file non elaborato per oggetti analizzabili, pannelli e rimozione di logo di SQL Server e la persistenza del layout.  
-   Aggiunti miglioramenti per la conversione di oggetti:  
    -   Pacchetti DBMS_LOB, conversione DBMS_SQL aggiunto.  
    -   Crea un join conversione rivista.  
    -   Modifica di record e le raccolte di conversione, ora di conversione di record nei casi più semplici rilasciati mediante variabili separate per ogni campo.  
    -   Miglioramenti dell'implementazione di record e raccolte.  
    -   Funzioni di aggregazione di windowing aggiunte.  
    -   Clausola ROLLUP o CUBE aggiunto.  
    -   Analisi utilizzo software per NEXTVAL/CURVAL.  
    -   Sono state aggiunte colonne nella clausola SET di raggruppamento, Grouping sets e ID di raggruppamento.  
    -   MERGE-istruzione aggiunto.  
    -   Supporto di nuovi tipi datetime e la conversione di record e le raccolte come tipi di dati CLR aggiunti.  
-   Aggiunta di nuove funzionalità di Tester. Tabelle possono ora essere testate come oggetti con Tester, è possibile modificare un ordine di chiamata di diversi oggetti testabili nel test case, utente eseguire il test di procedure e funzioni di record e le raccolte come parametri e restituire valori e un dipendenze analizzatore è stato aggiunto al controllo solo tabelle utilizzate.  
  
## <a name="august-2007"></a>Agosto 2007  
La versione di agosto 2007 di SSMA per Oracle sono incluse le seguenti modifiche:  
  
-   Aggiungere che un nuovo componente TESTER consente di creare, gestire ed eseguire i test case per verificare il codice SQL convertito.  
-   Aggiunta del supporto per la conversione dei sottotipi Oracle, raccolte e moduli locali sono stati aggiunti al convertitore di tipi SQL.  
-   Aggiungere che una nuova funzionalità di sincronizzazione consente di sincronizzare oggetti specifici con database di SQL Server.  
-   Aggiunte nuove opzioni di conversione.  
  
## <a name="april-2007"></a>April 2007  
La versione di aprile 2007 di SSMA per Oracle è la versione iniziale.
