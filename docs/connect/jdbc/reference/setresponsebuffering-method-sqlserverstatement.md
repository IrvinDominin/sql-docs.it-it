---
title: Metodo setResponseBuffering (SQLServerStatement) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apilocation:
- SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: 9f489835-6cda-4c8c-b139-079639a169cf
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 114bba1ad782a3cc14585267407386d30f4ac0b6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32845796"
---
# <a name="setresponsebuffering-method-sqlserverstatement"></a>Metodo setResponseBuffering (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta la risposta per questa modalità di buffering [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto distinzione **stringa completa** o **adattivo**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setResponseBuffering(java.lang.String value)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Valore*  
  
 Oggetto **stringa** che contiene la modalità di buffer di risposta. La modalità valida può essere una delle seguenti stringhe tra maiuscole e minuscole: **completo** o **adattivo**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 **adattivo** specifica il buffer di dati minima possibile quando necessario.  
  
 **completa** specifica la lettura dell'intero risultato dal server in fase di esecuzione.  
  
 Adaptive è il valore predefinito nel Driver JDBC versione 2.0 e 3.0. full è il valore predefinito prima di Driver JDBC versione 2.0.  
  
 Il [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) metodo consente di eseguire l'override di **responseBuffering** connessione **stringa** proprietà per l'oggetto corrente [ SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto. Per ulteriori informazioni sull'utilizzo della modalità di buffering di risposta, vedere [utilizzando il buffer adattivo](../../../connect/jdbc/using-adaptive-buffering.md).  
  
 Se l'applicazione specifica un valore di parametro non valido per il [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) (metodo), un [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) viene generata un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)   
 [Uso del buffer adattivo](../../../connect/jdbc/using-adaptive-buffering.md)  
  
  
