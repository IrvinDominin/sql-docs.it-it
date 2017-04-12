---
title: "Colonne di dati relative al caricamento e salvataggio dei file | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0101e809-d6ea-4d0c-95ec-65dd77acf665
caps.latest.revision: 5
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 5
---
# Colonne di dati relative al caricamento e salvataggio dei file
  La categoria di eventi relativa al caricamento e al salvataggio dei file presenta la classe di evento seguente:  
  
|**ID evento**|**Nome evento**|**Descrizione evento**|  
|------------------|--------------------|---------------------------|  
|90|Inizio caricamento file|Inizio caricamento file.|  
|91|Fine caricamento file|Fine caricamento file.|  
|92|Inizio salvataggio file|Inizio salvataggio file.|  
|93|Fine salvataggio file|Fine salvataggio file|  
|94|Inizio PageOut|Inizio PageOut.|  
|95|Fine PageOut|Fine PageOut|  
|96|Inizio PageIn|Inizio PageIn.|  
|97|Fine PageIn|Fine PageIn|  
  
 Nella tabella seguente sono incluse le colonne di dati per la classe di evento.  
  
## Inizio caricamento file  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|CurrentTime|2|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|JobID|7|1|ID processo per stato di avanzamento.|  
|SessionType|8|8|Tipo di sessione. Indica l'entità che ha causato l'operazione.|  
|ObjectID|11|8|ID oggetto (è una stringa).|  
|ObjectType|12|1|Tipo di oggetto.|  
|ObjectName|13|8|Nome dell'oggetto.|  
|ObjectPath|14|8|Percorso dell'oggetto. Elenco delimitato da virgole di elementi padre, a partire dall'elemento padre dell'oggetto.|  
|ConnectionID|25|1|ID connessione univoco.|  
|DatabaseName|28|8|Nome del database in cui è in esecuzione l'istruzione dell'utente.|  
|ClientProcessID|36|1|ID di processo dell'applicazione client.|  
|SessionID|39|8|GUID della sessione.|  
|TextData|42|9|Dati di testo associati all'evento.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
  
## Fine caricamento file  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|CurrentTime|2|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|EndTime|4|5|Ora di fine dell'evento. Questa colonna non viene popolata per le classi degli eventi di avvio, ad esempio SQL:BatchStarting o SP:Starting. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|Durata|5|2|Durata dell'evento in millisecondi.|  
|JobID|7|1|ID processo per stato di avanzamento.|  
|SessionType|8|8|Tipo di sessione. Indica l'entità che ha causato l'operazione.|  
|IntegerData|10|1|Dati di tipo integer.|  
|ObjectID|11|8|ID oggetto (è una stringa).|  
|ObjectType|12|1|Tipo di oggetto.|  
|ObjectName|13|8|Nome dell'oggetto.|  
|ObjectPath|14|8|Percorso dell'oggetto. Elenco delimitato da virgole di elementi padre, a partire dall'elemento padre dell'oggetto.|  
|Severity|22|1|Livello di gravità di un'eccezione.|  
|Operazione completata|23|1|1 = esito positivo. 0 = esito negativo (ad esempio, 1 indica l'esito positivo di un controllo delle autorizzazioni e 0 indica l'esito negativo di tale controllo).|  
|Errore|24|1|Numero di errore di un evento specifico.|  
|ConnectionID|25|1|ID connessione univoco.|  
|DatabaseName|28|8|Nome del database in cui è in esecuzione l'istruzione dell'utente.|  
|ClientProcessID|36|1|ID di processo dell'applicazione client.|  
|SessionID|39|8|GUID della sessione.|  
|TextData|42|9|Dati di testo associati all'evento.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
  
## Inizio salvataggio file  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|CurrentTime|2|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|JobID|7|1|ID processo per stato di avanzamento.|  
|SessionType|8|8|Tipo di sessione. Indica l'entità che ha causato l'operazione.|  
|ObjectID|11|8|ID oggetto (è una stringa).|  
|ObjectType|12|1|Tipo di oggetto.|  
|ObjectName|13|8|Nome dell'oggetto.|  
|ObjectPath|14|8|Percorso dell'oggetto. Elenco delimitato da virgole di elementi padre, a partire dall'elemento padre dell'oggetto.|  
|ConnectionID|25|1|ID connessione univoco.|  
|DatabaseName|28|8|Nome del database in cui è in esecuzione l'istruzione dell'utente.|  
|ClientProcessID|36|1|ID di processo dell'applicazione client.|  
|SessionID|39|8|GUID della sessione.|  
|TextData|42|9|Dati di testo associati all'evento.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
  
## Fine salvataggio file  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|CurrentTime|2|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|EndTime|4|5|Ora di fine dell'evento. Questa colonna non viene popolata per le classi degli eventi di avvio, ad esempio SQL:BatchStarting o SP:Starting. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|Durata|5|2|Durata dell'evento in millisecondi.|  
|JobID|7|1|ID processo per stato di avanzamento.|  
|SessionType|8|8|Tipo di sessione. Indica l'entità che ha causato l'operazione.|  
|IntegerData|10|1|Dati di tipo integer.|  
|ObjectID|11|8|ID oggetto (è una stringa).|  
|ObjectType|12|1|Tipo di oggetto.|  
|ObjectName|13|8|Nome dell'oggetto.|  
|ObjectPath|14|8|Percorso dell'oggetto. Elenco delimitato da virgole di elementi padre, a partire dall'elemento padre dell'oggetto.|  
|Severity|22|1|Livello di gravità di un'eccezione.|  
|Operazione completata|23|1|1 = esito positivo. 0 = esito negativo (ad esempio, 1 indica l'esito positivo di un controllo delle autorizzazioni e 0 indica l'esito negativo di tale controllo).|  
|Errore|24|1|Numero di errore di un evento specifico.|  
|ConnectionID|25|1|ID connessione univoco.|  
|DatabaseName|28|8|Nome del database in cui è in esecuzione l'istruzione dell'utente.|  
|ClientProcessID|36|1|ID di processo dell'applicazione client.|  
|SessionID|39|8|GUID della sessione.|  
|TextData|42|9|Dati di testo associati all'evento.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
  
## Inizio PageOut  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|CurrentTime|2|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|JobID|7|1|ID processo per stato di avanzamento.|  
|SessionType|8|8|Tipo di sessione. Indica l'entità che ha causato l'operazione.|  
|ObjectID|11|8|ID oggetto (è una stringa).|  
|ObjectType|12|1|Tipo di oggetto.|  
|ObjectName|13|8|Nome dell'oggetto.|  
|ObjectPath|14|8|Percorso dell'oggetto. Elenco delimitato da virgole di elementi padre, a partire dall'elemento padre dell'oggetto.|  
|ConnectionID|25|1|ID connessione univoco.|  
|DatabaseName|28|8|Nome del database in cui è in esecuzione l'istruzione dell'utente.|  
|ClientProcessID|36|1|ID di processo dell'applicazione client.|  
|SessionID|39|8|GUID della sessione.|  
|TextData|42|9|Dati di testo associati all'evento.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
  
## Fine PageOut  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|CurrentTime|2|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|EndTime|4|5|Ora di fine dell'evento. Questa colonna non viene popolata per le classi degli eventi di avvio, ad esempio SQL:BatchStarting o SP:Starting. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|Durata|5|2|Durata dell'evento in millisecondi.|  
|JobID|7|1|ID processo per stato di avanzamento.|  
|SessionType|8|8|Tipo di sessione. Indica l'entità che ha causato l'operazione.|  
|IntegerData|10|1|Dati di tipo integer.|  
|ObjectID|11|8|ID oggetto (è una stringa).|  
|ObjectType|12|1|Tipo di oggetto.|  
|ObjectName|13|8|Nome dell'oggetto.|  
|ObjectPath|14|8|Percorso dell'oggetto. Elenco delimitato da virgole di elementi padre, a partire dall'elemento padre dell'oggetto.|  
|Severity|22|1|Livello di gravità di un'eccezione.|  
|Operazione completata|23|1|1 = esito positivo. 0 = esito negativo (ad esempio, 1 indica l'esito positivo di un controllo delle autorizzazioni e 0 indica l'esito negativo di tale controllo).|  
|Errore|24|1|Numero di errore di un evento specifico.|  
|ConnectionID|25|1|ID connessione univoco.|  
|DatabaseName|28|8|Nome del database in cui è in esecuzione l'istruzione dell'utente.|  
|ClientProcessID|36|1|ID di processo dell'applicazione client.|  
|SessionID|39|8|GUID della sessione.|  
|TextData|42|9|Dati di testo associati all'evento.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
  
## Inizio PageIn  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|CurrentTime|2|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|JobID|7|1|ID processo per stato di avanzamento.|  
|SessionType|8|8|Tipo di sessione. Indica l'entità che ha causato l'operazione.|  
|ObjectID|11|8|ID oggetto (è una stringa).|  
|ObjectType|12|1|Tipo di oggetto.|  
|ObjectName|13|8|Nome dell'oggetto.|  
|ObjectPath|14|8|Percorso dell'oggetto. Elenco delimitato da virgole di elementi padre, a partire dall'elemento padre dell'oggetto.|  
|ConnectionID|25|1|ID connessione univoco.|  
|DatabaseName|28|8|Nome del database in cui è in esecuzione l'istruzione dell'utente.|  
|ClientProcessID|36|1|ID di processo dell'applicazione client.|  
|SessionID|39|8|GUID della sessione.|  
|TextData|42|9|Dati di testo associati all'evento.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
  
## Fine PageIn  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|CurrentTime|2|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|EndTime|4|5|Ora di fine dell'evento. Questa colonna non viene popolata per le classi degli eventi di avvio, ad esempio SQL:BatchStarting o SP:Starting. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|Durata|5|2|Durata dell'evento in millisecondi.|  
|JobID|7|1|ID processo per stato di avanzamento.|  
|SessionType|8|8|Tipo di sessione. Indica l'entità che ha causato l'operazione.|  
|IntegerData|10|1|Dati di tipo integer.|  
|ObjectID|11|8|ID oggetto (è una stringa).|  
|ObjectType|12|1|Tipo di oggetto.|  
|ObjectName|13|8|Nome dell'oggetto.|  
|ObjectPath|14|8|Percorso dell'oggetto. Elenco delimitato da virgole di elementi padre, a partire dall'elemento padre dell'oggetto.|  
|Severity|22|1|Livello di gravità di un'eccezione.|  
|Operazione completata|23|1|1 = esito positivo. 0 = esito negativo (ad esempio, 1 indica l'esito positivo di un controllo delle autorizzazioni e 0 indica l'esito negativo di tale controllo).|  
|Errore|24|1|Numero di errore di un evento specifico.|  
|ConnectionID|25|1|ID connessione univoco.|  
|DatabaseName|28|8|Nome del database in cui è in esecuzione l'istruzione dell'utente.|  
|ClientProcessID|36|1|ID di processo dell'applicazione client.|  
|SessionID|39|8|GUID della sessione.|  
|TextData|42|9|Dati di testo associati all'evento.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
  
## Vedere anche  
 [Categoria di eventi relativa al caricamento e salvataggio dei file](../../analysis-services/trace-events/file-load-and-save-event-category.md)  
  
  