---
title: Eliminare una versione (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- versions [Master Data Services], deleting
- deleting versions [Master Data Services]
ms.assetid: 2a4eeffe-8379-4744-ad44-c27d8c8ac9a8
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a6a7c9ca0b236fadbd10e0036baaf4759c99d43c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168341"
---
# <a name="delete-a-version-master-data-services"></a>Eliminare una versione (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]eliminare una versione quando si è certi che non sono più necessari i dati master a essa associati. Dopo avere eliminato una versione, non è possibile recuperare i dati master associati.  
  
> [!WARNING]  
>  Se un modello presenta una sola versione e la si elimina, il modello diventa inutilizzabile.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre delle autorizzazioni per visualizzare la vista mdm.viw_SYSTEM_SCHEMA_VERSION ed eseguire la stored procedure mds.udpVersionDelete nel database di [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Per altre informazioni, vedere [Sicurezza di oggetti di database &#40;Master Data Services&#41;](database-object-security-master-data-services.md).  
  
### <a name="to-delete-a-version"></a>Per eliminare una versione  
  
1.  Aprire [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] e connettersi all'istanza [!INCLUDE[ssDE](../includes/ssde-md.md)] per il database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Aprire la vista mdm.viw_SYSTEM_SCHEMA_VERSION.  
  
3.  Trovare la versione del modello che si vuole eliminare e copiare il valore nel campo **ID** .  
  
4.  Creare una nuova query.  
  
5.  Digitare il testo seguente, sostituendo *version_ID* con il valore copiato nel passaggio 2.  
  
    ```  
    EXEC [mdm].[udpVersionDelete] @Version_ID='version_ID'  
    ```  
  
6.  Consente di eseguire la query.  
  
    > [!NOTE]  
    >  Può essere necessario attendere alcuni minuti prima che l'applicazione Web rifletta la modifica.  
  
## <a name="see-also"></a>Vedere anche  
 [Versioni di &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)   
 [Copiare una versione &#40;Master Data Services&#41;](../../2014/master-data-services/copy-a-version-master-data-services.md)  
  
  