---
title: Aggiornare dal Database (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 84492f44-c368-4c75-954d-7307a2d2bbc0
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: decc6e25cc8480dfaf041a79baa0972bdd78e569
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47761499"
---
# <a name="refresh-from-database-oracletosql"></a>Eseguire l'aggiornamento dal database (OracleToSQL)
Il **aggiornare dal Database** nella finestra di dialogo consente di selezionare gli oggetti da aggiornare dal database Oracle. Le righe nella finestra di dialogo sono contraddistinte dal colore basato sullo stato dei metadati:  
  
-   Se i metadati dell'oggetto sono stato modificato in locale e nel database Oracle, la riga è blu.  
  
-   Se i metadati dell'oggetto sono stato modificato nel database Oracle ma non in SSMA, la riga è gialla.  
  
-   Se i metadati dell'oggetto sono stato modificato in locale, ma non nel database Oracle, la riga è verde.  
  
-   Se l'oggetto è nuovo nel database Oracle, la riga è di colore rosa.  
  
È possibile specificare le impostazioni di aggiornamento di oggetti predefiniti in di **impostazioni del progetto** nella finestra di dialogo. Per altre informazioni, vedere [impostazioni del progetto&#40;sincronizzazione&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-synchronization-oracletosql.md).  
  
Per l'accesso di **aggiornare dal Database** della finestra di dialogo scelta di un oggetto nel Visualizzatore metadati Oracle e fare clic su **aggiornare dal Database**.  
  
## <a name="options"></a>Opzioni  
**Comprimi (-)**  
Comprimi tutti i gruppi di oggetti per nascondere i singoli oggetti.  
  
**Espansione (+)**  
Espandere tutti i gruppi di oggetti per mostrare i singoli oggetti.  
  
**Mostra/Nascondi oggetti uguali**  
Gli oggetti nell'elenco viene nascosto se i metadati degli oggetti sono lo stesso nel database Oracle e in SSMA.  
  
**Aggiornare dal Database (freccia)**  
Utilizzare il pulsante freccia per specificare che i metadati per gli oggetti selezionati devono essere aggiornato in SSMA.  
  
**Eseguire l'operazione non aggiornato dal Database (pulsante) X**  
Utilizzare il pulsante X per specificare che i metadati per gli oggetti selezionati non devono essere aggiornati in SSMA.  
  
**Legenda**  
Consente di visualizzare una **legenda** nella finestra di dialogo. La legenda contiene il mapping tra i colori di riga e gli stati dei metadati.  
  
Per mantenere il **legenda** nella parte superiore della finestra di dialogo il **aggiornare dal Database** della finestra di dialogo Seleziona il **visualizzare nella parte superiore** casella di controllo.  
  
