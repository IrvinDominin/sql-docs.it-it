---
title: "Le proprietà della memoria | Documenti Microsoft"
ms.custom: 
ms.date: 01/23/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- LowMemoryLimit property
- MinimumAllocatedMemory property
- MidMemoryPrice property
- MemoryHeapType property
- memory [Analysis Services]
- DefaultPagesCountToReuse property
- TotalMemoryLimit property
- SessionMemoryLimit property
- VirtualMemoryLimit property
- WaitCountIfHighMemory property
- HighMemoryPrice property
- HeapTypeForObjects property
ms.assetid: 085f5195-7b2c-411a-9813-0ff5c6066d13
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 15e0fc6fa123fd4d9ca71f35804d2f06d0342b5a
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="memory-properties"></a>Proprietà della memoria
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prealloca una modesta quantità di memoria all'avvio in modo che le richieste possano essere gestite immediatamente. La memoria aggiuntiva viene allocata come query e i carichi di lavoro di elaborazione aumentano. 
  
  Tramite la specifica delle impostazioni di configurazione è possibile controllare le soglie di rilascio della memoria. L'impostazione **HardMemoryLimit** consente ad esempio di specificare una condizione di memoria esaurita imposta automaticamente (per impostazione predefinita, questa soglia non è abilitata), in cui le nuove richieste vengono rifiutate completamente finché non diventano disponibili altre risorse.

Per ulteriori informazioni sulla memoria massima utilizzata per ogni istanza di Analysis Services dall'edizione, vedere [edizioni e le funzionalità supportate di SQL Server](../../sql-server/editions-and-components-of-sql-server-2017.md#Cross-BoxScaleLimits).
  
 Se non diversamente specificato, le impostazioni seguenti si applicano sia in modalità server multidimensionale e tabulare.  
 
## <a name="default-memory-configuration"></a>Configurazione di memoria predefinita

Nella configurazione predefinita ogni istanza di Analysis Services consente di allocare all'avvio una piccola quantità di RAM (da 40 a 50 MB), anche se l'istanza è inattiva. 

Tenere presente che le impostazioni di configurazione si intendono per istanza. Se si eseguono più istanze di Analysis Services nello stesso hardware, ad esempio un'istanza tabulare e una multidimensionale, ogni istanza allocherà la propria memoria in modo indipendente dalle altre istanze.

La tabella seguente descrive brevemente le impostazioni di memoria più comuni. Per informazioni più dettagliate, vedere la sezione di riferimento. È consigliabile configurare queste impostazioni se Analysis Services entra in competizione per la memoria con altre applicazioni sullo stesso server:

Impostazione | Description
--------|------------
LowMemoryLimit | Per le istanze multidimensionali, una soglia inferiore a cui il server inizia prima il rilascio della memoria allocata agli oggetti usati raramente.
VertiPaqMemoryLimit | Per le istanze tabulari, una soglia inferiore a cui il server inizia prima il rilascio della memoria allocata agli oggetti usati raramente.
TotalMemoryLimit | Una soglia superiore a cui Analysis Services inizia il rilascio di memoria in maniera più drastica per liberare spazio per le richieste in esecuzione, nonché per le nuove richieste con priorità elevata. 
HardMemoryLimit | Un'altra soglia a cui Analysis Services inizia a rifiutare immediatamente le richieste a causa dell'utilizzo elevato di memoria. 
 
## <a name="property-reference"></a>Informazioni di riferimento sulle proprietà

Le proprietà seguenti si applicano sia alla modalità tabulare sia alla modalità multidimensionale, a meno che non sia specificato diversamente.

 I valori compresi tra 1 e 100 rappresentano le percentuali di **memoria fisica totale** o **spazio degli indirizzi virtuali**, a seconda di quale dei due elementi sia inferiore. I valori maggiori di 100 rappresentano limiti di memoria in byte.
  
 **LowMemoryLimit**  
 Una proprietà numero a virgola mobile a precisione doppia a 64 bit senza segno che definisce la prima soglia a cui Analysis Services inizia il rilascio di memoria per gli oggetti con priorità bassa, ad esempio una cache usata raramente. Dopo l'allocazione della memoria, il server non rilascia memoria al di sotto di questo limite. Il valore predefinito è 65 e indica che il limite inferiore della memoria è il 65% della memoria fisica o dello spazio di indirizzo virtuale, a seconda di quale dei due elementi sia inferiore.  
  
 **TotalMemoryLimit**  
 Definisce una soglia che, una volta raggiunta, induce il server a deallocare la memoria per fare spazio per altre richieste. Quando viene raggiunto questo limite, verrà avviata la cancellazione della memoria delle cache da parte dell'istanza, chiudendo le sessioni scadute e scaricando i calcoli inusati. Il valore predefinito è 80% della memoria fisica o dello spazio di indirizzo virtuale, a seconda di quale dei due elementi sia inferiore. Si noti che **TotalMemoryLimit** deve essere sempre minore di **HardMemoryLimit**  
  
 **HardMemoryLimit**  
 Specifica una soglia di memoria superata la quale le sessioni utente attive verranno immediatamente terminate dall'istanza per ridurre l'utilizzo della memoria. Per tutte le sessioni terminate verrà visualizzato un errore che indica l'annullamento a causa di un numero eccessivo di richieste di memoria. Con il valore predefinito, ovvero zero (0), il limite **HardMemoryLimit** sarà impostato su un valore mediano tra **TotalMemoryLimit** e la memoria fisica totale del sistema. Se quest'ultima è maggiore dello spazio di indirizzo virtuale del processo, per calcolare il limite **HardMemoryLimit**sarà invece usato lo spazio di indirizzo virtuale.  
  
 **VirtualMemoryLimit**  
  Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **VertiPaqPagingPolicy**  
  Solo per le istanze tabulari, specifica il comportamento di paging nel caso in cui la memoria del server sia insufficiente. I valori validi sono i seguenti:  
  
  

Impostazione  |Description  
---------|---------
**0**     |  Disabilita il paging. Se la memoria è insufficiente, l'elaborazione ha esito negativo e provoca un errore memoria insufficiente. Se si disabilita il paging, è necessario concedere i privilegi di Windows all'account del servizio. Per istruzioni, vedere [Configurare gli account del servizio &#40;Analysis Services&#41;](../../analysis-services/instances/configure-service-accounts-analysis-services.md). 
**1**     |  (Impostazione predefinita) Questa proprietà abilita il paging su disco usando il file di paging del sistema operativo (pagefile.sys).   
  
Quando è impostata su 1, è meno probabile che l'elaborazione non venga completata a causa di limitazioni di memoria perché il server tenterà di eseguire il paging su disco usando il metodo specificato. L'impostazione della proprietà **VertiPaqPagingPolicy** non garantisce che non si verificheranno mai gli errori della memoria. Gli errori di memoria insufficiente si possono comunque verificare nelle condizioni seguenti:  
  
-   Non c'è abbastanza memoria per tutti i dizionari. Durante l'elaborazione, Analysis Services blocca i dizionari per ogni colonna in memoria e tutti i dizionari insieme non possono essere maggiori del valore specificato per **VertiPaqMemoryLimit**.  
  
-   Lo spazio dell'indirizzo virtuale è insufficiente per il processo.  
  
 Per risolvere gli errori di memoria insufficiente persistenti è possibile riprogettare il modello per ridurre la quantità di dati che devono essere elaborati oppure è possibile aggiungere più memoria fisica al computer.  
  
 **VertiPaqMemoryLimit**  
 Solo per le istanze tabulari, se il paging su disco è consentito, questa proprietà consente di specificare il livello di utilizzo di memoria (come percentuale della memoria totale) da cui avrà inizio il paging. Il valore predefinito è 60. Se il consumo di memoria è inferiore al 60%, il server non eseguirà il paging su disco. Questa proprietà dipende da **VertiPaqPagingPolicyProperty**che deve essere impostata su 1 affinché si verifichi il paging.  
  
 **HighMemoryPrice**  
 Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MemoryHeapType**  
  Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] . I valori validi in SQL Server 2016 SP1 e versioni successive di Analysis Services sono i seguenti:
  
  Impostazione | Description
--------|------------
**-1** | (Impostazione predefinita) Automatico. Il motore stabilirà il valore da usare.
**1** | Heap Analysis Services.
**2** | LFH Windows.
**5** | Allocatore ibrido. L'allocatore utilizzerà LFH di Windows per \<= allocazioni 16 KB e l'Heap AS per > le allocazioni di 16 KB. 
**6** | Allocatore Intel TBB. Disponibile in SQL Server 2016 SP1 e versioni successive di Analysis Services.
  
  
 **HeapTypeForObjects**  
  Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] . I valori validi sono i seguenti:
  
   Impostazione | Description
--------|------------
**0** | Heap LFH Windows.
**1** | Allocatore slot Analysis Services.
**3** | Ogni oggetto ha un proprio heap Analysis Services.

 
 **DefaultPagesCountToReuse**  
 Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **HandleIA64AlignmentFaults**  
 Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MidMemoryPrice**  
 Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MinimumAllocatedMemory**  
 Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **PreAllocate**  
 Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **SessionMemoryLimit**  
 Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **WaitCountIfHighMemory**  
 Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà server in Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Determinare la modalità server di un'istanza di Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
