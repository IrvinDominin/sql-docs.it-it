---
title: Filtrare i dati prima dell'esportazione (componente aggiuntivo MDS per Excel) | Microsoft Docs
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
caps.latest.revision: 10
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 110771dc83b9c2e902738c2a9ce10bcfb118428b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37972350"
---
# <a name="filter-data-before-exporting-mds-add-in-for-excel"></a>Filtrare i dati prima dell'esportazione (componente aggiuntivo MDS per Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] filtrare i dati quando si desidera limitare la dimensione o l'ambito dei dati da esportare in Excel.  
  
## <a name="prerequisites"></a>Prerequisites  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'autorizzazione per accedere all'area funzionale **Esplora** .  
  
### <a name="to-filter-data-before-exporting"></a>Per filtrare i dati prima dell'esportazione  
  
1.  Aprire Excel e nella scheda **Dati master** connettersi a un repository MDS. Per altre informazioni, vedere [Connettersi a un repository MDS &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  Nel riquadro **Esplora dati master** selezionare un modello e una versione. L'elenco di entità viene popolato.  
  
    -   Se il riquadro **Esplora dati master** non è visibile, nel gruppo **Connetti e carica** fare clic su **Esplora dati master**.  
  
    -   Se il riquadro **Esplora dati master** è disabilitato, significa che il foglio esistente contiene già i dati gestiti da MDS. Per abilitare il riquadro, aprire un nuovo foglio di lavoro.  
  
3.  Nel riquadro **Esplora dati master** , nell'elenco di entità fare clic sull'entità che si desidera filtrare.  
  
4.  Sulla barra multifunzione, nel gruppo **Connetti e carica** fare clic su **Filtro**.  
  
5.  Completare la finestra di dialogo **Filtro** selezionando gli attributi (colonne) da visualizzare, impostando l'ordine delle colonne e se necessario, filtrando i dati in modo che vengano restituite meno righe. Visualizzare il riquadro **Riepilogo** per sapere quanti dati saranno restituiti. Per altre informazioni, vedere [Finestra di dialogo Filtro &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md).  
  
6.  Fare clic su **Carica dati**. Il foglio viene popolato con i dati gestiti da MDS.  
  
    > [!NOTE]  
    >  -   Solo il primo milione di membri viene caricato in Excel.  
    > -   Nelle colonne che sono elenchi vincolati (attributi basati su dominio) vengono caricati solo i primi 25000 valori per impostazione predefinita.  
  
## <a name="next-steps"></a>Next Steps  
 [Importare dati da Excel in Master Data Services &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica: Esportazione dei dati in Excel &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Finestra di dialogo Filtro &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md)   
 [Riordinare le colonne &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/reorder-columns-mds-add-in-for-excel.md)  
  
  
