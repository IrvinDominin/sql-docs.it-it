---
title: Nozioni di base di ADO MD | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO MD, fundamentals
ms.assetid: f6a20d9f-c1ab-474c-b9f3-82277e2a126d
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 92a245f79f7425d44aeb911edff479d80c08b08f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="ado-md-fundamentals"></a>Nozioni di base di ADO MD
Microsoft® ActiveX® Data Objects (ADO MD) (multidimensionale) consente di accedere ai dati multidimensionali da linguaggi, ad esempio Microsoft Visual Basic®, Microsoft Visual C++®. ADO MD estende Microsoft® dati oggetti ADO (ActiveX) per includere oggetti specifici di dati multidimensionali, ad esempio il [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) e [set di celle](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) oggetti. Con ADO MD è Sfoglia schema multidimensionale, un cubo di query e recuperare i risultati.  
  
 Ad esempio ADO, ADO MD utilizza un provider OLE DB sottostante per ottenere l'accesso ai dati. Per utilizzare ADO MD, il provider deve essere un provider di dati multidimensionali (dati Multidimensionali), come definito da OLE DB per OLAP. Un MDP presenta i dati in visualizzazioni anziché visualizzazioni tabulari, multidimensionali, ovvero come un provider di dati tabulare (TDP) presenta i dati. Consultare la documentazione per il provider OLE DB OLAP per ulteriori informazioni sulla sintassi specifica e il comportamento supportato dal provider.  
  
 Questo documento presuppone una conoscenza approfondita del linguaggio di programmazione Visual Basic e una conoscenza generale di ADO e OLAP. Per ulteriori informazioni, vedere il [manuale del programmatore ADO](../../../ado/guide/ado-programmer-s-guide.md) e [OLE DB per l'elaborazione OLAP (Online Analytical)](https://msdn.microsoft.com/library/windows/desktop/ms717005.aspx).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Panoramica di schemi e dati multidimensionali](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)  
  
-   [Utilizzo dei dati multidimensionali](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)  
  
-   [Uso di ADO con ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)  
  
-   [Programmazione con ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Modello a oggetti ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [Guida per programmatori ADO](../../../ado/guide/ado-programmer-s-guide.md)   
 [Estensioni ADO per Data Definition Language e protezione (ADOX)](../../../ado/guide/extensions/ado-extensions-for-data-definition-language-and-security-adox.md)   
 [Panoramica di schemi e dati multidimensionali](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [Programmazione con ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Utilizzo di ADO con ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)   
 [Utilizzo dei dati multidimensionali](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
