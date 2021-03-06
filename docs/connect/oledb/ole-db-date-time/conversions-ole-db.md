---
title: Associazioni e conversioni (OLE DB) | Microsoft Docs
description: Associazioni e conversioni (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB]
- bindings [OLE DB]
- OLE DB, bindings and conversions
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 9eca16e0908bac5134d459414cbd43ee19a4665a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47724959"
---
# <a name="conversions-ole-db"></a>Conversioni (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Questa sezione illustra come eseguire la conversione tra **data/ora** e **datetimeoffset** valori. Le conversioni descritte in questa sezione sono già disponibili in OLE DB o costituiscono un'estensione coerente di OLE DB.  
  
 Il formato di valori letterali e stringhe per date e ore in OLE DB segue in genere lo standard ISO e non dipende dalle impostazioni locali del client. Un'eccezione è rappresentata da DBTYPE_DATE, che utilizza come standard l'automazione OLE. Tuttavia, poiché il Driver OLE DB per SQL Server esegue solo la conversione tra tipi quando i dati vengono trasmessi al o dal client, non è in alcun modo per un'applicazione forzare il Driver OLE DB per SQL Server per la conversione tra DBTYPE_DATE e formati stringa. In caso contrario, le stringhe utilizzano i formati indicati di seguito. Il testo tra parentesi indica un elemento facoltativo.  
  
-   Il formato del **data/ora** e **datetimeoffset** stringhe è:  
  
     *aaaa*-*mm*-*gg*[ *hh*:*mm*:*ss*[. *9999999*] [+ *hh*:*mm*]]  
  
-   Il formato delle stringe **time** è:  
  
     *hh*:*mm*:*ss*[.*9999999*]  
  
-   Il formato del **data** stringhe è:  
  
     *aaaa*-*mm*-*gg*  
  
> [!NOTE]  
>  Le versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client e SQLOLEDB implementano conversioni OLE se le conversioni standard non vengono eseguite correttamente. Il Driver OLE DB per SQL Server segue lo stesso comportamento [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Di conseguenza, alcune conversioni eseguite da Driver OLE DB per SQL Server differiscono dalla specifica OLE DB.  
  
 Le conversioni dalle stringhe consentono flessibilità nella larghezza degli spazi vuoti e dei campi. Per altre informazioni, vedere la sezione "Dati nei formati: stringhe e valori letterali" in [supporto dei tipi di dati per data OLE DB e miglioramenti per la fase](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md).  
  
 Di seguito vengono fornite le regole di conversione generali:  
  
-   Quando una stringa viene convertita in un tipo di data/ora, la stringa viene prima analizzata come valore letterale ISO. Se l'operazione ha esito negativo, la stringa viene analizzata come valore letterale di data OLE, che include componenti per l'ora.  
  
-   Se l'ora non è presente ma il ricevitore può archiviare l'ora, questa viene impostata su zero. Se la data non è presente ma il ricevitore può archiviare la data, questa viene impostata sulla data corrente quando si utilizzano conversioni ISO e su 1899-12-30 quando si utilizzano conversioni OLE.  
  
-   Se nel tipo di dati utilizzato dal client non è presente il fuso orario, ma il server può archiviare il fuso orario, la data nel client viene considerata nel fuso orario utilizzato dal client stesso.  
  
-   Se nel server non è presente il fuso orario ma il client dispone di informazioni sul fuso orario, viene presupposto il fuso orario UTC. Questo comportamento differisce da quello del server.  
  
-   Se l'ora è presente ma il ricevitore non può archiviare l'ora, il componente per l'ora viene ignorato.  
  
-   Se la data è presente ma il ricevitore non può archiviare la data, il componente per la data viene ignorato.  
  
-   Se si verifica un troncamento di secondi o di secondi frazionari durante la conversione dal client al server, viene restituito DB_E_ERRORSOCCURRED e viene impostato lo stato DBSTATUS_E_DATAOVERFLOW.  
  
-   Se si verifica un troncamento di secondi o di secondi frazionari durante la conversione dal server al client, viene impostato lo stato DBSTATUS_S_TRUNCATED.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Conversioni eseguite da client a server](../../oledb/ole-db-date-time/conversions-performed-from-client-to-server.md)  
 Vengono descritte le conversioni di data/ora eseguite tra un'applicazione client scritta con la specifica driver OLE DB per SQL Server e [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (o versione successiva).  
  
 [Conversioni eseguite da server a client](../../oledb/ole-db-date-time/conversions-performed-from-server-to-client.md)  
 Vengono descritte le conversioni di data/ora eseguite tra [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], o versione successiva, e un'applicazione client scritta con driver OLE DB per SQL Server.  
  
## <a name="see-also"></a>Vedere anche  
 [Miglioramenti relativi a data e ora &#40;OLE DB&#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
