---
title: Uso di connessioni e sessioni in ADOMD.NET | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- sessions [ADOMD.NET]
- connections [ADOMD.NET]
ms.assetid: 72b43c06-f3e4-42c3-a696-4a3419c3b884
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 20cb03e5ccc65fe219426ba328501129e8747099
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48050231"
---
# <a name="working-with-connections-and-sessions-in-adomdnet"></a>Utilizzo di connessioni e sessioni in ADOMD.NET
  In XML for Analysis (XMLA) le sessioni forniscono supporto per le operazioni con stato durante l'accesso ai dati analitici. Le sessioni costituiscono l'ambito e il contesto di comandi e transazioni per un'origine dati analitici. Gli elementi XMLA utilizzati per gestire le sessioni vengono [BeginSession](../xmla/xml-elements-headers/beginsession-element-xmla.md), [sessione](../xmla/xml-elements-headers/session-element-xmla.md), e [EndSession](../xmla/xml-elements-headers/endsession-element-xmla.md).  
  
 ADOMD.NET utilizza questi tre elementi della sessione XMLA quando si avvia una sessione, si esegue una query o si recuperano dati durante una sessione e quando si chiude una sessione.  
  
## <a name="starting-a-session"></a>Avvio di una sessione  
 La proprietà <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A> dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> contiene l'identificatore della sessione attiva associata all'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>. L'utilizzo corretto di questa proprietà consente di controllare in modo efficace le informazioni sullo stato sia del client che del server nell'applicazione:  
  
-   Se la proprietà <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A> non è impostata su un ID di sessione valido quando il metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Open%2A> viene chiamato, per l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> è necessario impostare un nuovo ID di sessione dal provider. ADOMD.NET avvia una sessione inviando un'intestazione XMLA `BeginSession` al provider. Se la sessione viene avviata in modo corretto, ADOMD.NET imposta il valore della proprietà <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A> sull'ID di sessione della sessione appena creata.  
  
-   Se la proprietà <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A> è impostata su un ID di sessione valido quando il metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Open%2A> viene chiamato, l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> tenta di connettersi alla sessione specificata.  
  
 Se l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> non può connettersi alla sessione specificata o se il provider non supporta sessioni, viene generata un'eccezione.  
  
> [!NOTE]  
>  Dopo avere creato una sessione in ADOMD.NET, è possibile connettere più oggetti <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> solo a tale sessione attiva oppure è possibile disconnettere un unico oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> da tale sessione e riconnetterlo a un'altra sessione.  
  
## <a name="working-in-a-session"></a>Utilizzo di una sessione  
 Dopo che ADOMD.NET ha connesso l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> a una sessione valida, invierà un'intestazione XMLA `Session` al provider con tutte le richieste di dati o metadati fatti effettuate da un'applicazione. L'ID di sessione di ogni richiesta è impostato sul valore della proprietà <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A>.  
  
 Un ID di sessione non garantisce che una sessione rimanga valida. Se la sessione scade (ad esempio se si verifica un timeout o se la connessione si interrompe), il provider può scegliere di terminare le azioni di tale sessione e di eseguirne il rollback. In questo caso, tutte le chiamate successive al metodo dall'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> genereranno un'eccezione. Poiché le eccezioni vengono generate solo quando la successiva richiesta viene inviata al provider e non quando la sessione scade, l'applicazione deve essere in grado di gestire tali eccezioni in qualsiasi momento l'applicazione recuperi dati o metadati dal provider.  
  
## <a name="closing-a-session"></a>Chiusura di una sessione  
 Se il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Close%2A> viene chiamato senza specificare il valore della *endSession* parametro, o se il *endSession* parametro è impostato su True, sia la connessione alla sessione che la sessione associato il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> oggetto vengono chiusi. Per chiudere una sessione, ADOMD.NET invia un'intestazione XMLA `EndSession` al provider, con l'ID di sessione impostato sul valore della proprietà <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A>.  
  
 Se il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Close%2A> metodo viene chiamato con il *endSession* parametro impostato su False, la sessione associata la <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> oggetto rimane attivo, ma la connessione alla sessione viene chiusa.  
  
## <a name="example-of-managing-a-session"></a>Esempio di gestione di una sessione  
 Nell'esempio seguente viene illustrato come aprire una connessione, creare una sessione e chiudere la connessione mantenendo aperta la sessione in ADOMD.NET:  
  
```vb  
Public Function CreateSession(ByVal connectionString As String) As String  
    Dim strSessionID As String = ""  
    Dim objConnection As New AdomdConnection  
  
    Try  
        ' First, try to connect to the specified data source.  
        ' If the connection string is not valid, or if the specified  
        ' provider does not support sessions, an exception is thrown.  
        objConnection.ConnectionString = connectionString  
        objConnection.Open()  
  
        ' Now that the connection is open, retrieve the new  
        ' active session ID.  
        strSessionID = objConnection.SessionID  
        ' Close the connection, but leave the session open.  
        objConnection.Close(False)  
        Return strSessionID  
  
    Finally  
        objConnection = Nothing  
    End Try  
End Function  
```  
  
```csharp  
static string CreateSession(string connectionString)  
{  
    string strSessionID = "";  
    AdomdConnection objConnection = new AdomdConnection();  
    try  
    {  
        /*First, try to connect to the specified data source.  
          If the connection string is not valid, or if the specified  
          provider does not support sessions, an exception is thrown. */  
        objConnection.ConnectionString = connectionString;  
        objConnection.Open();  
  
        // Now that the connection is open, retrieve the new  
        // active session ID.  
        strSessionID = objConnection.SessionID;  
        // Close the connection, but leave the session open.  
        objConnection.Close(false);  
        return strSessionID;  
    }  
    finally  
    {  
        objConnection = null;  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di connessioni in ADOMD.NET](connections-in-adomd-net.md)  
  
  
