---
title: Oluşturma ve bir kaynağı uygulama
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.CreateResource
- VS.XamlDesigner.EditResource
ms.assetid: 3ff4006d-659d-4073-9a41-06ff85e6cfdf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 405b208df0aedffe69c9e476a5a31745faeb84f1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872570"
---
# <a name="how-to-create-and-apply-a-resource"></a>Oluşturma ve bir kaynağı uygulama
Stilleri ve şablonları XAML Tasarımcısı'nda öğeler için kaynakları adlı yeniden kullanılabilir varlıklarda depolanır. Stilleri öğesi özellikleri ayarlamanızı ve birden çok öğe arasında tutarlı bir görünüm için bu ayarları yeniden etkinleştirin. A [ControlTemplate](/uwp/api/Windows.UI.Xaml.Controls.ControlTemplate) denetiminin görünümünü tanımlar ve ayrıca bir kaynak olarak uygulanabilir. Daha fazla bilgi için [hızlı başlangıç: stil denetimleri](http://go.microsoft.com/fwlink/?LinkID=248239) ve [hızlı başlangıç: denetim şablonları](http://go.microsoft.com/fwlink/?LinkID=247982).

 Var olan bir özelliği, yeni bir kaynak oluşturduğunuzda [stili](/uwp/api/Windows.UI.Xaml.Style), veya `ControlTemplate`, **Kaynağı Oluştur** iletişim kutusu, kaynak uygulama düzeyinde, belge düzeyinde tanımlamanıza imkan tanır veya öğe düzeyi. Bu düzeyler, kaynağı nerede kullanabileceğinizi belirler. Örneğin, öğe düzeyinde kaynak tanımlarsanız, kaynak yalnızca üzerinde oluşturduğunuz öğesine uygulanabilir. Ayrıca, yeniden başka bir projede kullanabileceğiniz ayrı bir dosya olan bir kaynak sözlüğünde kaynağı saklamayı da seçebilirsiniz.

### <a name="to-create-a-new-resource"></a>Yeni bir kaynak oluşturmak için

1.  XAML Tasarımcısı'nda açık bir XAML dosyası, bir öğe oluşturun veya belge ana hattı pencerede bir öğe seçin.

2.  Özellikler penceresinde, bir özellik değeri sağındaki kutusunda sembol olarak görünür, özellik işaretçisi seçin ve ardından **yeni kaynağa dönüştürün**. Varsayılan değeri beyaz kutu simgesi gösterir ve bir siyah kutu sembol genellikle yerel kaynak uygulandığını gösterir.

     Bir kaynak oluşturmak için uygun bir iletişim kutusu görüntülenir. Bir fırçadan bir kaynak oluştururken bu iletişim kutusu görüntülenir:

     ![Kaynak Oluştur iletişim kutusu](../designers/media/xaml_create_resource.png)

3.  İçinde **adı (anahtar)** kutusunda, bir anahtar adı girin. Bu kaynak başvurmak için diğer öğeleri istediğiniz zaman kullanabileceğiniz addır.

4.  Altında **tanımlamak**, kaynağın tanımlanmasını istediğiniz yeri belirten seçeneği seçin:

    -   Kaynağınızı uygulamanızdaki herhangi bir belge kullanılabilir hale getirmek için seçin **uygulama**.

    -   Kaynağınızı yalnızca geçerli belgede kullanılabilir hale getirmek için seçin **bu belgeyi**.

    -   Kaynak kaynağın oluşturulduğu veya onun alt öğeleri sadece öğe kullanılabilir hale getirmek için seçin **bu belgeyi**, aşağı açılan listesinde seçin **öğesi**: **adı** .

    -   Diğer projelerde yeniden kullanılabilir bir kaynak sözlüğü dosyası içinde kaynağı tanımlamak için tıklatın **kaynak sözlüğü**ve ardından var olan bir kaynak sözlüğü dosyası gibi seçin **StandardStyles.xaml**, aşağı açılan listesinde.

5.  Seçin **Tamam** kaynak oluşturmak ve oluşturduğunuz bu öğeye uygulamak için düğme.

### <a name="to-apply-a-resource-to-an-element-or-property"></a>Bir öğe veya özellik için bir kaynak uygulamak için

1. Belge Anahattı penceresi içinde bir kaynak uygulamak istediğiniz öğeyi seçin.

2. Aşağıdakilerden birini yapın:

   - Bir kaynak bir özellik için geçerlidir. Özellikler penceresindeki özellik değerinin yanındaki özelliği işaretçisi seçin, **yerel kaynak** veya **sistem kaynağı**, görüntülenen listeden kullanılabilir bir kaynak seçin.

      Görmeyi beklediğiniz bir kaynak görmüyorsanız, kaynak türünü özelliğinin türü eşleşmediği için olabilir.

   - Bir stil veya denetim şablon kaynağı, bir denetim için geçerlidir. Açık Belge Anahattı penceresi denetiminde için bağlam menüsünü seçin **şablonu Düzen** veya **Düzenle ek şablonlar**, seçin **kaynağı Uygula**seçin Görüntülenen listeden denetim şablonunun adı.

     > [!NOTE]
     >  **Şablonu Düzen** denetim şablonları için geçerlidir. **Ek şablonlar Düzenle** diğer şablonu türleri için geçerlidir.

     Uyumlu oldukları yerde kaynaklara uygulayabilirsiniz. Örneğin, bir fırça kaynağı için uygulayabileceğiniz **ön plan** özelliği bir <xref:Windows.UI.Xaml.Controls.TextBox> denetimi.

### <a name="to-edit-a-resource"></a>Bir kaynak düzenlemek için

1.  Çalışma yüzeyinde veya belge ana hattı penceresinin bir öğe seçin.

2.  Özellikler penceresinde özelliğinin varsayılan veya yerel özellik işaretçiye seçin ve ardından **kaynağı Düzenle** açmak için **kaynağı Düzenle** iletişim kutusu.

3.  Kaynak seçeneklerini değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)