---
title: Creare un join di un database secondario a un gruppo di disponibilità (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.availabilitygroup.joindbs.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- secondary databases [SQL Server]
- Availability Groups [SQL Server], joining
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: fd7efe79-c1f9-497d-bfe7-b2a2b2321cf5
caps.latest.revision: 37
author: rothja
ms.author: jroth
manager: jhubbard
ms.openlocfilehash: 63a6421ede7afbae66b80fda01e50223e732a27a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068325"
---
# <a name="join-a-secondary-database-to-an-availability-group-sql-server"></a>Creare un join di un database secondario a un gruppo di disponibilità (SQL Server)
  In questo argomento viene illustrato come aggiungere un database secondario al gruppo di disponibilità AlwaysOn tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], o PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Dopo aver preparato un database secondario per una replica di secondaria, è necessario creare un join del database al gruppo di disponibilità non appena possibile. In questo modo verrà avviato lo spostamento di dati dal database primario corrispondente al database secondario.  
  
-   **Prima di iniziare:**  
  
     [Prerequisiti](#Prerequisites)  
  
     [Security](#Security)  
  
-   **Per preparare un database secondario tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
> [!NOTE]  
>  Per informazioni su cosa accade dopo un database secondario viene aggiunta al gruppo, vedere [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
  
-   È necessario essere connessi all'istanza del server che ospita la replica secondaria.  
  
-   È necessario avere già creato un join della replica secondaria al gruppo di disponibilità. Per altre informazioni, vedere [Creare un join di una replica secondaria a un gruppo di disponibilità &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
-   Il database secondario deve essere stato preparato recentemente. Per altre informazioni, vedere [Preparare manualmente un database secondario per un gruppo di disponibilità &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È necessaria l'autorizzazione ALTER AVAILABILITY GROUP nel gruppo di disponibilità, l'autorizzazione CONTROL AVAILABILITY GROUP, l'autorizzazione ALTER ANY AVAILABILITY GROUP o l'autorizzazione CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 **Per creare un join di un database secondario a un gruppo di disponibilità**  
  
1.  In Esplora oggetti connettersi all'istanza del server in cui viene ospitata la replica secondaria ed espandere l'albero del server.  
  
2.  Espandere il nodo **Disponibilità elevata AlwaysOn** e il nodo **Gruppi di disponibilità** .  
  
3.  Espandere il gruppo di disponibilità che si desidera modificare, quindi espandere il nodo **Database disponibili** .  
  
4.  Fare clic con il pulsante destro del mouse sul database e scegliere **Crea un join del gruppo di disponibilità**.  
  
5.  In questo modo verrà aperta la finestra di dialogo **Creare un join dei database al gruppo di disponibilità** . Verificare il nome del gruppo di disponibilità, visualizzato sulla barra del titolo, e il nome o i nomi dei database visualizzati nella griglia, quindi fare clic su **OK**o su **Annulla**.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
 **Per creare un join di un database secondario a un gruppo di disponibilità**  
  
1.  Connettersi all'istanza del server che ospita la replica secondaria.  
  
2.  Utilizzare la [clausola SET HADR dell'istruzione ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) come indicato di seguito:  
  
     ALTER DATABASE *database_name* SET HADR AVAILABILITY GROUP = *group_name*  
  
     dove *database_name* è il nome del database di cui creare il join e *group_name* è il nome del gruppo di disponibilità.  
  
     Nell'esempio seguente viene creato un join del database secondario, `Db1`, alla replica secondaria locale del gruppo di disponibilità `MyAG`.  
  
    ```  
    ALTER DATABASE Db1 SET HADR AVAILABILITY GROUP = MyAG;  
    ```  
  
    > [!NOTE]  
    >  Per un esempio di questa istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)] impiegata in un contesto, vedere [Creare un gruppo di disponibilità &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md).  
  
##  <a name="PowerShellProcedure"></a> Utilizzo di PowerShell  
 **Per creare un join di un database secondario a un gruppo di disponibilità**  
  
1.  Spostarsi nella directory (`cd`) all'istanza del server che ospita la replica secondaria.  
  
2.  Utilizzare il `Add-SqlAvailabilityDatabase` cmdlet per aggiungere uno o più database secondari al gruppo di disponibilità.  
  
     Ad esempio, il seguente comando crea un join di un database secondario, `Db1`, al gruppo di disponibilità `MyAG` in una delle istanze del server che ospita una replica secondaria.  
  
    ```  
    Add-SqlAvailabilityDatabase `   
    -Path SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MyAG `   
    -Database "Db1"  
    ```  
  
    > [!NOTE]  
    >  Per visualizzare la sintassi di un cmdlet, usare il `Get-Help` cmdlet nel [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ambiente PowerShell. Per altre informazioni, vedere [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Per impostare e utilizzare il provider PowerShell per SQL Server**  
  
-   [Provider PowerShell per SQL Server](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Creare un join di una replica secondaria a un gruppo di disponibilità &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Preparare manualmente un database secondario per un gruppo di disponibilità &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)   
 [Panoramica di gruppi di disponibilità AlwaysOn di &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Risolvere i problemi di configurazione dei gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;eliminato](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  
