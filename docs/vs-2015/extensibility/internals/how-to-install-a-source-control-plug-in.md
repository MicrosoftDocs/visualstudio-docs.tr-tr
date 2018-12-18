---
title: 'Nasıl yapılır: kaynak denetimi eklentisi yükleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5f151653387c95e77d775bfc9f37cbdfb9f824e7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741630"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Nasıl yapılır: kaynak denetimi eklentisi yükleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kaynak Denetimi Eklentisi oluşturma üç adımdan oluşur:  
  
1.  Bu belge kaynak denetimi eklentisi API başvuru bölümünde tanımlanan işlevleri ile bir dll dosyası oluşturun.  
  
2.  Kaynak Denetimi Eklentisi API tarafından tanımlanan işlevleri uygulayın. Zaman [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] çağrıları, eklentiden kullanılabilir duruma arabirimleri ve iletişim kutuları.  
  
3.  DLL uygun kayıt defteri girişlerini yaparak kaydedin.  
  
## <a name="integration-with-visual-studio"></a>Visual Studio ile Tümleştirme  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Kaynak denetimi için kaynak denetimi eklentisi API uygun eklentileri destekler.  
  
### <a name="registering-the-source-control-plug-in"></a>Kaynak Denetimi Eklentisi kaydediliyor  
 Çalışan bir tümleşik geliştirme ortamı (IDE), kaynak denetim sistemine çağrı yapmadan önce ilk kaynak bulmalıdır API dışarı aktarır eklentisi DLL'sini denetim.  
  
##### <a name="to-register-the-source-control-plug-in-dll"></a>Kaynak Denetimi Eklentisi DLL'sini kaydetmek için  
  
1.  Ürün adı alt anahtarı tarafından izlenen, şirket adı alt belirten yazılım alt HKEY_LOCAL_MACHINE anahtarı altında iki giriş ekleyin. HKEY_LOCAL_MACHINE\Software desendir\\ *[CompanyName]*\\ *[Ürün adı]*\\ *[Giriş]* = değer. İki girişin her zaman SCCServerName ve SCCServerPath çağrılır. Her bir normal bir dizedir.  
  
     Örneğin, şirket adınız, Microsoft ve kaynak denetimi ürününüzü ise SourceSafe, bu kayıt defteri yolu HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe şu şekilde olacaktır adı verilir. Bu alt anahtar ilk girişi SCCServerName, ürününüzü adlandırma bir kullanıcı tarafından okunabilen bir dizedir. İkinci girdi, SCCServerPath, kaynak tam yolunu kontrol IDE bağlanması gereken eklentisi DLL ' dir. Aşağıdaki örnek kayıt defteri girdileri sağlar:  
  
    |Örnek kayıt defteri girişi|Örnek değer|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|c:\vss\win32\ssscc.dll|  
  
    > [!NOTE]
    >  SCCServerPath SourceSafe eklentisinde tam yoludur. Kaynak Denetimi Eklentisi, aynı kayıt defteri girişi yolları ancak farklı şirket ve ürün adlarını kullanır.  
  
2.  Aşağıdaki isteğe bağlı bir kayıt defteri girdilerini, kaynak denetimi eklentiniz davranışını değiştirmek için kullanılabilir. Bu girişler SccServerName ve SccServerPath olarak aynı alt gidin.  
  
    -   Kaynak denetimi-Tak-eklentisi seçim listesinde görünmesini istediğiniz değil HideInVisualStudioregistry giriş kullanılabilir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Bu giriş, kaynak denetimi eklentisi otomatik geçiş da etkiler. Bu giriş için bir olası kullanım kaynak denetimi eklentiniz yerini alan bir kaynak denetim paketi sağladığınız ancak kullanıcı kaynak denetimi Eklentisi Kaynak denetimi pakete geçiş yapma kolaylaştırmak istiyorsanız ' dir. Kaynak Denetim paketi yüklendiğinde, eklenti gizler. Bu kayıt defteri girdisi ayarlar.  
  
         HideInVisualStudio bir DWORD değeri ve eklenti gizlemek için 1 veya eklenti göstermek için 0 olarak ayarlanır. Kayıt defteri girişini görünmüyorsa, varsayılan davranışı eklenti göstermektir.  
  
    -   DisableSccManager kayıt defteri girdisini devre dışı bırakmak veya gizlemek için kullanılabilir **başlatma \<kaynak denetim sunucusuna >** normalde altında görüntülenen menü seçeneği **dosya**  ->   **Kaynak denetimi** alt menü. Bu menü seçme seçeneği çağrıları [SccRunScc](../../extensibility/sccrunscc-function.md) işlevi. Kaynak Denetimi Eklentisi bir dış program desteklemiyor olabilir ve bu nedenle, hatta Gizle veya devre dışı bırakmak isteyebilirsiniz **başlatma** menü seçeneği.  
  
         DisableSccManager ayarlanmadı DWORD değerini 0 olarak etkinleştirmek için **başlatma \<kaynak denetim sunucusuna >** menü seçeneğini menü seçeneği devre dışı bırakmak için 1 olarak ayarlayın ve menü seçeneğini gizleme 2 olarak ayarlayın. Bu kayıt defteri girdisi görünmüyorsa, menü seçeneği varsayılan davranışı göstermektir.  
  
    |Örnek kayıt defteri girişi|Örnek değer|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio|1.|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager|1.|  
  
3.  Alt anahtar SourceCodeControlProvider, yazılım alt HKEY_LOCAL_MACHINE anahtarı altında ekleyin.  
  
     Bu alt anahtarı kayıt defteri girişini 1. adım kayıt defterinde yerleştirilen alt anahtarını temsil eden bir dize ProviderRegKey ayarlanır. HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey desendir yazılım =\\ *[CompanyName]*\\ *[Ürün adı]*.  
  
     Örnek içerik için bu alt anahtar verilmiştir.  
  
    |Kayıt defteri girdisi|Örnek değer|  
    |--------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Kaynak Denetimi Eklentisi giriş adları ve aynı alt kullanır ancak değeri farklı olacaktır.  
  
4.  InstalledSCCProviders SourceCodeControlProvider alt anahtarı altında adlı bir alt anahtarını oluşturmak ve ardından bu alt anahtarı altında bir girdi yerleştirebilirsiniz.  
  
     Bu giriş adı sağlayıcı (aynı SCCServerName girişi için belirtilen değer) kullanıcı tarafından okunabilen adıdır ve değeri, bir kez daha, 1. adımda oluşturduğunuz alt ise. HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders desendir\\ *[görünen adı]* yazılım =\\ *[CompanyName]* \\ *[Ürün adı]*.  
  
     Örneğin:  
  
    |Örnek kayıt defteri girişi|Örnek değer|  
    |---------------------------|------------------|  
    |Visual SourceSafe HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Birden çok kaynak denetimi bu şekilde kayıtlı eklentileri olabilir. Bu, nasıl [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tüm yüklü kaynak denetimi eklentisi API tabanlı eklentiler bulur.  
  
## <a name="how-an-ide-locates-the-dll"></a>Bir IDE DLL nasıl bulur  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE olan iki kaynak bulma yolları denetleyen eklentisi DLL'sini:  
  
- Varsayılan kaynak denetimi eklentisi bulmak ve sessiz bir şekilde bağlanabilir.  
  
- Tüm kayıtlı kaynak denetimi eklentileri, bir kullanıcının seçtiği bulun.  
  
  İlk yol DLL bulmak için IDE ProviderRegKey girdisiyle HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider alt anahtarı altında arar. Bu giriş değerini başka bir alt anahtarına işaret eder. IDE ardından bu ikinci subkey under HKEY_LOCAL_MACHINE dizinine SccServerPath adlı bir giriş arar. Bu giriş değerini IDE DLL'ye işaret eder.  
  
> [!NOTE]
>  IDE göreli yollar (örneğin,.\NewProvider.DLL) DLL'leri yüklenmez. DLL tam yolun belirtilmesi gerekir (örneğin, c:\Providers\NewProvider.DLL). Bu, yetkisiz veya başkasının kimliğine bürünülerek gerçekleştirilen eklentisi DLL'sini yüklemesini engelleyerek IDE güvenliğini güçlendirir.  
  
 İkinci bir yolla DLL bulmak için tüm girişleri için HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders alt anahtarı altında IDE arar<em>.</em> Her girişin bir ada ve değere sahip. IDE, kullanıcıya bu adlarının bir listesini görüntüler<em>.</em> Kullanıcı adları seçtiğinde, IDE bir alt anahtarına işaret eden seçilen adı değeri bulur. Bu subkey under HKEY_LOCAL_MACHINE dizinine SccServerPath adlı bir giriş IDE arar. Bu giriş değerini doğru DLL'ye IDE işaret eder.  
  
 DLL bulma her iki şekilde destek ve sonuç olarak, önceki bir ayarı üzerine ProviderRegKey, ayarlamak, kaynak denetimi eklentisi gerekir. Böylece kullanıcı kullanmak için hangi kaynak denetimi eklentisi seçeneği daha da önemlisi, onu kendisini InstalledSccProviders listesine eklemeniz gerekir.  
  
> [!NOTE]
>  Varsayılan kaynak denetimi eklentisi belirli bir makinede olarak HKEY_LOCAL_MACHINE anahtarı kullanıldığından yalnızca bir kaynak denetimi eklentisi kaydedilebilir (ancak [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kullanıcılara istedikleri gerçekten kullanmak için hangi kaynak denetimi eklentisini belirlemek bir belirli çözüm). Yükleme işlemi sırasında kaynak denetimi eklentisi zaten ayarlanmış olup olmadığını denetleyin; Bu durumda, kullanıcı yeni kaynak denetimi eklentisi varsayılan olarak yüklenen ayarlama gerekip gerekmediğini sorun. Yüklemeyi sırasında tüm kaynak denetimi eklentileri HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider içinde ortak olan diğer kayıt defteri alt anahtarları kaldırmayın; belirli, SCC alt kaldırın.  
  
## <a name="how-the-ide-detects-version-1213-support"></a>IDE sürüm 1.2/1.3 desteği nasıl algılar  
 Nasıl mu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bir eklentiyi destekler kaynak denetimi eklentisi API sürümü 1.2 ve 1.3 işlevsellik olup olmadığını Algıla? Gelişmiş beceri bildirmek için kaynak denetimi eklentisi karşılık gelen işlev uygulamanız gerekir.  
  
 İlk olarak, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] arama döndürülen değer denetler [SccGetVersion](../../extensibility/sccgetversion-function.md). Büyüktür veya eşittir 1.2 olmalıdır.  
  
 Ardından, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] belirli yeni özelliği inceleyerek desteklenip desteklenmediğini belirler `lpSccCaps` bağımsız değişkenine [Sccınitialize](../../extensibility/sccinitialize-function.md).  
  
 Bu koşulların her ikisi karşılanırsa 1.2 ve 1.3 sürümlerinde desteklenen yeni işlevler çağrılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

