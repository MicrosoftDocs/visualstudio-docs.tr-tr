---
title: 'Nasıl yapılır: kaynak denetimi eklentisi yükleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3487c796661a8194b9c920f43bae9df87f1ba57d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950270"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Nasıl yapılır: kaynak denetimi eklentisi yükleme
Kaynak Denetimi Eklentisi oluşturma üç adımdan oluşur:  

1. Bu belge kaynak denetimi eklentisi API başvuru bölümünde tanımlanan işlevleri ile bir dll dosyası oluşturun.  

2. Kaynak Denetimi Eklentisi API tarafından tanımlanan işlevleri uygulayın. Zaman [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] çağrıları, eklentiden kullanılabilir duruma arabirimleri ve iletişim kutuları.  

3. DLL uygun kayıt defteri girişlerini yaparak kaydedin.  

## <a name="integration-with-visual-studio"></a>Visual Studio ile Tümleştirme  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kaynak denetimi için kaynak denetimi eklentisi API uygun eklentileri destekler.  

### <a name="register-the-source-control-plug-in"></a>Kaynak Denetimi Eklentisi kaydetme  
 Çalışan bir tümleşik geliştirme ortamı (IDE), kaynak denetim sistemine çağrı yapmadan önce ilk kaynak bulmalıdır API dışarı aktarır eklentisi DLL'sini denetim.  

#### <a name="to-register-the-source-control-plug-in-dll"></a>Kaynak Denetimi Eklentisi DLL'sini kaydetmek için  

1. Altında iki giriş eklemek **HKEY_LOCAL_MACHINE** anahtarını **yazılım** , şirket adı alt belirten alt ürün adı alt anahtarı tarafından izlenen. Desen **HKEY_LOCAL_MACHINE\SOFTWARE\\\<şirket adı >\\\<ürün adı >\\\<Giriş >**  =  *değer*. İki girişin her zaman adlı **SCCServerName** ve **SCCServerPath**. Her bir normal bir dizedir.  

    Örneğin, Microsoft şirket adınızı ise ve kaynak denetimi ürününüzü SourceSafe adlandırılır, ardından bu kayıt defteri yolu olacaktır **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe**. Bu alt anahtar, ilk girişin **SCCServerName**, ürününüzü adlandırma kullanıcı tarafından okunabilen bir dize. İkinci girdi **SCCServerPath**, kaynak tam yolunu kontrol IDE bağlanması gereken eklentisi DLL'sini olduğu. Aşağıdaki örnek kayıt defteri girdileri sağlar:  

   |Örnek kayıt defteri girişi|Örnek değer|  
   |---------------------------|------------------|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|  

   > [!NOTE]
   >  SCCServerPath SourceSafe eklentisinde tam yoludur. Kaynak Denetimi Eklentisi, aynı kayıt defteri girişi yolları ancak farklı şirket ve ürün adlarını kullanır.  

2. Aşağıdaki isteğe bağlı bir kayıt defteri girdilerini, kaynak denetimi eklentiniz davranışını değiştirmek için kullanılabilir. Bu girişler aynı alt Git **SccServerName** ve **SccServerPath**.  

   - **HideInVisualStudioregistry** giriş denetimi Tak-açma görünmesini kaynağınızı istemiyorsanız kullanılabilir **Eklenti Seçimi** listesi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Bu giriş, kaynak denetimi eklentisi otomatik geçiş da etkiler. Bu giriş için bir olası kullanım kaynak denetimi eklentiniz yerini alan bir kaynak denetim paketi sağladığınız ancak kullanıcı kaynak denetimi Eklentisi Kaynak denetimi pakete geçiş yapma kolaylaştırmak istiyorsanız ' dir. Kaynak Denetim paketi yüklendiğinde, eklenti gizler. Bu kayıt defteri girdisi ayarlar.  

      **HideInVisualStudio** ayarlanır ve bir DWORD değeri *1* eklenti gizlemek için veya *0* eklenti gösterilecek. Kayıt defteri girişini görünmüyorsa, varsayılan davranışı eklenti göstermektir.  

   - **DisableSccManager** kayıt defteri girişi, devre dışı bırakmak veya gizlemek için kullanılabilir **başlatma \<kaynak denetim sunucusuna >** normalde altında görüntülenen menü seçeneği **dosya**  >  **Kaynak denetimi** alt. Bu menü seçme seçeneği çağrıları [SccRunScc](../../extensibility/sccrunscc-function.md) işlevi. Kaynak Denetimi Eklentisi bir dış program desteklemiyor olabilir ve bu nedenle, hatta Gizle veya devre dışı bırakmak isteyebilirsiniz **başlatma** menü seçeneği.  

      **DisableSccManager** ayarlanır ve bir DWORD değeri *0* etkinleştirmek için **başlatma \<kaynak denetim sunucusuna >** ayarlamak, menü seçeneği *1* için menü seçeneği devre dışı bırakın ve kümesine *2* menü seçeneğini gizleme. Bu kayıt defteri girdisi görünmüyorsa, menü seçeneği varsayılan davranışı göstermektir.  

   | Örnek kayıt defteri girişi | Örnek değer |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1. |
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1. |


3. Alt ekleyin **SourceCodeControlProvider**altında **HKEY_LOCAL_MACHINE** anahtarını **yazılım** alt.  

    Bu alt anahtar, kayıt defteri girişini altında **ProviderRegKey** adım 1'kayıt defterinde yerleştirilen alt anahtarını temsil eden bir dize olarak ayarlanmış. Desen **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey** = *yazılım\\< şirket adı\>\\< ürün adı \>*.  

    Örnek içerik için bu alt anahtar verilmiştir.  

   |Kayıt defteri girdisi|Örnek değer|  
   |--------------------|------------------|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  

   > [!NOTE]
   >  Kaynak Denetimi Eklentisi giriş adları ve aynı alt kullanır ancak değeri farklı olacaktır.  

4. Adlı bir alt anahtarını oluşturmak **InstalledSCCProviders** altında **SourceCodeControlProvider** alt anahtarını ve ardından bu alt anahtarı altında bir girdi yerleştirebilirsiniz.  

    Bu giriş adı sağlayıcı (aynı SCCServerName girişi için belirtilen değer) kullanıcı tarafından okunabilen adıdır ve değeri, bir kez daha, 1. adımda oluşturduğunuz alt ise. Desen **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\<display name>** = *yazılım\\< şirket adı\> \\< ürün adı\>*.  

    Örneğin:  

   |Örnek kayıt defteri girişi|Örnek değer|  
   |---------------------------|------------------|  
   |Visual SourceSafe HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft|SOFTWARE\Microsoft\SourceSafe|  

   > [!NOTE]
   >  Birden çok kaynak denetimi bu şekilde kayıtlı eklentileri olabilir. Bu, nasıl [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tüm yüklü kaynak denetimi eklentisi API tabanlı eklentiler bulur.  

## <a name="how-an-ide-locates-the-dll"></a>Bir IDE DLL nasıl bulur  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE olan iki kaynak bulma yolları denetleyen eklentisi DLL'sini:  

- Varsayılan kaynak denetimi eklentisi bulmak ve sessiz bir şekilde bağlanabilir.  

- Tüm kayıtlı kaynak denetimi eklentileri, bir kullanıcının seçtiği bulun.  

  İlk yol DLL bulmak için altında IDE arar **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider** giriş için alt anahtar **ProviderRegKey**. Bu giriş değerini başka bir alt anahtarına işaret eder. IDE ardından adlı bir giriş için görünür **SccServerPath** altında bu ikinci alt **HKEY_LOCAL_MACHINE**. Bu giriş değerini IDE DLL'ye işaret eder.  

> [!NOTE]
>  IDE göreli yolları DLL'leri yüklenmez (örneğin, *.\NewProvider.DLL*). DLL tam yolun belirtilmesi gerekir (örneğin, *c:\Providers\NewProvider.DLL*). Bu, yetkisiz veya başkasının kimliğine bürünülerek gerçekleştirilen eklentisi DLL'sini yüklemesini engelleyerek IDE güvenliğini güçlendirir.  

 İkinci bir yolla DLL bulmak için altında IDE arar **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** tüm girişleri için alt anahtar. Her girişin bir ada ve değere sahip. IDE, kullanıcıya bu adlarının bir listesini görüntüler. Kullanıcı adları seçtiğinde, IDE bir alt anahtarına işaret eden seçilen adı değeri bulur. Adlı bir giriş için IDE arar **SccServerPath** altında bu alt **HKEY_LOCAL_MACHINE**. Bu giriş değerini doğru DLL'ye IDE işaret eder.  

 Kaynak Denetimi Eklentisi DLL bulma her iki yönde desteklemesi gerekir ve sonuç olarak, ayarlar **ProviderRegKey**, önceki bir ayarı üzerine. Daha da önemlisi, kendisini listesine eklemelisiniz **InstalledSccProviders** kullanıcı kullanmak için hangi kaynak denetimi eklentisi, bir seçim olabilir.  

> [!NOTE]
>  Çünkü **HKEY_LOCAL_MACHINE** anahtarı kullanılır, yalnızca bir kaynak denetimi eklentisi, varsayılan kaynak denetimi eklentisi belirli bir makinede olarak kaydedilebilir (ancak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanıcılara hangi kaynak denetimi eklentisi belirlemek Bunlar aslında belirli bir çözüm için kullanmak istediğiniz). Yükleme işlemi sırasında kaynak denetimi eklentisi zaten ayarlanmış olup olmadığını denetleyin; Bu durumda, kullanıcı yeni kaynak denetimi eklentisi varsayılan olarak yüklenen ayarlama gerekip gerekmediğini sorun. Kaldırma sırasında tüm kaynak denetimi eklentilerini için ortak olan diğer kayıt defteri alt anahtarları kaldırmayın **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider**; yalnızca belirli, SCC alt kaldırın.  

## <a name="how-the-ide-detects-version-1213-support"></a>IDE sürüm 1.2/1.3 desteği nasıl algılar  
 Nasıl mu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir eklentiyi destekler kaynak denetimi eklentisi API sürümü 1.2 ve 1.3 işlevsellik olup olmadığını Algıla? Gelişmiş beceri bildirmek için kaynak denetimi eklentisi karşılık gelen işlev uygulamanız gerekir:  

 İlk olarak, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] arama döndürülen değer denetler [SccGetVersion](../../extensibility/sccgetversion-function.md). Büyüktür veya eşittir 1.2 olmalıdır.  

 Ardından, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] belirli yeni özelliği inceleyerek desteklenip desteklenmediğini belirler `lpSccCaps` bağımsız değişkenine [Sccınitialize](../../extensibility/sccinitialize-function.md).  

 Bu koşulların her ikisi karşılanırsa 1.2 ve 1.3 sürümlerinde desteklenen yeni işlevler çağrılabilir.  

## <a name="see-also"></a>Ayrıca bkz.  
 [Kaynak denetimi eklentileri ile çalışmaya başlama](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)