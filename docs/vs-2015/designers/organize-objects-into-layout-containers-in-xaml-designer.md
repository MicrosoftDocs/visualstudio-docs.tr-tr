---
title: Nesneleri Düzen kapsayıcılarına XAML Tasarımcısı'nda yerleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c92af4e78715c608fdee860690fd58561b8bb2d5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49219563"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>XAML Tasarımcısı’nda nesneleri düzen kapsayıcılarına yerleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nesneleri bir sayfada görüntülenmesini istediğiniz düşünün; Görüntü, düğmeler ve video gibi nesneleri. Dikey veya yatay veya sabit konumlarda satırlar ve sütunlar, tek bir satırda görünmesini istediğiniz olabilir.  
  
 Bir düzen paneli, sayfanın nasıl görünebilir hakkında düşünmek ettikten sonra seçin. Nesnelerinizi eklemeniz gerektiği için tüm sayfaları ile başlayın. Varsayılan olarak, bu bir **kılavuz** ancak isterseniz bunu değiştirebilirsiniz.  
  
 Düzen bölmeleri, sayfadaki nesneleri Düzenle yardımcı, ancak, birden fazla yapın. Bunlar farklı ekran boyutlarını ve çözünürlüklerini tasarım Yardım. Kullanıcıların uygulamanızı çalıştırdığınızda, her şeyi bir düzen paneli cihazlarının ekran gerçek boyutunuzu eşleşecek şekilde yeniden boyutlandırır. Elbette, düzeninizi yapmak istemiyorsanız, bir bölümü düzeni veya tüm düzeni için bu davranışı geçersiz kılabilirsiniz. Yükseklik ve genişlik Özellikleri'ı, kontrol etmek için kullanabilirsiniz.  
  
 Bu sayfa, Düzen bölmeleri ve denetimleri açıklar ve ardından size yardımcı olacak kısa videolar ile başlama yönlendirir.  
  
> [!NOTE]
>  Bazı videoları Blend veya Expression Blend, Visual Studio ve Visual Studio için Blend olarak aynı XAML Tasarımcısı'nı kullanan başvurabilir.  
  
## <a name="layout-panels"></a>Düzen bölmeleri  
 Sayfanız, bu düzen bölmelerini birini seçerek başlatın. Sayfanız birden fazla olabilir. Örneğin, ile başlayabilir bir **kılavuz** Düzen paneli ve ardından eklemek bir **StackPanel** bir alanda **kılavuz** böylece o öğenin dikey denetimlerinde düzenleyebilirsiniz.  
  
 Aşağıdaki Düzen bölmelerini bu özellik en kullanılır, ancak diğerleri vardır. Bunları bulabilirsiniz tümü **varlıklar** paneli.  
  
-   [Kılavuz](#Grid)  
  
-   [UniformGrid](#Uniform)  
  
-   [Tuval](#Canvas)  
  
-   [StackPanel](#Stack)  
  
-   [WrapPanel](#Wrap)  
  
-   [DockPanel](#Dock)  
  
###  <a name="Grid"></a> Kılavuz  
 Nesneleri, satırlar ve sütunlar halinde düzenleyin.  
  
 ![](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png "98b234b2-ac3b-441F-9136-98375fee87b7")  
  
 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [kullanarak Kılavuzlar](http://www.popscreen.com/v/6A4hj/Microsoft-Expression-Blend-Using-Grids)  
  
###  <a name="Uniform"></a> UniformGrid  
 Nesneler eşit veya tek düzen kılavuz bölgeye yerleştirin. Bu panelde, görüntülerin listesini düzenlemek için idealdir.  
  
 ![](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png "928b9284-a7e8-4678-875a-656b80b78076")  
  
 (Yalnızca WPF projeleri için kullanılabilir)  
  
 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [bir UniformGrid ile çalışma](http://www.popscreen.com/v/6A4iq/Microsoft-Expression-Blend-Working-with-a-UniformGrid)  
  
###  <a name="Canvas"></a> Tuval  
 Nesneleri istediğiniz gibi düzenleyin. Kullanıcıların uygulamanızı çalıştırdığınızda, bu öğeleri ekranında konumları sabit.  
  
 ![](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png "e1ae27f0-3a57-454e-b580-877dcea8836d")  
  
 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [tuval ile çalışma](http://www.popscreen.com/v/6A4hT/Microsoft-Expression-Blend-Working-with-the-Canvas)  
  
###  <a name="Stack"></a> StackPanel  
 Tek bir satırda nesneleri, yatay veya dikey olarak düzenleyin.  
  
 ![](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png "a85a7b57-b0a8-495e-b985-f0291e41d093")  
  
 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [StackPanel ve WrapPanel ile çalışma](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
###  <a name="Wrap"></a> WrapPanel  
 Nesneleri sırayla soldan sağa düzenleyin. Bölmenin en sağdaki ucuna dışında yer çalıştığında, *sarmalar* içeriği sonraki satıra vb. soldan sağa üst-alt. Böylece nesnelerin üst alta, akış, ayrıca bir sarmalama panelinin yönü dikey soldan sağa yapabilirsiniz.  
  
 (Yalnızca WPF projeleri için kullanılabilir)  
  
 ![](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png "b1c415fb-9a32-4a18-aa0b-308fca994ac9")  
  
 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [StackPanel ve WrapPanel ile çalışma](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
###  <a name="Dock"></a> DockPanel  
 Böylece bunlar kalmasını nesneleri düzenleyin veya *dock*, panelin bir kenarında için.  
  
 (Yalnızca WPF projeleri için kullanılabilir)  
  
 ![](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png "72d46b58-9a49-4dd5-8af7-6843c0440226")  
  
 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [WPF - DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)  
  
## <a name="layout-controls"></a>Düzen denetimleri  
 Nesnelerinizi Düzen denetimlere de ekleyebilirsiniz. Bunlar olarak olmayan özellik açısından zengin gibi bir düzen paneli, ancak bunları belirli senaryolar için yararlı bulabilirsiniz.  
  
 Aşağıdaki Düzen denetimler bu özellik en kullanılır, ancak diğerleri vardır. Bunları bulabilirsiniz tümü **varlıklar** paneli.  
  
-   [Kenarlık](#Border)  
  
-   [Açılan Pencere](#Popup)  
  
-   [ScrollViewer](#Scroll)  
  
-   [UniformGrid](#Uniform)  
  
-   [Viewbox](#View)  
  
###  <a name="Border"></a> Kenarlık  
 Kenarlık, arka plan veya her ikisi de bir nesnenin çevresindeki oluşturun. Yalnızca bir nesne için ekleyebileceğiniz bir **kenarlık**. Kenarlık veya arka plan bilgileri için birden fazla nesne uygulamak istediğiniz düzen paneline ekleyin **kenarlık**. Ardından, nesneleri, paneli veya denetim ekleyin.  
  
 ![](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png "e761238b-99fd-43c5-BBC4-57538b8289ff")  
  
 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [kenarlık ile çalışma](http://www.popscreen.com/v/6A4hB/Microsoft-Expression-Blend-Working-with-Borders)  
  
###  <a name="Popup"></a> Açılan menüsü  
 Bilgileri veya seçenekleri kullanıcılar bir pencerede gösterilir. Yalnızca bir nesne için ekleyebileceğiniz bir **açılan**. Varsayılan olarak, bir **açılan** içeren bir **kılavuz** ancak isterseniz bunu değiştirebilirsiniz.  
  
###  <a name="Scroll"></a> ScrollViewer  
 Bir sayfa veya bir sayfa alanı aşağı etkinleştir kullanır. İçin yalnızca bir nesne ekleyebileceğiniz bir **ScrollViewer** mantıklı bir düzen paneli gibi eklemek için kolaylaştırır. böylece bir **kılavuz** veya **StackPanel**.  
  
 ![](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png "06b326d4-f23d-41a6-b26b-e1aff37572a7")  
  
###  <a name="View"></a> Viewbox  
 Yakınlaştırma Denetimi ile ölçek nesneleri çok benzer olacaktır. Yalnızca bir nesne için ekleyebileceğiniz bir **Viewbox**. Birden fazla nesne için efekti uygulamak istiyorsanız, bir düzen paneline Ekle **ViewBox**ve ardından bu düzen paneline denetimleri ekleyin.  
  
 (Yalnızca WPF projeleri için kullanılabilir)  
  
 ![](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png "f5b13c66-d918-4141-8a16-bd8f8628687a")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML Tasarımcısı'nda öğelerle çalışma](../designers/working-with-elements-in-xaml-designer.md)   
 [XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)



