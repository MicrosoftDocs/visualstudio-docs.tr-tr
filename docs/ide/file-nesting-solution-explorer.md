---
title: Çözüm Gezgini için iç içe geçme kurallar dosyası
ms.date: 05/25/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
helpviewer_keywords:
- file nesting
- Solution Explorer, file nesting
author: angelosp
ms.author: angelpe
manager: douge
ms.openlocfilehash: d50d16d23c2f12ac5ac9feaaa37ee3797802c97e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928704"
---
# <a name="customize-file-nesting-in-solution-explorer"></a>Çözüm Gezgini’nde dosya iç içe yerleştirmeyi özelleştirme

İlgili dosyaları iç içe **Çözüm Gezgini** iç içe geçme kuralları hiçbir denetime sahip artık yeni, ancak kadar değil. Arasında önayarlarını seçebilirsiniz **kapalı**, **varsayılan** ve **Web**, ancak iç içe tam olarak istediğiniz gibi özelleştirebilirsiniz. Çözüme özel bile oluşturabilirsiniz ve projeye özgü ayarları, ancak daha sonra tüm. İlk üzerinden Bahsedelim kullanıma hazır alın.

> [!NOTE]
> Şu anda özelliğidir yalnızca ASP.NET Core projeleri için desteklenir.

## <a name="file-nesting-options"></a>Dosya iç içe geçmiş seçenekleri

![Açma/kapatma iç içe dosya kapatma düğmesi](media/filenesting_onoff.png)

Özelleştirilmiş olmayan dosya iç içe yerleştirme için kullanılabilir seçenekler şunlardır:

* **Kapalı**: Bu seçenek tüm geçmesiz dosyaların düz bir liste sağlar.

* **Varsayılan**: Bu seçenek size davranışı iç içe varsayılan dosya **Çözüm Gezgini**. Belirtilen proje türü için hiçbir ayar varsa, projede hiçbir dosya iç içe geçirilmiştir. İç içe geçme ayarlarını, örneğin, bir web projesi için mevcut durumunda uygulanır.

* **Web**: Bu seçenek geçerli **Web** geçerli Çözümdeki tüm projelere iç içe geçme davranışı dosya. Çok sayıda kurallarına sahiptir ve gözden geçirin ve düşüncelerinizi bize etmenizi öneririz. Bu seçenekle alın Dosya iç içe geçme davranış yalnızca birkaç örnek aşağıdaki ekran görüntüsünde vurgulanmıştır:

   ![Çözüm Gezgini içinde iç içe dosya](media/filenesting.png)

## <a name="customize-file-nesting"></a>Dosya iç içe yerleştime özelleştirme

Kullanıma hazır alma beğenmezseniz isteyin ayarları iç içe geçme, kendi özel dosya oluşturabilirsiniz **Çözüm Gezgini** dosyaları iç içe nasıl. İstediğiniz ve bunları istediğiniz gibi arasında geçiş yapabilirsiniz sayıda özel dosya iç içe geçme ayar ekleyebilirsiniz. Yeni bir özel ayarı oluşturmak için boş bir dosya ile başlayabilirsiniz veya kullanabileceğiniz **Web** , başlangıç noktası olarak ayarlar:

![Özel dosya iç içe geçme kuralları ekleme](media/filenesting_addcustom.png)

Kullanmanızı öneririz **Web** şeyle zaten işlevleri çalışmak daha kolay olduğundan, başlangıç ayarlarını gelin. Kullanırsanız **Web** ayarları, başlangıç noktası olarak *. filenesting.json* dosya şu dosyaya benzer görünür:

![Özel ayarlar için temel olarak iç içe kuralları varolan dosyayı kullan](media/filenesting_editcustom.png)

Şimdi düğüm üzerinde odaklanın **dependentFileProviders** ve onun alt düğümleri. Her alt düğümü, dosyaları yerleştirmek için Visual Studio'yu kullanabilirsiniz kural türüdür. Örneğin, **aynı dosya adı, ancak farklı bir uzantıya sahip** kuralı bir türüdür. Kullanılabilir kurallar şunlardır:

* **extensionToExtension**: iç içe yerleştirmek için bu kural türü kullanmak *file.js* altında *file.ts*

* **fileSuffixToExtension**: iç içe yerleştirmek için bu kural türü kullanmak *dosya vsdoc.js* altında *file.js*

* **addedExtension**: iç içe yerleştirmek için bu kural türü kullanmak *file.html.css* altında *file.html*

* **pathSegment**: iç içe yerleştirmek için bu kural türü kullanmak *jquery.min.js* altında *jquery.js*

* **allExtensions**: iç içe yerleştirmek için bu kural türü kullanmak *dosya.* * altında *file.js*

* **fileToFile**: iç içe yerleştirmek için bu kural türü kullanmak *bower.json* altında *.bowerrc*

### <a name="the-extensiontoextension-provider"></a>ExtensionToExtension sağlayıcısı

Bu sağlayıcı belirli dosya uzantılarını kullanarak dosya iç içe geçme kuralları tanımlamanıza olanak sağlar. Aşağıdaki örnek göz önünde bulundurun:

![extentionToExtension örnek kural](media/filenesting_extensiontoextension.png) ![extentionToExtension örnek etkisi](media/filenesting_extensiontoextension_effect.png)

* *Cart.js* altında iç içe *cart.ts* ilk nedeniyle **extensionToExtension** kuralı

* *Cart.js* altında iç içe *cart.tsx* çünkü **.ts** önce gelen **.tsx** kuralları ve ayrıca bir üst yalnızca olabilir

* *Light.css* altında iç içe *light.sass* ikinci nedeniyle **extensionToExtension** kuralı

* *Home.HTML* altında iç içe *home.md* üçüncü nedeniyle **extensionToExtension** kuralı

### <a name="the-filesuffixtoextension-provider"></a>FileSuffixToExtension sağlayıcısı

Bu sağlayıcının gibi çalışıp **extensionToExtension** tek fark dosyanın uzantısı yerine sonek kuralı bakan olan ile sağlayıcısı. Aşağıdaki örnek göz önünde bulundurun:

![fileSuffixToExtension örnek kural](media/filenesting_filesuffixtoextension.png) ![fileSuffixToExtension örnek etkisi](media/filenesting_filesuffixtoextension_effect.png)

* *Portal vsdoc.js* altında iç içe *portal.js* nedeniyle **fileSuffixToExtension** kuralı

* Her bir kural yönüyle aynı şekilde çalışır **extensionToExtension**

### <a name="the-addedextension-provider"></a>AddedExtension sağlayıcısı

Bu sağlayıcı ek uzantısız dosya altında ek uzantılı dosyalar gömer. Ek uzantı yalnızca tam dosya adının sonunda yer alabilir. Aşağıdaki örnek göz önünde bulundurun:

![addedExtension örnek kural](media/filenesting_addedextension.png) ![addedExtension örnek etkisi](media/filenesting_addedextension_effect.png)

* *File.HTML.css* altında iç içe *file.html* nedeniyle **addedExtension** kuralı

### <a name="the-pathsegment-provider"></a>PathSegment sağlayıcısı

Bu sağlayıcı ek uzantısız dosya altında ek uzantılı dosyalar gömer. Ek uzantı yalnızca tam dosya adı ortasını görünür. Aşağıdaki örnek göz önünde bulundurun:

![pathSegment örnek kural](media/filenesting_pathsegment.png) ![pathSegment örnek etkisi](media/filenesting_pathsegment_effect.png)

* *JQuery.Min.js* altında iç içe *jquery.js* nedeniyle **pathSegment** kuralı

### <a name="the-allextensions-provider"></a>AllExtensions sağlayıcısı

Bu sağlayıcı, uzantıyı ancak aynı temel dosya adı olan dosyalar için dosya iç içe geçme kuralları tanımlamanıza olanak sağlar. Aşağıdaki örnek göz önünde bulundurun:

![allExtensions örnek kural](media/filenesting_allextensions.png) ![allExtensions örnek etkisi](media/filenesting_allextensions_effect.png)

* *Template.cs* ve *template.doc* altında iç içe *template.tt* nedeniyle **allExtensions** kuralı.

### <a name="the-filetofile-provider"></a>FileToFile sağlayıcısı

Bu sağlayıcı, tüm dosya adları üzerinde dayalı dosya iç içe geçme kuralları tanımlamanıza olanak sağlar. Aşağıdaki örnek göz önünde bulundurun:

![fileToFile örnek kural](media/filenesting_filetofile.png) ![fileToFile örnek etkisi](media/filenesting_filetofile_effect.png)

* *.bowerrc* altında iç içe *bower.json* nedeniyle **fileToFile** kuralı

### <a name="rule-order"></a>Kural sırası

Sıralama her özel ayarlar dosyanızı bölümünde önemlidir. Hangi kuralları çalıştırılır yukarı veya aşağı içine taşıyarak sırasını değiştirebilirsiniz **dependentFileProvider** düğümü. Örneğin, yapan bir kuralı varsa **file.js** üst **file.ts** ve yapan başka bir kural **file.coffee** üst **file.ts**, üç dosya mevcut olduğunda dosyasında göründükleri sırayla iç içe geçme davranışını belirler. Bu yana **file.ts** yalnızca bir üste sahip olabilmesidir, hangi kural ilk WINS yürütür.

Sıralama da kural bölümlerin kendileri yalnızca bir bölümü içindeki dosyalar için önemlidir. Dosyalarının bir çiftini dosya iç içe geçmiş bir kuralla eşleşiyor hemen sonra diğer kurallardan daha da aşağı dosyasında göz ardı edilir ve sonraki çift dosya işlenebilir.

### <a name="file-nesting-button"></a>Dosya iç içe geçme düğmesi

Aynı düğmeye aracılığıyla kendi özel ayarlar dahil olmak üzere, tüm ayarlarını yönetebilirsiniz **Çözüm Gezgini**:

![Özel dosya iç içe geçme kurallarını etkinleştirme](media/filenesting_activatecustom.png)

## <a name="create-solution-specific-and-project-specific-settings"></a>Çözüm ve proje özgü ayarları oluşturma

Her çözüm ve proje bağlam menüsü aracılığıyla çözüm ve proje özgü ayarları oluşturabilirsiniz:

![Çözüm ve proje özel iç içe geçme kuralları](media/filenesting_solutionprojectspecific.png)

Çözüm ve proje özgü ayarları, etkin Visual Studio ayarları ile birleştirilir. Örneğin, bir boş projeye özgü ayarları dosyasına sahip olabilir ancak **Çözüm Gezgini** hala dosyaları iç içe. İç içe geçme davranışı, çözüme özel ayarlar veya Visual Studio ayarları kullanıma sunulacaktır. İç içe dosya ayarları birleştirmek için bir öncelik olduğundan: Visual Studio > çözüm > Proje.

Seçeneğini etkinleştirerek dosyalar disk üzerinde mevcut olsa bile, çözüm ve proje özgü ayarları yok saymak için Visual Studio söyleyebilirsiniz **çözüm ve proje ayarlarını Yoksay** altında **Araçları**  >  **Seçenekleri** > **ASP.NET Core** > **dosya iç içe geçme**.

Bunun tersini yapmak ve bildirmek için Visual Studio *yalnızca* ayarlayarak çözüme özel veya projeye özgü ayarları kullanın **kök** düğüme **true**. Visual Studio, o düzeydeki dosyaları birleştirme durdurur ve dosyalarla hiyerarşisinde yukarı daha yüksek birleştirme değil.

Çözüm ve proje özgü ayarları, kaynak denetimi ve bunları paylaşabilirsiniz kod temeli üzerinde çalışır ekibin tamamı denetlenebilir.

## <a name="disable-global-file-nesting-rules-for-a-particular-solution-or-project"></a>Belirli bir çözüm veya proje için genel dosya iç içe geçme kurallarını devre dışı bırakın

Kullanarak varolan genel dosya iç içe geçme kurallarını belirli çözümlerin veya projelerin için devre dışı bırakabilirsiniz **Kaldır** yerine bir sağlayıcı için eylem **ekleme**. Örneğin, bir proje için aşağıdaki ayarları kod eklerseniz tüm **pathSegment** bu belirli bir proje için genel olarak bulunabilir kuralları devre dışı bırakılır:

```json
"dependentFileProviders": {
  "remove": {
    "pathSegment": {}
  }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md)
