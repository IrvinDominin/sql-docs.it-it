## <a name="connect-locally"></a>Eseguire la connessione in locale

Nella procedura seguente viene usato **sqlcmd** per connettersi in locale alla nuova istanza di SQL Server.

1. Eseguire **sqlcmd** con i parametri per il nome di Server SQL (-S), il nome utente (-U) e la password (-P). In questa esercitazione la connessione viene eseguita in locale, pertanto il nome del server è `localhost`. Il nome utente è `SA` e la password è quella specificata per l'account SA durante la configurazione.

   ```bash
   sqlcmd -S localhost -U SA -P '<YourPassword>'
   ```

   > [!TIP]
   > È possibile omettere la password nella riga di comando perché venga richiesto di immetterla.

   > [!TIP]
   > Se successivamente si decide di connettersi da remoto, specificare il nome del computer o l'indirizzo IP per il parametro **-S** e assicurarsi che la porta 1433 sia aperta nel firewall.

1. Se la connessione viene eseguita correttamente, il prompt dei comandi **sqlcmd** sarà: `1>`.

1. Se si verifica un errore di connessione, provare a diagnosticare il problema dal messaggio di errore. Rivedere poi i [consigli per la risoluzione dei problemi di connessione](../linux/sql-server-linux-troubleshooting-guide.md#connection).

## <a name="create-and-query-data"></a>Creare i dati e recuperarli tramite query
Nelle sezioni seguenti viene descritto l'uso di **sqlcmd** per creare un nuovo database, aggiungere dati ed eseguire una query semplice.

### <a name="create-a-new-database"></a>Creare un nuovo database

La seguente procedura consente di creare un nuovo database denominato `TestDB`.

1. Dal prompt dei comandi **sqlcmd** incollare il comando seguente di Transact-SQL per creare un database di test:

   ```sql
   CREATE DATABASE TestDB
   ```

1. Nella riga successiva scrivere una query perché vengano restituiti i nomi di tutti database nel server:

   ```sql
   SELECT Name from sys.Databases
   ```

1. I due comandi precedenti non sono stati eseguiti immediatamente. È necessario digitare `GO` in una nuova riga per eseguire i comandi precedenti:

   ```sql
   GO
   ```

### <a name="insert-data"></a>Inserire i dati

Creare poi una nuova tabella `Inventory` e inserire due nuove righe.

1. Dal prompt dei comandi **sqlcmd** spostare il contesto nel nuovo database `TestDB`:

   ```sql
   USE TestDB
   ```

1. Creare una nuova tabella denominata `Inventory`:

   ```sql
   CREATE TABLE Inventory (id INT, name NVARCHAR(50), quantity INT)
   ```

1. Inserire i dati nella nuova tabella:

   ```sql
   INSERT INTO Inventory VALUES (1, 'banana', 150); INSERT INTO Inventory VALUES (2, 'orange', 154);
   ```

1. Digitare `GO` per eseguire i comandi precedenti:

   ```sql
   GO
   ```

### <a name="select-data"></a>Selezionare i dati

A questo punto, eseguire una query per restituire i dati dalla tabella `Inventory`.

1. Dal prompt dei comandi **sqlcmd** immettere una query che restituisca le righe dalla tabella `Inventory` che ne contiene oltre 152:

   ```sql
   SELECT * FROM Inventory WHERE quantity > 152;
   ```

1. Eseguire il comando:

   ```sql
   GO
   ```

### <a name="exit-the-sqlcmd-command-prompt"></a>Uscire dal prompt dei comandi sqlcmd

Per terminare la sessione **sqlcmd**, digitare `QUIT`:

```sql
QUIT
```

## <a name="connect-from-windows"></a>Eseguire la connessione da Windows

Gli strumenti di SQL Server in Windows consentono di connettersi alle istanze di SQL Server in Linux nello stesso modo in cui si connettono a qualsiasi istanza remota di SQL Server.

Se si usa un computer Windows con possibilità di connessione al computer Linux, seguire la stessa procedura descritta in questo argomento da un prompt dei comandi di Windows che esegue **sqlcmd**. Verificare però che si stiano usando il nome del computer Linux e l'indirizzo IP di destinazione anziché il localhost. Assicurarsi anche che la porta TCP 1433 sia aperta. Nel caso di problemi di connessione da Windows, vedere i [consigli per la risoluzione dei problemi di connessione](../linux/sql-server-linux-troubleshooting-guide.md#connection).

Per altri strumenti che vengono eseguiti in Windows, ma si connettono a SQL Server in Linux, vedere:

- [SQL Server Management Studio (SSMS)](../linux/sql-server-linux-develop-use-ssms.md)
- [Windows PowerShell](../linux/sql-server-linux-manage-powershell.md)
- [SQL Server Data Tools (SSDT)](../linux/sql-server-linux-develop-use-ssdt.md)

## <a name="additional-resources"></a>Risorse aggiuntive

Per altri scenari di installazione, vedere le risorse seguenti:

|||
|---|---|
| [Aggiornamento](../linux/sql-server-linux-setup.md#upgrade) | Informazioni su come aggiornare un'installazione esistente di SQL Server in Linux |
| [Disinstallazione](../linux/sql-server-linux-setup.md#uninstall) | Disinstallare SQL Server in Linux |
| [Installazione automatica](../linux/sql-server-linux-setup.md#unattended) | Informazioni su come creare uno script per eseguire l'installazione senza interazioni |
| [Installazione offline](../linux/sql-server-linux-setup.md#offline) | Informazioni su come scaricare manualmente i pacchetti per l'installazione offline |

Per esplorare altri modi per connettersi e gestire SQL Server, è possibile esaminare gli strumenti seguenti:

|||
|---|---|
| [Visual Studio Code](../linux/sql-server-linux-develop-use-vscode.md) | Un editor di codice multipiattaforma GUI che eseguono istruzioni Transact-SQL con l'estensione mssql. |
| [Studio di operazioni di SQL Server](../sql-operations-studio/index.md) | Un'utilità di gestione database GUI di multipiattaforma. |
| [mssql-cli](https://github.com/dbcli/mssql-cli/tree/master/doc) | Un'interfaccia della riga di comando multipiattaforma per l'esecuzione di comandi Transact-SQL. |
| [SQL Server Management Studio](../linux/sql-server-linux-develop-use-ssms.md) | Un'utilità di gestione database interfaccia utente grafica basata su Windows che può connettersi e gestire le istanze di SQL Server in Linux. |

Per altre informazioni sulla scrittura di istruzioni e query Transact-SQL, vedere [Esercitazione: Scrittura di istruzioni Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md).

> [!TIP]
> Per le risposte alle domande più frequenti, vedere il [SQL Server in domande frequenti su Linux](../linux/sql-server-linux-faq.md).

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Esplorare le esercitazioni per SQL Server in Linux](../linux/sql-server-linux-migrate-restore-database.md)