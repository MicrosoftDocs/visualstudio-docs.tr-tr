---
title: Başvuru Eklerken NuGet veya Uzantı SDK Kullanma Karşılaştırması
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a895124effa8155ab2edb4652962b605926234d5
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349484"
---
# <a name="adding-references-using-nuget-versus-an-extension-sdk"></a>Başvuru eklerken NuGet karşı uzantı SDK kullanma

NuGet veya bir yazılım geliştirme seti (SDK) kullanarak Visual Studio projeleri içinde kullanım için bir paket sağlayabilirsiniz. Arasındaki benzerlikleri ve farkları iki mekanizma açıklayarak, bu makalede, görev için en iyi seçmenize yardımcı olabilir.

- NuGet, bir proje çözümde kitaplıkları ekleme işlemini basitleştiren bir açık kaynak, paket Yönetimi sistemidir. Daha fazla bilgi için [NuGet belgeleri](/nuget).

- SDK, Visual Studio tek başvuru öğesi olarak davranır dosyaları koleksiyonudur. **Başvuru Yöneticisi** iletişim kutusu, bu iletişim kutusu görüntülediğinizde, açık olan proje için uygun olan tüm SDK'ları listeler. Bir SDK için bir proje eklediğinizde, tüm bu SDK içeriği IntelliSense erişebilir **araç kutusu**, tasarımcılar, **Nesne Tarayıcısı**, MSBuild, dağıtım, hata ayıklama ve paketleme. SDK'ları hakkında daha fazla bilgi için bkz. [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md).

## <a name="which-mechanism-should-i-use"></a>Hangi mekanizması kullanmalıyım?

Aşağıdaki tablo başvuru özelliklerinin bir SDK'sı NuGet başvuru özellikleriyle karşılaştırmanıza yardımcı olur.

| Özellik | SDK desteği | SDK notları | NuGet desteği | NuGet notları |
| - | - | - |---------------| - |
| Bir varlığı mekanizması başvuruyor ve tüm dosyaları ve işlevsellik sonra kullanılabilir. | Y | Kullanarak bir SDK'sı ekleme **başvuru Yöneticisi** iletişim kutusunu ve tüm dosyaları ve işlevleri geliştirme iş akışı sırasında kullanılabilir. | Y | |
| MSBuild derlemeleri ve Windows meta verileri otomatik olarak kullanır (*.winmd*) dosyaları. | Y | SDK'de başvuruların derleyicinin otomatik olarak geçirilir. | Y | |
| MSBuild .h veya .lib dosyaları otomatik olarak kullanır. | Y | *SDKName.props* dosya Visual C++ dizini ve benzeri, otomatik ayarlama nasıl Visual Studio söyler *.h* veya *.lib* tüketim dosya. | N | |
| MSBuild otomatik olarak kullanan *.js* veya *.css* dosyaları. | Y | İçinde **Çözüm Gezgini**, tek tek göstermek için JavaScript SDK'sı başvurusu düğümü genişletebilir *.js* veya *.css* ardından oluşturun ve dosyalarını `<source include/>` sürükleyerek etiketleri Bu dosyalar kaynak dosyalarına. F5'e ve otomatik paket Kurulum SDK'yı destekler. | Y | |
| MSBuild denetimde otomatik olarak ekler **araç kutusu**. | Y | **Araç kutusu** SDK'ları kullanabilir ve belirttiğiniz sekmeleri denetimlerini gösterir. | N | |
| Mekanizması, Visual Studio Yükleyicisi için uzantıları (VSIX) destekler. | Y | VSIX özel bildirimi ve SDK paketleri oluşturmak için mantıksal sahiptir. | Y | VSIX başka bir Kurulum programı eklenebilir. |
| **Nesne Tarayıcısı** başvuruları numaralandırır. | Y | **Nesne Tarayıcısı** otomatik olarak SDK'ları başvuruları listesini alır ve bunları numaralandırır. | N | |
| Dosyaları ve bağlantıları otomatik olarak eklenmesini için **başvuru Yöneticisi** iletişim kutusu (Yardım bağlantıları ve benzeri Otomatik Doldur) | Y | **Başvuru Yöneticisi** iletişim kutusu SDK bağımlılıkları listesi ve Yardım bağlantıları yanı sıra SDK'ları, otomatik olarak numaralandırır. | N | NuGet sağlar, kendi **NuGet paketlerini Yönet** iletişim kutusu. |
| Birden fazla mimari mekanizması destekler. | Y | SDK'ları birden çok yapılandırma sevk edebilir. MSBuild, her bir proje yapılandırması için uygun dosyaları kullanır. | N | |
| Mekanizması birden çok yapılandırmayı destekler. | Y | SDK'ları birden çok yapılandırma sevk edebilir. Proje mimarisine bağlı olarak, uygun dosyaları her proje mimari MSBuild tüketir. | N | |
| Mekanizması "kopya için." belirtebilirsiniz. | Y | Dosyaları bırakılan bağlı olarak *\redist* veya *\designtime* klasörü, alıcı uygulamanın paket kopyalanacak dosyaları denetleyebilirsiniz. | N | Paketi bildiriminde kopyalamak için hangi dosyaların bildirdiğiniz. |
| İçeriği, yerelleştirilmiş dosyalarında görünür. | Y | SDK'ları yerelleştirilmiş XML belgelerinde bir daha iyi tasarım zamanı deneyimi için otomatik olarak dahil edilir. | N | |
| MSBuild SDK birden çok sürümünü aynı anda tüketen destekler. | Y | SDK, birden çok sürümü aynı anda tüketen destekler. | N | Buna başvuran değil. Projenizdeki NuGet dosyaların birden fazla sürümünü aynı anda sahip olamaz. |
| Geçerli hedef çerçeve, Visual Studio sürümleri ve proje türleri belirtme mekanizması destekler. | Y | **Başvuru Yöneticisi** iletişim kutusu ve **araç kutusu** kullanıcılar daha kolay uygun SDK'ları seçebilmeniz bir proje için geçerli olan SDK'lar göster. | Y (kısmi) | Pivot hedef çerçevedir. Kullanıcı arabiriminde filtre yoktur. Yükleme sırasında bir hata döndürebilir. |
| Mekanizması için yerel Winmd'lerin belirten kayıt bilgi destekler. | Y | .Winmd dosyası ve .dll dosyasında arasındaki bağıntıyı belirtebilirsiniz *SDKManifest.xml*. | N | |
| Diğer SDK'lar üzerinde bağımlılıkları belirtme mekanizması destekler. | Y | SDK'sı yalnızca kullanıcıya bildirir; Kullanıcı yine de bunları yüklemeniz ve bunları el ile başvuru gerekir. | Y | NuGet bunları otomatik olarak çeker; Kullanıcı bildirilmez. |
| Mekanizması ile tümleşir [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] uygulama bildirimi ve Framework kimliği gibi kavramları | Y | SDK'sı özgü kavramları geçmelidir [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] kullanılabilen Sdk'leri ile paketleme ve F5'ın düzgün çalışması için[!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]. | N | |
| İşlem hattı için uygulamanızı mekanizması tümleşir [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] uygulamalar. | Y | SDK'sı geçmelidir [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]-ilgili belirli kavramları kullanılabilir SDK'lar ile paketleme ve F5'ın düzgün çalışması için [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]. | Y | NuGet içeriği projenin bir parçası haline gelir. Hiçbir F5 yükseltilmesine gereklidir. |
| Mekanizması uygulama bildirimleri ile tümleştirilir. | Y | SDK'sı geçmelidir [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]-ilgili belirli kavramları kullanılabilir SDK'lar ile paketleme ve F5'ın düzgün çalışması için [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]. | Y | NuGet içeriği projenin bir parçası haline gelir. Hiçbir F5 yükseltilmesine gereklidir. |
| Başvuru olmayan dosyaları mekanizması dağıtır (örneğin, testleri çalıştırmak için temel test çerçevesi dağıtma [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] uygulamaları). | Y | Dosyaları sürükleyip bıraktığınızda *\redist* klasör dosyaları otomatik olarak dağıtılır. | Y | |
| Mekanizması, platform SDK'ları Visual Studio IDE içinde otomatik olarak ekler. | Y | Bıraktığınız varsa [!INCLUDE[win8](../debugger/includes/win8_md.md)] SDK veya Windows Phone SDK'sı ile belirli bir düzeni, belirli bir konumda SDK'sı, otomatik olarak Visual Studio özellikleri ile tümleşiktir. | N | |
| Mekanizması temiz Geliştirici makinesinde destekler. (Diğer bir deyişle, hiçbir yüklenmesi gerekiyor ve kaynak kod denetiminden basit alma çalışır.) | N | Bir SDK'sına başvuran çünkü çözümünüzü ve SDK ayrı olarak işaretlemeniz gerekir. MSBuild SDK'ları yinelenir iki kayıt defteri olmayan varsayılan konumlardan SDK denetleyebilirsiniz (Ayrıntılar için bkz [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md)). Alternatif olarak, SDK'ları özel bir konuma oluşuyorsa proje dosyasında aşağıdaki kodu belirtebilirsiniz:<br /><br />`<PropertyGroup>`<br />&nbsp;&nbsp;`<SDKReferenceDirectoryRoot>`<br />&nbsp;&nbsp;`C:\MySDKs`<br />&nbsp;&nbsp;`</SDKReferenceDirectoryRoot>`<br />`</PropertyGroup>`<br /><br /> Ardından SDK, bu konuma kontrol edin. | Y | Çözümü denetleyebilir ve Visual Studio hemen tanır ve dosyalar üzerinde çalışır. |
| Paket yazarlarının oluşan büyük bir mevcut topluluk birleştirebilirsiniz. | Yok | Topluluk, yeni bir özelliktir. | Y | |
| Var olan büyük bir topluluk paket tüketici katılabilirsiniz. | Yok | Topluluk, yeni bir özelliktir. | Y | |
| (Özel galeriler, depolar ve diğerleri) iş ortaklarından oluşan bir ekosistem katılabilirsiniz. | Yok | Visual Studio Market, Microsoft Download Center, mevcut depolara içerir ve [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]. | Y | |
| Paket oluşturma hem tüketim için sürekli tümleştirme yapı sunucularını mekanizması tümleşir. | Y | SDK'sı iade konumu (SDKReferenceDirectoryRoot özelliği) için MSBuild komut satırında geçmesi gerekir. | Y | |
| Mekanizması hem kararlı ve yayın öncesi paket sürümlerini destekler. | Y | SDK, birden fazla sürüm ekleme başvuruları destekler. | Y | |
| Mekanizması otomatik güncelleştirme için yüklü paketleri destekler. | Y | Sevk VSIX veya Visual Studio otomatik güncelleştirmelerin parçası olarak otomatik bildirimler SDK'sı sağlar. | Y | |
| Tek başına mekanizması içeren *.exe* dosyası oluşturma ve paketleri kullanma. | Y | SDK'sını içeren *MSBuild.exe*. | Y | |
| Paketler, sürüm denetiminden denetlenebilir. | Y | Uzantı SDK'ları yapılmayacağını yani Belgeler düğümü dışındaki her şeyi iade edemezsiniz. Uzantı SDK'sı boyutu büyük olabilir. | Y | |
| Paket oluşturma ve kullanma için bir PowerShell arabirimini kullanabilirsiniz. | Y (tüketim) N (oluşturma) | SDK oluşturma için hiçbir araç. Tüketim MSBuild komut satırında yürütüyor. | Y | |
| Hata ayıklama desteği için bir sembol paketi kullanabilirsiniz. | Y | Bıraktığınız varsa *.pdb* SDK dosyalarında dosyaları toplanmış otomatik olarak. | Y | |
| Paket Yöneticisi otomatik olarak güncelleştirilir mekanizması destekler. | Yok | SDK'sı, MSBuild ile düzenlendi. | Y | |
| Bu mekanizma, basit bir bildirim biçimi destekler. | Y | *SDKManifest.xml* birçok özniteliklerini de destekler, ancak küçük bir alt genellikle gerekli değildir. | Y | |
| Mekanizması, tüm Visual Studio sürümleri için kullanılabilir. | Y | SDK, tüm Visual Studio sürümlerini destekler. | Y | NuGet tüm Visual Studio sürümlerini destekler. |
| Tüm proje türleri için kullanıma mekanizmadır. | N | SDK'yı destekleyen [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] başlatmadaki uygulamaları [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]. | N | İzin verilen projelerin bir listesini gözden geçirebilirsiniz. |

## <a name="see-also"></a>Ayrıca bkz.

- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)
- [(Mac için Visual Studio) bir projedeki başvuruları yönetme](/visualstudio/mac/managing-references-in-a-project)