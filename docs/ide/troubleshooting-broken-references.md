---
title: Bozuk başvurularda sorun giderme
ms.date: 03/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3c1879b67558cb57fba7bc462e4c7df03fb5efc8
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32064356"
---
# <a name="troubleshoot-broken-references"></a>Bozuk başvurularda sorun giderme

Uygulamanızı kırık referans kullanmaya çalışırsa, bir özel durum hatası oluşturulur. Başvurulan bileşeni bulun yeteneğinin, hata için birincil tetikleyici olmakla birlikte bozuk bir başvuru düşünülebilir bazı durumlar vardır. Bu örnekler aşağıdaki listede gösterilir:

- Projenin başvurusu yanlış veya tamamlanmamış yoludur.

- Başvurulan dosya silindi.

- Başvurulan dosyası yeniden adlandırıldı.

- Ağ bağlantısını veya kimlik doğrulama başarısız oldu.

- Referans bilgisayarda yüklü değil bir COM bileşeni sağlamaktır.

Bu sorunları çözümler aşağıda verilmiştir.

> [!NOTE]
> Derleme dosyalarında proje dosyasında mutlak yollar ile başvurulur. Bu nedenle, yerel ortamlarında başvurulan bir derleme eksik geliþtiricili ortamında çalışan kullanıcıların mümkündür. Bu hataları önlemek için proje proje başvuruları eklemek için bu gibi durumlarda daha iyi olur. Daha fazla bilgi için bkz: [Derlemelerle programlama](/dotnet/framework/app-domains/programming-with-assemblies).

## <a name="reference-path-is-incorrect"></a>Başvuru yolu geçersiz

Farklı bilgisayarlarda Paylaşılan projeleri, her bilgisayarda farklı bir dizinde bir bileşen bulunduğunda bazı başvuruları bulunmayabilir. Başvuruları bileşen dosya adı altında depolanır (örneğin, *MyComponent*). Bir başvuru projeye eklendiğinde, bileşen dosya klasör konumunu (örneğin, *C:\MyComponents*) eklenir **ReferencePath** proje özelliği.

Proje açıldığında, başvuru yolundaki dizinlerde bakarak bu başvurulan bileşen dosyaları bulmaya çalışır. Proje bileşeni gibi farklı bir dizinde depolayan bir bilgisayarda açılırsa *D:\MyComponents*, başvurusu bulunamıyor ve bir hata görünür **görev listesi**.

Bu sorunu gidermek için kırık referans silin ve sonra onu kullanarak değiştirmek **Başvuru Ekle** iletişim kutusu. Başka bir çözüm **başvuru yolu** projenin özellik sayfalarında madde ve klasörler listesinde doğru konuma işaret edecek şekilde değiştirin. **Başvuru yolu** özelliği, her bilgisayardaki her kullanıcı için kalıcıdır. Bu nedenle, başvuru yolun değiştirilmesi projenin diğer kullanıcıların etkilemez.

> [!TIP]
> Proje Proje başvuruları bu sorunları gerekmez. Şunları yapabilirsiniz, bu nedenle, dosya referansları yerine kullanın.

### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>Referans yolu düzelterek bozuk proje başvurusu düzeltmek için

1. İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklatın ve **özellikleri**.

   **Proje Tasarımcısı** görüntülenir.

1. Visual Basic kullanıyorsanız seçin **başvuruları** sayfasında ve tıklayın **başvuru yollarını** düğmesi. İçinde **başvuru yollarını** iletişim kutusunda, başvuru istediğiniz öğeyi içeren klasörün yolunu yazın **klasörü** alan ve ardından **klasörü Ekle** düğmesi.

    C# kullanıyorsanız seçin **başvuru yollarını** sayfası. İçinde **klasörü** alan, başvuru ve ardından istediğiniz öğeyi içeren klasörün yolunu yazın **klasörü Ekle** düğmesi.

## <a name="referenced-file-has-been-deleted"></a>Başvurulan dosya silindi

Başvurulan dosya silindi ve artık sürücüde yok mümkündür.

### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>Artık bir dosyanın bozuk proje başvurusu diskinize düzeltmek için

- Başvuru silin.

- Bilgisayarınızda başka bir konuma başvuru zaten varsa, o konumdan okuyun.

## <a name="referenced-file-has-been-renamed"></a>Başvurulan dosya yeniden adlandırıldı

Başvurulan dosyası yeniden adlandırıldı mümkündür.

### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>Kopuk bir başvuruyu yeniden adlandırılmış bir dosya için düzeltme

- Başvuru silin ve sonra yeniden adlandırılmış dosya için bir başvuru ekleyin.

- Bilgisayarınızda başka bir konuma başvuru bulunması durumunda içinde o konumdan okumak zorunda.

## <a name="network-connection-or-authentication-has-failed"></a>Ağ bağlantısı veya kimlik doğrulama başarısız oldu

Erişilemeyen dosyalar birçok olası nedeni olabilir: başarısız ağ bağlantısı veya başarısız bir kimlik doğrulama, örneğin. Her neden kurtarma benzersiz bir çeşit olabilir; Örneğin, gerekli kaynaklara erişimi için yerel yönetici başvurun gerekebilir. Ancak, başvuru silme ve onu kullanılan kod çözme her zaman bir seçenektir.

## <a name="com-component-is-not-installed-on-computer"></a>COM bileşeni bilgisayarda yüklü değil

Bir kullanıcı bir COM bileşeni başvuru ekledi ve kod bu bileşeni yüklü olmayan bir bilgisayarda çalıştırmak ikinci bir kullanıcı çalışırsa, ikinci kullanıcı başvuru bozuk olduğunu belirten bir hata alırsınız. İkinci bilgisayarda bileşeni yüklemeyi hatayı düzeltin. COM bileşenlerini başvurular projelerinizde kullanma hakkında daha fazla bilgi için bkz: [.NET Framework uygulamalarında COM birlikte çalışabilirliği](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications).

## <a name="see-also"></a>Ayrıca bkz.

- [Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)