---
title: COLUMNS_UPDATED (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLUMNS_UPDATED_TSQL
- COLUMNS_UPDATED
dev_langs:
- TSQL
helpviewer_keywords:
- COLUMNS_UPDATED function
- testing columns
- column testing [SQL Server]
- updated columns
ms.assetid: 765fde44-1f95-4015-80a4-45388f18a42c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: a64b20ce0d429ccd257c178abdb7c04630e409ec
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="columnsupdated-transact-sql"></a>COLUMNS_UPDATED (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un **varbinary** schema di bit che indica le colonne in una tabella o vista che sono state inserite o aggiornate. COLUMNS_UPDATED viene utilizzata in qualsiasi punto all'interno del corpo di un trigger [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT o UPDATE per controllare se il trigger deve eseguire operazioni specifiche.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
COLUMNS_UPDATED ( )   
```  
  
## <a name="return-types"></a>Tipi restituiti
**varbinary**
  
## <a name="remarks"></a>Osservazioni  
COLUMNS_UPDATED controlla l'esecuzione delle operazioni UPDATE o INSERT in più colonne. Per eseguire il test per l'aggiornamento o inserimento tenta in una colonna, utilizzare [Update ()](../../t-sql/functions/update-trigger-functions-transact-sql.md).
  
COLUMNS_UPDATED restituisce uno o più byte ordinati da sinistra a destra, dove il bit meno significativo in ogni byte occupa la posizione più a destra. Il bit più a destra del primo byte rappresenta la prima colonna della tabella, il bit successivo a sinistra rappresenta la seconda colonna e così via. COLUMNS_UPDATED restituisce più byte se la tabella in cui viene creato il trigger include più di 8 colonne e il primo byte corrisponde al byte meno significativo. In operazioni INSERT COLUMNS_UPDATED restituisce TRUE per tutte le colonne in quanto nelle colonne vengono inseriti valori espliciti o impliciti (NULL).
  
Per controllare l'esecuzione di operazioni di aggiornamento o inserimento in colonne specifiche, aggiungere alla sintassi un operatore bit per bit e una maschera di bit di valori interi delle colonne sottoposte a controllo. Ad esempio, tabella **t1** contiene colonne **C1**, **C2**, **C3**, **C4**, e **C5** . Per verificare che le colonne **C2**, **C3**, e **C4** sono state aggiornate (con la tabella **t1** include un trigger UPDATE), seguire la sintassi con **& 14**. Per verificare se l'unica colonna **C2** viene aggiornata, specificare **& 2**.
  
È possibile utilizzare COLUMNS_UPDATED in qualsiasi punto all'interno di un trigger [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT o UPDATE.
  
La colonna ORDINAL_POSITION della vista INFORMATION_SCHEMA.COLUMNS non è compatibile con lo schema di bit delle colonne restituite da COLUMNS_UPDATED. Per ottenere uno schema di bit compatibile con COLUMNS_UPDATED, fare riferimento alla proprietà `ColumnID` della funzione di sistema `COLUMNPROPERTY` quando si esegue una query sulla vista `INFORMATION_SCHEMA.COLUMNS`, come illustrato nell'esempio seguente.
  
```sql
SELECT TABLE_NAME, COLUMN_NAME,  
    COLUMNPROPERTY(OBJECT_ID(TABLE_SCHEMA + '.' + TABLE_NAME),  
    COLUMN_NAME, 'ColumnID') AS COLUMN_ID  
FROM AdventureWorks2012.INFORMATION_SCHEMA.COLUMNS  
WHERE TABLE_NAME = 'Person';  
```  
  
## <a name="column-sets"></a>Set di colonne
Quando un set di colonne è definito in una tabella, il comportamento della funzione COLUMNS_UPDATED è il seguente:
-   Quando una colonna appartenente al set di colonne viene aggiornata in modo esplicito, il bit corrispondente per tale colonna e il bit per il set di colonne vengono impostati su 1.  
-   Quando un set di colonne viene aggiornato in modo esplicito, il bit per il set di colonne e i bit per tutte le colonne di tipo sparse della tabella vengono impostati su 1.  
-   Per le operazioni di inserimento, tutti i bit vengono impostati su 1.  
  
     Poiché le modifiche a un set di colonne determinano l'impostazione dei bit di tutte le colonne del set su 1, le colonne di un set che non erano state modificate sembreranno esserlo. Per altre informazioni sui set di colonne, vedere [Utilizzare set di colonne](../../relational-databases/tables/use-column-sets.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-columnsupdated-to-test-the-first-eight-columns-of-a-table"></a>A. Utilizzo di COLUMNS_UPDATED per controllare le prime 8 colonne di una tabella  
Nell'esempio seguente vengono create due tabelle, ovvero `employeeData` e `auditEmployeeData`. La tabella `employeeData` include informazioni riservate sulle retribuzioni dei dipendenti e può essere modificata dai membri dell'ufficio del personale. Se il numero di codice fiscale (SSN, Social Security Number), lo stipendio annuale o il numero di conto bancario relativi a un dipendente cambiano, nella tabella di controllo `auditEmployeeData` viene generato e inserito un record di controllo.
  
Grazie a `COLUMNS_UPDATED()` è possibile controllare rapidamente eventuali modifiche apportate alle colonne contenenti informazioni riservate relative ai dipendenti. L'utilizzo precedentemente descritto di `COLUMNS_UPDATED()` è valido solo se si tenta di rilevare le modifiche alle prime otto colonne della tabella.
  
```sql
USE AdventureWorks2012;  
GO  
IF EXISTS(SELECT TABLE_NAME FROM INFORMATION_SCHEMA.TABLES  
   WHERE TABLE_NAME = 'employeeData')  
   DROP TABLE employeeData;  
IF EXISTS(SELECT TABLE_NAME FROM INFORMATION_SCHEMA.TABLES  
   WHERE TABLE_NAME = 'auditEmployeeData')  
   DROP TABLE auditEmployeeData;  
GO  
CREATE TABLE dbo.employeeData (  
   emp_id int NOT NULL PRIMARY KEY,  
   emp_bankAccountNumber char (10) NOT NULL,  
   emp_salary int NOT NULL,  
   emp_SSN char (11) NOT NULL,  
   emp_lname nchar (32) NOT NULL,  
   emp_fname nchar (32) NOT NULL,  
   emp_manager int NOT NULL  
   );  
GO  
CREATE TABLE dbo.auditEmployeeData (  
   audit_log_id uniqueidentifier DEFAULT NEWID() PRIMARY KEY,  
   audit_log_type char (3) NOT NULL,  
   audit_emp_id int NOT NULL,  
   audit_emp_bankAccountNumber char (10) NULL,  
   audit_emp_salary int NULL,  
   audit_emp_SSN char (11) NULL,  
   audit_user sysname DEFAULT SUSER_SNAME(),  
   audit_changed datetime DEFAULT GETDATE()  
   );  
GO  
CREATE TRIGGER dbo.updEmployeeData   
ON dbo.employeeData   
AFTER UPDATE AS  
/*Check whether columns 2, 3 or 4 have been updated. If any or all  
columns 2, 3 or 4 have been changed, create an audit record. The
bitmask is: power(2,(2-1))+power(2,(3-1))+power(2,(4-1)) = 14. To test   
whether all columns 2, 3, and 4 are updated, use = 14 instead of >0  
(below).*/
  
   IF (COLUMNS_UPDATED() & 14) > 0  
/*Use IF (COLUMNS_UPDATED() & 14) = 14 to see whether all columns 2, 3,   
and 4 are updated.*/  
      BEGIN  
-- Audit OLD record.  
      INSERT INTO dbo.auditEmployeeData  
         (audit_log_type,  
         audit_emp_id,  
         audit_emp_bankAccountNumber,  
         audit_emp_salary,  
         audit_emp_SSN)  
         SELECT 'OLD',   
            del.emp_id,  
            del.emp_bankAccountNumber,  
            del.emp_salary,  
            del.emp_SSN  
         FROM deleted del;  
  
-- Audit NEW record.  
      INSERT INTO dbo.auditEmployeeData  
         (audit_log_type,  
         audit_emp_id,  
         audit_emp_bankAccountNumber,  
         audit_emp_salary,  
         audit_emp_SSN)  
         SELECT 'NEW',  
            ins.emp_id,  
            ins.emp_bankAccountNumber,  
            ins.emp_salary,  
            ins.emp_SSN  
         FROM inserted ins;  
   END;  
GO  
  
/*Inserting a new employee does not cause the UPDATE trigger to fire.*/  
INSERT INTO employeeData  
   VALUES ( 101, 'USA-987-01', 23000, 'R-M53550M', N'Mendel', N'Roland', 32);  
GO  
  
/*Updating the employee record for employee number 101 to change the   
salary to 51000 causes the UPDATE trigger to fire and an audit trail to   
be produced.*/  
  
UPDATE dbo.employeeData  
   SET emp_salary = 51000  
   WHERE emp_id = 101;  
GO  
SELECT * FROM auditEmployeeData;  
GO  
  
/*Updating the employee record for employee number 101 to change both   
the bank account number and social security number (SSN) causes the   
UPDATE trigger to fire and an audit trail to be produced.*/  
  
UPDATE dbo.employeeData  
   SET emp_bankAccountNumber = '133146A0', emp_SSN = 'R-M53550M'  
   WHERE emp_id = 101;  
GO  
SELECT * FROM dbo.auditEmployeeData;  
  
GO  
```  
  
### <a name="b-using-columnsupdated-to-test-more-than-eight-columns"></a>B. Utilizzo di COLUMNS_UPDATED per controllare più di 8 colonne  
Per controllare gli aggiornamenti eseguiti su colonne diverse dalle prime otto colonne di una tabella, utilizzare la funzione `SUBSTRING` per controllare il bit corretto restituito da `COLUMNS_UPDATED`. Nell'esempio seguente verifica disponibilità di aggiornamenti che influiscono sulle colonne `3`, `5`, e `9` nel `AdventureWorks2012.Person.Person` tabella.
  
```sql
USE AdventureWorks2012;  
GO  
IF OBJECT_ID (N'Person.uContact2', N'TR') IS NOT NULL  
    DROP TRIGGER Person.uContact2;  
GO  
CREATE TRIGGER Person.uContact2 ON Person.Person  
AFTER UPDATE AS  
    IF ( (SUBSTRING(COLUMNS_UPDATED(),1,1) & 20 = 20)   
        AND (SUBSTRING(COLUMNS_UPDATED(),2,1) & 1 = 1) )   
    PRINT 'Columns 3, 5 and 9 updated';  
GO  
  
UPDATE Person.Person   
   SET NameStyle = NameStyle,  
      FirstName=FirstName,  
      EmailPromotion=EmailPromotion;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche
[Operatori bit per bit &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
[CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)  
[AGGIORNAMENTO &#40; &#41; &#40; Transact-SQL &#41;](../../t-sql/functions/update-trigger-functions-transact-sql.md)
  
  
