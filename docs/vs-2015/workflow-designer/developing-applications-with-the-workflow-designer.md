---
title: İş Akışı Tasarımcısı ile uygulama geliştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- DefaultWorkflowDesigner
- DefaultWorkflowDesigner.UI
helpviewer_keywords:
- Visual Studio 2010 Workflow Designer [WFD], overview
- Workflow Designer [WFD]
- Visual Studio 2010 Workflow Designer [WFD]
- Workflow Designer [WFD], overview
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 71cde900802543a21a20bc02e95bcfedc50d5541
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259161"
---
# <a name="developing-applications-with-the-workflow-designer"></a>İş Akışı Tasarımcısı ile uygulama geliştirme
[!INCLUDE[wfd1](../includes/wfd1-md.md)] Bir görsel tasarımcı ve grafik oluşturma ve hata ayıklama için hata ayıklayıcı [!INCLUDE[wf](../includes/wf-md.md)] uygulamalarda [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] barındırılan [!INCLUDE[vs2010](../includes/vs2010-md.md)] geliştirme ortamı. Bir bileşik iş akışı uygulaması, etkinlik kitaplığı oluşturma olanak tanır veya [!INCLUDE[indigo1](../includes/indigo1-md.md)] hizmet şablonları ve etkinlik tasarımcıları kullanarak. [!INCLUDE[crabout](../includes/crabout-md.md)] İş akışları için bkz: [Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/library/9a23ea6b-d600-483e-89cd-8889cfec5f66).  
  
 Bu yeni sürümünü birkaç yeni tasarım özelliklerinin şunlardır [!INCLUDE[wfd2](../includes/wfd2-md.md)] eski sürümlerini dışında [!INCLUDE[wfd2](../includes/wfd2-md.md)]:  
  
-   [!INCLUDE[wfd2](../includes/wfd2-md.md)] Kullanılarak oluşturulan [!INCLUDE[avalon1](../includes/avalon1-md.md)]. Bu etkinlik Tasarımcısı deneyimini geliştirir ve büyük ve karmaşık iş akışları için performansı geliştirir.  
  
-   Özel etkinlikler ile tasarlanmaktadır [!INCLUDE[avalon2](../includes/avalon2-md.md)], etkinlik tasarımcıları oluşturma Basitleştirilmiş için XAML ve programlama modeli kullanarak.  
  
-   Tanıdık akış stilini modelleme kullanarak program akışını görselleştirmenizi bir akış etkinliği uygulandı.  
  
-   [!INCLUDE[wfd2](../includes/wfd2-md.md)] Bunları etkinliklerini bağlama bildirme ve iş akışlarınızı, değişkenler kapsam olanak tanıyan bir yeni değişken tasarımcısını sahiptir.  
  
-   İçinde [!INCLUDE[vs2010](../includes/vs2010-md.md)], [!INCLUDE[wfd2](../includes/wfd2-md.md)] içinde Visual Basic deyimleri yazılırken tüm IntelliSense özelliklerini sağlar, [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] iş akışları.  
  
-   Hata ayıklama deneyimi artık XAML iş akışı tanımınızı ve çalışma zamanında yönetilen kodda benzer bir deneyim sağlar, XAML kod içine Adımlama, kesme noktaları ayarlamanıza olanak sağlayan XAML içinde genişletir.  
  
-   Yeniden barındırma [!INCLUDE[wfd2](../includes/wfd2-md.md)] dışında [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] artık yalnızca birkaç satır kod gerektiren önceki sürümlere kıyasla önemli ölçüde basitleştirilmiştir.  
  
-   Yeni <xref:System.Activities.Statements.Flowchart> etkinlik ve [akış](../workflow-designer/flowchart-activity-designer.md) tanıdık akış stilini modelleme kullanarak, program akışını görselleştirin olanak sağlar.  
  
-   Mesajlaşma etkinlikleri, yazmak tam bildirim temelli sağlayarak geliştirilmiştir (kod) [!INCLUDE[indigo1](../includes/indigo1-md.md)] Hizmetleri.  
  
-   **Hizmet Başvurusu Ekle...** işlev otomatik olarak Web Hizmetleri erişen etkinlikler oluşturmanıza olanak tanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İş Akışı Tasarımcısını Kullanma](../workflow-designer/using-the-workflow-designer.md)  
 Yeni etkinlikler ve yerleşik tasarımcıları kullanarak iş akışı projeleri oluşturma ve tasarımcı tarafından sağlanan diğer araçlar bağımsız değişkenler, değişkenleri, ifadeleri, içeri aktarmalar ve içerik haritalı gezinme işlemek için nasıl kullanılacağını gösterir.  
  
 [Etkinlik Tasarımcılarını kullanma](../workflow-designer/using-the-activity-designers.md)  
 Etkinlikler, şablonları ve sistem tarafından sağlanan, tasarımcılar kategorileri açıklanmaktadır.  
  
 [İş Akışı Tasarımcısı ile İş Akışlarında Hata Ayıklama](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 Geleneksel hata ayıklama yordamları yanı sıra XAML ve ifadeler hata ayıklama gerçekleştirmeyi açıklar.  
  
 [İş Akışı Tasarımcısı Kullanıcı Arabirimi Yardımı](../workflow-designer/workflow-designer-ui-help.md)  
 Tarafından sağlanan iletişim kutuları için bağlama duyarlı Yardım konularını içerir [!INCLUDE[wfd1](../includes/wfd1-md.md)], kısayolları ve hata iletileri Tasarımcısı Kabuk özellikleri hakkında daha fazla rehberlik yanı sıra, klavye.  
  
 [.NET 3.0 veya .NET 3.5 Framework’ü Hedefleyen İş Akışı Uygulamaları Geliştirme](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 Hedefleyen eski Tasarımcı kullanma yönergeleri içeren [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 [Tasarımcı yeniden barındırma &#91;WF örnekleri&#93;](http://msdn.microsoft.com/library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d)  
 Bu örnek, Tasarımcı içerecek şekilde WPF düzen oluşturma işlemi gösterilmektedir.  
  
 [Özel Etkinlik Tasarımcıları](http://msdn.microsoft.com/library/dcf14dca-ce6d-4278-96ba-062f0a679075)  
 Bu bölüm, iş akışı tasarımcısında görüntülemek için özel tasarımcılar kullanın etkinliği örneği içerir.