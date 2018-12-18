---
title: Birlikte çalışma derlemelerini kullanarak | Microsoft Docs
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
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: 34
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: df6cee6a2904bd7763f6ae4e18bdd34823ec6c04
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067555"
---
# <a name="using-visual-studio-interop-assemblies"></a>Visual Studio Birlikte Çalışma Bütünleştirilmiş Kodlarını Kullanma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio birlikte çalışma derlemelerini yönetilen uygulamaların, Visual Studio genişletilebilirlik sağlayan COM arabirimleri erişmesine izin verin. Düz COM arabirimleri ile birlikte çalışma sürümlerine arasındaki bazı farklar vardır. Örneğin, HRESULTs genellikle tamsayı değerleri olarak temsil edilir ve özel durumlar olarak aynı şekilde ele alınmaları gerekir ve parametreleri (özellikle out Parametreleri) farklı olarak kabul edilir.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Yönetilen kod için COM'dan döndürülen HRESULTs işleme
 Yönetilen koddan bir COM arabirimi çağırdığınızda HRESULT değerini inceleyin ve gerekirse bir özel durum. <xref:Microsoft.VisualStudio.ErrorHandler> Sınıfı içeren <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> HRESULT değerine bağlı olarak bir COM özel durumu oluşturan yöntem kendisine geçirilen.

 Varsayılan olarak, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> değeri sıfırdan küçük olan bir HRESULT geçirilen her bir özel durum oluşturur. Ek HRESULTS değerlerini olduğu gibi HRESULTs kabul edilebilir değerler ve hiçbir özel durum durumlarda iletilmesi gereken <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> değerleri test sonra. Test edilen HRESULT açıkça geçirilecek herhangi bir HRESULT değerlerini eşleşip eşleşmediğini <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, hiçbir özel durum.

> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants> Sınıfı sabitler gibi ortak HRESULT'ları için içeren <xref:Microsoft.VisualStudio.VSConstants.S_OK> ve <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, ve [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] HRESULTS, örneğin, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> ve <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> Ayrıca sağlar <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> ve <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> com başarılı ve başarısız makrolarındaki karşılık gelen yöntemleri

 Örneğin, aşağıdaki işlev çağrısı göz önünde bulundurun <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> kabul edilebilir bir dönüş değeri başka bir HRESULT hata küçüktür sıfır temsil nesnesidir.

 [!code-csharp[VSSDKHRESULTInformation#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]

 Varsa birden fazla dönüş kabul edilebilir değerler, ek HRESULT değerleri yalnızca çağrı listesine eklenebilecek <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.

 [!code-csharp[VSSDKHRESULTInformation#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]

## <a name="returning-hresults-to-com-from-managed-code"></a>HRESULT'ları, yönetilen koddan COM döndürme
 Hiçbir özel durum oluşursa, kod döndürür yönetilen <xref:Microsoft.VisualStudio.VSConstants.S_OK> adlı COM işlev. COM birlikte çalışma, yönetilen kodda kesin olarak belirlenmiştir ortak özel durumu destekler. Örneğin, kabul edilebilir bir alan bir yöntem `null` bağımsız değişkeni oluşturur bir <xref:System.ArgumentNullException>.

 Hangi özel durum throw emin değilseniz ancak HRESULT biliyorsanız döndürmek için COM, kullanabileceğiniz istediğiniz <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> uygun özel durum için yöntemi. Bu standart olmayan hatayla bile bir örneğin çalışır <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> kesin türü belirtilmiş bir özel durum girişimi HRESULT eşlemek için geçirilen. Erişilemiyorsa, bunun yerine genel bir COM özel durumu oluşturur. Ultimate sonucudur HRESULT için geçirdiğiniz olduğunu <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> yönetilen koddan adlı COM işlevi döndürülür.

> [!NOTE]
>  Özel durumlar, performans tehlikeye ve anormal program koşullarını göstermek için tasarlanmıştır. Genellikle ortaya koşullarını oluşan bir özel durum yerine işlenmiş satır içi olması gerekir.

## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown parametreleri türü void ** geçirildi
 [Out] türü olarak tanımlanmış parametreleri Ara `void **` COM arabirimi, ancak tanımlı olarak `[``iid_is``]` içinde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] birlikte çalışma derlemesi yöntemi prototip.

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

## <a name="optional-out-parameters"></a>[Out] parametreleri isteğe bağlı
 [Out] tanımlanan parametreler için konum veri türü (`int`, `object`, vb.) COM arabirimi, ancak tanımlanmış aynı veri türü bir dizi olarak [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] birlikte çalışma derlemesi yöntemi prototip.

 Gibi bazı COM arabirimleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, [out] parametreleri isteğe bağlı olarak değerlendir. Bir nesne gerekli değilse, bu COM arabirimleri dönüş bir `null` [out] nesne oluşturmak yerine bu parametrenin değeri olarak işaretçi. Bu tasarım gereğidir. Bu arabirimler için `null` işaretçileri doğru davranış göstermesini VSPackage'ı bir parçası olarak kabul ve herhangi bir hata döndürülür.

 CLR bir [out] parametre değerini izin vermediğinden `null`, bu arabirimler tasarlanmış davranışını parçası, yönetilen kod içinde doğrudan kullanılabilir değil. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Etkilenen arabirimleri için birlikte çalışma derlemesi yöntemler, arayanın CLR izin verdiğinden ilgili parametreler olarak diziler tanımlayarak sorunu geçici olarak işe `null` dizileri.

 Yönetilen uygulamaları bu yöntemlerin put bir `null` olduğunda döndürülecek bir şey parametre dizisine. Aksi takdirde, doğru türde tek öğeli bir dizi oluşturun ve dönüş değeri dizide yerleştirin.

 Yönetilen isteğe bağlı [out] arabirimleriyle bilgi almak için yöntemler parametre, parametre olarak bir dizi alma. Yalnızca dizinin ilk öğesinin değerini inceleyin. Değilse `null`, özgün parametresi gibi ilk öğesi kabul edin.

## <a name="passing-constants-in-pointer-parameters"></a>İşaretçi parametreleri geçirme sabitleri
 [İn] COM arabiriminde işaretçileri olarak tanımlandı ancak olarak tanımlanan parametreler için konum bir <xref:System.IntPtr> yazın [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] birlikte çalışma derlemesi yöntemi prototip.

 Özel bir değer, 0, -1 veya – 2 yerine bir nesne işaretçisi gibi bir COM arabirimi başarılı olduğunda benzer bir sorun oluşur. Aksine [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], CLR nesneler olarak yayınlanamadı sabitleri izin vermiyor. Bunun yerine, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] birlikte çalışma derlemesi tanımlar parametre olarak bir <xref:System.IntPtr> türü.

 Bu yöntemlerin yönetilen uygulamaları avantajından olgu, <xref:System.IntPtr> sınıf her ikisi de sahip `int` ve `void *` oluşturmak için oluşturucular bir <xref:System.IntPtr> bir nesne veya bir tamsayı sabiti, uygun şekilde.

 Yönetilen alma yöntemleri <xref:System.IntPtr> bu tür parametreleri kullanması gereken <xref:System.IntPtr> sonuçları işlemek için dönüştürme işleçleri yazın. Dönüştürmeniz <xref:System.IntPtr> için `int` ve ilgili tamsayı sabitleri karşı test edin. Yok değerleri eşleşirse, gerekli türü bir nesneye dönüştürmek ve devam et.

 Bu örnekler için bkz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.

## <a name="ole-return-values-passed-as-out-parameters"></a>OLE dönüş değerleri olarak geçirildi [out] parametreleri
 Sahip yöntemler için konum bir `retval` COM arabirimi, ancak, dönüş değerine sahip bir `int` dönüş değeri ve ek bir [out] dizi parametresinde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] birlikte çalışma derlemesi yöntemi prototip. Bu yöntemler için özel işlem gerektiren açık olmalıdır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] COM arabirim yöntemleri'den bir daha fazla parametre birlikte çalışma derlemesi yöntemi prototipe sahip.

 OLE etkinliği ile işlem birçok COM arabirimleri geri depolanan çağıran program OLE durumu hakkındaki bilgileri göndermek `retval` arabiriminin değeri döndürür. Buna karşılık gelen bir dönüş değeri yerine [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] birlikte çalışma derlemesi yöntemleri geri [out] içinde depolanan çağıran program bilgileri Gönder dizi parametresi.

 Yönetilen uygulamaları bu yöntemlerin [out] parametresi ile aynı türdeki tek öğeli bir dizi oluşturup parametreyi koymak. Dizi öğesinin değeri, uygun COM ile aynı olmalıdır `retval`.

 Bu tür arabirimleri çağıran yönetilen yöntemleri ilk öğe dışında [out] dizi çekmelidir. Bu öğe olarak bulunuyorlarmış işlenebilir bir `retval` karşılık gelen bir COM arabiriminden değeri döndürür.

## <a name="see-also"></a>Ayrıca Bkz.
 [Yönetilmeyen Kod ile Birlikte Çalışma](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
