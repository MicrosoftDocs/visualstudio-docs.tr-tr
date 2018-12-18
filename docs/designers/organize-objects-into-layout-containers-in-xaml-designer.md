---
title: XAML Tasarımcısı’nda nesneleri düzen kapsayıcılarına yerleştirme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: f8faa01ddc56c5beaa2412bd91a9e68a8bba9525
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38978183"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>XAML Tasarımcısı’nda nesneleri düzen kapsayıcılarına yerleştirme

Bu makalede, XAML Tasarımcısı için Düzen panelleri ve denetimleri açıklar.

Nesneleri bir sayfada görüntülenmesini istediğiniz düşünün; Görüntü, düğmeler ve video gibi nesneleri. Dikey veya yatay veya sabit konumlarda satırlar ve sütunlar, tek bir satırda görünmesini istediğiniz olabilir.

Bir düzen paneli, sayfanın nasıl görünebilir hakkında düşünmek ettikten sonra seçin. Nesnelerinizi eklediğiniz bir şey gerektiğinden tüm sayfaları ile başlayın. Varsayılan olarak bu bir **kılavuz**, ancak isterseniz bunu değiştirebilirsiniz.

Düzen bölmeleri, sayfadaki nesneleri Düzenle yardımcı, ancak, birden fazla yapın. Bunlar farklı ekran boyutlarını ve çözünürlüklerini tasarım Yardım. Kullanıcıların uygulamanızı çalıştırdığınızda, her şeyi bir düzen paneli cihazlarının ekran gerçek boyutunuzu eşleşecek şekilde yeniden boyutlandırır. Elbette, düzeninizi yapmak istemiyorsanız, bir bölümü düzeni veya tüm düzeni için bu davranışı geçersiz kılabilirsiniz. Yükseklik ve genişlik Özellikleri'ı, kontrol etmek için kullanabilirsiniz.

## <a name="layout-panels"></a>Düzen bölmeleri

Sayfanız, bu düzen bölmelerini birini seçerek başlatın. Sayfanız birden fazla olabilir. Örneğin, ile başlayabilir bir **kılavuz** Düzen paneli ve ardından eklemek bir **StackPanel** bir alanda **kılavuz** böylece o öğenin dikey denetimlerinde düzenleyebilirsiniz.

Aşağıdaki Düzen bölmelerini bu özellik en kullanılır, ancak diğerleri vardır. Bunları bulabilirsiniz tümü **varlıklar** paneli.

- [Kılavuz](#Grid)

- [UniformGrid](#UniformGrid)

- [Tuval](#Canvas)

- [StackPanel](#stackpanel)

- [WrapPanel](#wrappanel)

- [DockPanel](#dockpanel)

### <a name="grid"></a>Kılavuz

Nesneleri, satırlar ve sütunlar halinde düzenleyin.

![Kılavuz Düzen panelini](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png)

### <a name="uniformgrid"></a>UniformGrid

Nesneler eşit veya tek düzen kılavuz bölgeye yerleştirin. Bu panelde, görüntülerin listesini düzenlemek için idealdir.

![UniformGrid Düzen paneli](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png)

(Yalnızca WPF projeleri için kullanılabilir.)

### <a name="canvas"></a>Tuval

Nesneleri istediğiniz gibi düzenleyin. Kullanıcıların uygulamanızı çalıştırdığınızda, bu öğeleri ekranında konumları sabit.

![Tuval düzeni panelini](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png)

### <a name="stackpanel"></a>StackPanel

Tek bir satırda nesneleri, yatay veya dikey olarak düzenleyin.

![StackPanel Düzen paneli](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png)

### <a name="wrappanel"></a>WrapPanel

Nesneleri sırayla soldan sağa düzenleyin. Bölmenin en sağdaki ucuna dışında yer çalıştığında, *sarmalar* içeriği sonraki satıra vb. soldan sağa üst-alt. Böylece nesnelerin üst alta, akış, ayrıca bir sarmalama panelinin yönü dikey soldan sağa yapabilirsiniz.

(Yalnızca WPF projeleri için kullanılabilir.)

![WrapPanel Düzen paneli](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png)

### <a name="dockpanel"></a>DockPanel

Böylece bunlar kalmasını nesneleri düzenleyin veya *dock*, panelin bir kenarında için.

(Yalnızca WPF projeleri için kullanılabilir.)

![DockPanel Düzen paneli](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png)

**Kısa bir video izleyin:** ![Oynat düğmesine](../designers/media/bldadminconsoleinitialconfigicon.PNG) [WPF - DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)

## <a name="layout-controls"></a>Düzen denetimleri

Nesnelerinizi Düzen denetimlere de ekleyebilirsiniz. Bunlar olarak olmayan özellik açısından zengin gibi bir düzen paneli, ancak bunları belirli senaryolar için yararlı bulabilirsiniz.

Aşağıdaki düzen denetimleri en popüler olduğunu, ancak diğerleri vardır. Bunları bulabilirsiniz tümü **varlıklar** paneli.

- [Kenarlık](#Border)

- [Açılan Pencere](#Popup)

- [ScrollViewer](#scrollviewer)

- [Viewbox](#viewbox)

### <a name="border"></a>Kenarlık

Kenarlık, arka plan veya her ikisi de bir nesnenin çevresindeki oluşturun. Yalnızca bir nesne için ekleyebileceğiniz bir **kenarlık**. Kenarlık veya arka plan bilgileri için birden fazla nesne uygulamak istediğiniz düzen paneline ekleyin **kenarlık**. Ardından, nesneleri, paneli veya denetim ekleyin.

![Kenarlık düzen denetimi](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png)

### <a name="popup"></a>Açılan Pencere

Bilgileri veya seçenekleri kullanıcılar bir pencerede gösterilir. Yalnızca bir nesne için ekleyebileceğiniz bir **açılan**. Varsayılan olarak, bir **açılan** içeren bir **kılavuz** ancak isterseniz bunu değiştirebilirsiniz.

### <a name="scrollviewer"></a>ScrollViewer

Bir sayfa veya alan bir sayfa kaydırarak olanak tanıyın. İçin yalnızca bir nesne ekleyebileceğiniz bir **ScrollViewer** mantıklı bir düzen paneli gibi eklemek için kolaylaştırır. böylece bir **kılavuz** veya **StackPanel**.

![ScrollViewer düzen denetimi](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png)

### <a name="viewbox"></a>Viewbox

Yakınlaştırma Denetimi ile ölçek nesneleri çok benzer olacaktır. Yalnızca bir nesne için ekleyebileceğiniz bir **Viewbox**. Birden fazla nesne için efekti uygulamak istiyorsanız, bir düzen paneline Ekle **ViewBox**ve ardından bu düzen paneline denetimleri ekleyin.

(Yalnızca WPF projeleri için kullanılabilir.)

![ViewBox düzen denetimi](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png)

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Tasarımcısı’nda öğelerle çalışma](../designers/working-with-elements-in-xaml-designer.md)
- [XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)