---
title: Visualizzare e risolvere i conflitti di dati per le pubblicazioni di tipo merge | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], viewing conflicts
- viewing conflict information
- conflict resolution [SQL Server replication], merge replication
ms.assetid: aeee9546-4480-49f9-8b1e-c71da1f056c7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3cd37fbe598fe93f5c5af5a63789511d667162ca
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47701239"
---
# <a name="view-and-resolve-data-conflicts-for-merge-publications"></a>Visualizzare e risolvere i conflitti di dati per le pubblicazioni di tipo merge
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  I conflitti nella replica di tipo merge vengono risolti in base al sistema di risoluzione specificato per ogni articolo. Per impostazione predefinita, i conflitti vengono risolti senza che sia necessario l'intervento dell'utente. È tuttavia possibile visualizzare i conflitti e modificare il risultato della risoluzione nel Visualizzatore conflitti di replica [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 I dati dei conflitti sono disponibili nel Visualizzatore conflitti di replica per l'intervallo di tempo specificato per il periodo di memorizzazione dei conflitti, che per impostazione predefinita è di 14 giorni. Per impostare il periodo di memorizzazione dei conflitti, eseguire una delle operazioni seguenti:  
  
-   Specificare un valore del periodo di memorizzazione per il parametro **@conflict_retention** di [sp_addmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md).  
  
-   Specificare un valore di **conflict_retention** per il parametro **@property** e un valore del periodo di memorizzazione per il parametro **@value** di [sp_changemergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md).  
  
 Per impostazione predefinita, le informazioni sui conflitti vengono archiviate:  
  
-   Nel server di pubblicazione e nel Sottoscrittore se il livello di compatibilità della pubblicazione è pari a 90RTM o superiore.  
  
-   Nel server di pubblicazione se il livello di compatibilità della pubblicazione è inferiore a 80RTM.  
  
-   Nel server di pubblicazione se i Sottoscrittori eseguono [!INCLUDE[ssEW](../../includes/ssew-md.md)]. I dati in conflitto non possono essere archiviati nei Sottoscrittori [!INCLUDE[ssEW](../../includes/ssew-md.md)] .  
  
 L'archivio delle informazioni sui conflitti viene controllato dalla proprietà **conflict_logging** della pubblicazione. Per altre informazioni, vedere [sp_addmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) e [sp_changemergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md).  
  
 I conflitti possono inoltre essere risolti in modo interattivo durante la sincronizzazione tramite il sistema di risoluzione interattivo [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Il sistema di risoluzione interattivo è disponibile tramite Gestione sincronizzazione [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Per altre informazioni, vedere [Sincronizzare una sottoscrizione mediante Gestione sincronizzazione Microsoft Windows &#40;Gestione sincronizzazione Microsoft Windows&#41;](../../relational-databases/replication/synchronize-a-subscription-using-windows-synchronization-manager.md).  
  
### <a name="to-view-and-resolve-conflicts-for-merge-publications"></a>Per visualizzare e risolvere i conflitti relativi alle pubblicazioni di tipo merge  
  
1.  Connettersi al server di pubblicazione, o al Sottoscrittore se appropriato, in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Fare clic con il pulsante destro del mouse sulla pubblicazione per la quale si desidera visualizzare i conflitti e quindi scegliere **Visualizza conflitti**.  
  
    > [!NOTE]  
    >  Se è stato specificato il valore **'subscriber'** per la proprietà **conflict_logging** , la voce di menu **Visualizza conflitti** non sarà disponibile. Per visualizzare i conflitti, avviare ConflictViewer.exe dal prompt dei comandi. Per impostazione predefinita, ConflictViewer.exe si trova nella directory Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE. Per un elenco di parametri di avvio validi, eseguire ConflictViewer.exe -?.  
  
4.  Nella finestra di dialogo **Seleziona tabella con conflitti** selezionare un database, una pubblicazione e una tabella per cui visualizzare i conflitti.  
  
5.  Nel Visualizzatore conflitti di replica è possibile:  
  
    -   Filtrare le righe con i pulsanti a destra della griglia superiore.  
  
    -   Selezionare una riga nella griglia superiore per visualizzare le informazioni su tale riga nella griglia inferiore.  
  
    -   Selezionare una o più righe nella griglia superiore e quindi fare clic su **Rimuovi**, che equivale a fare clic sul pulsante **Invia riga in conflitto confermata** , senza apportare alcuna modifica ai dati.  
  
    -   Fare clic sul pulsante delle proprietà (**…**) per visualizzare ulteriori informazioni su una colonna coinvolta in un conflitto.  
  
    -   Modificare i dati nella colonna **Riga in conflitto confermata** o **Riga in conflitto ignorata** prima di inviare i dati, che sono di sola lettura se la colonna è grigia.  
  
    -   Fare clic su **Invia riga in conflitto confermata** per accettare la riga designata come riga confermata.  
  
    -   Fare clic su **Invia riga in conflitto ignorata** per non accettare la risoluzione e per propagare a tutti i nodi della topologia il valore designato come ignorato.  
  
    -   Selezionare **Registra informazioni dettagliate sul conflitto** per registrare i dati del conflitto in un file. Per specificare un percorso per il file, scegliere **Opzioni** dal menu **Visualizza**. Immettere un valore o fare clic sul pulsante Sfoglia (**...**) e quindi passare al file appropriato. Fare clic su **OK** per chiudere la finestra di dialogo **Opzioni** .  
  
6.  Chiudere il Visualizzatore conflitti di replica.  
  
## <a name="see-also"></a>Vedere anche  
 [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Specificare un sistema di risoluzione dei conflitti dell'articolo di merge](../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)  
  
  
