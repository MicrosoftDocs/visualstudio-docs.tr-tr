---
title: Eski dil Hizmeti Arabirimleri | Microsoft Docs
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
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a5e574267ac83d145c5f3fb44117534127e3f1fd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785852"
---
# <a name="legacy-language-service-interfaces"></a>Eski Dil Hizmeti Arabirimleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Belirli bir programlama dili için aynı anda bir dil hizmeti yalnızca bir örneği olabilir. Ancak, bir tek dil hizmeti birden fazla Düzenleyicisi görebilir.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Dil hizmeti herhangi belirli bir düzenleyici ile ilişkilendirmez. Bu nedenle, bir dil hizmeti işlemi istediğinizde, parametre olarak uygun Düzenleyici belirlemeniz gerekir.  
  
## <a name="common-interfaces-associated-with-language-services"></a>Dil Hizmetleri ile ilişkili ortak arabirimi  
 Çağırarak, dil hizmeti düzenleyicinin alır <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> uygun VSPackage'ı üzerinde. Hizmet kimliği (SID) bu çağrıda geçirilen istenen dil hizmeti tanımlar.  
  
 Ayrı sınıfları herhangi bir sayıda çekirdek dil hizmeti arabirimleri uygulayabilir. Ancak, yaygın bir yaklaşım tek bir sınıfta aşağıdaki arayüzleri uygulamak yazmaktır:  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (isteğe bağlı)  
  
  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Tüm dil hizmetlerinde arabirimi uygulanır. Dil hizmeti ve nasıl bir Renklendirici almak ilişkili dosya adı uzantıları dil yerelleştirilmiş adı gibi dil hizmeti hakkında bilgi sağlar.  
  
## <a name="additional-language-service-interfaces"></a>Ek dil Hizmeti Arabirimleri  
 Diğer arabirimleri dil hizmetinizle sağlanabilir. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] metin arabelleğinin her örneği için bu arabirimler ayrı bir örneğini ister. Bu nedenle, bu arabirimlerin her biri kendi nesne üzerinde uygulamalıdır. Aşağıdaki tabloda, metin arabelleği örneği başına tek örnek gerekli arabirimleri gösterir.  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Aşağı açılan çubuğu gibi kod penceresinde Kenarlıklar yönetir. Bu arabirim kullanarak alabilirsiniz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> yöntemi. Bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> kod penceresi başına.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Dil anahtar sözcükleri ve sınırlayıcıları renklendirmesi. Bu arabirim kullanarak alabilirsiniz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> yöntemi. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Boya zaman çağrılır. Hesaplama yoğunluklu iş içinde önlemek <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> veya performans düşebilir.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|IntelliSense parametresi araç ipuçları sağlar. Dil hizmeti bu yöntemi verileri gösteren bir karakter olmalıdır tanıdığında, bir açık parantez gibi görüntülenen çağırdığı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> görüntüleme metni için yöntemi bir parametre bilgisi araç ipucunu görüntülemek dil hizmeti hazır. Metin görünümünü daha sonra tekrar içine dil hizmeti tarafından yöntemleri kullanılarak yapılan çağrılar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> araç ipucunu görüntülemek için gerekli bilgileri almak için arabirim.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|IntelliSense deyim tamamlamada sağlar. Dil hizmeti tamamlanma listesini görüntülemek hazır olduğunda, çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metni görünümü yöntemi. Metin görünümünü daha sonra tekrar içine dil hizmeti tarafından yöntemleri kullanarak yapılan çağrılar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> nesne.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Komut işleyici kullanarak metin görüntüleme için değiştirilmesini sağlar. İçinde uygulama sınıfı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> arabirimi de uygulanmalı <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi. Metin görünümünü alır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> sorgulanırken nesne <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> yöntemlere geçirilen nesne <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> yöntemi. Olmalıdır bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> her görünüm için nesne.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Kullanıcı kodu penceresine türleri komutları kesintiye uğratır. İzleme çıktısı, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> özel tamamlama bilgileri sağlayın ve değişikliği görmek için uygulama<br /><br /> Geçirmek için <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> metni görünümü veya çağrı nesnesine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski dil hizmeti geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Denetim Listesi: Eski Dil Hizmeti Oluşturma](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

