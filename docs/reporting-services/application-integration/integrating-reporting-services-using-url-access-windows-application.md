---
title: Accesso tramite URL in un'applicazione Windows | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Windows applications [Reporting Services]
- Web Browser controls [Reporting Services]
- Windows Forms [Reporting Services]
- browser controls [Reporting Services]
- URL access [Reporting Services], Windows applications
ms.assetid: a4b222e5-0cbd-409c-92c4-046a674db8ac
caps.latest.revision: 48
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 6174bfd45317faf9b6c8c7131dd1c5026d3a4d51
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="integrating-reporting-services-using-url-access---windows-application"></a>Integrazione di Reporting Services con accesso tramite URL - applicazione di Windows
  Sebbene l'accesso con URL a un server di report sia ottimizzato per un ambiente Web, è possibile utilizzarlo anche per incorporare i report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in un'applicazione [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Per l'accesso con URL che comporta l'utilizzo di Windows Form è tuttavia necessario utilizzare comunque la tecnologia del browser Web. È possibile utilizzare gli scenari di integrazione seguenti con l'accesso con URL e Windows Form:  
  
-   Visualizzazione di un report da un'applicazione Windows Form avviando un browser a livello di programmazione.  
  
-   Utilizzo del controllo <xref:System.Windows.Forms.WebBrowser> in un Windows Form per visualizzare un report.  
  
## <a name="starting-internet-explorer-from-a-windows-form"></a>Avvio di Internet Explorer da un Windows Form  
 È possibile utilizzare la classe <xref:System.Diagnostics.Process> per accedere a un processo in esecuzione in un computer. Il <xref:System.Diagnostics.Process> classe è utile [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] costrutto per avviare, arrestare, il controllo e monitoraggio delle applicazioni. Per visualizzare un report specifico nel database del server di report, è possibile avviare il **IExplore** processo, passando l'URL del report. L'esempio di codice seguente può essere utilizzato per avviare [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer e passare un URL del report specifico quando l'utente fa clic su un pulsante in un Windows Form.  
  
```vb  
Private Sub viewReportButton_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles viewReportButton.Click  
   ' Build the URL access string based on values supplied by a user  
   Dim url As String = serverUrlTextBox.Text + "?" & reportPathTextBox.Text & _  
   "&rs:Command=Render" & "&rs:Format=HTML4.0"  
  
   ' If the user does not select the toolbar check box,  
   ' turn the toolbar off in the HTML Viewer  
   If toolbarCheckBox.Checked = False Then  
      url += "&rc:Toolbar=False"  
   End If  
   ' load report in the Web browser  
   Try  
      System.Diagnostics.Process.Start("IExplore", url)  
   Catch  
      MessageBox.Show("The system could not start the specified report using Internet Explorer.", _  
      "An error has occurred", MessageBoxButtons.OK, MessageBoxIcon.Error)  
   End Try  
End Sub 'viewReportButton_Click  
```  
  
```csharp  
// Sample click event for a Button control on a Windows Form  
private void viewReportButton_Click(object sender, System.EventArgs e)  
{  
   // Build the URL access string based on values supplied by a user  
   string url = serverUrlTextBox.Text + "?" + reportPathTextBox.Text +  
      "&rs:Command=Render" + "&rs:Format=HTML4.0";  
  
   // If the user does not check the toolbar check box,  
   // turn the toolbar off in the HTML Viewer  
   if (toolbarCheckBox.Checked == false)  
      url += "&rc:Toolbar=False";  
  
   // load report in the Web browser  
   try  
   {  
      System.Diagnostics.Process.Start("IExplore", url);  
   }  
  
   catch (Exception)  
   {  
      MessageBox.Show(  
         "The system could not open the specified report using Internet Explorer.",   
         "An error has occurred", MessageBoxButtons.OK, MessageBoxIcon.Error);  
   }  
}  
```  
  
## <a name="embedding-a-browser-control-on-a-windows-form"></a>Incorporamento di un controllo browser in un Windows Form  
 Se non si desidera visualizzare il report in un browser esterno, è possibile incorporare in modo semplice un browser come parte di un Windows Form utilizzando il controllo <xref:System.Windows.Forms.WebBrowser>.  
  
###### <a name="to-add-the-webbrowser-control-to-your-windows-form"></a>Per aggiungere il controllo WebBrowser al Windows Form  
  
1.  Creare una nuova applicazione Windows in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] o [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].  
  
2.  Individuare il <xref:System.Windows.Forms.WebBrowser> controllo il **della casella degli strumenti** la finestra di dialogo.  
  
     Se il **della casella degli strumenti** è visibile non è possibile accedervi facendo clic di **vista** voce di menu e selezionando **della casella degli strumenti**.  
  
3.  Trascinare il <xref:System.Windows.Forms.WebBrowser>controllo sull'area di progettazione di Windows Form.  
  
     Il <xref:System.Windows.Forms.WebBrowser>controllo denominato webBrowser1 verrà aggiunto al Form  
  
 Diretta di <xref:System.Windows.Forms.WebBrowser> controllo a un URL chiamando il relativo **Naviga** (metodo). È possibile assegnare una stringa di accesso con URL specifica al controllo <xref:System.Windows.Forms.WebBrowser> in fase di esecuzione come illustrato nell'esempio seguente.  
  
```vb  
Dim url As String = "http://localhost/reportserver?/" & _  
                    "AdventureWorks2012 Sample Reports/" & _  
                    "Company Sales&rs:Command=Render"  
WebBrowser1.Navigate(url)  
```  
  
```csharp  
string url = "http://localhost/reportserver?/" +  
             "AdventureWorks2012 Sample Reports/" +  
             "Company Sales&rs:Command=Render";  
webBrowser1.Navigate(url);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Integrazione di Reporting Services nelle applicazioni](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [Integrazione di Reporting Services con accesso tramite URL](../../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)   
 [Integrazione di Reporting Services tramite SOAP](../../reporting-services/application-integration/integrating-reporting-services-using-soap.md)   
 [Integrazione di Reporting Services utilizzando i controlli ReportViewer](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md)   
 [Accesso con URL &#40; SSRS &#41;](../../reporting-services/url-access-ssrs.md)  
  
  