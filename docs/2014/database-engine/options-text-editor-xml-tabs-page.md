---
title: 'Opzioni (pagina XML:Tabs: Editor di testo) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Tabs
ms.assetid: 13bf5f8c-aba3-4c05-b8bb-eb475797c9bd
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 30842eec745c87848e4eb1c78c4806639da3ac0b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48050151"
---
# <a name="options-text-editorxmltabs-page"></a>Opzioni (Editor di testo/XML - Pagina Schede)
  Questa finestra di dialogo consente di cambiare il comportamento di tabulazione dell'editor XML utilizzato per modificare i documenti XML. Per visualizzare queste impostazioni, scegliere **Opzioni** dal menu **Strumenti** , espandere la cartella **Editor di testo** , espandere la sottocartella **XML** e quindi fare clic su **Tabulazioni**.  
  
## <a name="setting-options-in-multiple-locations"></a>Opzioni di impostazione in più posizioni  
 Le opzioni per l'editor XML possono essere impostate anche nella finestra di dialogo **Tutti i linguaggi - Generale** . Se si utilizza la finestra di dialogo **Tutti i linguaggi** per impostare opzioni diverse per gli altri editor di [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , ad esempio DMX o MDX, è necessario reimpostare le opzioni dell'editor XML tramite questa finestra di dialogo.  
  
## <a name="indenting"></a>Stili rientri  
 **Nessuno**  
 Quando questa opzione è selezionata, la nuova riga creata in seguito alla pressione di INVIO non viene rientrata. Il cursore viene posizionato in corrispondenza della prima colonna della nuova riga.  
  
 **Blocco**  
 Quando è selezionata questa opzione la nuova riga creata premendo INVIO viene rientrata automaticamente della stessa distanza della riga precedente.  
  
 **Smart**  
 Quando questa opzione è selezionata, la nuova riga creata in seguito alla pressione di INVIO viene posizionata in base al contesto. Ad esempio, dopo una parentesi graffa di apertura ({) le righe incluse vengono rientrate automaticamente di una tabulazione aggiuntiva. La corrispondente parentesi graffa di chiusura (}) viene riallineata con quella di apertura.  
  
## <a name="tabs"></a>Tabulazioni  
 **Dimensione tabulazione**  
 Consente di impostare la distanza in spazi tra le tabulazioni. Il valore predefinito è quattro spazi.  
  
 **Dimensione del rientro**  
 Consente di impostare la dimensione in spazi di un rientro automatico. Il valore predefinito è quattro spazi. Per riempire il rientro specificato verranno inseriti caratteri di tabulazione, caratteri di spazio o entrambi.  
  
 **Inserisci gli spazi**  
 Quando questa opzione è selezionata, durante le operazioni di rientro vengono inseriti solo caratteri spazio, non caratteri di tabulazione. Se la **Dimensione rientro** è impostata su 5, ad esempio, verranno inseriti cinque caratteri di spazio ogni volta che viene premuto TAB o si fa clic sul pulsante **Aumenta rientro** sulla barra degli strumenti della finestra principale di [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] .  
  
 **Mantieni tabulazioni**  
 Quando questa opzione è selezionata, durante le operazioni di rientro viene inserito il numero massimo di caratteri di tabulazione possibile. Ogni carattere di tabulazione riempie il numero di spazi specificato in **Dimensione tabulazione**. Se il valore specificato per l'opzione **Dimensione rientro** non è un multiplo pari del valore specificato per l'opzione **Dimensione tabulazione**, per riempire la differenza vengono aggiunti caratteri spazio.  
  
  
