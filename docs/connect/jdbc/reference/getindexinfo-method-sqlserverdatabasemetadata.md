---
title: Metodo getIndexInfo (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getIndexInfo
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8a677cc6-8e33-4e57-8678-0849345aa8d0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d7d66a175522cd89cf4bd0aca567779244b0a385
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47789828"
---
# <a name="getindexinfo-method-sqlserverdatabasemetadata"></a>Metodo getIndexInfo (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una descrizione degli indici e delle statistiche per la tabella specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.ResultSet getIndexInfo(java.lang.String cat,  
                                       java.lang.String schema,  
                                       java.lang.String table,  
                                       boolean unique,  
                                       boolean approximate)  
```  
  
#### <a name="parameters"></a>Parametri  
 *cat*  
  
 Valore **String** contenente il nome del catalogo.  
  
 *schema*  
  
 Valore **String** contenente il nome dello schema.  
  
 *table*  
  
 Valore **String** contenente il nome della tabella.  
  
 *unique*  
  
 **true** indici per i valori univoci vengono restituiti solo. **false** se vengono restituiti tutti gli indici.  
  
 *approximate*  
  
 **true** se i risultati riflettono i valori approssimati o non aggiornati. **false** se i risultati siano accurati.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getIndexInfo viene specificato dal metodo getIndexInfo nell'interfaccia DatabaseMetaData.  
  
 Il set di risultati restituito dal metodo getIndexInfo conterrà le informazioni seguenti:  
  
|nome|Tipo|Descrizione|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|Nome del database contenente la tabella specificata.|  
|TABLE_SCHEM|**String**|Schema della tabella.|  
|TABLE_NAME|**String**|Nome della tabella.|  
|NON_UNIQUE|**boolean**|Indica se i valori di indice possono essere non univoci.|  
|INDEX_QUALIFIER|**String**|Nome del proprietario dell'indice. Sarà Null se TYPE è tableIndexStatistic.|  
|INDEX_NAME|**String**|Nome dell'indice.|  
|TYPE|**short**|Tipo dell'indice. Può essere uno dei valori seguenti:<br /><br /> tableIndexStatistic (0)<br /><br /> tableIndexClustered (1)<br /><br /> tableIndexHashed (2)<br /><br /> tableIndexOther (3)|  
|ORDINAL_POSITION|**short**|Posizione ordinale della colonna nell'indice. La prima colonna nell'indice è 1.|  
|COLUMN_NAME|**String**|Nome della colonna.|  
|ASC_OR_DESC|**String**|Ordine utilizzato nelle regole di confronto dell'indice. Può essere uno dei valori seguenti:<br /><br /> A (crescente)<br /><br /> D (decrescente)<br /><br /> NULL (non applicabile)<br /><br /> **Nota:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] restituisce sempre "A".|  
|CARDINALITY|**int**|Numero di righe nella tabella o di valori univoci nell'indice.|  
|PAGES|**int**|Numero di pagine utilizzate per l'archiviazione dell'indice o della tabella.|  
|FILTER_CONDITION|**String**|Condizione di filtro.<br /><br /> **Nota:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] restituisce sempre null.|  
  
> [!NOTE]  
>  Per altre informazioni sui dati restituiti dal metodo getIndexInfo, vedere "sp_indexes (Transact-SQL)" nella documentazione online di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra come usare il metodo getIndexInfo per restituire le informazioni sugli indici e sulle statistiche della tabella Person.Contact del database di esempio di [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
```  
public static void executeGetIndexInfo(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getIndexInfo("AdventureWorks", "Person", "Contact", false, true);  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }   
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
