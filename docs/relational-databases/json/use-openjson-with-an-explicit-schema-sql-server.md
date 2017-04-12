---
title: "Usare OPENJSON con uno schema esplicito (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "OPENJSON, con schema esplicito"
ms.assetid: 9c1c3bfb-e1ad-4659-b94f-722b0848d5a2
caps.latest.revision: 13
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 12
---
# Usare OPENJSON con uno schema esplicito (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Usare **OPENJSON** con uno schema esplicito per restituire una tabella formattata come specificato nella clausola WITH.  
  
 Di seguito sono riportati alcuni esempi che usano **OPENJSON** con uno schema esplicito. Per altre informazioni ed esempi, vedere [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md).  
  
## Esempio: usare la clausola WITH per formattare l'output  
 La query seguente restituisce i risultati mostrati nella tabella riportata di seguito. Notare come la clausola AS JSON causa la restituzione dei valori come oggetti JSON anziché come valori scalari in col5 e array_element.  
  
```tsql  
DECLARE @json NVARCHAR(MAX) =
N'{"someObject":   
   {"someArray":  
     [  
         {"k1": 11, "k2": null, "k3": "text"},  
         {"k1": 21, "k2": "text2", "k4": { "data": "text4" }},  
         {"k1": 31, "k2": 32},  
         {"k1": 41, "k2": null, "k4": { "data": false }}     
      ]  
   }  
}'  
  
SELECT * FROM  
OPENJSON(@json, N'lax $.someObject.someArray')  
WITH ( k1 int,   
       k2 varchar(100),  
       col3 varchar(6) N'$.k3',  
       col4 varchar(10) N'lax $.k4.data',  
       col5 nvarchar(MAX) N'lax $.k4' AS JSON, 
       array_element nvarchar(MAX) N'$' AS JSON  
)  
```  
  
 **Risultati**  
  
|k1|k2|col3|col4|col5|array_element|  
|--------|--------|----------|----------|----------|--------------------|  
|11|*NULL*|"text"|*NULL*|*NULL*|{"k1": 11, "k2": null, "k3": "text"}|  
|21|"text2"|*NULL*|"text4"|{ "data": "text4" }|{"k1": true, "k2": "text2", "k4": { "data": "text4" } }|  
|31|"32"|*NULL*|*NULL*|*NULL*|{"k1": 31, "k2": 32 }|  
|41|*NULL*|*NULL*|false|{ "data": false }|{"k1": 41, "k2": null,       "k4": { "data": false }    }|  
  
## Esempio: caricare JSON in una tabella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
 Nell'esempio seguente viene caricato un intero oggetto JSON in una tabella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
```tsql  
declare @json nvarchar(max) = '{  
 "id" : 2,  
 "firstName": "John",  
 "lastName": "Smith",  
 "isAlive": true,  
 "age": 25,  
 "dateOfBirth": "2015-03-25T12:00:00",  
 "spouse": null  
 }';  
  
 INSERT INTO Person  
 SELECT *   
 FROM OPENJSON(@json)  
 WITH (id int,  
       firstName nvarchar(50), lastName nvarchar(50),   
       isAlive bit, age int,  
       dateOfBirth datetime2, spouse nvarchar(50))  
  
```  
  
## Vedere anche  
 [OPENJSON &#40; Transact-SQL &#41;](../../t-sql/functions/openjson-transact-sql.md)  
  
  