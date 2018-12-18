---
title: Devenv komut satırı anahtarları | Microsoft Docs
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
- switches, Devenv
- builds [Team System], command-line
- applications [Visual Studio], executing
- compiling source code, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
- environment, Devenv commands
- compilers, Devenv commands
- switches
- Devenv, syntax and list of switches
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
caps.latest.revision: 36
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7ee1596cf59fb4ba9b21772cdabc0c875ef8779a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49215040"
---
# <a name="devenv-command-line-switches"></a>Devenv Komut Satırı Anahtarları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Devenv, tümleşik geliştirme ortamı (IDE) için çeşitli seçenekleri de derleme, hata ayıklama ve projeleri, komut satırından dağıtma olanak tanır. Bu anahtarlar, IDE bir betik veya .bat dosyası, örneğin, Gecelik Yapı betiği çalıştırmak için veya belirli bir yapılandırmada IDE başlatmak için kullanın.  
  
> [!NOTE]
>  Derlemeyle ilgili görevler için devenv yerine MSBuild kullanmak artık önerilir. Daha fazla bilgi için [komut satırı başvurusu](../../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Devenv kullanmak için bir yönetici çalıştırmalısınız [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) ve [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) anahtarlar.  
  
## <a name="devenv-switch-syntax"></a>Devenv anahtarı sözdizimi  
 Varsayılan olarak, devenv komutları anahtarları devenv.com yardımcı programı geçirin.  
  
 Devenv.com yardımcı programı aracılığıyla standart sistem akışları çıkış teslimini gibi sağlar `stdout` ve `stderr`ve bu çıktı, örneğin, bir .txt dosyasına yakaladığında uygun g/ç yönlendirmesi belirler. Bunun yerine ile başlayan komutlar `devenv.exe` aynı anahtarlar kullanabilirsiniz, ancak bunları devenv.com yardımcı programı atlayarak devenv.exe program gönderir.  
  
 Sözdizimi kurallarını için `devenv` anahtarları benzer diğer DOS komut satırı yardımcı programları için olanlar. Aşağıdaki sözdizimi kurallarını tümüne uygula `devenv` anahtarlar ve bunların bağımsız değişkenleri:  
  
-   İle başlayan komutlar `devenv`.  
  
-   Anahtarlar büyük küçük harfe duyarlı değildir.  
  
-   Bir çözüm veya proje belirtirken, ilk bağımsız değişken çözüm dosyası veya dosya yolu da dahil olmak üzere proje dosyasının adıdır.  
  
-   İlk bağımsız değişken bir çözüm veya proje değil bir dosya ise, bu dosyayı IDE yeni bir örneğini uygun düzenleyicisinde açılır.  
  
-   Bir proje dosyası adı bir çözüm dosyası adı yerine sağladığında bir `devenv` komut aynı ada sahip bir çözüm dosyası için proje dosyasının üst klasörü arar. Örneğin, komut `devenv /build myproject1.vbproj` üst klasör için "myproject1.sln" adlı bir çözüm dosyası arar.  
  
    > [!NOTE]
    >  Bu projeye başvuran bir ve yalnızca bir çözüm dosyası, kendi üst klasörde bulunmalıdır. Üst klasör bu projeye başvuran hiçbir çözüm dosyasını içeren ya da üst klasör ona başvuran iki veya daha fazla çözüm dosyası içeriyorsa, bir geçici çözüm dosyası oluşturulur, bu proje için adı ve başvurduğu.  
  
-   Dosya yolları ve dosya adı boşluklar, bunları çift tırnak içine almalısınız (""). Örneğin, "c:\project bir\\".  
  
-   Anahtarlar ve bağımsız değişkenler aynı satırda arasında bir boşluk karakteri Ekle. Örneğin, komut **devenv/log çýktý.txt** IDE açılır ve tüm bilgilerini günlüğe kaydetme oturumu için için çýktý.txt çıkarır.  
  
-   Desen eşleştirme sözdizimi kullanamazsınız `devenv` komutları.  
  
## <a name="devenv-switches"></a>Devenv anahtarları  
 IDE görüntülemek ve açıklandığı gibi görev gerçekleştirmek için aşağıdaki komut satırı anahtarları kullanın.  
  
|Komut satırı anahtarı|Açıklama|  
|-------------------------|-----------------|  
|[/ Komut (devenv.exe)](../../ide/reference/command-devenv-exe.md)|IDE'yi başlatır ve belirtilen komutu yürütür.|  
|[/ DebugExe (devenv.exe)](../../ide/reference/debugexe-devenv-exe.md)|Yükleri bir [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] hata ayıklayıcının denetiminin altında yürütülebilir. Bu anahtar için kullanılabilir değil [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../includes/csprcs-md.md)] yürütülebilir. Daha fazla bilgi için [otomatik olarak hata ayıklayıcıda bir işlem başlatmak](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).|  
|[/ LCID (devenv.exe)](../../ide/reference/lcid-devenv-exe.md) veya `/l`|IDE için varsayılan dili ayarlar. Belirtilen dil Visual Studio yüklemenizde dahil edilmemişse, bu ayar yoksayılır.|  
|[/ Log (devenv.exe)](../../ide/reference/log-devenv-exe.md)|Başlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ve tüm etkinlik günlük dosyasına kaydeder.|  
|[/ Çalıştırın (devenv.exe)](../../ide/reference/run-devenv-exe.md) veya `/r`|Derler ve belirtilen çözüm çalıştırır.|  
|[/ Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)|Derler ve belirtilen çözüm çalıştırır, çözüm çalıştırılır ve çözüm çalışması bittikten sonra IDE'yi kapatır, IDE'nin en aza indirir.|  
|[/ UseEnv (devenv.exe)](../../ide/reference/useenv-devenv-exe.md)|YOL, Ekle ve kitaplığı ortam değişkenlerini kullanmak IDE neden [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] VC ++ dizinleri kısmında belirtilen ayarlara yerine derleme **projeleri** seçeneklerini **seçenekleri** iletişim kutusu. Daha fazla bilgi için [komut satırı derlemeleri için yolu ve ortam değişkenlerini ayarlama](http://msdn.microsoft.com/library/99389528-deb5-43b9-b99a-03c8773ebaf4)|  
|[/ Düzenle (devenv.exe)](../../ide/reference/edit-devenv-exe.md)|Belirtilen dosyalar, bu uygulamanın çalışan bir örneğini açar. Çalışan örnek yoksa varsa, yeni bir örneği bir Basitleştirilmiş pencere düzeni ile başlar.|  
|[/ ResetAddin (devenv.exe)](../../ide/reference/resetaddin-devenv-exe.md)|Belirtilen eklenti yüklemeden Visual Studio IDE bir örneğini başlatır.|  
|[/ SafeMode (devenv.exe)](../../ide/reference/safemode-devenv-exe.md)|Başlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] güvenli modda ve yalnızca varsayılan ortama ve hizmetler yükler ve üçüncü taraf paketi sürümlerini birlikte gönderilir.|  
|[/ ResetSkipPkgs (devenv.exe)](../../ide/reference/resetskippkgs-devenv-exe.md)|Sorun VSPackages yüklenmesini engellemek istediğiniz kullanıcılar tarafından Vspackages'a eklenmiş tüm SkipLoading etiketlerini temizler.|  
|[/ Kurulum (devenv.exe)](../../ide/reference/setup-devenv-exe.md)|Menüleri, araç çubukları ve komut grupları, kullanılabilir tüm VSPackages tanımlayan kaynak meta verileri birleştirmek için Visual Studio zorlar.|  
  
 Aşağıdaki komut satırı anahtarları açıklandığı gibi görev gerçekleştirmek için kullanın. Bu komut satırı anahtarları IDE görüntülemez.  
  
|Komut satırı anahtarı|Açıklama|  
|-------------------------|-----------------|  
|[/? (devenv.exe)](../../ide/reference/q-devenv-exe.md)|Devenv anahtarları için yardımı görüntüler **komut istemi penceresi**.<br /><br /> **Devenv /?**|  
|[/ Derleme (devenv.exe)](../../ide/reference/build-devenv-exe.md)|Belirtilen çözüm veya projeyi yapılandırmasına göre belirtilen çözümü derler.<br /><br /> **Myproj.csproj. / Build Devenv**|  
|[/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)|Kaynak dosyaları etkilemeden oluşturma komutu tarafından oluşturulan tüm dosyaları siler.<br /><br /> **Devenv myproj.csproj / Temizle**|  
|[/ (Devenv.exe) dağıtma](../../ide/reference/deploy-devenv-exe.md)|Çözümleri yapılandırmasına bir dağıtım için gerekli dosyaları ile birlikte çözümü derler.<br /><br /> **Devenv myproj.csproj / dağıtma**|  
|[/Diff](../../ide/reference/diff.md)|İki dosyayı karşılaştırır.  Dört parametreleri: Kaynakdosya, Hedefdosya, SourceDisplayName(optional),TargetDisplayName(optional) alır.|  
|[/ Installvstemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md)|Bulunan proje veya öğe şablonları kaydeder  *\<VisualStudioInstallDir >* \Common7\IDE\ProjectTemplates veya  *\<VisualStudioInstallDir >* \Common7 \IDE\ItemTemplates aracılığıyla erişilebilir olacak şekilde **yeni proje** ve **Yeni Öğe Ekle** iletişim kutuları.<br /><br /> **Devenv /InstallVSTemplates**|  
|[/ (Devenv.exe out)](../../ide/reference/out-devenv-exe.md)|Oluşturma sırasında hatalar almak için bir dosya belirtmenizi sağlar.<br /><br /> **Myproj.csproj. / Build Devenv/out log.txt**|  
|[/ Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)|Projeyi oluşturmak için temizlemek veya dağıtmak. Yalnızca / Build ayrıca sağladıysanız bu anahtarı kullanabilirsiniz. / rebuild, / clean veya / deploy anahtarı.|  
|[/ ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)|Derleme veya dağıtım için proje yapılandırmasını belirtir. Yalnızca/Project anahtarı da sağladıysanız bu anahtarı kullanabilirsiniz.|  
|[/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)|Temizler ve daha sonra belirtilen çözüm veya projeyi yapılandırmasına göre belirtilen çözümü derler.|  
|[/ ResetSettings (devenv.exe)](../../ide/reference/resetsettings-devenv-exe.md)|Visual Studio varsayılan ayarlarına geri yükler. İsteğe bağlı olarak belirtilen .vssettings dosya ayarlarını sıfırlar.|  
|[/ Updateconfiguration (devenv.exe)](../../ide/reference/updateconfiguration-devenv-exe.md)|Bildirir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] birleştirilecek [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sistem ve MEF paketleri önbelleğe herhangi bir değişiklik.|  
|[/ Yükseltme (devenv.exe)](../../ide/reference/upgrade-devenv-exe.md)|Belirtilen çözüm dosyasını ve tüm proje dosyaları ya da belirtilen proje dosyası, geçerli yükseltme [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bu dosyaların biçimleri.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)



