---
title: 'Nasıl yapılır: Etki Alanına Özgü Dil Çözümü Oluşturma'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f138f1f809ae5a81aa97c571a147c679bacaa3b2
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967239"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Nasıl yapılır: Etki Alanına Özgü Dil Çözümü Oluşturma
Bir etki alanına özgü dil (DSL) özel bir Visual Studio çözümünü kullanarak oluşturulur.

## <a name="prerequisites"></a>Önkoşullar
 Bu yordama başlamadan önce bu bileşenleri yüklemelisiniz:


| | |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580) |
| Visual Studio Görselleştirme ve modelleme SDK'sı | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


## <a name="creating-a-domain-specific-language-solution"></a>Bir etki alanına özgü dil çözümü oluşturma

#### <a name="to-create-a-domain-specific-language-solution"></a>Bir etki alanına özgü dil çözümü oluşturma

1. DSL Sihirbazı'nı başlatın.

   1. Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.

   2. **Yeni proje** iletişim kutusu görüntülenir.

   3. Altında **proje türleri**, genişletme **diğer proje türleri** düğüm seçeneğine tıklayıp **genişletilebilirlik**.

   4. Tıklayın **etki alanına özgü dil tasarımcısını**.

   5. İçinde **adı** çözüm için bir ad yazın. **Tamam**'ı tıklatın.

       **Etki alanına özgü dil Tasarımcısı Sihirbazı** görünür.

      > [!NOTE]
      >  Tercihen, kodu oluşturmak için kullanılabilir olmadığından geçerli bir Visual C# tanımlayıcısı, yazdığınız ad olmalıdır.

      ![DSL iletişim kutusu oluşturma](../modeling/media/create_dsldialog.png)

2. Bir DSL şablonu seçin.

    Üzerinde **etki alanına özgü dil seçenekleri** sayfasında, çözüm şablonları gibi birini **Minimal dil**. Oluşturmak istediğiniz DSL için benzer bir şablon seçin.

    Çözüm şablonları hakkında daha fazla bilgi için bkz: [bir etki alanına özgü dil çözümü şablonu seçme](../modeling/choosing-a-domain-specific-language-solution-template.md).

3. Bir dosya adı uzantısı girin **dosya uzantısı** sayfası. Bilgisayarınızın benzersiz olmalıdır ve DSL yüklemek istediğiniz tüm bilgisayarlara içinde. Şu iletiyi görürsünüz **bu uygulamaları ya da Visual Studio düzenleyicileri kullanın**.

   -   Tam olarak yüklenmemiş önceki Deneysel DSL içinde dosya adı uzantısı'nı kullandıysanız, bunları dışarı kullanarak temizleyebilir **Deneysel örneğini sıfırlama** aracı, Visual Studio SDK menüsünde bulunabilir.

   -   Bu dosya uzantısı kullanan başka bir Visual Studio uzantısı tam olarak bilgisayarınızda yüklüyse kaldırmayı göz önünde bulundurun. Üzerinde **Araçları** menüsünde tıklatın **Uzantı Yöneticisi**.

4. İnceleyin ve gerekirse ayarlayın, sihirbazın kalan sayfalarında alanları. Seçimlerden memnun olduğunuzda tıklayın **son**. Ayarlar hakkında daha fazla bilgi için bkz. [DSL Tasarımcısı Sihirbazı sayfaları](#settings).

    Sihirbaz, adlandırılmış iki proje içeren bir çözüm oluşturur. **Dsl** ve **DslPackage**.

   > [!NOTE]
   >  Güvenilmeyen kaynaklardan metin şablonlarını çalıştırmak için değil uyaran bir ileti görürseniz **Tamam**. Bu ileti yeniden görünür değil ayarlayabilirsiniz.

## <a name="settings"></a> DSL Tasarımcısı Sihirbazı sayfaları
 Bazı alanlar, varsayılan değerleri değiştirmeden bırakabilirsiniz. Ancak, dosya uzantısı alanın ayarlanmış emin olun.

### <a name="solution-settings-page"></a>Çözüm Ayarları sayfası
 **Hangi şablonun etki alanına özgü dil için temel almak istersiniz?**
Oluşturmak istediğiniz DSL için benzer bir şablon seçin. Farklı şablonları, kullanışlı bir başlangıç noktası sağlar. Bir çözüm şablonu seçtiğinizde, sihirbaz açıklamasını görüntüler. Çözüm şablonları hakkında daha fazla bilgi için bkz: [bir etki alanına özgü dil çözümü şablonu seçme](../modeling/choosing-a-domain-specific-language-solution-template.md).

 **Ne, etki alanına özgü dil adı istiyorsunuz?**
Varsayılan olarak çözüm adı. Kod, bu değeri oluşturulur. C# sınıf adı olarak geçerli olmalıdır.

### <a name="file-extension-page"></a>Dosya uzantısı sayfası
 **Hangi uzantısının modellemelidir kullanan dosyaları?**
Yeni bir dosya uzantısını yazın.

 Bu dosya uzantısı zaten kullanılmak üzere bu bilgisayarı şu şekilde kaydedilmemiş olduğunu doğrulayın:

 Altına bakın **bu uzantıyı işlemek için diğer araçları ve uygulamaları kayıtlı**. İletiyi görürseniz **bu uygulamaları ya da Visual Studio düzenleyicileri kullanın**, bu dosya uzantısı kullanabilirsiniz.

 Araçlar veya paketler listesini görürseniz, aşağıdakilerden birini yapmalısınız:

-   Farklı dosya uzantısını yazın.

     \- veya -

-   Visual Studio Deneysel örneğini sıfırlama. Bu, tüm daha önce hazırladığınız DSL'ler kaydını kaldırır. Üzerinde **Başlat** menüsünde tıklayın **tüm programlar**, **Microsoft Visual Studio 2010 SDK**, **Araçları**ve ardından **Sıfırla Microsoft Visual Studio 2010 deneysel örneğinde**. Yeniden kullanmak istediğiniz diğer bir DSL yeniden oluşturabilirsiniz.

     \- veya -

-   Bu dosya uzantısı kullanan Visual Studio uzantısı tam olarak bilgisayarınızda yüklüyse, bunu kaldırın. Üzerinde **Araçları** menüsünde tıklatın **Uzantı Yöneticisi**.

### <a name="product-settings-page"></a>Ürün Ayarları sayfası
 **Yeni alana özgü dilin ait olduğu ürünün adı nedir?**
Varsayılan olarak DSL adı.

 Bu değer, Windows Explorer (veya dosya Gezgini) Bu dosya uzantısına sahip dosyaları tanımlamak için kullanılır.

 **Ürünün ait şirketin adı nedir?**
Şirketinizin adını.

 Bu değer, DSL paketinizin AssemblyInfo özelliklerine eklenmiştir.

 **Bu çözümdeki projelerin kök ad alanı nedir?**
Bu, şirketinizin oluşan bir ad ve ürün adları için varsayılan olarak.

### <a name="signing-page"></a>İmzalama sayfası
 **Tanımlayıcı ad anahtar dosyası oluştur** , DSL derlemeyi imzalamak için yeni bir anahtar oluşturmak için varsayılan seçenektir.

 **Var olan bir tanımlayıcı ad anahtarını kullan** DSL'nizi başka bir derleme ile tümleştirmek istiyorsanız bu seçeneği kullanın.

 Tanımlayıcı adlandırma hakkında daha fazla bilgi için bkz. [bkz](http://go.microsoft.com/fwlink/?LinkId=186073).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
- [Etki alanına özgü dil araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
