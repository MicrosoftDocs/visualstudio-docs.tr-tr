---
title: Visual Studio birlikte çalışma derlemeleri kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ca0ff9a75d72bc723b767a43f12123094a520644
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31146825"
---
# <a name="using-visual-studio-interop-assemblies"></a>Visual Studio birlikte çalışma derlemeleri kullanma
Visual Studio birlikte çalışma derlemeleri yönetilen uygulamaların Visual Studio genişletilebilirlik sağlayan COM arabirimleri erişmesine izin verin. Düz COM arabirimleri ile birlikte çalışma sürümlerine arasında bazı farklar vardır. Örneğin, HRESULTs genellikle int değerler olarak temsil edilir ve özel durumlar olarak aynı şekilde ele alınması gerekir ve parametreleri (özellikle out Parametreleri) farklı şekilde işlenir.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Yönetilen kod için COM döndürülen HRESULTs işleme  
 Yönetilen koddan COM arabirimi çağırdığınızda, HRESULT değerini inceleyin ve gerekirse bir özel durum. <xref:Microsoft.VisualStudio.ErrorHandler> Sınıfı içeren <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> HRESULT değerine bağlı olarak bir COM özel durumu oluşturan yöntem kendisine geçirilen.  
  
 Varsayılan olarak, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> sıfır'den küçük bir değere sahip bir HRESULT geçirilen her bir özel durum oluşturur. Ek HRESULTS değerleri olduğu gibi HRESULTs kabul edilebilir değerler ve hiçbir özel durum durumlarda iletilmesi gereken <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> değerleri test sonra. Sınanan HRESULT açıkça geçirilen HRESULT değerleri eşleşip eşleşmediğini <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, hiçbir özel durum oluşur.  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants> Sınıfı sabitleri Örneğin, ortak HRESULTS için içerir <xref:Microsoft.VisualStudio.VSConstants.S_OK> ve <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULTS, örneğin, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> ve <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> Ayrıca sağlar <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> ve <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> com başarılı ve başarısız makrolarındaki karşılık gelen yöntemleri  
  
 Örneğin, aşağıdaki işlev çağrısı göz önünde bulundurun <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> kabul edilebilir bir dönüş değeri ancak diğer HRESULT değerinden sıfır gösteren bir hata değildir.  
  
 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]  
  
 Varsa birden fazla kabul edilebilir dönüş değerleri, ek HRESULT değerleri yalnızca çağrısında listesine eklenebilen <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.  
  
 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Yönetilen koddan COM HRESULTS döndürme  
 Hiçbir özel durum oluşursa, yönetilen kod döndürür <xref:Microsoft.VisualStudio.VSConstants.S_OK> adlı COM işlevi. COM birlikte çalışma yönetilen kodda kesin türü belirtilmiş ortak özel durumları destekler. Örneğin, kabul edilebilir bir alan bir yöntem `null` bağımsız değişkeni atar bir <xref:System.ArgumentNullException>.  
  
 Hangi özel durum throw belirli değildir ancak HRESULT biliyorsanız döndürmek COM için kullanabileceğiniz istediğiniz <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> yöntemi uygun bir özel durum. Bu, örneğin, standart olmayan hatasıyla bile bir çalışır <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> kesin türü belirtilmiş bir özel durum HRESULT eşlemek girişimlerini geçirilen. Başaramazsa, bunun yerine genel bir COM özel durumu oluşturur. Ultimate sonucudur HRESULT için geçirdiğiniz olduğunu <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> yönetilen koddan adlı COM işlevi döndürülür.  
  
> [!NOTE]
>  Özel durumlar tehlikeye performans ve anormal program koşulları belirtmek için tasarlanmıştır. Sık gerçekleşecek koşullar oluşturulan bir özel durum yerine işlenmiş satır içi olmalıdır.  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown parametreleri türü void ** geçirilen  
 [Out] türü olarak tanımlanmış parametreleri Ara `void **` COM arabirimi, ancak, tanımlanmış olarak `[``iid_is``]` içinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışma derlemesi yöntemi prototip.  
  
 Bazı durumlarda, COM arabirimi oluşturan bir `IUnknown` nesne ve COM arabirimini daha sonra geçirir, türü olarak `void **`. Bu arabirimleri özellikle önemlidir çünkü değişkeni olarak tanımlanmışsa [out] IDL içinde sonra `IUnknown` nesne başvuruları sayılan ile `AddRef` yöntemi. Nesne düzgün işlenmemiş bellek sızıntısı ortaya çıkar.  
  
> [!NOTE]
>  Bir `IUnknown` COM arabirimi tarafından oluşturulan ve bir [out] değişkeninde döndürülen nesnenin açıkça serbest varsa bellek sızıntısı neden olur.  
  
 Bu tür nesneleri işlemek yönetilen yöntemleri kabul <xref:System.IntPtr> gösteren bir işaretçi olarak bir `IUnknown` nesne ve arama <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> nesne elde etmek için yöntemi. Arayan sonra hangi tür uygun olan dönüş değeri atamalısınız. Nesne artık gerekli olmadığında çağrı <xref:System.Runtime.InteropServices.Marshal.Release%2A> bunu serbest bırakmak için.  
  
 Çağırma örneği aşağıdadır <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> yöntemi ve işleme `IUnknown` doğru nesnesi:  
  
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
>  Geçirmek için aşağıdaki yöntemlerden bilinen `IUnknown` nesne işaretçileri türü <xref:System.IntPtr>. Bunları, bu bölümde açıklandığı gibi işler.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>[Out] parametreleri isteğe bağlı  
 [Out] tanımlanan parametreler için ara veri türü (`int`, `object`, vb.) COM arabirimi, ancak tanımlanmış aynı veri türünde bir dizi olarak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışma derlemesi yöntemi prototip.  
  
 Gibi bazı COM arabirimleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, [out] parametreleri isteğe bağlı olarak ele alın. Bir nesne gerekli değilse, bu COM arabirimleri dönmesini bir `null` işaretçi [out] nesnesi oluşturmak yerine bu parametrenin değeri olarak. Bu tasarım gereğidir. Bu arabirimleri için `null` işaretçileri VSPackage doğru davranış bir parçası olarak kabul edilir ve hiçbir hata döndürülür.  
  
 CLR olmasını [out] parametresi değerini izin vermediğinden `null`, bu arabirimleri tasarlanmış davranışını parçası yönetilen kod içinde doğrudan kullanılabilir değil. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Etkilenen arabirimleri için birlikte çalışma derlemesi yöntemleri CLR arayanın verdiğinden ilgili parametreleri olarak diziler tanımlayarak sorunun geçici çalışma `null` dizileri.  
  
 Bu yöntemlerin yönetilen uygulamaları put bir `null` olduğunda döndürülecek hiçbir şey parametre dizisine. Aksi takdirde doğru türde tek öğeli bir dizi oluşturun ve dönüş değeri dizideki koyun.  
  
 Yönetilen isteğe bağlı [Çıkış] arabirimleriyle bilgi almak yöntemleri parametreleri bir dizi parametre alırsınız. Yalnızca dizisinin ilk öğesi değerini inceleyin. Değilse `null`, özgün parametresi değilmiş gibi ilk öğesi kabul edin.  
  
## <a name="passing-constants-in-pointer-parameters"></a>İşaretçi parametrelerinde geçirme sabitleri  
 [İn] işaretçileri gibi COM arabirimi içinde tanımlı, ancak olarak tanımlanan parametreler için konum bir <xref:System.IntPtr> yazın [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışma derlemesi yöntemi prototip.  
  
 COM arabirimi özel bir değer, 0, -1 veya bir nesne işaretçisi yerine -2 gibi geçtiğinde benzer bir sorun oluşur. Farklı [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], CLR nesneler olarak yayınlanamıyor sabitleri izin vermiyor. Bunun yerine, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışma derlemesi parametre olarak tanımlayan bir <xref:System.IntPtr> türü.  
  
 Bu yöntemlerin yönetilen uygulamaları avantajından olgu, <xref:System.IntPtr> sınıfına sahip her ikisi de `int` ve `void *` oluşturmak için oluşturucular bir <xref:System.IntPtr> olarak bir nesne veya tamsayı sabiti uygun.  
  
 Yönetilen alma yöntemleri <xref:System.IntPtr> parametreleri bu tür kullanması gereken <xref:System.IntPtr> sonuçlarını işlemek için dönüşüm işleçleri yazın. Dönüştürmeniz <xref:System.IntPtr> için `int` ve ilgili tamsayı sabitleri karşı test etme. Yok değerleri eşleşirse, gerekli türünde bir nesneye dönüştürün ve devam edin.  
  
 Bu örnekler için bkz: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE dönüş değerleri geçirilen olarak [out] parametreleri  
 İçin sahip yöntemleri arayın bir `retval` COM arabirimi ancak dönüş değerine sahip bir `int` dönüş değeri ve ek bir [out] dizi parametresinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışma derlemesi yöntemi prototip. Bu yöntemler için özel olarak işlenmesi gerektiği açık olmalıdır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışma derlemesi yöntemi prototipleri COM arabirim yöntemleri'den bir daha fazla parametre vardır.  
  
 OLE etkinlikle ilgili birçok COM arabirimleri geri depolanan çağıran program OLE durumu hakkında bilgi göndermek `retval` arabirimi değerini döndürür. Karşılık gelen bir dönüş değeri kullanmak yerine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışma derlemesi yöntemleri [out] içinde depolanan geri çağırma programın bilgi gönder dizi parametresi.  
  
 Bu yöntemlerin yönetilen uygulamaları, [out] parametresi ile aynı türde tek öğeli bir dizi oluşturmak ve parametresinde yerleştirin. Dizi öğesi değerini uygun COM ile aynı olmalıdır `retval`.  
  
 Bu tür arabirimleri çağrı yönetilen yöntemleri [out] dizi dışında ilk öğe çekme. Bu öğe olarak olsaydı işlenebilir bir `retval` karşılık gelen COM arabiriminden dönüş değeri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilmeyen Kod ile Birlikte Çalışma](/dotnet/framework/interop/index)