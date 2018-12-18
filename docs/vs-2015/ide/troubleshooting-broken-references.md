---
title: Bozuk başvurularda sorun giderme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
ms.assetid: 00a9ade9-652e-40de-8ada-85f63cd183ee
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ae619be498fcb1c48bbea8b706f0b0b5fa4db54c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950673"
---
# <a name="troubleshooting-broken-references"></a>Bozuk Başvurularda Sorun Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanızı kırık referans kullanmaya çalışırsa, bir özel durum hatası oluşturulur. Yükleyememesine başvurulan bileşen bulmak için hatanın birincil tetikleyici olmakla birlikte bozuk bir referans kabul edilebilir birkaç durum mevcuttur. Aşağıdaki listede bu örnekler gösterilmektedir:  
  
- Proje başvuru yolu yanlış veya eksik.  
  
- Başvurulan dosya silindi.  
  
- Başvurulan dosya yeniden adlandırıldı.  
  
- Ağ bağlantısı veya kimlik doğrulaması başarısız oldu.  
  
- Bilgisayarda yüklü olmayan bir COM bileşenine başvuru yapılır.  
  
  Bu sorunları çözümler aşağıda verilmiştir.  
  
> [!NOTE]
>  Derlemelerde dosyaları, proje dosyasındaki mutlak yollar ile başvurulur. Bu nedenle, başvurulan bir derlemenin yerel ortamlarında eksik geliþtiricili ortamında çalışan kullanıcıların mümkündür. Bu hataları önlemek için projeden projeye başvurular eklemek için bu gibi durumlarda daha iyi olur. Daha fazla bilgi için [nasıl NIB: başvurular ekleme veya kaldırma Başvurusu Ekle iletişim kutusunu kullanarak](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) ve [Derlemelerle programlama](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6).  
  
## <a name="reference-path-is-incorrect"></a>Başvuru yolu yanlış  
 Farklı bilgisayarlarda Paylaşılan projeleri, bir bileşen farklı bir dizinde her bilgisayarda bulunan, bazı başvuruları bulunmayabilir. Başvurular (örneğin, MyComponent) bileşen dosyası adı altında depolanır. Bir projeye bir başvuru eklendiğinde, Bileşen dosyası klasör konumuna (örneğin, C:\MyComponents\\) eklenir **ReferencePath** proje özelliği.  
  
 Bir proje açıldığında, başvuru yolu dizinleri bakarak bu başvurulan bileşen dosyaları bulmayı dener. Proje bileşen D:\MyComponents gibi farklı bir dizinde depolar bir bilgisayarda açılıp açılmadığını\\, başvuru bulunamadı ve bir hata görev listesinde görüntülenir.  
  
 Bu sorunu gidermek için kırık referans silebilir ve Başvuru Ekle iletişim kutusunu kullanarak değiştirin. Başka bir çözüm **başvuru yolu** öğesini projenin özellik sayfaları'nda ve klasörler listesinde, doğru konuma işaret edecek şekilde değiştirin. **Başvuru yolu** özelliği, her bilgisayardaki her kullanıcı için kalıcıdır. Bu nedenle, Başvuru yolunuza değiştirme projenin diğer kullanıcıların etkilemez.  
  
> [!TIP]
>  Projeden projeye başvurular, bu sorun yoktur. Mümkünse, bu nedenle, bunları dosya başvuruları yerine kullanın.  
  
#### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>Bozuk bir proje başvurusu, başvuru yolu düzelterek düzeltmek için  
  
1.  İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve tıklayın **özellikleri**.  
  
2.  **Proje Tasarımcısı** görünür.  
  
3.  Visual Basic kullanıyorsanız **başvuruları** sayfasında ve tıklayın **başvuru yolları** düğmesi. İçinde **başvuru yolları** iletişim içinde başvurmak istediğiniz öğeyi içeren klasörün yolunu yazın **klasör** alan ve ardından **klasörü Ekle** düğmesi.  
  
     veya  
  
     Visual C# kullanıyorsanız **başvuru yolları** sayfası. İçinde **klasör** alan, başvuru ve ardından istediğiniz öğeyi içeren klasörün yolunu yazın **klasörü Ekle** düğmesi.  
  
## <a name="referenced-file-has-been-deleted"></a>Başvurulan dosya silindi  
 Bu, başvurulan dosya silindi ve artık sürücüde mevcut mümkündür.  
  
#### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>Artık bir dosya bozuk proje başvurusunu sürücünüzde düzeltmek için  
  
-   Başvuruyu silin.  
  
-   Başvuru bilgisayarınızda başka bir konum varsa, o konumdan okuyun.  
  
-   Daha fazla bilgi için [nasıl NIB: başvurular ekleme veya kaldırma Başvurusu Ekle iletişim kutusunu kullanarak](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## <a name="referenced-file-has-been-renamed"></a>Başvurulan dosya yeniden adlandırıldı  
 Bu, başvurulan dosya yeniden adlandırıldı mümkündür.  
  
#### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>Bozuk bir başvuruyu yeniden adlandırıldı bir dosya için düzeltme  
  
-   Başvuru silin ve ardından yeniden adlandırılan dosyaya bir başvuru ekleyin.  
  
-   Başvuru bilgisayarınızda başka bir konum varsa, onu o konumdan okumak zorundasınız. Daha fazla bilgi için [nasıl NIB: başvurular ekleme veya kaldırma Başvurusu Ekle iletişim kutusunu kullanarak](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## <a name="network-connection-or-authentication-has-failed"></a>Ağ bağlantısı veya kimlik doğrulaması başarısız oldu  
 Erişilemeyen dosyalar için birçok olası nedenleri şunlar olabilir: başarısız bir ağ bağlantısı veya örneğin başarısız bir kimlik doğrulama. Her bir nedenden kurtarma benzersiz bir çeşit olabilir; Örneğin, gerekli kaynaklara erişim için yerel yönetici başvurmanız gerekebilir. Ancak, başvuru silme ve onu kullanan kod çözme her zaman bir seçenektir. Daha fazla bilgi için [nasıl NIB: başvurular ekleme veya kaldırma Başvurusu Ekle iletişim kutusunu kullanarak](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## <a name="com-component-is-not-installed-on-computer"></a>COM bileşeni bilgisayarda yüklü değil  
 Bir kullanıcı bir COM bileşenine bir başvuru eklemiştir ve bu bileşeni yüklü olmayan bir bilgisayarda kodu çalıştırmak ikinci bir kullanıcı çalışırsa, ikinci kullanıcı başvuru bozuk olduğunu belirten bir hata alırsınız. Bileşeni, ikinci bilgisayara yükleniyor. hatayı düzeltin. COM bileşenleri başvurular projelerinizde kullanma hakkında daha fazla bilgi için bkz. [.NET Framework uygulamalarında COM birlikte çalışabilirliği](http://msdn.microsoft.com/library/f5a72143-c268-4dff-a019-974ad940e17d).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)   
 [Başvurular sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)   
 [NIB nasıl yapılır: başvurular ekleme veya kaldırma Başvuru Ekle iletişim kutusunu kullanarak](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)



