---
title: Implementazione di endpoint | Documenti Microsoft
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: endpoints [SMO]
ms.assetid: f8674dbb-9bc0-488f-9def-e9e0ce1ddf86
caps.latest.revision: "45"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a1d8ce479654f80d54c1a5aef6fb63138e13dbc6
ms.sourcegitcommit: cb2f9d4db45bef37c04064a9493ac2c1d60f2c22
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/12/2018
---
# <a name="implementing-endpoints"></a>Implementazione di endpoint
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Un endpoint è un servizio che può restare in attesa di richieste a livello nativo. SMO supporta vari tipi di endpoint tramite il <xref:Microsoft.SqlServer.Management.Smo.Endpoint> oggetto. È possibile creare un servizio di endpoint che gestisce un tipo specifico di payload, il quale utilizza un protocollo specifico, creando un'istanza di un oggetto <xref:Microsoft.SqlServer.Management.Smo.Endpoint> e impostandone le proprietà.  
  
 Il <xref:Microsoft.SqlServer.Management.Smo.Endpoint.EndpointType%2A> proprietà del <xref:Microsoft.SqlServer.Management.Smo.Endpoint> oggetto può essere utilizzato per specificare uno dei seguenti tipi di payload:  
  
-   Mirroring del database  
  
-   SOAP (il supporto per gli endpoint SOAP è presente in [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] e nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)])  
  
-   Service Broker  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)]  
  
 La proprietà <xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> può inoltre essere utilizzata per specificare i due protocolli supportati seguenti:  
  
-   Protocollo HTTP  
  
-   Protocollo TCP  
  
 Avendo specificato il tipo di payload, il payload effettivo può essere impostato utilizzando il <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Payload%2A> proprietà dell'oggetto. La proprietà dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Payload> fornisce un riferimento a un oggetto payload del tipo specificato, per cui è possibile modificare le proprietà.  
  
 Per l'oggetto <xref:Microsoft.SqlServer.Management.Smo.DatabaseMirroringPayload>, è necessario specificare il ruolo di mirroring e se è abilitata o meno la crittografia. Il <xref:Microsoft.SqlServer.Management.Smo.ServiceBrokerPayload> oggetto richiede informazioni sull'inoltro di messaggi, il numero massimo di connessioni consentite e la modalità di autenticazione. L'oggetto <xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethod.%23ctor%2A> richiede l'impostazione di varie proprietà tra cui la proprietà dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethodCollection.Add%2A> che specifica i metodi di payload SOAP disponibili ai client (stored procedure e funzioni definite dall'utente).  
  
 Analogamente, il protocollo può essere impostato tramite la proprietà dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Protocol%2A> che fa riferimento a un oggetto protocollo del tipo specificato dalla proprietà <xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A>. L'oggetto <xref:Microsoft.SqlServer.Management.Smo.HttpProtocol> richiede un elenco di indirizzi IP con restrizioni e informazioni relative a porte, siti Web e autenticazione. Il <xref:Microsoft.SqlServer.Management.Smo.TcpProtocol> oggetto richiede inoltre un elenco di indirizzi IP con restrizioni e informazioni sulla porta.  
  
 Quando l'endpoint è stato creato e definito completamente, è possibile concedere, revocare e negare l'accesso a utenti, gruppi, ruoli e account di accesso del database.  
  
## <a name="example"></a>Esempio  
 Per l'esempio di codice seguente, è necessario selezionare l'ambiente, il modello e il linguaggio di programmazione per la creazione dell'applicazione. Per ulteriori informazioni, vedere [crea un Visual C &#35; Progetto SMO in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-visual-basic"></a>Creazione di un servizio di endpoint del mirroring del database in Visual Basic  
 Nell'esempio di codice viene illustrato come creare un endpoint del mirroring del database in SMO. È necessario eseguire questa operazione prima di creare un database mirror. Utilizzare <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> e altre proprietà nell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Database> per creare un mirroring del database.  
  
```VBNET
'Set up a database mirroring endpoint on the server before setting up a database mirror.
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Define an Endpoint object variable for database mirroring.
Dim ep As Endpoint
ep = New Endpoint(srv, "Mirroring_Endpoint")
ep.ProtocolType = ProtocolType.Tcp
ep.EndpointType = EndpointType.DatabaseMirroring
'Specify the protocol ports.
ep.Protocol.Http.SslPort = 5024
ep.Protocol.Tcp.ListenerPort = 6666
'Specify the role of the payload.
ep.Payload.DatabaseMirroring.ServerMirroringRole = ServerMirroringRole.All
'Create the endpoint on the instance of SQL Server.
ep.Create()
'Start the endpoint.
ep.Start()
Console.WriteLine(ep.EndpointState)
``` 
  
## <a name="creating-a-database-mirroring-endpoint-service-in-visual-c"></a>Creazione di un servizio di endpoint del mirroring del database in Visual C#  
 Nell'esempio di codice viene illustrato come creare un endpoint del mirroring del database in SMO. È necessario eseguire questa operazione prima di creare un database mirror. Utilizzare <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> e altre proprietà nell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Database> per creare un mirroring del database.  
  
```csharp  
{  
            //Set up a database mirroring endpoint on the server before   
        //setting up a database mirror.   
        //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Define an Endpoint object variable for database mirroring.   
            Endpoint ep = default(Endpoint);  
            ep = new Endpoint(srv, "Mirroring_Endpoint");  
            ep.ProtocolType = ProtocolType.Tcp;  
            ep.EndpointType = EndpointType.DatabaseMirroring;  
            //Specify the protocol ports.   
            ep.Protocol.Http.SslPort = 5024;  
            ep.Protocol.Tcp.ListenerPort = 6666;  
            //Specify the role of the payload.   
            ep.Payload.DatabaseMirroring.ServerMirroringRole = ServerMirroringRole.All;  
            //Create the endpoint on the instance of SQL Server.   
            ep.Create();  
            //Start the endpoint.   
            ep.Start();  
            Console.WriteLine(ep.EndpointState);  
        }  
```  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-powershell"></a>Creazione di un servizio di endpoint del mirroring del database in PowerShell  
 Nell'esempio di codice viene illustrato come creare un endpoint del mirroring del database in SMO. È necessario eseguire questa operazione prima di creare un database mirror. Utilizzare <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> e altre proprietà nell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Database> per creare un mirroring del database.  
  
```powershell  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = get-item default  
  
#Get a new endpoint to congure and add  
$ep = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Endpoint -argumentlist $srv,"Mirroring_Endpoint"  
  
#Set some properties  
$ep.ProtocolType = [Microsoft.SqlServer.Management.SMO.ProtocolType]::Tcp  
$ep.EndpointType = [Microsoft.SqlServer.Management.SMO.EndpointType]::DatabaseMirroring  
$ep.Protocol.Http.SslPort = 5024  
$ep.Protocol.Tcp.ListenerPort = 6666 #inline comment  
$ep.Payload.DatabaseMirroring.ServerMirroringRole = [Microsoft.SqlServer.Management.SMO.ServerMirroringRole]::All  
  
# Create the endpoint on the instance  
$ep.Create()  
  
# Start the endpoint  
$ep.Start()  
  
# Report its state  
$ep.EndpointState;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Endpoint del mirroring del database &#40;SQL Server&#41;](../../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
  
  
