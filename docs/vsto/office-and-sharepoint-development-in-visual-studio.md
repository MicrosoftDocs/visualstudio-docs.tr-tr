---
title: Visual Studio'da Office ve SharePoint geliştirme
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], about developing applications
- Office development in Visual Studio
- Office projects
- Visual Studio Tools for Office, see Office development in Visual Studio
- Office applications [Office development in Visual Studio]
- Office Business Applications
- applications [Office development in Visual Studio]
- programming [Office development in Visual Studio]
- VSTO, see Office development in Visual Studio
- Office, development with Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 38291b46f2f9fee83ba9af0ae553cecca5ee35f6
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671709"
---
# <a name="office-and-sharepoint-development-in-visual-studio"></a>Visual Studio'da Office ve SharePoint geliştirme
  Microsoft Office ve SharePoint basit bir uygulama oluşturarak genişletebilir veya kullanıcılar indirir, eklenti [Office Store](https://store.office.com/) veya Kurumsal katalog veya yüklemek, kullanıcıların .NET Framework tabanlı bir çözüm oluşturarak bir bilgisayar.  
  
 Bu konuda:  
  
-   [Office ve SharePoint için eklentileri oluşturma](#Apps)  
  
-   [Bir VSTO eklentisi oluşturma](#Add-ins)  
  
-   [Bir SharePoint çözümünü oluşturun](#Solutions)  
  
##  <a name="Apps"></a> Office ve SharePoint için eklentileri oluşturma  
 Office 2013 ve SharePoint 2013'ü oluşturmak, dağıtmak ve Office ve SharePoint'i genişletin eklentileri paraya yardımcı olan yeni bir eklenti modeli sunar.  Bu eklenti Office veya SharePoint Online'da çalıştırabilirsiniz ve kullanıcıların birçok cihazından bunlarla etkileşim kurabilir.  
  
 Yeni nasıl öğrenmek [Office eklenti modeli](/office/dev/add-ins/overview/office-add-ins) Office kullanıcılarınızın deneyimini genişletmek için.  
  
 VSTO eklentileri ve çözümlerle karşılaştırıldığında küçük kaplama bu eklentiler sahiptir ve neredeyse tüm web teknolojisi HTML5, JavaScript, CSS3 ve XML gibi programlama kullanarak oluşturabilirsiniz.  Başlamak için Office geliştirici araçları Visual Studio içinde veya basit web tabanlı araç kullanımı Napa Office 365 geliştirme projeleri oluşturma, kod yazma ve eklentilerinizi tarayıcıda çalışan olanak sağlayan araçları, kod adıyla.  
  
 ![Uygulamalar için Office ve SharePoint kavramsal model](../vsto/media/officeandsharepointapps2015.png "Office ve SharePoint kavramsal model için uygulamalar")  
  
### <a name="build-an-office-add-in"></a>Office Eklentisi oluştur  
 Office eklentisinin Office genişletmek için oluşturun. Bu temelde, Excel, Word, Outlook ve PowerPoint gibi bir Office uygulamasında barındırılan bir Web sayfası olur. Uygulamanızı, belgeler, çalışma, e-posta iletilerini, randevuları, sunumlar ve projeleri için işlevleri ekleyebilirsiniz.  
  
 Office Store uygulamanızda satabilirsiniz.  [Office Store](https://store.office.com/) eklentilerinizi paraya çevirmek, güncelleştirmeleri yönetmek ve telemetri izlemek daha kolay hale getirir. Uygulamanızın, SharePoint veya Exchange sunucusu üzerinde bir uygulama Kataloğu aracılığıyla kullanıcılara da yayımlayabilirsiniz.  
  
 Aşağıdaki Office uygulamasının Bing harita üzerindeki çalışma sayfası verilerini gösterir.  
  
 ![Office içerik uygulamasının](../vsto/media/appforoffice.png "Office içerik uygulamasının")  
  
 **Daha fazla bilgi edinin**  
  
|Bitiş|Bkz. |  
|--------|---------|  
|Office eklentileri hakkında daha fazla bilgi edinin ve daha sonra bir oluşturabilirsiniz.|[Office eklentileri](/office/dev/add-ins/publish/publish)|  
|Farklı şekilde, Office ve genişletmek için kullanabileceğiniz, bir uygulama veya bir Office eklentisinin kullanıp kullanmadığını karar karşılaştırın.|[Office eklentileri, VSTO ve VBA için yol haritası](https://blogs.msdn.microsoft.com/officeapps/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba/)|  
  
### <a name="build-a-sharepoint-add-in"></a>Bir SharePoint eklentisi oluşturma  
 Kullanıcılarınız için SharePoint genişletmek için bir SharePoint eklentisi oluşturun. Temel olarak, bu gereksinimi kullanıcılar ya da işletmeniz çözer bir küçük, kullanımı kolay, tek başına uygulamasıdır.  
  
 SharePoint için uygulamanızı satmanıza [Office Store](https://store.office.com/). Ayrıca, eklentiniz eklenti Kataloğu SharePoint üzerinden kullanıcılara yayımlayabilirsiniz.  Site sahipleri yükleme, yükseltme ve eklentinizi grubu sunucusu veya site koleksiyonu Yöneticisi Yardımı olmadan SharePoint sitelerinde kaldırın.  
  
 Kullanıcıların iş kişileri Yönet yardımcı olan SharePoint için bir uygulama bir örneği aşağıda verilmiştir.  
  
 ![SharePoint için iş Kişi Yöneticisi uygulaması](../vsto/media/appforsharepoint.png "SharePoint için iş Kişi Yöneticisi uygulaması")  
  
 **Daha fazla bilgi edinin**  
  
|Bitiş|Bkz. |  
|--------|---------|  
|SharePoint eklentileri hakkında daha fazla bilgi edinin ve daha sonra bir oluşturabilirsiniz.|[SharePoint eklentileri](/sharepoint/dev/sp-add-ins/sharepoint-add-ins)|  
|Eklentileri, SharePoint için geleneksel SharePoint çözümleri ile karşılaştırın.|[SharePoint eklentileri'nde SharePoint çözümleri ile karşılaştırılan](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|  
|Bir SharePoint eklentisi veya bir SharePoint çözümünü oluşturmak isteyip istemediğinizi seçin.|[SharePoint eklentileri ve SharePoint çözümleri arasında karar verin](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
  
##  <a name="Add-ins"></a> Bir VSTO eklentisi oluşturma  
 Bir VSTO eklenti Office 2007 veya Office 2010 veya Office 2013 ve Office 2016, Office eklentileri ile olasılıklara ötesine genişletmek için oluşturun. VSTO eklentileri yalnızca masaüstünde çalışır. Kullanıcıların, VSTO eklentileri, dağıtmak ve desteklemek genellikle daha zor bulunmaları yüklemeniz gerekmez.  Ancak, VSTO eklentinizi daha yakından Office ile tümleştirilebilir. Örneğin, sekmeler ve denetimler için Office Şerit ekleyin ve belgelerin birleştirilmesi veya grafikleri değiştirme gibi gelişmiş Otomasyon görevlerini gerçekleştirmek. .NET Framework yararlanın ve C# ve Visual Basic Office nesnelerle etkileşim kurmak için kullanın.  
  
 Hangi bir VSTO eklentisinin yapmak için bir örnek aşağıda verilmiştir. Bu VSTO eklenti PowerPoint'e Şerit denetimleri, özel görev bölmesi ve bir iletişim kutusu ekler.  
  
 ![PowerPoint eklenti çözüm](../vsto/media/powerpointaddin.png "PowerPoint eklenti çözümü")  
  
 **Daha fazla bilgi edinin**  
  
|Bitiş|Oku|  
|--------|----------|  
|Farklı şekilde, Office ve genişletmek için kullanabileceğiniz, bir VSTO eklentisinin veya bir Office eklentisinin kullanması gerekip gerekmediğini karar karşılaştırın.|[Office eklentileri, VSTO ve VBA için yol haritası](https://blogs.msdn.microsoft.com/officeapps/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba/)|  
|Bir VSTO eklentisi oluşturma.|[VSTO eklentileri, Visual Studio ile derleme](create-vsto-add-ins-for-office-by-using-visual-studio.md)|  
  
##  <a name="Solutions"></a> Bir SharePoint çözümünü oluşturun  
 Hedef SharePoint Foundation 2010 ve SharePoint Server 2010 veya SharePoint 2013 ve SharePoint 2016 dışındaki bir SharePoint eklentisi ile olası şekilde genişletmek için bir SharePoint çözümünü oluşturun.  
  
 SharePoint çözümleri, şirket içi SharePoint grubunun sunucuları gerektirir. Yöneticiler yüklemeniz gerektiğinde ve SharePoint'te çözümleri çalıştırmak için sunucu performansını etkileyebilir. Ancak, çözümleri daha ayrıntılı SharePoint nesnelere erişim sağlar. Ayrıca, bir SharePoint çözüm derlediğinizde, .NET Framework yararlanın ve C# ve Visual Basic SharePoint nesnelerle etkileşim kurmak için kullanın.  
  
 **Daha fazla bilgi edinin**  
  
|Bitiş|Bkz. |  
|--------|---------|  
|SharePoint çözümleri SharePoint eklentileri ile karşılaştırın.|[SharePoint eklentileri'nde SharePoint çözümleri ile karşılaştırılan](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|  
|Bir SharePoint çözümünü oluşturun.|[SharePoint çözümleri oluşturma](../sharepoint/create-sharepoint-solutions.md)|  
  
  
