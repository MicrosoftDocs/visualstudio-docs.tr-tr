---
title: Visual C++ kodu (Sınıf Tasarımcısı) ile çalışma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f777c9bdd0cf2ea300d2df8e7cbfbc8900c25c2a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929536"
---
# <a name="working-with-visual-c-code-class-designer"></a>Visual C++ Kodu ile Çalışma (Sınıf Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sınıf Tasarımcısı görüntüler olarak adlandırılan bir görsel tasarım yüzeyine bir *sınıf diyagramı* kod öğeleri, projenizdeki görsel bir gösterimini sağlar. Tasarım ve sınıflar ve diğer proje türleri görselleştirmek için sınıf diyagramlarını kullanabilirsiniz.  
  
 Sınıf Tasarımcısı aşağıdaki C++ kod öğeleri destekler:  
  
-   (Birden çok devralma ilişkisi olabilir bir yönetilen sınıf şeklinin benzer) sınıfı  
  
-   Anonim sınıf (anonim tür sınıfı görünümün oluşturulan adını görüntüler.)  
  
-   Şablon sınıfı  
  
-   Yapı  
  
-   Enum  
  
-   Makro (makro sonrası işlenen görünümünü görüntüler)  
  
-   tür tanımı  
  
> [!NOTE]
>  Bu bir modelleme projesinde oluşturduğunuz UML sınıf diyagramı ile aynı değildir. Daha fazla bilgi için [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md).  
  
## <a name="troubleshooting-type-resolution-and-display-issues"></a>Tür çözümlemesi ve görüntü sorunları giderme  
  
### <a name="location-of-source-files"></a>Kaynak dosyalarının konumu  
 Sınıf Tasarımcısı kaynak dosyalarının konumunu izler mi değil. Bu nedenle, Sınıf Tasarımcısı proje değiştirmek ya da kaynak dosyalarını projenizde taşımak, parça türü (özellikle kaynak türü bir tür tanımı, temel sınıflar veya ilişki türlerini) kaybedebilir. Gibi bir hata alabilirsiniz **Sınıf Tasarımcısı bu türü görüntüleyemiyor**. Bunu yaparsanız, değiştirilmiş ya da yeni yerlerine kaynak kodu yeniden görüntülemek için sınıf diyagramına sürükleyin.  
  
### <a name="update-and-performance-issues"></a>Güncelleştirme ve performans konuları  
 Visual C++ projeleri için sınıf diyagramında görüntülenecek kaynak dosyada bir değişiklik 30 ila 60 saniye sürebilir. Bu gecikme hata oluşturmak Sınıf Tasarımcısı da neden **hiçbir tür seçiminde bulundu**. Bunun gibi bir hata alırsanız, tıklayın **iptal** hata iletisi ve kod öğesi, Sınıf Görünümü'nde görünmesini bekleyin. Bunu yaptıktan sonra Sınıf Tasarımcısı görüntüleyebilir türü olmalıdır.  
  
 Bir sınıf diyagramı, kodda yaptığınız değişikliklerle güncelleştirmezse diyagramı kapatın ve yeniden açın gerekebilir.  
  
### <a name="type-resolution-issues"></a>Tür çözümlemesi sorunları  
 Sınıf Tasarımcısı, türleri aşağıdaki nedenlerden dolayı çözmek mümkün olmayabilir:  
  
- Bir proje veya sınıf diyagramı içeren bir projeden başvurulan değil derleme türüdür. Bu hatayı düzeltmek için proje ya da türünü içeren derlemeyi bir başvuru ekleyin. Daha fazla bilgi için [nasıl NIB: başvurular ekleme veya kaldırma Başvurusu Ekle iletişim kutusunu kullanarak](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
- Sınıf Tasarımcısı bulamazsanız şekilde türü doğru kapsamda değil. Kodu eksik olmadığından emin olun bir `using`, `imports`, veya `#include` deyimi. Ayrıca, türü (veya ilişkili bir türün) içinde bulunduğu orijinal yere ad alanı dışında taşınmış değil, emin olun.  
  
- Türü yok (veya açıklama satırı). Bu hatayı düzeltmek için bilgisayarınızda değil yorum veya türü silinmiş olması emin olun.  
  
- Türü bir #import yönergesi tarafından başvurulan bir kitaplıkta yer alır. İçin oluşturulan kodu (.tlh dosyası) el ile eklemek için olası bir geçici çözüm olan bir # üstbilgi dosyasına include yönergesi.  
  
  Tür çözümleme sorunu için görmek en olası hata **kodu sınıf diyagramına bir veya daha fazla şekilleri için bulunamadı '\<öğesi >'**. Bu hata iletisini kodunuzu hatadır gelmeyebilir. Bu, Sınıf Tasarımcısı yalnızca kodunuzu görüntüleyemedi gösterir. Aşağıdaki ölçüleri deneyin.  
  
- Türü olduğundan emin olun. Yanlışlıkla değil yorum veya kaynak kodu silinmiş olduğundan emin olun.  
  
- Sınıf Tasarımcısı, girdiğiniz türünü desteklediğinden emin olun. Bkz: [C++ kod öğeleri için kısıtlamalar](#limitations).  
  
- Türü çözmeye çalışın. Bir proje ya da sınıf diyagramı içeren bir projeden başvurulan değil derleme türü olabilir. Bu hatayı düzeltmek için proje ya da türünü içeren derlemeyi bir başvuru ekleyin. Daha fazla bilgi için [nasıl NIB: başvurular ekleme veya kaldırma Başvurusu Ekle iletişim kutusunu kullanarak](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
- Sınıf Tasarımcısı bulabilmesi türü doğru kapsamda olduğundan emin olun. Kodu eksik olmadığından emin olun bir `using`, `imports`, veya `#include` deyimi. Ayrıca, türü (veya ilişkili bir türün) içinde bulunduğu orijinal yere ad alanı dışında taşınmış değil, emin olun.  
  
### <a name="troubleshooting-other-error-messages"></a>Diğer hata iletileri sorunları giderme  
 Microsoft Developer Network (MSDN) ortak forumlarında sorun giderme hataları ve Uyarıları ile ilgili Yardım bulabilirsiniz. Bkz: [Visual Studio Sınıf Tasarımcısı Forumu](http://go.microsoft.com/fwlink/?linkid=160754).  
  
##  <a name="limitations"></a> C++ kod öğeleri için kısıtlamalar  
  
-   Ne zaman Visual C++ projesi yüklenir, Sınıf Tasarımcısı işlevleri bir salt okunur şekilde. Sınıf diyagramı değiştirebilirsiniz, ancak sınıf diyagramından kaynak koduna değişiklikleri kaydedemezsiniz.  
  
-   Sınıf Tasarımcısı yalnızca yerel C++ semantiği destekler. Yönetilen kod derlenmiş Visual C++ projeleri için Sınıf Tasarımcısı yalnızca yerel türler kod öğelerini görselleştirin. Bu nedenle, bir sınıf diyagramı projeye ekleyebilirsiniz, ancak Sınıf Tasarımcısı izin vermez, öğeleri görselleştirmek `IsManaged` özelliği `true` (diğer bir deyişle, değer türleri ve başvuru türleri).  
  
-   Visual C++ projeleri için Sınıf Tasarımcısı yalnızca türünün tanımını okur. Örneğin, bir üstbilgi (.h) dosyasına tanımlayan bir tür ve üyeleri tanımlayan bir uygulama (.cpp) dosyasında varsayalım. Uygulama (.cpp) dosyasında "sınıf diyagramını görüntüle" çağırma, Sınıf Tasarımcısı hiçbir şey görüntülenir. Başka bir örnek olarak kullanan bir .cpp dosya çubuğunda "sınıf diyagramını görüntüle" çağırma bir `#include` deyimini diğer dahil etme dosyaları, ancak herhangi bir gerçek sınıf tanımı içermiyor, Sınıf Tasarımcısı yeniden görüntüler hiçbir şey.  
  
-   C++ yerel koda derlenmiş sürece IDL (.idl) dosyaları, COM arabirimi tanımlayın ve tür kitaplığı, diyagramlarında görüntülemez.  
  
-   Sınıf Tasarımcısı, genel işlevler ve değişkenler desteklemez.  
  
-   Sınıf Tasarımcısı, birleşimler desteklemez. Ayrılan belleğin yalnızca tutarı Birliği'nin en büyük veri üyesi için gerekli olduğu sınıf özel bir tür budur.  
  
-   Sınıf Tasarımcısı temel veri türleri gibi görüntülemez `int` ve `char`.  
  
-   Sınıf Tasarımcısı proje doğru başvuru türlerine sahip değilse, geçerli projenin dışında tanımlanan türlerinden görüntülemez.  
  
-   Sınıf Tasarımcısı, iç içe geçmiş türler ancak iç içe türü ve diğer türleri arasında ilişkileri görüntüleyebilir.  
  
-   Sınıf Tasarımcısı, void olan veya, void bir türden türetilmiş türlerini görüntüleyemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sınıfları ve türleri tasarlama ve görüntüleme](../ide/designing-and-viewing-classes-and-types.md)   
 [Sınıflarla ve diğer türlerle (Sınıf Tasarımcısı) ile çalışma](../ide/working-with-classes-and-other-types-class-designer.md)   
 [Sınıf diyagramları (Sınıf Tasarımcısı) ile çalışma](../ide/working-with-class-diagrams-class-designer.md)   
 [Sınıfları ve türleri tasarlama (Sınıf Tasarımcısı)](../ide/designing-classes-and-types-class-designer.md)   
 [Sınıf Tasarımcısı hataları hakkında ek bilgi](../ide/additional-information-about-class-designer-errors.md)   
 [Sınıf tasarımcısında Visual C++ sınıfları](../ide/visual-cpp-classes-in-class-designer.md)   
 [Sınıf tasarımcısında Visual C++ yapılandırmaları](../ide/visual-cpp-structures-in-class-designer.md)   
 [Sınıf tasarımcısında Visual C++ numaralandırmaları](../ide/visual-cpp-enumerations-in-class-designer.md)   
 [Sınıf Tasarımcısında Visual C++ Typedefs](../ide/visual-cpp-typedefs-in-class-designer.md)



