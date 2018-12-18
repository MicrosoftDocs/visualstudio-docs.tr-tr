---
title: Özel projeler sürüm ile uyumlu hale getirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5233d3ff-6e89-4401-b449-51b4686becca
caps.latest.revision: 33
manager: douge
ms.openlocfilehash: 038f478d6a8dbdd3dc050b6db85af82be377c325
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833011"
---
# <a name="making-custom-projects-version-aware"></a>Özel projeler sürüm ile uyumlu hale getirme
Özel proje sisteminizi projeleri Visual Studio birden çok sürümünü yüklemek için bu türdeki izin verebilirsiniz. Bu tür projeleri, Visual Studio'nun bir önceki sürümünde yüklenmesini de engelleyebilirsiniz. Proje Proje Onar, dönüştürme ya da kullanımdan kaldırma gerektiriyor durumunda sonraki bir sürüme kendisini tanımlamak de etkinleştirebilirsiniz.  
  
## <a name="allowing-projects-to-load-in-multiple-versions"></a>Birden çok sürümü projelere yük izin verme  
 Kullanılarak oluşturulmuş çoğu proje değiştirebileceğiniz [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 veya daha sonra birden çok sürümlerinde çalışır.  
  
 Visual Studio bir proje yüklenmeden önce çağıran <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> proje yükseltilebilir olup olmadığını belirlemek için yöntemi. Proje yükseltme yaptıysanız `UpgradeProject_CheckOnly` yöntemi, bir sonraki çağrısına neden olan bir bayrak ayarlar <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> projeyi yükseltmek için yöntemi. Uyumsuz projeleri yükseltebilmeniz için `UpgradeProject_CheckOnly` ilk proje uyumluluğu için önceki bölümde açıklanan şekilde işaretlemeniz gerekir.  
  
 Bir proje sistemi yazarı, uygulama `UpgradeProject_CheckOnly` (gelen `IVsProjectUpgradeViaFactory4` arabirimi) bir yükseltme denetimi ile kullanıcılar, proje sistemi sağlamak için. Kullanıcılar bir projeyi açtığınızda, bu yöntem, yüklenmeden önce bir proje onarıldı olup olmadığını belirlemek için çağrılır. Olası yükseltme gereksinimleri listelenen `VSPUVF_REPAIRFLAGS`, ve bunlar aşağıdaki olasılıkları içerir:  
  
1.  `SPUVF_PROJECT_NOREPAIR`: Hiçbir onarım gerektirir.  
  
2.  `VSPUVF_PROJECT_SAFEREPAIR`: Projenin daha önceki bir sürümü ile uyumlu sahip olabileceğiniz önceki ürün sürümleriyle sorunlarla olmadan yapar.  
  
3.  `VSPUVF_PROJECT_UNSAFEREPAIR`: Bazı karşılaşmış sorunları riskini önceki ürün sürümleriyle geriye dönük uyumlu ancak proje yapar. Örneğin, proje üzerinde farklı SDK sürümleri bağımlı olduğu uyumlu olmayacaktır.  
  
4.  `VSPUVF_PROJECT_ONEWAYUPGRADE`: Projenin daha önceki bir sürümü ile uyumsuz hale getiriyor.  
  
5.  `VSPUVF_PROJECT_INCOMPATIBLE`: Bu projenin geçerli sürümü desteklemediğini gösterir.  
  
6.  `VSPUVF_PROJECT_DEPRECATED`: Bu proje artık desteklenip desteklenmediğini belirtir.  
  
> [!NOTE]
>  Bunları ayarladığınızda, Karışıklığı önlemek için yükseltme bayraklarını birleştirmek yok. Örneğin, belirsiz bir yükseltme durumu gibi oluşturmayın `VSPUVF_PROJECT_SAFEREPAIR | VSPUVF_PROJECT_DEPRECATED`.  
  
 Proje Özellikleri işlevi uygulamak `UpgradeProjectFlavor_CheckOnly` gelen `IVsProjectFlavorUpgradeViaFactory2` arabirimi. İş, bu işlev yapmak için `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly` uygulamayı daha önce bahsedilen, çağırması gerekir. Bu çağrı, Visual Basic veya C# temel proje sistemde zaten uygulanır. Bu işlev etkisini de ne temel proje sistemi belirledi ek olarak, bir proje yükseltme gereksinimlerini belirlemek proje özellikleri sağlar. En önemlisi, iki gereksinimden uyumluluk iletişim kutusunu gösterir.  
  
 Visual Studio bir yükseltme denetimi gerçekleştirdiğinde, Visual Studio'nun önceki sürümlerinde olduğu gibi bir NULL değer yerine bir Günlükçü sağlar. Günlükçü proje sistemleri sağlar ve yardımcı olabilecek ek bilgileri sağlamak için özellikleri düzgün şekilde eski projeleriniz için gerekli değişiklikleri yapısını anlayın. İletişim kutularını kullanmak yerine daha fazla bilgi sağlamak için Günlükçü kullanmanızı öneririz. Daha fazla bilgi için [yükseltme Günlükçü](../misc/making-custom-projects-version-aware.md#BKMK_UpgradeLogger) bu konuda.  
  
 Yönetilen uygulamalar için proje yükseltme arabirimleri Microsoft.VisualStudio.Shell.Interop.11.0.dll birlikte çalışma derlemesi içinde kullanılabilir.  
  
 `UpgradeProject` Yöntemi, yaptığı değişiklikleri projeyi Visual Studio'nun önceki bir sürümünde yüklenmesini önlemeyeceğini belirleyebilir. Bu durumda, yöntem proje uyumsuz işaretler. Nasıl bir proje olarak uyumsuz işaretlenmiş anlamak için bkz [proje uyumsuz olarak işaretleme](../misc/making-custom-projects-version-aware.md#BKMK_Incompat) bu konuda daha önce. Bu iletişim kutusu görüntülendikten sonra projeyi uyumsuz olarak yöntemi çağırarak işaretlemek, öneririz `IVsAppCompat.BreakAssetCompatibility` ilk çağırmak yerine doğrudan `IVsAppCompat.AskForUserConsentToBreakAssetCompat` yöntemi gerekmediğinden iletişim kutusunda iki kez görünür.  
  
 Yardımcı uyumluluğu kullanıcı deneyimini özetlemek için bir örnek aşağıda verilmiştir. Bir projeyi önceki bir sürümde oluşturulmuş ve geçerli sürüme yükseltme gerekli olduğunu belirler, Visual Studio değişiklik yapma iznine için kullanıcıdan bir iletişim kutusu görüntülenir. Kullanıcı kabul ederse projeyi değiştirilebilir ve ardından yüklendi. Çözüm ardından kapalı ve önceki sürümde açılamaz bir-way yükseltilen proje uyumsuz ve yüklü değil. Proje (yükseltme) yerine bir onarım yalnızca gerekli, onarılan proje yine de her iki sürümde de açılır.  
  
##  <a name="BKMK_Incompat"></a> Bir proje uyumsuz olarak işaretleme  
 Bir proje, Visual Studio'nun önceki sürümleriyle uyumsuz olarak işaretleyebilirsiniz.  Örneğin, bir .NET Framework 4.5 özelliği kullanan bir proje oluşturduğunuzu varsayalım. Bu proje oluşturulamıyor çünkü [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], bu sürümü yüklemek çalışmasını engellemek için uyumsuz olarak işaretler.  
  
 Proje uyumsuz olarak işaretlemek için uyumsuz özellik ekler bileşen sorumludur. Bileşen erişiminiz olmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> projelerine temsil eden arabirim.  
  
#### <a name="to-mark-a-project-as-incompatible"></a>Bir proje uyumsuz işaretlemek için  
  
1.  Bileşeninde almak bir `IVsAppCompat` küresel hizmet SVsSolution arabiriminden.  
  
     Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>.  
  
2.  Bileşen, çağrı `IVsAppCompat.AskForUserConsentToBreakAssetCompat`ve bir dizi geçirin `IVsHierarchy` projelerine temsil eden arabirim.  
  
     Bu yöntem, aşağıdaki imzası vardır:  
  
    ```  
    HRESULT AskForUserConsentToBreakAssetCompat([in] SAFEARRAY(IVsHierarchy*) sarrProjectHierarchies)  
  
    ```  
  
     Bu kod uygularsanız, bir proje uyumluluğu iletişim kutusu görünür. İletişim kutusu olacak kullanıcı için belirtilen tüm projeleri uyumsuz işaretlemek izin ister. Kullanıcı kabul ederse `AskForUserConsentToBreakAssetCompat` döndürür `S_OK`; Aksi takdirde `AskForUserConsentToBreakAssetCompat` döndürür `OLE_E_PROMPTSAVECANCELLED`.  
  
    > [!WARNING]
    >  En yaygın senaryolarda `IVsHierarchy` yalnızca bir öğe dizisi içerir.  
  
3.  Varsa `AskForUserConsentToBreakAssetCompat` döndürür `S_OK`, bileşen yapar veya uyumluluk kesme değişiklikleri kabul eder.  
  
4.  Bileşeninizin çağrısı `IVsAppCompat.BreakAssetCompatibility` uyumsuz olarak işaretlemek istediğiniz her proje için yöntemi. Bileşen parametresinin değeri ayarlayabilirsiniz `lpszMinimumVersion` Visual Studio kayıt defterinde geçerli sürüm dizesi aramak yerine belirli bir en düşük sürüm. Bu yaklaşım bileşen yanlışlıkla ne kayıt defterinde o anda göre daha yüksek bir değer gelecekte ayarının riskini en aza indirir. Bu daha yüksek bir değere ayarlandıysa, Visual Studio projesi açılamadı.  
  
     Bu yöntem, aşağıdaki imzası vardır:  
  
    ```  
    HRESULT BreakAssetCompatibility([in] IVsHierarchy * pProjHier), [in] LPCOLESTR lpszMinimumVersion);  
  
    ```  
  
     Bileşen ayarlarsa `lpszMinimumVersion` null, `BreakAssetCompatibility` yöntem çağrılarını `IVsAppCompat.GetCurrentDesignTimeCompatVersion` Visual Studio'nun geçerli sürümünü temsil eden bir dize elde etmek için yöntemi.  
  
     Bu yöntem, aşağıdaki imzası vardır:  
  
    ```  
    HRESULT GetCurrentDesignTimeCompatVersion([out] BSTR * pbstrCurrentDesignTimeCompatVersion)  
    ```  
  
     Daha sonra BreakAssetCompatibility yöntemi çağırır `IVsHierarchy.SetProperty` kök ayarlanacak yöntemi `VSHPROPID_MinimumDesignTimeCompatVersion` özelliği için önceki adımda elde edilen sürüm dizesi değeri.  
  
     Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  
  
> [!IMPORTANT]
>  Uygulamanız gereken `VSHPROPID_MinimumDesignTimeCompatVersion` proje uyumlu veya uyumsuz olarak işaretlemek için özellik. Örneğin, proje sistemi bir MSBuild proje dosyası kullanıyorsa, proje dosyasına ekleyin. bir `<MinimumVisualStudioVersion>` eşit karşılık gelen bir değere sahip özellik yapı `VSHPROPID_MinimumDesignTimeCompatVersion` özellik değeri.  
  
## <a name="detecting-whether-a-project-is-incompatible"></a>Uyumsuz algılama olup olmadığını bir proje olan  
 Geçerli Visual Studio sürümü ile uyumlu olan proje yüklenmesini tutulması gerekir. Ayrıca, uyumsuz olan proje yükseltme veya onarılamıyor. Bu nedenle, bir proje uyumluluğu için iki kez denetlenmesi gerekir: ilk bunu kabul edilir, yükseltme veya onarım ve saniye önce yüklendiği.  
  
 Proje uyumsuzluk algılamayı etkinleştirmek için uygulamanız gereken <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> yöntemleri. Bir proje uyumsuzsa `UpgradeProject_CheckOnly` başarı kodu döndürmelidir `VS_S_INCOMPATIBLEPROJECT`, ve `CreateProject` hata kodu döndürmesi gerekir `VS_E_INCOMPATIBLEPROJECT`. Projeler için uygulamanız gereken `IVsProjectFlavorUpgradeViaFactory2.UpgradeProjectFlavor_CheckOnly` yerine `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly`.  
  
 Proje sistemi, web, Office (VSTO), Silverlight veya üzerinde oluşturulmuş başka bir proje türü varsa çok olarak flavored olarak adlandırılır. Uygulama zaten daha eski proje sistemleri `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` ve markdown'lar zaten uygulayan proje sistemleri `IVsProjectFlavorUpgradeViaFactory.UpgradeProjectFlavor_CheckOnly` desteklemeye devam eder. Eski sürümü `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` aşağıdaki uygulama imzası:  
  
```  
IVsProjectUpgradeViaFactory::UpgradeProject_CheckOnly(  
  
/* [in] */ BSTR bstrFileName,  
/* [in] */ IVsUpgradeLogger *pLogger,  
/* [out] */ BOOL *pUpgradeRequired,  
/* [out] */ GUID *pguidNewProjectFactory,  
/* [out] */ VSPUVF_FLAGS *pUpgradeProjectCapabilityFlags  
)  
```  
  
 Bu yöntem ayarlarsa `pUpgradeRequired` TRUE ve döndürür `S_OK`, sonuç "Güncelleştirme" olarak kabul edilir ve olarak rağmen set metodu bir yükseltme bayrağı değerine `VSPUVF_PROJECT_ONEWAYUPGRADE`, bu konunun ilerleyen bölümlerinde açıklanmıştır. Aşağıdaki değerler, bu eski yöntem ancak yalnızca kullanarak desteklenir dönüş `pUpgradeRequired` TRUE olarak ayarlayın:  
  
1. `VS_S_PROJECT_SAFEREPAIRREQUIRED`. Bu dönüş değeri çevirir `pUpgradeRequired` TRUE değerine eşdeğer olarak `VSPUVF_PROJECT_SAFEREPAIR`, bu konunun ilerleyen bölümlerinde açıklanmıştır.  
  
2. `VS_S_PROJECT_UNSAFEREPAIRREQUIRED`. Bu dönüş değeri çevirir `pUpgradeRequired` TRUE değerine eşdeğer olarak `VSPUVF_PROJECT_UNSAFEREPAIR`, bu konunun ilerleyen bölümlerinde açıklanan  
  
3. `VS_S_PROJECT_ONEWAYUPGRADEREQUIRED`. Bu dönüş değeri çevirir `pUpgradeRequired` TRUE değerine eşdeğer olarak `VSPUVF_PROJECT_ONEWAYUPGRADE`, bu konunun ilerleyen bölümlerinde açıklanmıştır.  
  
   Yeni uygulamalarında `IVsProjectUpgradeViaFactory4` ve `IVsProjectFlavorUpgradeViaFactory2` geçiş türü daha kesin olarak belirterek etkinleştirin.  
  
> [!NOTE]
>  Uyumluluk denetimi tarafından sonucunu önbelleğe alabilir `UpgradeProject_CheckOnly` BT'nin ayrıca sonraki çağrı tarafından kullanılabilmesi için yöntemi `CreateProject`.  
  
 Örneğin, varsa `UpgradeProject_CheckOnly` ve `CreateProject` için yazılan yöntemleri bir [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 proje sistemi bir proje dosyasını inceleyin ve Bul `<MinimumVisualStudioVersion>` yapı özelliği "11.0", Visual Studio 2010 SP1 ile projeyi yüklenemediğini. Ayrıca, **Çözüm Gezgini** proje "uyumsuz" ve onu yüklenmiyor gösterir.  
  
##  <a name="BKMK_UpgradeLogger"></a> Yükseltme Günlükçü  
 Çağrı `IVsProjectUpgradeViaFactory::UpgradeProject` içeren bir `IVsUpgradeLogger` Kaydedici, sorun giderme için yükseltme ayrıntılı izleme sağlamak için hangi proje sistemleri ve özellikleri kullanmalıdır. Bir uyarı veya hata günlüğe kaydedilir, Visual Studio yükseltme raporunu gösterir.  
  
 Yükseltme Günlükçü için yazarken aşağıdaki yönergeleri göz önünde bulundurun:  
  
-   Tüm projeleri yükseltme işlemi tamamlandıktan sonra visual Studio temizleme çağırır. Bu, proje sisteminizi çağırmaz.  
  
-   LogMessage işlevi aşağıdaki ErrorLevels sahiptir:  
  
    -   0, izlemek istediğiniz herhangi bir bilgi içindir.  
  
    -   1 için bir uyarıdır.  
  
    -   bir hata için 2.  
  
    -   3 için rapor biçimlendiricidir. Projenizi yükseltildiğinde, sözcük "Dönüştürülen" bir kez oturum ve sözcük yerelleştirmiyorum.  
  
-   Bir proje herhangi bir onarım gerektirmeyen veya yalnızca proje sistemi bir uyarı veya hata sırasında UpgradeProject_CheckOnly veya UpgradeProjectFlavor_CheckOnly yöntemi oturum açmış yükseltme, Visual Studio günlük dosyası oluşturur.