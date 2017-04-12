---
title: "Componenti jolly e convalida del contenuto | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "componenti jolly [XML]"
  - "convalida del contenuto [XML]"
ms.assetid: ffa7d974-3645-446c-8425-f0b22b6b060a
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# Componenti jolly e convalida del contenuto
  I componenti jolly vengono utilizzati per consentire una maggiore flessibilità riguardo agli elementi che è possibile includere in un modello di contenuto. Tali componenti vengono supportati nel linguaggio XSD nei modi seguenti:  
  
-   Elemento componenti jolly. Sono rappresentati dall'elemento **\<xsd:any>**.  
  
-   Attributo componenti jolly. Sono rappresentati dall'elemento **\<xsd:anyAttribute>**.  
  
 Entrambi gli elementi dei caratteri jolly, **\<xsd:any>** e **\<xsd:anyAttribute>**, supportano l'uso di un attributo **processContents**. Questo attributo consente di specificare un valore che indica il modo in cui le applicazioni XML gestiscono la convalida del contenuto di documenti associato a tali elementi dei caratteri jolly. Valori diversi e relativo effetto:  
  
-   Il valore **strict** specifica che viene eseguita la convalida completa del contenuto.  
  
-   Il valore **skip** specifica che non viene eseguita la convalida del contenuto.  
  
-   Il valore **lax** specifica che viene eseguita solo la convalida di elementi e attributi per i quali sono disponibili definizioni di schemi.  
  
## Elementi della convalida lax e del tipo xs:anyType  
 La specifica di XML Schema utilizza la convalida **lax** per elementi del tipo **anyType** . Poiché [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] non supportava la convalida di tipo lax, per gli elementi di tipo **anyType**veniva applicata la convalida di tipo strict. A partire da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], la convalida lax è supportata. Il contenuto degli elementi del tipo **anyType** sarà convalidato utilizzando la convalida lax.  
  
 L'esempio seguente illustra la convalida lax. L'elemento schema `e` è del tipo **anyType** . L'esempio crea variabili **xml** tipizzate e illustra la convalida lax dell'elemento di tipo **anyType** .  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"   
        targetNamespace="http://ns">  
   <element name="e" type="anyType"/>  
   <element name="a" type="byte"/>  
   <element name="b" type="string"/>  
 </schema>'  
GO  
```  
  
 L'esempio seguente è corretto in quanto la convalida di `<e>` ha esito positivo:  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>1</a><b>data</b></e>'  
GO  
```  
  
 L'esempio seguente ha esito positivo. L'istanza è accettata, anche se non è definito alcun elemento `<c>` nello schema:  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>1</a><c>Wrong</c><b>data</b></e>'  
GO  
```  
  
 L'istanza XML nell'esempio seguente è rifiutata, perché la definizione dell'elemento `<a>` non consente un valore della stringa.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>Wrong</a><b>data</b></e>'  
SELECT @var  
GO  
```  
  
## Vedere anche  
 [Requisiti e limitazioni per l'utilizzo di raccolte di XML Schema nel server](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  