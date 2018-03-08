---
title: Note - Microsoft ODBC Driver for SQL Server in Linux e macOS | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8fe5c32ed34d9056c69069d6b390a49fc71b396c
ms.sourcegitcommit: 4edac878b4751efa57601fe263c6b787b391bc7c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2018
---
# <a name="release-notes-for-the-microsoft-odbc-driver-for-sql-server-on-linux-and-macos"></a>Note sulla versione per Microsoft ODBC Driver for SQL Server in Linux e macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversionmdmd-on-linux-and-macos"></a>Novità di [!INCLUDE[msCoName](../../../includes/msconame_md.md)] 17 Driver ODBC per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] su Linux e macOS

**Nuove distribuzioni supportate**: macOS High Sierra e Ubuntu 17.10 

**Miglioramenti delle prestazioni**: maggiore di 10 volte il miglioramento delle prestazioni quando il driver converte da e verso UTF-8/16.

**Funzionalità aggiunte**:

Always Encrypted supporto per API BCP

Nuovo attributo di stringa di connessione UseFMTOnly causa del driver per l'uso di metadati legacy in casi particolari richiede che le tabelle temporanee.

Supporto per l'istanza gestita di SQL Azure (anteprima privata estesa). 
> [!NOTE]
> Quando si utilizza l'istanza gestita, esistono alcune differenze:
> -   FILESTREAM non è supportato 
> -   Accesso ai file System locale non è supportata, ma necessari per elementi quali tracefiles 
> -   Il nome di tipo definito dall'utente locale percorso non è supportato. 
> -   Autenticazione integrata di Windows non è supportata. 
> -   DTC non è supportata. 
> -   l'account 'sa' non è presente (l'account predefinito viene chiamato 'cloudSA')
> -   Errore nel token TDS (0xAA) restituisce il nome server errato
> -   Non sono supportati i caratteri speciali nei nomi di database 
> -   ALTER DATABASE [dbname1] MODIFY NAME = [dbname2] non è supportata.
> -   I messaggi di errore vengono sempre visualizzati in inglese, indipendentemente dal linguaggio impostazioni (come Azure) 

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-131-for-includessnoversionincludesssnoversionmdmd-on-linux-and-macos"></a>Novità di [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13.1 per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] su Linux e macOS  

ODBC Driver 13.1 per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] aggiunge il supporto per Always Encrypted e Azure Active Directory utilizzato in combinazione con Microsoft SQL Server 2016.

**Nuove distribuzioni supportate**: OS X 10.11 e macOS 10.12 sono supportati nella prima versione del Driver ODBC in macOS. Ubuntu 16.10 ora anche supportato, insieme a Red Hat 6, 7 e 12 SUSE. Ogni piattaforma dispone di un pacchetto relativi alla piattaforma (RPM o DEB) per semplificare l'installazione e configurazione.  Vedere [l'installazione del Driver](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) per le istruzioni di installazione.

**Modifiche al supporto 2.3.1 di gestione Driver unixODBC**: il provider ODBC non dipende più pacchetti personalizzati per la gestione driver unixODBC (tranne RedHat 6) e si basa su Gestione distribuzione del pacchetto per risolvere la dipendenza UnixODBC da repository della distribuzione.

**Supporto API BCP**: il driver ODBC di Linux e macOS ora supporta l'utilizzo del [funzioni API BCP (**bcp_init**, ecc.)](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)

## <a name="whats-new-in-the-microsoft-odbc-driver-130-for-includessnoversionincludesssnoversionmdmd-on-linux"></a>Novità di Microsoft ODBC Driver 13.0 per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] su Linux  
Con Microsoft ODBC Driver 13.0 per SQL Server, SQL Server 2014 e SQL Server 2016 ora supportati anche.  

**Nuove distribuzioni supportate**:

Ubuntu è ora supportato, insieme a Red Hat e SUSE. Ogni piattaforma dispone di un pacchetto relativi alla piattaforma (RPM o DEB) per semplificare l'installazione e configurazione.  Vedere [l'installazione del Driver](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) per le istruzioni di installazione.

**Supporto 2.3.1 di gestione Driver unixODBC**: oltre a una Gestione driver più recente, è disponibile un pacchetto per l'installazione di questa dipendenza che semplifica l'installazione e configurazione.  

**Risoluzione IP di rete Transparent**: trasparente la risoluzione IP di rete è una revisione della funzionalità di Failover su più Subnet esistente che influisce sulla sequenza di connessione del driver nel caso in cui il primo risolto non IP dell'host rispondere e sono presenti più indirizzi IP associati al nome host.

**Supporto di TLS 1.2**: il 13.0 di Microsoft ODBC Driver for SQL Server in Linux supporta TLS 1.2 quando vengono utilizzate proteggere le comunicazioni con SQL Server.

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-11-for-includessnoversionincludesssnoversionmdmd-on-linux"></a>Novità di [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] su Linux  
Il driver ODBC in SUSE Linux (anteprima) supporta SUSE Linux Enterprise 11 Service Pack 2 a 64 bit. Per ulteriori informazioni, vedere [requisiti di sistema](../../../connect/odbc/linux-mac/system-requirements.md).  

Il driver ODBC in Linux supporta [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]. Per ulteriori informazioni, vedere [Driver ODBC in Linux supporto per il ripristino di emergenza a disponibilità elevata](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md).  

Il driver ODBC in Linux supporta le connessioni al database SQL di Microsoft Azure. Per altre informazioni, vedere la pagina relativa alla [procedura di connessione al database SQL di Windows Azure usando ODBC](http://msdn.microsoft.com/library/hh974312.aspx).  

Il `-l` opzione (timeout di accesso) è stata aggiunta a `bcp`. Per ulteriori informazioni, vedere [connessione con **bcp**](../../../connect/odbc/linux-mac/connecting-with-bcp.md).
