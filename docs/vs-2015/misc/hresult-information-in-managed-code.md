---
title: Yönetilen kodda HRESULT bilgi | Microsoft Docs
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
- VSPackages, HRESULT information
- HRESULT, managed VSPackages
ms.assetid: 0795ee94-17a8-4327-bf57-27cd5e312a4c
caps.latest.revision: 29
manager: douge
ms.openlocfilehash: 08d14f1155838e53321224280a69e7a76bf07b52
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911856"
---
# <a name="hresult-information-in-managed-code"></a>Yönetilen kodda HRESULT bilgileri
HRESULT dönüş değerlerini karşılaştığında, yönetilen kodda COM arasındaki etkileşimi sorunlara neden olabilir.  
  
 Bir COM arabirimi içinde bu rolleri HRESULT dönüş değerini yürütebilirsiniz:  
  
- Hata bilgisi sunar (örneğin, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>).  
  
- Programın normal davranış hakkında durum bilgileri sağlar.  
  
  HRESULT'ları, COM yönetilen kodu çağırdığında, bu sorunlara neden olabilir:  
  
- HRESULT değerleri dönüş küçüktür sıfır (hata kodları) COM İşlevler, özel durum oluşturur.  
  
- Dönüş düzenli olarak iki veya daha fazla farklı başarı kodları, örneğin, COM yöntemleri <xref:Microsoft.VisualStudio.VSConstants.S_OK> veya <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>, ayırt edici olamaz.  
  
  Çünkü çoğu [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] HRESULT değerlerini değerinden, sıfır veya farklı bir başarı kodu döndürür ya da dönüş COM işlevleri [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] birlikte çalışma derlemelerini yazılı böylece yöntem imzaları korunur. Tüm [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] birlikte çalışma yöntemlerdir `int` türü. HRESULT değerleri, birlikte çalışma katmanı değişikliğinin ve özel durumların olmadan aracılığıyla geçirilir.  
  
  Bir COM işlev çağıran yönetilen yönteme HRESULT döndürdüğünden, çağıran Metoda HRESULT denetleyin ve gerekirse özel durumlar gerekir.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Yönetilen kod için COM'dan döndürülen HRESULTs işleme  
 Yönetilen koddan bir COM arabirimi çağırdığınızda HRESULT değerini inceleyin ve gerekirse bir özel durum. <xref:Microsoft.VisualStudio.ErrorHandler> Sınıfı içeren <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> HRESULT değerine bağlı olarak bir COM özel durumu oluşturan yöntem kendisine geçirilen.  
  
 Varsayılan olarak, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> değeri sıfırdan küçük olan bir HRESULT geçirilen her bir özel durum oluşturur. Ek HRESULTS değerlerini olduğu gibi HRESULTs kabul edilebilir değerler ve hiçbir özel durum durumlarda iletilmesi gereken <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> değerleri test sonra. Test edilen HRESULT açıkça geçirilecek herhangi bir HRESULT değerlerini eşleşip eşleşmediğini <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, hiçbir özel durum.  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants> Sınıfı sabitler gibi ortak HRESULT'ları için içeren <xref:Microsoft.VisualStudio.VSConstants.S_OK> ve <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, ve [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] HRESULTS, örneğin, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> ve <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> Ayrıca sağlar <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> ve <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> com başarılı ve başarısız makrolarındaki karşılık gelen yöntemleri  
  
 Örneğin, aşağıdaki işlev çağrısı göz önünde bulundurun <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> kabul edilebilir bir dönüş değeri başka bir HRESULT hata küçüktür sıfır temsil nesnesidir.  
  
 [!code-csharp[VSSDKHRESULTInformation#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]  
  
 Varsa birden fazla dönüş kabul edilebilir değerler, ek HRESULT değerleri yalnızca çağrı listesine eklenebilecek <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.  
  
 [!code-csharp[VSSDKHRESULTInformation#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>HRESULT'ları, yönetilen koddan COM döndürme  
 Hiçbir özel durum oluşursa, kod döndürür yönetilen <xref:Microsoft.VisualStudio.VSConstants.S_OK> adlı COM işlev. COM birlikte çalışma, yönetilen kodda kesin olarak belirlenmiştir ortak özel durumu destekler. Örneğin, kabul edilebilir bir alan bir yöntem `null` bağımsız değişkeni oluşturur bir <xref:System.ArgumentNullException>.  
  
 Hangi özel durum throw emin değilseniz ancak HRESULT biliyorsanız döndürmek için COM, kullanabileceğiniz istediğiniz <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> uygun özel durum için yöntemi. Bu standart olmayan hatayla bile bir örneğin çalışır <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> kesin türü belirtilmiş bir özel durum girişimi HRESULT eşlemek için geçirilen. Erişilemiyorsa, bunun yerine genel bir COM özel durumu oluşturur. Ultimate sonucudur HRESULT için geçirdiğiniz olduğunu <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> yönetilen koddan adlı COM işlevi döndürülür.  
  
> [!NOTE]
>  Özel durumlar, performans tehlikeye ve anormal program koşullarını göstermek için tasarlanmıştır. Genellikle ortaya koşullarını oluşan bir özel durum yerine işlenmiş satır içi olması gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen VSPackage'ları](../misc/managed-vspackages.md)   
 [Yönetilmeyen kod ile birlikte çalışma](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)   
 [Nasıl yapılır: HRESULTs ve özel durumları eşleme](http://msdn.microsoft.com/library/610b364b-2761-429d-9c4a-afbc3e66f1b9)   
 [Birlikte çalışma için COM bileşenleri oluşturma](http://msdn.microsoft.com/en-us/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [Yönetilen VSPackage'ları](../misc/managed-vspackages.md)