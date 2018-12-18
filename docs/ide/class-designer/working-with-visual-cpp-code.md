---
title: Visual C++ Kodu ile Çalışma (Sınıf Tasarımcısı)
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.cpplimitation
helpviewer_keywords:
- Visual C++, Class Designer
- Class Designer, Visual C++ support
- Class Designer, limitations
- Class Designer, tasks in Visual C++
- Visual C++, class diagrams
- C++, class diagrams
- C++, Class Designer
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 109c2408e16c5ca4943855889191733234778761
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958457"
---
# <a name="work-with-visual-c-code-in-class-designer"></a>Sınıf tasarımcısında Visual C++ kodu ile çalışma

**Sınıf Tasarımcısı** adlı bir görsel tasarım yüzeyi görüntüler bir *sınıf diyagramı* görsel bir projenizdeki kod öğeleri sağlar. Sınıf diyagramları tasarlama ve sınıfları ve diğer türleri projesinde görselleştirmek için kullanabilirsiniz.

**Sınıf Tasarımcısı** aşağıdaki C++ kod öğeleri destekler:

- (Birden çok devralma ilişkisine sahip olabilir ancak bu bir yönetilen sınıf şekli benzer) sınıfı

- Anonim sınıf (anonim bir tür için üretilen ad sınıfı görünümün görüntüler)

- Şablon sınıfı

- Yapı

- Enum

- Makro (makrosu sonrası işlenen görünümünü görüntüler)

- TypeDef

> [!NOTE]
> Bu model bir projede oluşturabilirsiniz UML sınıf diyagramı ile aynı değildir. Daha fazla bilgi için bkz: [UML sınıf diyagramları: başvuru](../../modeling/uml-class-diagrams-reference.md).

## <a name="troubleshoot-type-resolution-and-display-issues"></a>Türü çözümlemesi sorun giderme ve sorunları görüntüleme

### <a name="location-of-source-files"></a>Kaynak dosyalarının konumu

**Sınıf Tasarımcısı** kaynak dosyalarının konumunu izlemenize değil. Bu nedenle, proje yapınızı değiştirmek veya kaynak dosyalarını projenizde, taşırsanız **Sınıf Tasarımcısı** İzle (özellikle kaynak türü bir typedef, temel sınıf veya ilişki türleri) türündeki kaybedebilir. Hata gibi alabilirsiniz **Sınıf Tasarımcısı bu tür görüntüleyemiyor**. Bunu yaparsanız, yeniden yeniden görüntülemek için sınıf diyagramı konumlandırılan veya değiştirilen kaynak kodunu sürükleyin.

### <a name="update-and-performance-issues"></a>Güncelleştirme ve performans sorunları

Visual C++ projeleri için bu sınıf diyagramında görüntülenecek kaynak dosyasında değişiklik 30-60 saniye sürebilir. Bu gecikmeyi ayrıca neden olabilir **Sınıf Tasarımcısı** hata vermesini **hiçbir türleri seçim bulunamadı**. Bunun gibi bir hata alırsanız, tıklatın **iptal** hata iletisi ve görünmesi code öğesi bekle **sınıf görünümü**. Bunu yaptıktan sonra **Sınıf Tasarımcısı** türü görüntüleyemeyecek olmalıdır.

Sınıf diyagramında kodunda yaptığınız değişikliklerle güncelleştirmez, diyagram kapatıp yeniden açmanız gerekebilir.

### <a name="type-resolution-issues"></a>Türü çözümlemesi sorunları

**Sınıf Tasarımcısı** türleri aşağıdaki nedenlerle çözümleyebilmesi olmayabilir:

- Bir proje veya sınıf diyagramı içeren projeden başvurulmuyor derleme türüdür. Bu hatayı düzeltmek için proje veya türünü içeren bütünleştirilmiş bir başvuru ekleyin. Daha fazla bilgi için bkz: [bir projedeki başvuruları yönetme](../managing-references-in-a-project.md).

- Türü doğru kapsamda böylece değil **Sınıf Tasarımcısı** onu bulamıyor. Kodu eksik olmadığından emin olun bir `using`, `imports`, veya `#include` deyimi. Ayrıca, türü (veya ilgili bir türü) başlangıçta bulunduğu olduğu ad alanı dışında taşınmaz olduğundan emin olun.

- Türü yok (veya çıkışı açıklamalı). Bu hatayı düzeltmek için olmayan kılınmıştır veya türü silinmiş emin olun.

- #İmport yönergesi tarafından başvurulan bir kitaplık türü bulunur. Olası bir geçici çözüm el ile oluşturulan kodun (.tlh dosyası) için eklemektir bir # üstbilgi dosyasına include yönergesi.

- Emin **Sınıf Tasarımcısı** girdiğiniz türünü destekler. Bkz: [C++ kod öğeleri için sınırlamalar](#limitations-for-c-code-elements).

Hata türü çözümleme sorunu için bkz: büyük olasılıkla **kodu sınıf diyagramı'de bir veya daha fazla şekilleri bulunamadı '\<öğesi >'**. Bu hata iletisini kodunuzu hatadır gelmeyebilir. Yalnızca bu sınıf Tasarımcısı kodunuzu görüntüleyemedi belirtir. Aşağıdaki ölçütler deneyin:

- Türü olduğundan emin olun. Bilgisayarınızda değil istemeden kılınmıştır veya kaynak kodu silinmiş olması emin olun.

- Türü çözmeye çalışın. Bir proje veya sınıf diyagramı içeren projeden başvurulmuyor derleme türü olabilir. Bu hatayı düzeltmek için proje veya türünü içeren bütünleştirilmiş bir başvuru ekleyin. Daha fazla bilgi için bkz: [bir projedeki başvuruları yönetme](../managing-references-in-a-project.md).

- Sınıf Tasarımcısı bulabilmesi türü doğru kapsamında olduğundan emin olun. Kodu eksik olmadığından emin olun bir `using`, `imports`, veya `#include` deyimi. Ayrıca, türü (veya ilgili bir türü) başlangıçta bulunduğu olduğu ad alanı dışında taşınmaz olduğundan emin olun.

### <a name="troubleshoot-other-error-messages"></a>Diğer hata iletilerinde sorun giderme

Microsoft Developer Network (MSDN) ortak forumlarında sorun giderme hataları ve Uyarıları Yardım bulabilirsiniz. Bkz: [Visual Studio Sınıf Tasarımcısı Forumu](http://go.microsoft.com/fwlink/?linkid=160754).

## <a name="limitations-for-c-code-elements"></a>C++ kod öğeleri için sınırlamalar

- Visual C++ projesi yüklendiğinde **Sınıf Tasarımcısı** bir salt okunur şekilde işlevleri. Sınıf diyagramında değiştirebilirsiniz, ancak kaynak koduna sınıfı diyagramdan değişiklikler kaydedilemiyor.

- **Sınıf Tasarımcısı** yalnızca yerel C++ semantiği destekler. Yönetilen koda derlenmiş Visual C++ projeleri için **Sınıf Tasarımcısı** yalnızca yerel türler kod öğeleri görselleştirmek. Bu nedenle, bir proje için bir sınıf diyagramı ekleyebilirsiniz ancak **Sınıf Tasarımcısı** , hangi öğelerin görselleştirmek izin verme `IsManaged` özelliği ayarlanmış `true` (diğer bir deyişle, değer türleri ve başvuru türleri).

- Visual C++ projeleri için **Sınıf Tasarımcısı** yalnızca tanım türü okur. Örneğin, bir başlık (.h) dosyasında tür tanımlama ve bir uygulama (.cpp) dosyasına üyelerini tanımlamak varsayın. "Görünümü sınıf diyagramında" uygulama (.cpp) dosya çağırma varsa **Sınıf Tasarımcısı** hiçbir şey görüntüler. "Görünümü sınıf diyagramında" kullanan .cpp dosyayı çağırırsanız, başka bir örnek olarak, bir `#include` diğer bildirimini dosyaları ancak herhangi bir gerçek sınıf tanımları içermiyor **Sınıf Tasarımcısı** yeniden hiçbir şey görüntüler.

- Yerel C++ koda derlenen sürece COM arabirimleri tanımlayın ve tür kitaplıkları, IDL (.idl) dosyaları diyagramlarda görüntülemez.

- **Sınıf Tasarımcısı** genel işlevler ve değişkenler desteklemiyor.

- **Sınıf Tasarımcısı** birleşimler desteklemiyor. Bu, ayrılan bellek yalnızca tutar UNION'ın en büyük veri üyesi için gerekli olduğu sınıfın özel bir türüdür.

- **Sınıf Tasarımcısı** temel veri türleri gibi görüntülemez `int` ve `char`.

- **Sınıf Tasarımcısı** projesi bu tür doğru başvuruları yoksa dışında geçerli proje tanımlanan türleri görüntülemez.

- **Sınıf Tasarımcısı** iç içe geçmiş türler ancak iç içe geçmiş tür ve diğer türleri arasında ilişkileri görüntüleyebilirsiniz.

- **Sınıf Tasarımcısı** , void veya türü void türetilen türler görüntülenemiyor.

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıfları ve Türleri Tasarlama ve Görüntüleme (Sınıf Tasarımcısı)](designing-and-viewing-classes-and-types.md)
- [Sınıf Diyagramları ile Çalışma](working-with-class-diagrams.md)
- [Sınıfları ve Türleri Tasarlama ve Görüntüleme (Sınıf Tasarımcısı)](designing-and-viewing-classes-and-types.md)
- [Sınıf Tasarımcısı Hataları Hakkında Ek Bilgiler](additional-information-about-errors.md)
- [Sınıf Tasarımcısında Visual C++ Sınıfları](visual-cpp-classes.md)
- [Sınıf Tasarımcısında Visual C++ Yapılandırmaları](visual-cpp-structures.md)
- [Sınıf Tasarımcısında Visual C++ Numaralandırmaları](visual-cpp-enumerations.md)
- [Sınıf Tasarımcısında Visual C++ Typedefs](visual-cpp-typedefs.md)
