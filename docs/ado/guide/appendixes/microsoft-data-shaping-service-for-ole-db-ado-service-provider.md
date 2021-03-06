---
title: Microsoft Data Shaping Service per OLE DB (ADO Service Provider) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], data shaping service for OLE DB
- data shaping service for OLE DB [ADO]
ms.assetid: 523009ce-e01b-4e2d-a7df-816d7688aff0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1e3dac6aefb8db2dbd1c651f0a2cf27b0f29559c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47735007"
---
# <a name="microsoft-data-shaping-service-for-ole-db-overview"></a>Microsoft Data Shaping servizi per Panoramica OLE DB
> [!IMPORTANT]
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Al contrario, le applicazioni devono utilizzare XML.

 Il servizio Microsoft di Data Shaping per provider di servizi OLE DB supporta la creazione della gerarchica (a forma di) [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetti da un provider di dati.

## <a name="provider-keyword"></a>Parola chiave provider
 Per richiamare il servizio di Data Shaping dei dati per OLE DB, specificare la parola chiave e il valore seguenti nella stringa di connessione.

```
"Provider=MSDataShape"
```

## <a name="dynamic-properties"></a>Proprietà dinamiche
 Quando viene richiamato questo provider di servizi, le seguenti proprietà dinamiche vengono aggiunti per il [le proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme del[connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto.

|Nome della proprietà dinamica|Description|
|---------------------------|-----------------|
|**Nomi univoci nuova forma**|Indica se **Recordset** gli oggetti con valori duplicati per loro **Reshape Name** sono consentite proprietà. Se questa proprietà dinamica **True** e un nuovo **Recordset** viene creato con lo stesso nome specificato dall'utente reshape esistente **Recordset**, quindi il nuovo  **Recordset** reshape name dell'oggetto viene modificato per renderlo univoco. Se questa proprietà è **False** e un nuovo **Recordset** viene creato con lo stesso nome specificato dall'utente reshape esistente **Recordset**, entrambi **Recordset**  gli oggetti abbiano lo stesso nome di modifica della forma. Di conseguenza, nessuno dei due **Recordset** possono essere ridefinite fino a quando esistono entrambi gli oggetti.<br /><br /> Il valore predefinito della proprietà è **False**.|
|**Provider di dati**|Indica il nome del provider che fornirà le righe da assumere una forma. Questo valore può essere NONE se non verrà utilizzato un provider per fornire le righe.|

 È anche possibile impostare proprietà dinamiche scrivibile specificando i relativi nomi come parole chiave nella stringa di connessione. Ad esempio, in Microsoft Visual Basic, impostare il **Provider di dati** proprietà dinamica da "MSDASQL", specificando:

```
Dim cn as New ADODB.Connection
cn.Open "Provider=MSDataShape;Data Provider=MSDASQL"
```

 È anche possibile impostare o recuperare una proprietà dinamica specificandone il nome dell'indice per la [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) proprietà. Ad esempio, il codice seguente recupera e stampa il valore corrente della **Provider di dati** proprietà dinamica, quindi imposta un nuovo valore se cn. DataProvider è stata impostata su "MSDataShape" (direttamente o indirettamente tramite la stringa di connessione) e non è stata aperta la connessione:

```
Debug.Print cn.Properties("Data Provider")
cn.Properties("Data Provider") = "MSDASQL"
```

> [!NOTE]
>  La proprietà dinamica **Provider di dati**, può essere impostato solo su una non aperta **connessione** oggetto. Una volta che viene aperta la connessione, il **Provider di dati** proprietà diventa di sola lettura.

 Per altre informazioni sul data shaping, vedere [Data Shaping](../../../ado/guide/data/data-shaping-overview.md).

## <a name="see-also"></a>Vedere anche
 [Appendice A: Provider](../../../ado/guide/appendixes/appendix-a-providers.md)
