---
title: Başvuru eklerken NuGet karşı uzantı SDK kullanma | Microsoft Docs
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
- vs.toolsoptionspages.nuget_package_manager.general
- vs.toolsoptionspages.nuget_package_manager.package_sources
ms.assetid: 2175581e-83cb-444c-bb52-cc1fca8ea196
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 031b582665abeb14f705725c7bee97f272bd5ab4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49235813"
---
# <a name="adding-references-using-nuget-versus-an-extension-sdk"></a>Başvuru Eklerken NuGet veya Uzantı SDK Kullanma Karşılaştırması
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir paketi, Visual Studio için NuGet uzantısı ya da bir yazılım geliştirme seti (SDK) kullanarak Visual Studio projeleri içinde kullanılmaya sağlayabilir. Arasındaki benzerlikleri ve farkları iki mekanizma açıklayarak, bu konuda en iyi göreviniz için seçmenize yardımcı olabilir.  
  
-   NuGet, bir proje çözümde kitaplıkları ekleme işlemini basitleştiren bir açık kaynak, paket Yönetimi sistemidir. Daha fazla bilgi için [NuGet genel bakış](http://go.microsoft.com/fwlink/?LinkId=254877).  
  
-   SDK, Visual Studio tek başvuru öğesi olarak davranır dosyaları koleksiyonudur. **Başvuru Yöneticisi** iletişim kutusu, bu iletişim kutusu görüntülediğinizde, açık olan proje için uygun olan tüm SDK'ları listeler. Bir SDK için bir proje eklediğinizde, tüm bu SDK içeriği IntelliSense erişebilir **araç kutusu**, tasarımcılar, **Nesne Tarayıcısı**, MSBuild, dağıtım, hata ayıklama ve paketleme. SDK'ları hakkında daha fazla bilgi için bkz. [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md).  
  
## <a name="which-mechanism-should-i-use"></a>Hangi mekanizması kullanmalıyım?  
 Aşağıdaki tablo başvuru özelliklerinin bir SDK'sı NuGet başvuru özellikleriyle karşılaştırmanıza yardımcı olur.  
  
|Özellik|SDK desteği|SDK notları|NuGet desteği|NuGet notları|  
|-------------|-----------------|---------------|-------------------|-----------------|  
|Bir varlığı mekanizması başvuruyor ve tüm dosyaları ve işlevsellik sonra kullanılabilir.|Y|Kullanarak bir SDK'sı ekleme **başvuru Yöneticisi** iletişim kutusunu ve tüm dosyaları ve işlevleri geliştirme iş akışı sırasında kullanılabilir.|Y||  
|MSBuild, derlemeleri ve Windows meta veri (.winmd) dosyalarını otomatik olarak kullanır.|Y|SDK'de başvuruların derleyicinin otomatik olarak geçirilir.|Y||  
|MSBuild .h veya .lib dosyaları otomatik olarak kullanır.|Y|*SDKName*.props dosyası Visual Studio Visual C++ dizini ve otomatik .h veya .lib dosyası tüketim için belirli bir benzeri nasıl ayarlanacağı söyler.|N||  
|MSBuild .js veya .css dosyaları otomatik olarak kullanır.|Y|İçinde **Çözüm Gezgini**, tek tek .js göstermek için JavaScript SDK'sı başvurusu düğümü genişletebilir veya .css dosyaları ve ardından oluşturmak `<source include/>` dosyaları kaynak dosyalarına sürükleyerek etiketler. F5'e ve otomatik paket Kurulum SDK'yı destekler.|Y||  
|MSBuild denetimde otomatik olarak ekler **araç kutusu**.|Y|**Araç kutusu** SDK'ları kullanabilir ve belirttiğiniz sekmeleri denetimlerini gösterir.|N||  
|Mekanizması, Visual Studio Yükleyicisi için uzantıları (VSIX) destekler.|Y|VSIX özel bildirimi ve SDK paketleri oluşturmak için mantıksal sahiptir.|Y|VSIX başka bir Kurulum programı eklenebilir.|  
|**Nesne Tarayıcısı** başvuruları numaralandırır.|Y|**Nesne Tarayıcısı** otomatik olarak SDK'ları başvuruları listesini alır ve bunları numaralandırır.|N||  
|Dosyaları ve bağlantıları otomatik olarak eklenmesini için **başvuru Yöneticisi** iletişim kutusu (Yardım bağlantıları ve benzeri Otomatik Doldur)|Y|**Başvuru Yöneticisi** iletişim kutusu SDK bağımlılıkları listesi ve Yardım bağlantıları yanı sıra SDK'ları, otomatik olarak numaralandırır.|N|NuGet sağlar, kendi **NuGet paketlerini Yönet** iletişim kutusu.|  
|Birden fazla mimari mekanizması destekler.|Y|SDK'ları birden çok yapılandırma sevk edebilir. MSBuild, her bir proje yapılandırması için uygun dosyaları kullanır.|N||  
|Mekanizması birden çok yapılandırmayı destekler.|Y|SDK'ları birden çok yapılandırma sevk edebilir. Proje mimarisine bağlı olarak, uygun dosyaları her proje mimari MSBuild tüketir.|N||  
|Mekanizması "kopya için." belirtebilirsiniz.|Y|Dosyaları \redist veya \designtime klasöründe olup bırakılan bağlı olarak, alıcı uygulamanın paket kopyalanacak dosyaları denetleyebilirsiniz.|N|Paketi bildiriminde kopyalamak için hangi dosyaların bildirdiğiniz.|  
|İçeriği, yerelleştirilmiş dosyalarında görünür.|Y|SDK'ları yerelleştirilmiş XML belgelerinde bir daha iyi tasarım zamanı deneyimi için otomatik olarak dahil edilir.|N||  
|MSBuild SDK birden çok sürümünü aynı anda tüketen destekler.|Y|SDK, birden çok sürümü aynı anda tüketen destekler.|N|Buna başvuran değil. Projenizdeki NuGet dosyaların birden fazla sürümünü aynı anda sahip olamaz.|  
|Geçerli hedef çerçeve, Visual Studio sürümleri ve proje türleri belirtme mekanizması destekler.|Y|**Başvuru Yöneticisi** iletişim kutusu ve **araç kutusu** kullanıcılar daha kolay uygun SDK'ları seçebilmeniz bir proje için geçerli olan SDK'lar göster.|Y (kısmi)|Pivot hedef çerçevedir. Kullanıcı arabiriminde filtre yoktur. Yükleme sırasında bir hata döndürebilir.|  
|Mekanizması için yerel Winmd'lerin belirten kayıt bilgi destekler.|Y|.Winmd dosyası ve .dll dosyası arasındaki bağıntıyı SDKManifest.xml belirtebilirsiniz.|N||  
|Diğer SDK'lar üzerinde bağımlılıkları belirtme mekanizması destekler.|Y|SDK'sı yalnızca kullanıcıya bildirir; Kullanıcı yine de bunları yüklemeniz ve bunları el ile başvuru gerekir.|Y|NuGet bunları otomatik olarak çeker; Kullanıcı bildirilmez.|  
|Mekanizması ile tümleşir [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)] uygulama bildirimi ve Framework kimliği gibi kavramları|Y|SDK'sı özgü kavramları geçmelidir [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)] kullanılabilen Sdk'leri ile paketleme ve F5'ın düzgün çalışması için[!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)].|N||  
|İşlem hattı için uygulamanızı mekanizması tümleşir [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamalar.|Y|SDK'sı geçmelidir [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)]-ilgili belirli kavramları kullanılabilir SDK'lar ile paketleme ve F5'ın düzgün çalışması için [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)].|Y|NuGet içeriği projenin bir parçası haline gelir. Hiçbir F5 yükseltilmesine gereklidir.|  
|Mekanizması uygulama bildirimleri ile tümleştirilir.|Y|SDK'sı geçmelidir [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)]-ilgili belirli kavramları kullanılabilir SDK'lar ile paketleme ve F5'ın düzgün çalışması için [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)].|Y|NuGet içeriği projenin bir parçası haline gelir. Hiçbir F5 yükseltilmesine gereklidir.|  
|Başvuru olmayan dosyaları mekanizması dağıtır (örneğin, testleri çalıştırmak için temel test çerçevesi dağıtma [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamaları).|Y|\Redist klasöründe dosyaları sürükleyip bırakabilir, dosyaları otomatik olarak dağıtılır.|Y||  
|Mekanizması, platform SDK'ları Visual Studio IDE içinde otomatik olarak ekler.|Y|Bıraktığınız varsa [!INCLUDE[win8](../includes/win8-md.md)] SDK veya Windows Phone SDK'sı ile belirli bir düzeni, belirli bir konumda SDK'sı, otomatik olarak Visual Studio özellikleri ile tümleşiktir.|N||  
|Mekanizması temiz Geliştirici makinesinde destekler. (Diğer bir deyişle, hiçbir yüklenmesi gerekiyor ve kaynak kod denetiminden basit alma çalışır.)|N|Bir SDK'sına başvuran çünkü çözümünüzü ve SDK ayrı olarak işaretlemeniz gerekir. MSBuild SDK'ları yinelenir iki kayıt defteri olmayan varsayılan konumlardan SDK denetleyebilirsiniz (Ayrıntılar için bkz [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md)). Alternatif olarak, SDK'ları özel bir konuma oluşuyorsa proje dosyasında aşağıdaki kodu belirtebilirsiniz:<br /><br /> `<PropertyGroup>    <SDKReferenceDirectoryRoot>C:\MySDKs</SDKReferenceDirectoryRoot>   </PropertyGroup>`<br /><br /> Ardından SDK, bu konuma kontrol edin.|Y|Çözümü denetleyebilir ve Visual Studio hemen tanır ve dosyalar üzerinde çalışır.|  
|Paket yazarlarının oluşan büyük bir mevcut topluluk birleştirebilirsiniz.|Yok|Topluluk, yeni bir özelliktir.|Y||  
|Var olan büyük bir topluluk paket tüketici katılabilirsiniz.|Yok|Topluluk, yeni bir özelliktir.|Y||  
|(Özel galeriler, depolar ve diğerleri) iş ortaklarından oluşan bir ekosistem katılabilirsiniz.|Yok|Visual Studio Galerisi, Microsoft Download Center, mevcut depolara içerir ve [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].|Y||  
|Paket oluşturma hem tüketim için sürekli tümleştirme yapı sunucularını mekanizması tümleşir.|Y|SDK'sı iade konumu (SDKReferenceDirectoryRoot özelliği) için MSBuild komut satırında geçmesi gerekir.|Y||  
|Mekanizması hem kararlı ve yayın öncesi paket sürümlerini destekler.|Y|SDK, birden fazla sürüm ekleme başvuruları destekler.|Y||  
|Mekanizması otomatik güncelleştirme için yüklü paketleri destekler.|Y|Sevk VSIX veya Visual Studio otomatik güncelleştirmelerin parçası olarak otomatik bildirimler SDK'sı sağlar.|Y||  
|Mekanizması oluşturmak ve bu paketleri kullanan tek başına bir .exe dosyası içerir.|Y|SDK'sı, MSBuild.exe içerir.|Y||  
|Paketler, sürüm denetiminden denetlenebilir.|Y|Uzantı SDK'ları yapılmayacağını yani Belgeler düğümü dışındaki her şeyi iade edemezsiniz. Uzantı SDK'sı boyutu büyük olabilir.|Y||  
|Paket oluşturma ve kullanma için bir PowerShell arabirimini kullanabilirsiniz.|Y (tüketim) N (oluşturma)|SDK oluşturma için hiçbir araç. Tüketim MSBuild komut satırında yürütüyor.|Y||  
|Hata ayıklama desteği için bir sembol paketi kullanabilirsiniz.|Y|SDK'sında .pdb dosyaları sürükleyip bırakabilir, dosyaları otomatik olarak toplanmış.|Y||  
|Paket Yöneticisi otomatik olarak güncelleştirilir mekanizması destekler.|Yok|SDK'sı, MSBuild ile düzenlendi.|Y||  
|Bu mekanizma, basit bir bildirim biçimi destekler.|Y|SDKManifest.xml birçok özniteliklerini de destekler, ancak küçük bir alt genellikle gerekli değildir.|Y||  
|Mekanizması, tüm Visual Studio sürümleri için kullanılabilir.|Y|SDK, Visual Studio Express gelen tüm Visual Studio sürümleri destekler. [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].|Y|NuGet destekleyen tüm Visual Studio sürümleri, Express ayarlama yoluyla [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].|  
|Tüm proje türleri için kullanıma mekanizmadır.|N|SDK'yı destekleyen [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] başlatmadaki uygulamaları [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|N|İzin verilen projelerin bir listesini gözden geçirebilirsiniz.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)



