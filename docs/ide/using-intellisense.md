---
title: Parametre bilgisi, listesi üyeleri ve hızlı bilgi
ms.date: 05/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vc.tools.intellisense
helpviewer_keywords:
- Quick info
- Parameter info
- Complete word
- List members
- IntelliSense [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e00b43f1705079a86d511239d7b38119868d8f4
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748481"
---
# <a name="intellisense-in-visual-studio"></a>Visual Studio'da IntelliSense

IntelliSense olan bir dizi özellik içeren bir kod tamamlama Yardımı: listesi üyeleri, parametre bilgisi, hızlı bilgi ve tam sözcük. Bu özellikler, kullanmakta olduğunuz kod hakkında daha fazla bilgi için yazmakta olduğunuz ve özellikleri ve yöntemleri yalnızca birkaç tuş vuruşları ile çağrıları ekleme parametreleri izlemenize yardımcı olur.

IntelliSense'in birçok yönü dile özgüdür. Farklı diller için IntelliSense hakkında daha fazla bilgi için listelenen konulara bakın [Ayrıca bkz.](#see-also) bölümü.

## <a name="list-members"></a>Üyeleri Listeleme

Bir tetikleyici karakter yazdıktan sonra bir türü (veya ad alanı) geçerli üyeler listesi görüntülenir (örneğin, bir süre (`.`) yönetilen kodda veya `::` C++'ta). Karakterleri yazmaya devam ederseniz, listeye bu karakterlerle başlayan üyeleri içerecek şekilde filtre veya where başlangıcı *herhangi* ad içindeki Word'ü bu karakterlerle başlatır. Eşleşmeleri görmek için üye adı yalnızca başlamalıdır her sözcüğün ilk harfi girebilmeniz için IntelliSense "ortası büyük eşleştirme" de gerçekleştirir.

Bir öğe seçtikten sonra kodunuza tuşlarına basarak eklenebilir **sekmesini** veya boşluk yazarak. Öğeyi seçip bir nokta yazarsanız, bu noktanın arkasında başka üye listesini getiren bir öğe görüntülenir. Bir öğe seçtiğinizde, öğeyi eklemeden önce öğeye ilişkin Hızlı Bilgi alırsınız.

Üye listesinde, soldaki simge ad alanı, sınıf, işlev veya değişken gibi bir üye türünü temsil eder. Simge listesi için bkz [sınıf görünümü ve Nesne Tarayıcısı simgeleri](../ide/class-view-and-object-browser-icons.md). Basabilirsiniz şekilde listesi çok uzun olabilir **PgUp** ve **PgDn** listede yukarı veya aşağı gitme.

![Visual Studio üye listesi](../ide/media/vs2015_intellisense.png)

Çağırabilirsiniz **listesi üyeleri** yazarak el ile özellik **Ctrl**+**J**, seçme **Düzenle**  >  **IntelliSense** > **listesi üyeleri**, veya seçerek **listesi üyeleri** Düzenleyicisi araç çubuğunda. Boş bir satırda veya tanınabilir bir kapsamın dışında çağrıldığında, bu liste genel ad alanında simgeleri görüntüler.

Üyeleri listeleme (onun özellikle çağrılan sürece görünmemesi için) varsayılan olarak devre dışı bırakmak için Git **Araçları** > **seçenekleri** > **tüm diller**ve seçimini **otomatik listesi üyeleri**. Listesi üyeleri yalnızca belirli bir dil için etkinleştirmek istiyorsanız, Git **genel** o dil için ayarlar.

Sadece yazdığınız metnin kodun içine eklendiği öneri moduna da geçebilirsiniz. Liste ve tuşuna değil bir tanımlayıcı girin, örneğin, **sekmesini**, tamamlanmasında modu giriş yazılan tanımlayıcı değiştirirsiniz. Tamamlanma modu ve öneri modu arasında geçiş yapmak için basın **Ctrl**+**Alt**+**alanı**, veya seçin **Düzenle**  >  **IntelliSense** > **geçiş tamamlama modu**.

## <a name="parameter-info"></a>Parametre Bilgisi

Parametre Bilgisi; bir yöntem, öznitelik genel tür parametresi (C#) veya şablon (C++) tarafından istenen parametrelerin sayısı, adları ve türleri hakkında bilgi verir.

Kalın yazı tipli parametre, işlevi yazarken gerekli olan bir sonraki parametreyi gösterir. Aşırı yüklenen işlevler için kullandığınız **yukarı** ve **aşağı** işlev aşırı yüklemelerinin alternatif parametre bilgilerini görüntülemek için ok tuşlarını.

![Parametre Bilgisi](../ide/media/vs2015_param_info.png)

XML Belgeleri yorumlarıyla işlevlere ve parametrelere ek açıklamalar koyduğunuzda, yorumlar Parametre Bilgisi olarak görüntülenir. Daha fazla bilgi için bkz: [tedarik XML kodu açıklamaları](../ide/supplying-xml-code-comments.md).

Parametre bilgisi seçerek el ile çalıştırabilirsiniz **Düzenle** > **IntelliSense** > **parametre bilgisi**, basarak **Ctrl**  + **Shift**+**alanı**, veya seçerek **parametre bilgisi** Düzenleyicisi araç çubuğunda.

## <a name="quick-info"></a>Hızlı Bilgi

Hızlı bilgi kodunuzdaki herhangi bir tanımlayıcı için bütün bildirimi görüntüler.

![Visual Studio hızlı bilgi](../ide/media/vs2015_quick_info.png)

Üyeden seçtiğinizde **listesi üyeleri** kutusunda, hızlı bilgi de görünür.

![Parametre bilgisi bir c&#35; kod dosyası](../ide/media/vs2015_paraminfo.png)

Seçerek el ile hızlı bilgi çağırabileceği **Düzenle** > **IntelliSense** > **hızlı bilgi**, basarak **Ctrl** + **I**, veya seçerek **hızlı bilgi** Düzenleyicisi araç çubuğunda.

Bir işlev aşırı yüklenmişse, IntelliSense, tüm aşırı yük biçimleri için bilgileri görüntülemeyebilir.

Hızlı bilgi C++ kodunu giderek kapatabilirsiniz **Araçları** > **seçenekleri** > **metin düzenleyici** > **C / C++** > **Gelişmiş**ve ayarı **otomatik hızlı bilgi** için `false`.

## <a name="complete-word"></a>Tam Sözcük

Terim belirsizliğini ortadan kaldırmak için yeterli sayıda karakter girdikten sonra tam sözcüğü bir değişken, komut veya işlev adı kalan tamamlar. Tam sözcük seçerek çağırabileceği **Düzenle** > **IntelliSense** > **tam sözcüğü**, basarak **Ctrl** + **Alanı**, veya seçerek **tam sözcüğü** Düzenleyicisi araç çubuğunda.

## <a name="intellisense-options"></a>IntelliSense seçenekleri

IntelliSense seçenekleri varsayılan olarak açıktır. Bunları devre dışı bırakmak için seçin **Araçları** > **seçenekleri** > **metin düzenleyici** ve seçimini **parametre bilgilerini**veya **otomatik listesi üyeleri** üyeleri listeleme özelliği istemiyorsanız.

## <a name="troubleshoot-intellisense"></a>IntelliSense sorunlarını giderme

IntelliSense seçenekleri, belirli durumlarda beklediğiniz gibi çalışmayabilir.

**İmleç bir kod hatası var.** IntelliSense tamamlanmamış işlevi varsa kullanmanız mümkün olmayabilir veya IntelliSense kod öğeleri ayrıştırabiliyor olmayabileceğinden imleci yukarıdaki kodu başka bir hata bulunmaktadır. Uygulanabilir kodu açıklama olarak ekleyerek bu sorunu çözebilirsiniz.

**İmleç bir kod açıklaması ' dir.** İmleci, kaynak dosyanızdaki açıklamanın ise IntelliSense kullanamazsınız.

**İmleç bir dize sabit değeri var.** İmleç bir aşağıdaki örnekteki değişmez dize değeri tırnak ise IntelliSense kullanamazsınız:

```cpp
MessageBox( hWnd, "String literal|")
```

**Otomatik seçenekleri devre dışı bırakılmıştır.** Varsayılan olarak, IntelliSense otomatik olarak çalışır, ancak devre dışı bırakabilirsiniz. Otomatik deyim tamamlama devre dışı olsa bile, bir IntelliSense özelliğini çağırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md)
- [C# IntelliSense](../ide/visual-csharp-intellisense.md)
- [JavaScript IntelliSense](../ide/javascript-intellisense.md)
- [Yazma ve düzenleme kod (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [XML kodu açıklamaları sağlayın](../ide/supplying-xml-code-comments.md)