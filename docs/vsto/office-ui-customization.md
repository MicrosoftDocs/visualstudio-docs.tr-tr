---
title: Office kullanıcı arabirimini özelleştirme
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- menus [Office development in Visual Studio], customizing
- actions panes [Office development in Visual Studio], creating
- WPF [Office development in Visual Studio]
- toolbars [Office development in Visual Studio], customizing
- Office applications [Office development in Visual Studio], UI customization
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 48c7fe1948231f88aba8309d6d06186848d32455
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836774"
---
# <a name="office-ui-customization"></a>Office kullanıcı arabirimini özelleştirme
  Visual Studio'da Office geliştirme araçlarını kullanarak, kullanıcı arabirimi (UI) Microsoft Office uygulamalarının özelleştirebilirsiniz. Bu konu aşağıdaki bölümlerde özelleştirebileceğiniz kullanıcı Arabirimi özellikleri açıklar:  
  
-   [Kullanıcı Arabirimi özellikleri karşılaştırması](#Comparison)  
  
-   [Eylemler bölmeleri ve özel görev bölmeleri](#Actions)  
  
-   [Özel Şerit UI'si](#Ribbon)  
  
-   [Backstage görünümü](#Backstage)  
  
-   [Outlook form bölgeleri](#FormRegion)  
  
-   [Belgelerindeki denetimler](#Controls)  
  
-   [Kısayol menüleri](#Shortcut)  
  
##  <a name="Comparison"></a> Kullanıcı Arabirimi özellikleri karşılaştırması  
 Aşağıdaki tabloda, Microsoft Office projelerinde özelleştirebilirsiniz ana kullanıcı Arabirimi özellikleri karşılaştırılmaktadır.  
  
|Özellik|Desteklenen proje türleri|Desteklenen Microsoft Office uygulamaları|  
|-------------|-----------------------------|---------------------------------------------|  
|Eylemler bölmesi|Belge düzeyinde özelleştirmeler|Excel<br /><br /> Word|  
|Özel görev bölmeleri|VSTO eklentileri|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word<br /><br /> Excel|  
|Özel Şerit UI'si|Belge düzeyinde özelleştirmeler<br /><br /> VSTO eklentileri|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Proje<br /><br /> Word<br /><br /> Visio|  
|Backstage görünümü|Belge düzeyinde özelleştirmeler<br /><br /> VSTO eklentileri|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)].<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Proje<br /><br /> Word<br /><br /> Visio|  
|Outlook form bölgeleri|VSTO eklentileri|Outlook|  
|Belgelerindeki denetimler|Belge düzeyinde özelleştirmeler<br /><br /> VSTO eklentileri|Excel<br /><br /> Word|  
|Kısayol menüleri|Belge düzeyinde özelleştirmeler<br /><br /> VSTO eklentileri|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Proje<br /><br /> Word<br /><br /> Visio<br /><br /> Excel|  
  
##  <a name="Actions"></a> Eylemler bölmeleri ve özel görev bölmeleri  
 Görev bölmeleri, genellikle bir Microsoft Office uygulamasının bir pencerede bir tarafı yerleştirilmiş kullanıcı arabirimi bölmeleri bulunur. Yerleşik görev bölmeleri, neredeyse tüm Microsoft Office uygulamalarını içerir. Bir görev bölmesi Word Yardım görev bölmesinde örneğidir.  
  
 Visual Studio'da Office geliştirme araçları, görev bölmeleri özelleştirmek için iki farklı şekilde sağlayın:  
  
- Belge düzeyi özelleştirmesinde, Eylemler bölmesi ekleyebilirsiniz. Varsayılan olarak, Eylemler bölmesinde belge sağındaki uygulama sağ tarafında görüntülenir. Ancak, Eylemler bölmesi sol, üst veya alt belgenin görüntülenebilir.  
  
- Özel görev bölmesi, VSTO eklentisi için ekleyebilirsiniz. Kullanıcılar, uygulama penceresinin farklı kenarlara özel görev bölmeleri sabitleyebileceğiniz veya penceresinde herhangi bir konuma özel görev bölmeleri sürükleyebilirsiniz.  
  
  Eylemler bölmeleri ve özel görev bölmeleri denetimleri ile veri girişi gibi görevleri kullanıcılara yardımcı olmak için çeşitli barındırarak işlevselliği sağlar. Şerit grubuna karşılaştırıldığında, Eylemler bölmesi ve özel görev bölmeleri, metin ve denetimler eklemek için daha geniş bir alan sağlar.  
  
  Eylemler bölmeleri hakkında daha fazla bilgi için bkz: [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md). Özel görev bölmeleri hakkında daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).  
  
##  <a name="Ribbon"></a> Özel Şerit UI'si  
 Office uygulamalarında eklediğiniz işlevselliği göstermek için Şerit kullanıcı arabirimini özelleştirebilirsiniz. Şerit, böylece bunlar daha kolay olur (denetimleri biçiminde) ilgili komutları düzenlemek için bir yoldur. Kendi Şerit sekmelerini ve çözümünüzde sağlayan işlevsellik, kullanıcılara erişim vermek için grupları oluşturabilirsiniz. Microsoft Office sistemi önceki sürümlerinde menüleri ve araç çubukları tarafından erişilen özelliklerin çoğu, Şerit kullanarak artık erişilebilir.  
  
 Daha fazla bilgi için [Şerite Genel Bakış](../vsto/ribbon-overview.md).  
  
##  <a name="Backstage"></a> Backstage görünümü  
 Office uygulamalarında tıklayarak **dosya** sekmesi, Backstage görünümü açılır. Backstage görünümü dosya düzeyinde görevleri ve eylemleri birleştirir ve benzer bir işlevsellik Microsoft Office düğmesinden erişilen 2007 Microsoft Office sistemi değiştirir, bir kullanıcı Arabirimi sağlar. Backstage görünümü, XML kullanarak tam olarak genişletilebilir.  
  
 Visual Studio Tasarımcı veya API'leri Backstage görünümünü özelleştirme için sağlamaz. Ancak, eklerseniz bir **Ribbon (XML)** öğesi Office projenize XML Backstage görünümünü özelleştirmek için Şerit XML dosyasına ekleyebilirsiniz. Hakkında daha fazla bilgi için **Ribbon (XML)** öğeleri görmek [Ribbon XML](../vsto/ribbon-xml.md).  
  
 Backstage görünümünü özelleştirme hakkında daha fazla bilgi için bkz. [geliştiriciler için Office 2010 Backstage görünümüne giriş](http://go.microsoft.com/fwlink/?LinkId=182189) ve [geliştiriciler için Office 2010 Backstage görünümünü özelleştirme](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
##  <a name="FormRegion"></a> Outlook form bölgeleri  
 Standart Microsoft Office Outlook formlarına özel işlevsellik eklemek için form bölgeleri'ni kullanın. Ek alanlar veya denetimleri ile var olan herhangi bir biçimde genişletmek form bölgeleri oluşturabilirsiniz. Visual Studio'da Office geliştirme araçlarını kullanarak yeni bir form bölgesi oluşturursanız, yalnızca Windows Forms denetimleri form bölgesini kullanabilirsiniz. Outlook'ta tasarlanan form bölgesini içeri aktarırsanız, sadece yerel Outlook denetimleri kullanabilirsiniz.  
  
 Outlook kullanıcı arabirimini farklı alanlarını kaplayabilir form bölgeleri oluşturabilirsiniz. Örneğin, bitişik form bölgeleri formun ilk sayfasının alt kısmında görüntülenir ve her bir bitişik form bölgesinin daraltılabilir. Ayrıca, herhangi bir mevcut standart form veya özel formu üzerinde tam ek form sayfası olarak görüntülenir ve görünen, ayrı form bölgesini ekleyebilirsiniz.  
  
 Daha fazla bilgi için [oluşturma Outlook form bölgeleri](../vsto/creating-outlook-form-regions.md).  
  
##  <a name="Controls"></a> Belgelerindeki denetimler  
 Word belgelerini ve Excel çalışma sayfaları için denetimleri çeşitli ekleyebilirsiniz. Örneğin, kullanıcı standart bir biçimde tarihleri girin veya bir veritabanına veri göndermek için bir çalışma sayfasına bir düğme put belgeye bir tarih seçici denetimi eklemek isteyebilirsiniz.  
  
 Excel veya Word için belge düzeyi projesi geliştirdiğinizde, denetimleri projenizde belge veya çalışma kitabındaki tasarım zamanında eklemek için Visual Studio Tasarımcısı'nı kullanabilirsiniz veya program aracılığıyla çalışma zamanında denetimler ekleyebilirsiniz. Excel veya Word için VSTO eklentisi projesi geliştirdiğinizde, herhangi bir açık belge veya çalışma zamanında denetimler program aracılığıyla ekleyebilirsiniz.  
  
 Daha fazla bilgi için [konak öğelerini ve denetimlerine genel bakış için ana bilgisayar](../vsto/host-items-and-host-controls-overview.md) ve [Windows forms denetimlerine Office belgeleri genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
##  <a name="Shortcut"></a> Kısayol menüleri  
 Bir belge veya uygulama penceresinin sağ tıklattığınızda bir kısayol menü görünür. Bir olay gibi bir kullanıcı bir belge, çalışma kitabı veya ana bilgisayar denetimi tıklattığında, gerçekleştikten sonra görünmesi için bir kısayol menüsü ayarlayabilirsiniz. Bir kısayol menüsüne bir dizi farklı komutlar veya denetimler ekleyebilirsiniz. Kısayol menüleri XML kullanarak oluşturun. Eklerseniz bir **Ribbon (XML)** öğesi Office projeniz için kısayol menüleri oluşturma için Ribbon XML dosyasındaki XML ekleyebilirsiniz. Kısayol menüleri oluşturmak için XML kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: kısayol menülerine komut ekleme](../vsto/how-to-add-commands-to-shortcut-menus.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Şerite Genel Bakış](../vsto/ribbon-overview.md)   
 [Windows forms denetimleri Office belgeleri genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)   
 [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)   
 [Özel görev bölmeleri](../vsto/custom-task-panes.md)   
 [Office çözümlerinde WPF denetimlerini kullanma](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)   
 [Nasıl yapılır: kullanıcı arayüzü hatalarını gösterme eklentisi](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [İzlenecek yol: bir Windows formu kullanarak veri toplama](../vsto/walkthrough-collecting-data-using-a-windows-form.md)  
  
  