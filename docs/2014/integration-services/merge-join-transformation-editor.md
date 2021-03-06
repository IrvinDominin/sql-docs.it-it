---
title: Editor trasformazione Merge Join | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.mergejointransformation.f1
helpviewer_keywords:
- Merge Join Transformation Editor
ms.assetid: ac06f419-30b3-42aa-8b34-42000bec4285
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6f6f584d49bfa238a5eda76b18f0dccb59db303f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48186831"
---
# <a name="merge-join-transformation-editor"></a>Editor trasformazione Merge join
  Utilizzare la finestra di dialogo **Editor trasformazione Merge join** per specificare il tipo di join, le colonne di join e le colonne di output per l'unione di due input combinati tramite un join.  
  
> [!IMPORTANT]  
>  Per eseguire la trasformazione Merge join, è necessario che i relativi dati di input siano ordinati. Per altre informazioni su questo requisito importante, vedere [Ordinamento dei dati per le trasformazioni Unione e Merge Join](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).  
  
 Per ulteriori informazioni sulla trasformazione Merge Join, vedere [Merge Join Transformation](data-flow/transformations/merge-join-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Tipo di join**  
 Consente di specificare se utilizzare un inner join, un outer join sinistro o un full join.  
  
 **Inverti ordine input**  
 Il pulsante **Inverti ordine input** consente di invertire l'ordine degli input. Questa selezione può risultare utile in caso si scelga di utilizzare un outer join sinistro.  
  
 **Input**  
 Per ogni colonna che si desidera includere nell'output unito, è innanzitutto necessario procedere a una selezione nell'elenco degli input disponibili.  
  
 Gli input vengono visualizzati in due tabelle separate. Selezionare le colonne da includere nell'output. Trascinare le colonne per creare un join tra le tabelle. Per eliminare un join, selezionarlo e quindi premere CANC.  
  
 **Colonna di input**  
 Selezionare una colonna da includere nell'output unito dall'elenco delle colonne disponibili nell'input selezionato.  
  
 **Alias di output**  
 Consente di digitare un alias per ogni colonna di output. Per impostazione predefinita viene suggerito il nome della colonna di input. È comunque possibile scegliere qualsiasi nome descrittivo univoco.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Ordinamento dei dati per le trasformazioni unione e Merge Join](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)   
 [Estendere un set di dati tramite la trasformazione Merge Join](data-flow/transformations/extend-a-dataset-by-using-the-merge-join-transformation.md)   
 [Unione-trasformazione](data-flow/transformations/merge-transformation.md)   
 [Trasformazione Unione input multipli](data-flow/transformations/union-all-transformation.md)  
  
  
