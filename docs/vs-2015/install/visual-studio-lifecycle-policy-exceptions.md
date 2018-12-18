---
title: Visual Studio yaşam döngüsü ilkesi özel durumları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c238489d-6181-42c6-aa60-f75d0889dc68
caps.latest.revision: 3
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: c7c60747429bd702cdcea5f19891829411cd4a9c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772631"
---
# <a name="visual-studio-lifecycle-policy-exceptions"></a>Visual Studio yaşam döngüsü ilkesi özel durumları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio, derleyiciler, diller, çalışma zamanları, ortamlar ve diğer kaynaklardan oluşturulmuş, birçok Microsoft platformu için geliştirmeye olanak tanıyan bir koleksiyon içerir. Visual Studio müşterilerimize kolaylık sağlamak için, Visual Studio söz konusu Microsoft platformlarını hedefleyen ve destekleyen bazı Microsoft SDK’lerini ve diğer Microsoft bileşenlerini yükleyebilir. Bu bileşenler, kendi koşulları ve ilkeleri kapsamında lisanslandır ve desteklenir.  
  
## <a name="external-components-that-follow-a-lifecycle-policy-other-than-the-visual-studio-policy"></a>Visual Studio İlkesi dışında bir yaşam döngüsü ilkesi uyan dış bileşenler  
 Aşağıdaki tablo, Visual Studio ile (belirli sürümü Visual Studio yazılımlarına bağlı olarak) dahil edilebilir ve kendi destek ilkeleri ve zaman çerçevelerine tabidir olan Microsoft platform bileşenleri listeler.  
  
|ÜRÜN AİLESİ|DIŞ AD|  
|--------------------|-------------------|  
|[.NET 3.5](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=net%20framework%203.5&Filter=FilterNO)|.NET 3.5 SDK<br /><br /> Windows Identity Foundation|  
|[.NET 4.5](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=net%20framework%204.5&Filter=FilterNO)|.NET 4.5 SDK|  
|[.NET 4.5.1](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=.NET%20Framework%204.5.1&Filter=FilterNO)|.NET 4.5.1 MT Pack (Klasik)<br /><br /> .NET 4.5.1 Çoklu Sürüm Desteği Paketi (Mağaza)<br /><br /> .NET 4.5.1 OOB MSU<br /><br /> .NET 4.5.1 Redist<br /><br /> .NET 4.5.1 Yeniden Dağıtılabilir Dil Paketleri<br /><br /> .NET 4.5.1 SDK|  
|[ASP.NET Web Yığını](http://go.microsoft.com/fwlink/?LinkId=328918)|ASP.NET MVC 4<br /><br /> ASP.NET MVC 5<br /><br /> ASP.NET Web API<br /><br /> ASP.NET Web API 2<br /><br /> ASP.NET Web Sayfaları 2<br /><br /> ASP.NET Web Sayfaları 3|  
|[Entity Framework 6](http://go.microsoft.com/fwlink/?LinkId=328950)|Entity Framework 6|  
|[Exchange 2013](http://go.microsoft.com/fwlink/?LinkId=328950)|Exchange Web Hizmetleri|  
|[Microsoft OWIN](http://go.microsoft.com/fwlink/?LinkId=328951)|Microsoft OWIN|  
|[Microsoft Web geliştirici araçları 2013](http://go.microsoft.com/fwlink/?LinkId=328952)|Microsoft Web Geliştirici Araçları 2013|  
|Bu bileşenlerde yapılan güncelleştirmeler NuGet üzerinden dağıtılır ve standart Microsoft yaşam döngüsü ilkelerine uymaz.  Bkz: [ http://docs.nuget.org/ ](http://docs.nuget.org/) daha fazla bilgi için.|Microsoft .NET Framework 4.5 için JSON Web belirteci işleyicisi<br /><br /> NuGet 2.7<br /><br /> SignalR<br /><br /> Web Optimization Framework<br /><br /> WebGrease|  
|[ODataLib](http://go.microsoft.com/fwlink/?LinkId=328954)|ODataLib|  
|[Office 2013](http://support.microsoft.com/lifecycle/?p1=16674)|Open XML SDK|  
|[Çevrimiçi Hizmetler İlkesi](http://support.microsoft.com/gp/OSSLpolicy)|Microsoft Ads SDK|  
|[SharePoint 2013](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=sharepoint%20server%202013&Filter=FilterNO)|SharePoint İstemci Bileşenleri<br /><br /> SharePoint Foundation 2013<br /><br /> Windows Identity Foundation Uzantıları|  
|[Silverlight 5](http://support.microsoft.com/lifecycle/?p1=16278)<br /><br /> <br />> Ayrıca bkz: [http://support.microsoft.com/gp/lifean45](http://support.microsoft.com/gp/lifean45)|Silverlight 5 Çalışma Zamanı<br /><br /> Silverlight 5 SDK|  
|[SQL Server 2008 R2](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=SQL%20Server%202008%20R2&Filter=FilterNO)|SQL Sistem CLR Türleri (SQL Server 2008 R2)|  
|[SQL Server 2012](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=SQL%20Server%202012&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> SQL Komut Satırı Yardımcı Programları<br /><br /> SQL dil hizmeti - IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Yerel İstemcisi (Sqlncli)<br /><br /> SQL Server Express 2012 SP1<br /><br /> SQL Sistemi CLR Türleri (SQL Server 2012)<br /><br /> SQLDOM|  
|[SQL Server 2014](https://support.microsoft.com/en-us/lifecycle/search?sort=PN&alpha=SQL%20Server%202014&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> SQL Komut Satırı Yardımcı Programları<br /><br /> SQL dil hizmeti - IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Yerel İstemcisi (Sqlncli)<br /><br /> SQL Server Express 2014<br /><br /> SQL Sistem CLR Türleri (SQL Server 2014)<br /><br /> SQLDOM|  
|[SQL Server Compact Edition 4.0](http://support.microsoft.com/lifecycle/?p1=16106)|SQL Server Compact Edition 4.0|  
|[WCF RIA Hizmetleri v1.0 SP2](http://go.microsoft.com/fwlink/?LinkId=328955)|WCF RIA Services v1.0 SP2|  
|[Windows Server 2008](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=Windows%20Server%202008&Filter=FilterNO)|Windows Server 2008 için Windows Web Hizmetleri (WWS)|  
|[Windows 7](http://support.microsoft.com/lifecycle/?c2=14019)|Windows 7 SDK|  
|[Windows 8](http://support.microsoft.com/lifecycle/?c2=16796)|Windows 8 SDK|  
|[Windows 8.1](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=windows%208.1&Filter=FilterNO)|Windows 8.1 SDK<br /><br /> JavaScript için Windows Kitaplığı (WinJS)|  
|[Microsoft Azure](http://support.microsoft.com/gp/azure-cloud-lifecycle-faq)<br /><br /> <br />> Ayrıca bkz: [çevrimiçi yaşam döngüsü ilkesi](http://support.microsoft.com/gp/OSSLpolicy)|Microsoft Azure Mobile Services SDK<br /><br /> Microsoft Azure Mobile Services Araçları|