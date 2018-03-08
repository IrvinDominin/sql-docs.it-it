---
title: "Proprietà server (RDS) | Documenti Microsoft"
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.component: reference
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- RDS::IBindMgr21::Server
helpviewer_keywords:
- Server property [RDS]
ms.assetid: d2727ce7-da9f-4271-ae3c-9334ef477c14
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8a81a3139892898b8468d73f53d22d8bd29c4b63
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="server-property-rds"></a>Proprietà server (RDS)
Indica il protocollo di comunicazione e nome di Internet Information Services (IIS).  
  
 È possibile impostare il **Server** in fase di progettazione nei tag dell'oggetto di proprietà di[RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) dell'oggetto o in fase di esecuzione nel codice di script.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
 **HTTP**  
  
 Sintassi in fase di progettazione  
  
```  
  
<PARAM NAME="Server" VALUE="http:  
//awebsrvr:port  
">  
  
```  
  
 Sintassi in fase di esecuzione  
  
```  
  
DataControl  
.Server="http://  
awebsrvr:port  
"  
  
```  
  
 **HTTPS**  
  
 Sintassi in fase di progettazione  
  
```  
  
<PARAM NAME="Server" VALUE="https://awebsrvr:port">  
```  
  
 Sintassi in fase di esecuzione  
  
```  
  
DataControl.Server="https://awebsrvr:port"  
```  
  
 **DCOM**  
  
 Sintassi in fase di progettazione  
  
```  
  
<PARAM NAME="Server" VALUE="  
computername  
">  
  
```  
  
 Sintassi in fase di esecuzione  
  
```  
  
DataControl.Server="computername"  
```  
  
 **In-process**  
  
 Sintassi in fase di progettazione  
  
```  
  
<PARAM NAME="Server" VALUE="">  
  
```  
  
 Sintassi in fase di esecuzione  
  
```  
  
DataControl.Server=""  
```  
  
## <a name="parameters"></a>Parametri  
 *awebsrvr*o *computername*  
 Oggetto **stringa** valore che contiene un Internet o intranet percorso o nome del computer, se il server è in un computer remoto; o una stringa vuota se il server nel computer locale.  
  
 *port*  
 Facoltativa. Porta utilizzata per connettersi a un server che esegue IIS. Il numero di porta viene impostato in Internet Explorer (sul **vista** menu, fare clic su **opzioni**e quindi selezionare il **connessione** scheda) o in IIS.  
  
 *DataControl*  
 Una variabile oggetto che rappresenta un **RDS. DataControl** oggetto.  
  
## <a name="remarks"></a>Osservazioni  
 Il server è il percorso in cui il **RDS. DataControl** elaborazione richiesta (ovvero, una query o aggiornamento). Per impostazione predefinita, tutte le richieste vengono elaborate le [RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) oggetto [MSDFMAP. Gestore](../../../ado/guide/remote-data-service/datafactory-customization.md) componente e [MSDFMAP. INI](../../../ado/guide/remote-data-service/understanding-the-customization-file.md) file nel server specificato. Ricordare che quando si modificano i server per riconciliare le impostazioni nel vecchio e nuovo **MSDFMAP. INI** file. Incompatibilità possono causare richieste con esito positivo su un server in un altro. Se la proprietà del Server è impostata su una stringa vuota "", tali oggetti verranno utilizzati nel computer locale.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (Servizi Desktop remoto)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà server (VBScript)](../../../ado/reference/rds-api/server-property-example-vbscript.md)   
 [Proprietà Connect (RDS)](../../../ado/reference/rds-api/connect-property-rds.md)   
 [Proprietà SQL](../../../ado/reference/rds-api/sql-property.md)   
 [Metodo SubmitChanges (Servizi Desktop remoto)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


