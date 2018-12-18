---
title: Seçenekler, metin düzenleyici, C/C++, Deneysel
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
author: mikeblome
ms.author: mblome
manager: wpickett
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- cplusplus
ms.openlocfilehash: 3f5ddf5a42199c8097e982c6ddd8e559185787fb
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672346"
---
# <a name="options-text-editor-cc-experimental"></a>Seçenekler, metin düzenleyici, C/C++, Deneysel

Bu seçenekler değiştirerek, C veya C++ ortamında programlama, IntelliSense ve gözatma veritabanı ilgili davranışı değiştirebilirsiniz. Bu özellikler gerçekten Deneysel ve değiştirilebilir veya gelecekteki bir sürümde Visual Studio'dan kaldırıldı. Bu konu, Visual Studio 2017'de seçeneklerini açıklar. Visual Studio 2015 için seçin **2015** içindekiler tablosu üzerinde Seçici içinde.

Bu özellik sayfasına erişmek için basın **Control + Q** etkinleştirmek için `Quick Launch` "Deneysel" yazın. Hızlı Başlatma sonra ilk birkaç harfini sayfasında bulabilirsiniz. Seçim yaparak kendisine da edinebilirsiniz **araçları | Seçenekleri** ve genişletme **metin düzenleyici**, ardından **C/C++** ve ardından **Deneysel**.

Bu özellikler, bir Visual Studio 2017 yüklemesini kullanılabilir.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Bkz: [Visual Studio IDE'yi kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-predictive-intellisense"></a>Tahmine dayalı IntelliSense'i etkinleştir

Tahmine dayalı IntelliSense bağlamında ilgili sonuçları görebilmesi için IntelliSense açılan listede görüntülenen sonuçların sayısını sınırlar. Örneğin, <code>int x =</code> ve IntelliSense açılan çağırmak, yalnızca tamsayılar ya da, tamsayı döndüren işlevlere görürsünüz. Tahmine dayalı IntelliSense, varsayılan olarak kapalıdır.

## <a name="enable-faster-project-load"></a>Daha hızlı proje yüklemeyi etkinleştir

**Visual Studio 2017 sürüm 15.3 ve üzeri**: Bu özellik artık adlı **projeyi önbelleğe almayı etkinleştir** ve e taşınmıştır [VC ++ proje ayarları](vcpp-project-settings-projects-and-solutions-options-dialog-box.md) özellik sayfası.
Bu seçenek, Visual Studio Proje verileri önbelleğe almak için etkinleştirir projeyi sonraki açtığınızda, proje dosyalarından yeniden hesaplama yerine verileri önbelleğe yükleyebilirsiniz. Önbelleğe alınan verileri kullanarak proje yükleme süresini önemli ölçüde hızlandırabilirsiniz.

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Visual Studio Market'te ek özellikler

Ek Metin Düzenleyicisi özelliklerinin göz atabilirsiniz [Visual Studio Market](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads). Bir örnek [C++ hızlı düzeltmeler](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.CQuickFixes2017), aşağıdakileri destekler:

- **Eksik Ekle #include** -ilgili önerir #include kodunuzu bilinmeyen sembolleri

- **Ekleme simge ad alanı/tam olarak nitelemek** - önceki öğeyi gibi ancak ad alanları için

- **Eksik noktalı virgül Ekle**

- **Çevrimiçi Yardım** -arama, hata iletileri için çevrimiçi Yardım

- ve daha fazlası...

## <a name="see-also"></a>Ayrıca bkz.

- [Dile Özgü Düzenleyici Seçeneklerini Ayarlama](../../ide/reference/setting-language-specific-editor-options.md)
- [C++'da (VC blogunda) yeniden düzenleme](https://blogs.msdn.microsoft.com/vcblog/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview/)
