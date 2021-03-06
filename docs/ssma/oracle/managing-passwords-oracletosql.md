---
title: La gestione delle password (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Managing Passwords in Oracle, Exporting or Importing Encrypted Password
- Managing passwords in Oracle, Securing Password
ms.assetid: 8c7d9f8e-06bb-476c-bbd2-15b61d5bba3c
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: aab7c06903f334ee0b24907cb4189b56d620b49a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47842969"
---
# <a name="managing-passwords-oracletosql"></a>Gestione delle password (OracleToSQL)
Questa sezione riguarda la protezione delle password di database e la procedura per importare o esportare tali tra server:  
  
1.  Protezione di Password  
  
2.  L'esportazione o importazione di Password crittografata  
  
## <a name="securing-password"></a>Protezione di Password  
SSMA consente di proteggere la password di un database.  
  
Usare la procedura seguente per implementare una connessione sicura:  
  
Specificare una password valida usando uno dei tre metodi seguenti:  
  
1.  **Testo non crittografato:** digitare la password del database nell'attributo valore del nodo 'password'. Si trova sotto il nodo della definizione di server nella sezione Server di file di script o file di connessione server.  
  
    Le password in testo non crittografato non sono protette. Pertanto, si verificherà il seguente messaggio di avviso nell'output della console: *"Server &lt;id server&gt; password viene fornita in formato testo non crittografato non sicure, applicazione Console SSMA fornisce un'opzione per proteggere il la password mediante crittografia, vedere opzione – securepassword in SSMA file per informazioni dettagliate della Guida."*  
  
    **Le password crittografate:** la password specificata, in questo caso, viene archiviata in formato crittografato nel computer locale in ProtectedStorage.ssma.  
  
    -   **Protezione delle password**  
  
        -   Eseguire la `SSMAforOracleConsole.exe` con il `–securepassword` e aggiunge l'opzione nella riga di comando passando il server di connessione o file script che contiene il nodo della password nella sezione Definizione server.  
  
        -   Al prompt dei comandi, l'utente viene richiesto di immettere la password del database e confermarla.  
  
            Gli ID definizione di server e relativa password crittografata corrispondenti vengono archiviate in un file nel computer locale  
            
            Esempio 1:  
            
                Specify password
                
                C:\SSMA\SSMAforOracleConsole.EXE –securepassword –add all –s "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\AssessmentReportGenerationSample.xml" –v "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\ VariableValueFileSample.xml"
                
                Enter password for server_id 'XXX_1': xxxxxxx
                
                Re-enter password for server_id 'XXX_1': xxxxxxx
            
            Esempio 2:
            
                C:\SSMA\SSMAforOracleConsole.EXE –securepassword –add "source_1,target_1" –c "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\ServersConnectionFileSample.xml" – v "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\ VariableValueFileSample.xml" -o
                
                Enter password for server_id 'source_1': xxxxxxx
                
                Re-enter password for server_id 'source_1': xxxxxxx
                
                Enter password for server_id 'target_1': xxxxxxx
                
                Re-enter password for server_id 'target _1': xxxxxxx  
    
    -   **Rimozione delle password crittografate**  
  
        Eseguire la `SSMAforOracleConsole.exe` con il`–securepassword` e `–remove` passare alla riga di comando passando l'ID server, per rimuovere le password crittografate dal file di archiviazione protetto presentano nel computer locale.  
        
        Esempio:  
        
            C:\SSMA\SSMAforOracleConsole.EXE –securepassword –remove all
            C:\SSMA\SSMAforOracleConsole.EXE –securepassword –remove "source_1,target_1"  
  
    -   **Elenco di ID Server le cui password vengono crittografate**  
  
        Eseguire la `SSMAforOracleConsole.exe` con il `–securepassword` e `–list` passare alla riga di comando per elencare tutti gli ID server le cui password sono state crittografate.  
  
        Esempio:  
        
            C:\SSMA\SSMAforOracleConsole.EXE –securepassword –list  
  
    > [!NOTE]  
    > 1.  La password in testo non crittografato indicato nel file di connessione di server o lo script ha la precedenza sulla password crittografata nel file protetto.  
    > 2.  Quando è presente alcuna password nella sezione server di file di connessione del server o il file di script o se non è stato protetto nel computer locale, la console viene richiesto di immettere la password.  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>Esportare o importare le password crittografate  
L'applicazione Console SSMA consente di esportare le password crittografate del database presente in un file nel computer locale in un file protetto e viceversa. È utile nella creazione della macchina password crittografate indipendenti. La funzionalità di esportazione legge l'id del server e protetto da archiviazione di password da locale e Salva le informazioni in un file crittografato. L'utente viene richiesto di immettere la password per il file protetto. Assicurarsi che la password immessa è 8 caratteri o più. Questo file protetto sia portabile tra computer diversi. Funzionalità di importazione legge il server di informazioni su id e la password dal file protetto. L'utente viene richiesto di immettere la password per il file protetto e aggiunge le informazioni nell'archiviazione locale protetto.  
  
Esempio:  

    Export password
    
    Enter password for protecting the exported file C:\SSMA\SSMAforOracleConsole.EXE –securepassword –export all "machine1passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforOracleConsole.EXE –p –e "OracleDB_1_1,Sql_1" "machine2passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
Esempio:  

    Import an encrypted password
    
    Enter password for protecting the imported file C:\SSMA\SSMAforOracleConsole.EXE –securepassword –import all "machine1passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforOracleConsole.EXE –p –i "OracleDB_1,Sql_1" "machine2passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
## <a name="see-also"></a>Vedere anche  
[Esecuzione della Console SSMA (Oracle)](http://msdn.microsoft.com/en-us/7228ccba-c69f-4b4c-8664-01a2750183c5)  
  
