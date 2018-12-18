---
title: 'Nasıl yapılır: bir etki alanına özgü dil çözümü oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
ms.assetid: e585b63b-34d2-405a-8d81-39ea22317975
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2650afc2172cdcceca892d4ad19a05becac3e472
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908962"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Nasıl yapılır: Etki Alanına Özgü Dil Çözümü Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir etki alanına özgü dil (DSL) özelleştirilmiş kullanılarak oluşturulan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözüm.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu yordama başlamadan önce bu bileşenleri yüklemelisiniz:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|Visual Studio Görselleştirme ve modelleme SDK'sı|[http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|  
  
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
  
      ![DSL iletişim oluşturma](../modeling/media/create-dsldialog.png "Create_DSLDialog")  
  
2. Bir DSL şablonu seçin.  
  
    Üzerinde **etki alanına özgü dil seçenekleri** sayfasında, çözüm şablonları gibi birini **Minimal dil**. Oluşturmak istediğiniz DSL için benzer bir şablon seçin.  
  
    Çözüm şablonları hakkında daha fazla bilgi için bkz: [bir etki alanına özgü dil çözümü şablonu seçme](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
3. Bir dosya adı uzantısı girin **dosya uzantısı** sayfası. Bilgisayarınızın benzersiz olmalıdır ve DSL yüklemek istediğiniz tüm bilgisayarlara içinde. Şu iletiyi görürsünüz **bu uygulamaları ya da Visual Studio düzenleyicileri kullanın**.  
  
   -   Tam olarak yüklenmemiş önceki Deneysel DSL içinde dosya adı uzantısı'nı kullandıysanız, bunları dışarı kullanarak temizleyebilir **Deneysel örneğini sıfırlama** bulunabilir aracı [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] SDK menüsü.  
  
   -   Başka bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bu uzantıyı kullanan uzantısı tam olarak yüklü bilgisayarınızda, kaldırmayı göz önünde bulundurun. Üzerinde **Araçları** menüsünde tıklatın **Uzantı Yöneticisi**.  
  
4. İnceleyin ve gerekirse ayarlayın, sihirbazın kalan sayfalarında alanları. Seçimlerden memnun olduğunuzda tıklayın **son**. Ayarlar hakkında daha fazla bilgi için bkz. [DSL Tasarımcısı Sihirbazı sayfaları](#settings).  
  
    Sihirbaz, adlandırılmış iki proje içeren bir çözüm oluşturur. **Dsl** ve **DslPackage**.  
  
   > [!NOTE]
   >  Güvenilmeyen kaynaklardan metin şablonlarını çalıştırmak için değil uyaran bir ileti görürseniz **Tamam**. Bu ileti yeniden görünür değil ayarlayabilirsiniz.  
  
##  <a name="settings"></a> DSL Tasarımcısı Sihirbazı sayfaları  
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
  
-   Sıfırlama [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] deneysel örneği. Bu, tüm daha önce hazırladığınız DSL'ler kaydını kaldırır. Üzerinde **Başlat** menüsünde tıklayın **tüm programlar**, **Microsoft Visual Studio 2010 SDK**, **Araçları**ve ardından **Sıfırla Microsoft Visual Studio 2010 deneysel örneğinde**. Yeniden kullanmak istediğiniz diğer bir DSL yeniden oluşturabilirsiniz.  
  
     \- veya -  
  
-   Varsa bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bu uzantıyı kullanan uzantısı tam olarak yüklü bilgisayarınızda, bunu kaldırın. Üzerinde **Araçları** menüsünde tıklatın **Uzantı Yöneticisi**.  
  
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
 **Tanımlayıcı ad anahtar dosyası oluştur**  
 DSL derlemenizi oturum açmak için yeni bir anahtar oluşturmak için varsayılan seçenektir.  
  
 **Var olan bir tanımlayıcı ad anahtarını kullan**  
 DSL'nizi başka bir derleme ile tümleştirmek istiyorsanız bu seçeneği kullanın.  
  
 Tanımlayıcı adlandırma hakkında daha fazla bilgi için bkz. [bkz](http://go.microsoft.com/fwlink/?LinkId=186073).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md)   
 [Etki alanına özgü dil araçları sözlüğü](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



