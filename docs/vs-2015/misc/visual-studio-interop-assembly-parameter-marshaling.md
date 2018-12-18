---
title: Visual Studio birlikte çalışma bütünleştirilmiş kodu parametresi hazırlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting Visual Studio SDK interop assemblies
- interop assemblies, parameter marshaling
- interop assemblies, troubleshooting
ms.assetid: 89123eae-0fef-46d5-bd36-3d2a166b14e3
caps.latest.revision: 24
manager: douge
ms.openlocfilehash: e18667adb48f565f73acc14f5012f9c96283efe9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195025"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Visual Studio birlikte çalışma bütünleştirilmiş kodu parametresi hazırlama
Yönetilen kodda yazılır VSPackages çağrı yapma veya yönetilmeyen COM kod tarafından çağrılmak gerekebilir. Genellikle, yöntem bağımsız değişkenleri dönüştürülmüş veya otomatik olarak birlikte çalışma sıralayıcısı göre sıralanır. Ancak, bazen bağımsız değişkenleri basit bir şekilde dönüştürülemez. Bu gibi durumlarda birlikte çalışma derlemesi yöntemi prototip parametreleri COM işlev parametrelerini mümkün olduğunca yakın eşleştirmek için kullanılır. Daha fazla bilgi için [birlikte çalışma hazırlama](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).  
  
## <a name="general-suggestions"></a>Genel öneriler  
  
##### <a name="read-the-reference-documentation"></a>Başvuru belgeleri okuyun  
 Her yöntem için başvuru belgeleri okumak için birlikte çalışabilirlik sorunlarını algılamak için verimli bir yöntem var.  
  
 Her yöntem için başvuru belgeleri üç ilgili bölümleri içerir:  
  
-   [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] COM işlev prototipi.  
  
-   Birlikte çalışma derlemesi yöntemi prototipi.  
  
-   COM parametreleri ve her kısa bir açıklamasını listesi.  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>İki prototip arasındaki farklar arayın  
 COM arabirimi içinde belirli bir tür tanımı hem de aynı türden tanımı uyuşmazlıklarını çoğu birlikte çalışabilirlik sorunlarını türetilmesi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] birlikte çalışma bütünleştirilmiş kodları. Örneğin, geçirme özelliği fark düşünün bir `null` [out] parametresi değeri. İki prototip arasındaki farklar arayın ve geçirilen veriler için kendi ayrımlar göz önünde bulundurun gerekir.  
  
##### <a name="read-the-parameter-definitions"></a>Parametre tanımlarını oku  
 Parametre tanımlarıyla okuyun. COM farklı türde tek bir parametre verilerinde karıştırma hakkında ortak dil çalışma zamanı (CLR) daha az katı. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] COM arabirimleri bu esneklik avantajlarından yararlanın. Geçti veya standart olmayan bir değer veya işaretçi parametresi, sabit bir değer gibi bir veri türü gerektiren herhangi bir parametre belgelerinde şekilde açıklanmalıdır.  
  
### <a name="iunknown-objects-passed-as-type-void"></a>IUnknown nesneleri türü void ** geçirildi  
 [Out] türü olarak tanımlanmış parametreleri Ara `void **` COM arabirimi, ancak tanımlı olarak `[``iid_is``]` içinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] birlikte çalışma derlemesi yöntemi prototip.  
  
 Bazı durumlarda, bir COM arabirimi oluşturan bir `IUnknown` nesne ve COM arabirimi sonra geçirir, türü olarak `void **`. Bu arabirimler özellikle önemlidir çünkü değişken olarak tanımlanmışsa [out] IDL ile sonra `IUnknown` nesne başvuru sayılan ile `AddRef` yöntemi. Bir bellek sızıntısı, nesneyi doğru işlenmiyor oluşur.  
  
> [!NOTE]
>  Bir `IUnknown` COM arabirimi tarafından oluşturulan ve bir [out] değişkeninde döndürülen nesne açıkça serbest, bellek sızıntısı neden olur.  
  
 Bu nesneleri işlemek, yönetilen yöntemleri kabul <xref:System.IntPtr> işaretçisi olarak bir `IUnknown` nesne ve çağrı <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> nesne elde etmek için yöntemi. Çağıran, hangi tür uygun olan dönüş değeri ardından atamalısınız. Nesne artık gerekmediğinde çağrı <xref:System.Runtime.InteropServices.Marshal.Release%2A> bunu serbest bırakmak için.  
  
 Çağırma örneği aşağıdadır <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> yöntemi ve işleme `IUnknown` doğru nesne:  
  
```  
MyClass myclass;  
Object object;  
IntPtr pObj;  
Guid iid = Typeof(MyClass).Guid;  
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);     
if (NativeMethods.Succeeded(hr))   
{  
    try   
    {  
        object = Marshal.GetObjectForIUnknown(pObj);  
        myclass = object;  
    }  
    finally   
    {  
        Marshal.Release(pObj);  
    }  
}  
else   
{  
    // error calling QueryViewInterface  
}  
```  
  
> [!NOTE]
>  Geçirmek için aşağıdaki yöntemlerden bilinen `IUnknown` nesne işaretçileri türü <xref:System.IntPtr>. Bunları, bu bölümde açıklanan şekilde işleyin.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
### <a name="optional-out-parameters"></a>[Out] parametreleri isteğe bağlı  
 [Out] tanımlanan parametreler için konum veri türü (`int`, `object`, vb.) COM arabirimi, ancak tanımlanmış aynı veri türü bir dizi olarak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] birlikte çalışma derlemesi yöntemi prototip.  
  
 Gibi bazı COM arabirimleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, [out] parametreleri isteğe bağlı olarak değerlendir. Bir nesne gerekli değilse, bu COM arabirimleri dönüş bir `null` [out] nesne oluşturmak yerine bu parametrenin değeri olarak işaretçi. Bu tasarım gereğidir. Bu arabirimler için `null` işaretçileri doğru davranış göstermesini VSPackage'ı bir parçası olarak kabul ve herhangi bir hata döndürülür.  
  
 CLR bir [out] parametre değerini izin vermediğinden `null`, bu arabirimler tasarlanmış davranışını parçası, yönetilen kod içinde doğrudan kullanılabilir değil. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Etkilenen arabirimleri için birlikte çalışma derlemesi yöntemler, arayanın CLR izin verdiğinden ilgili parametreler olarak diziler tanımlayarak sorunu geçici olarak işe `null` dizileri.  
  
 Yönetilen uygulamaları bu yöntemlerin put bir `null` olduğunda döndürülecek bir şey parametre dizisine. Aksi takdirde, doğru türde tek öğeli bir dizi oluşturun ve dönüş değeri dizide yerleştirin.  
  
 Yönetilen isteğe bağlı [out] arabirimleriyle bilgi almak için yöntemler parametre, parametre olarak bir dizi alma. Yalnızca dizinin ilk öğesinin değerini inceleyin. Değilse `null`, özgün parametresi gibi ilk öğesi kabul edin.  
  
### <a name="passing-constants-in-pointer-parameters"></a>İşaretçi parametreleri geçirme sabitleri  
 [İn] COM arabiriminde işaretçileri olarak tanımlandı ancak olarak tanımlanan parametreler için konum bir <xref:System.IntPtr> yazın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] birlikte çalışma derlemesi yöntemi prototip.  
  
 Özel bir değer, 0, -1 veya – 2 yerine bir nesne işaretçisi gibi bir COM arabirimi başarılı olduğunda benzer bir sorun oluşur. Aksine [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], CLR nesneler olarak yayınlanamadı sabitleri izin vermiyor. Bunun yerine, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] birlikte çalışma derlemesi tanımlar parametre olarak bir <xref:System.IntPtr> türü.  
  
 Bu yöntemlerin yönetilen uygulamaları avantajından olgu, <xref:System.IntPtr> sınıf her ikisi de sahip `int` ve `void *` oluşturmak için oluşturucular bir <xref:System.IntPtr> bir nesne veya bir tamsayı sabiti, uygun şekilde.  
  
 Yönetilen alma yöntemleri <xref:System.IntPtr> bu tür parametreleri kullanması gereken <xref:System.IntPtr> sonuçları işlemek için dönüştürme işleçleri yazın. Dönüştürmeniz <xref:System.IntPtr> için `int` ve ilgili tamsayı sabitleri karşı test edin. Yok değerleri eşleşirse, gerekli türü bir nesneye dönüştürmek ve devam et.  
  
 Bu örnekler için bkz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>OLE dönüş değerleri olarak geçirildi [out] parametreleri  
 Sahip yöntemler için konum bir `retval` COM arabirimi, ancak, dönüş değerine sahip bir `int` dönüş değeri ve ek bir [out] dizi parametresinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] birlikte çalışma derlemesi yöntemi prototip. Bu yöntemler için özel işlem gerektiren açık olmalıdır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] COM arabirim yöntemleri'den bir daha fazla parametre birlikte çalışma derlemesi yöntemi prototipe sahip.  
  
 OLE etkinliği ile işlem birçok COM arabirimleri geri depolanan çağıran program OLE durumu hakkındaki bilgileri göndermek `retval` arabiriminin değeri döndürür. Buna karşılık gelen bir dönüş değeri yerine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] birlikte çalışma derlemesi yöntemleri geri [out] içinde depolanan çağıran program bilgileri Gönder dizi parametresi.  
  
 Yönetilen uygulamaları bu yöntemlerin [out] parametresi ile aynı türdeki tek öğeli bir dizi oluşturup parametreyi koymak. Dizi öğesinin değeri, uygun COM ile aynı olmalıdır `retval`.  
  
 Bu tür arabirimleri çağıran yönetilen yöntemleri ilk öğe dışında [out] dizi çekmelidir. Bu öğe olarak bulunuyorlarmış işlenebilir bir `retval` karşılık gelen bir COM arabiriminden değeri döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Birlikte çalışma hazırlama](http://msdn.microsoft.com/en-us/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Birlikte çalışma hazırlama](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [Birlikte çalışabilirlik sorunlarını giderme](http://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [Yönetilen VSPackage'ları](../misc/managed-vspackages.md)