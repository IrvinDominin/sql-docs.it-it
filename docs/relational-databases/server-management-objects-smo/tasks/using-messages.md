---
title: Utilizzo dei messaggi | Documenti Microsoft
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
helpviewer_keywords: messages [SMO]
ms.assetid: 4037a866-4826-4c1f-890c-e7e3658adf13
caps.latest.revision: "40"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3ed18e9b9b7f91613a23d0146b79e0da2b056618
ms.sourcegitcommit: cb2f9d4db45bef37c04064a9493ac2c1d60f2c22
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/12/2018
---
# <a name="using-messages"></a>Utilizzo di messaggi
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  In SMO i messaggi di sistema sono rappresentati dal <xref:Microsoft.SqlServer.Management.Smo.SystemMessageCollection> oggetto a cui appartiene il **Server** oggetto. Poiché i messaggi di sistema non possono essere modificati, **SystemMessage** proprietà dell'oggetto sono di sola lettura.  
  
 In SMO i messaggi definiti dall'utente sono rappresentati a livello di codice dall'oggetto <xref:Microsoft.SqlServer.Management.Smo.UserDefinedMessageCollection>. È possibile individuare i messaggi definiti dall'utente esistenti scorrendo la raccolta. Nuovi messaggi definiti dall'utente possono essere creati creando un nuovo **UserDefinedMessage** oggetto e impostando le proprietà appropriate.  
  
## <a name="examples"></a>Esempi  
 Per gli esempi di codice seguenti, è necessario selezionare l'ambiente, il modello e il linguaggio di programmazione per la creazione dell'applicazione. Per ulteriori informazioni, vedere [crea un Visual C &#35; Progetto SMO in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="finding-a-particular-system-message-in-visual-basic"></a>Individuazione di un messaggio di sistema particolare in Visual Basic  
 Nell'esempio di codice viene illustrato come identificare un messaggio di sistema in base al numero ID e come visualizzarlo.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference an existing system message using the ItemByIdAndLanguage method.
Dim msg As SystemMessage
msg = srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english")
'Display the message ID and  text.
Console.WriteLine(msg.ID.ToString + " " + msg.Text)
```
  
## <a name="finding-a-particular-system-message-in-visual-c"></a>Individuazione di un messaggio di sistema particolare in Visual C#  
 Nell'esempio di codice viene illustrato come identificare un messaggio di sistema in base al numero ID e come visualizzarlo.  
  
```csharp  
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Reference an existing system message using the   
            //ItemByIdAndLanguage method.   
            SystemMessage msg = default(SystemMessage);  
            msg = srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english");  
            //Display the message ID and text.   
            Console.WriteLine(msg.ID.ToString() + " " + msg.Text);  
        }  
```  
  
## <a name="finding-a-particular-system-message-in-powershell"></a>Individuazione di un messaggio di sistema particolare in PowerShell  
 Nell'esempio di codice viene illustrato come identificare un messaggio di sistema in base al numero ID e come visualizzarlo.  
  
```powershell  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = get-item default  
  
#Get the message 14126 in US English and display it  
$msg = $srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english")  
$msg.ID.ToString() + " "+ $msg.Text  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-basic"></a>Aggiunta di un nuovo messaggio definito dall'utente in Visual Basic  
 Nell'esempio di codice viene illustrato come creare un messaggio definito dall'utente con un ID maggiore di 50000.  
  
```VBNET  
Dim mysrv As Server  
mysrv = New Server  
Dim udm As UserDefinedMessage  
udm = New UserDefinedMessage(mysrv, 50003, "us_english", 16, "Test message")  
udm.Create()  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-c"></a>Aggiunta di un nuovo messaggio definito dall'utente in Visual C#  
 Nell'esempio di codice viene illustrato come creare un messaggio definito dall'utente con un ID maggiore di 50000.  
  
```csharp  
{  
  
            Server mysrv = new Server();  
  
            UserDefinedMessage udm = new UserDefinedMessage(mysrv, 50030, "us_english",16, "Test message");  
            udm.Create();  
             UserDefinedMessage  msg = mysrv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
            //Display the message ID and text.   
            Console.WriteLine(msg.ID.ToString() + " " + msg.Text);  
  
        }  
```  
  
## <a name="adding-a-new-user-defined-message-in-powershell"></a>Aggiunta di un nuovo messaggio definito dall'utente in PowerShell  
 Nell'esempio di codice viene illustrato come creare un messaggio definito dall'utente con un ID maggiore di 50000.  
  
```powershell  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a new message  
  
$udm = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedMessage -argumentlist `  
$srv, 50030, "us_english", 16, "Test message"  
$udm.Create()  
$msg = $srv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
$msg  
```  
  
  
