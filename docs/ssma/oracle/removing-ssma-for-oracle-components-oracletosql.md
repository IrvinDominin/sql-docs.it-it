---
title: Rimozione di SSMA per i componenti Oracle (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Uninstalling the Extension Pack
ms.assetid: 8b527a56-4e52-487a-9ac9-2320388e6d7d
caps.latest.revision: "6"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 369c3d4cba7e60bde7c7f55bb1e96fd0d7ac4381
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="removing-ssma--for-oracle-components-oracletosql"></a>Rimozione di SSMA per i componenti Oracle (OracleToSQL)
Al termine di migrazione di database da Oracle a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile disinstallare i componenti SSMA. È possibile disinstallare i componenti client in qualsiasi momento. Tuttavia, non è opportuno disinstallare il pacchetto di estensione da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , a meno che i database migrati non usare più funzioni nel **ssma_oracle** dello schema del **sysdb** database.  
  
## <a name="uninstalling-the-ssma-for-oracle-client"></a>Disinstallazione di SSMA per Client Oracle  
È possibile disinstallare SSMA utilizzando **Aggiungi / Rimuovi programmi**.  
  
**Per disinstallare SSMA**  
  
1.  Nel Pannello di controllo aprire **Aggiungi / Rimuovi programmi**.  
  
2.  Selezionare  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant per Oracle**, quindi fare clic su **rimuovere**.  
  
3.  Per confermare che si desidera disinstallare SSMA, fare clic su **Sì**.  
  
## <a name="uninstalling-the-extension-pack"></a>Disinstallare il pacchetto di estensione  
Se si è certi dei database migrati non utilizzano gli oggetti di **sysdb.ssma_oracle** dello schema, è possibile rimuovere il pacchetto di estensione utilizzando **Aggiungi / Rimuovi programmi**.  
  
**Per disinstallare il pacchetto di estensione**  
  
1.  Nel Pannello di controllo aprire **Aggiungi / Rimuovi programmi**.  
  
2.  Selezionare **Microsoft SQL Server Migration Assistant per Oracle estensione Pack**, quindi fare clic su **rimuovere**.  
  
3.  Per confermare che si desidera disinstallare il pacchetto di estensione, fare clic su **Sì**.  
  
4.  Nelle istanze con pagina utilità degli script del Database, selezionare un'istanza e quindi fare clic su **Avanti**.  
  
5.  Nella pagina parametri di connessione, selezionare il metodo di autenticazione e quindi fare clic su **Avanti**.  
  
    L'autenticazione di Windows utilizzerà le credenziali di Windows per tentare di accedere all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Se si seleziona [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] l'autenticazione, è necessario immettere un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] nome account di accesso e password.  
  
6.  Nella pagina operazione completata, fare clic su **OK**.  
  
7.  Nell'ultima pagina, fare clic su **uscita**.  
  
Dopo la disinstallazione, è possibile confermare che gli oggetti di **sysdb.ssma_oracle** schema ed eventualmente l'intero **sysdb** del database, è stato rimosso utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. Tuttavia, se si utilizzano altri prodotti SSMA, anche usano il **sysdb** database. Se il database esista e si è certi che nessun altro database fanno riferimento a oggetti in questo database, è possibile scollegare il database.  
  
## <a name="see-also"></a>Vedere anche  
[Installazione di SSMA per Client Oracle &#40; OracleToSQL &#41;](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[Installazione dei componenti SSMA OracleToSQL SQL Server &#40; &#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
  
