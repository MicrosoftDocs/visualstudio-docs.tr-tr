---
title: Özel renklendirilebilir öğeler | Microsoft Docs
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
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 272d16b9f5f8fb33b68c911c5e7bd27923f4c2db
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796954"
---
# <a name="custom-colorable-items"></a>Özel Renklendirilebilir Öğeler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Özel renklendirilebilir öğeler, dil hizmetinin bir parçası olarak uygulayarak, renklendirme, anahtar sözcükleri ve açıklamalar gibi türlerinin listesi kılabilirsiniz.  
  
## <a name="user-settings-of-colorable-items"></a>Kullanıcı ayarlarını renklendirilebilir öğeler  
 Görüntüleyebileceğiniz **yazı tipleri ve renkler** iletişim kutusunu seçerek **seçenekleri** üzerinde **Araçları** menüsüne ve ardından seçerek **yazı tipleri ve renkler** altında **ortam**. Seçtiğinizde, bir görüntü gibi **metin düzenleyici** veya **komut penceresi**, **görüntü öğeleri** liste kutusu görüntüleyen tüm renklendirilebilir öğeleri gösterir. Görüntüleyebilir ve yazı tipi, boyutu, ön plan rengini ve renklendirilebilir her öğe için arka plan rengini değiştirin. Seçimlerinizi kayıt defteri önbellekte depolanır ve renklendirilebilir öğe adı tarafından erişilebilir.  
  
## <a name="presentation-of-colorable-items"></a>Sunu renklendirilebilir öğeleri  
 IDE içinde renklendirilebilir öğeleri kullanıcı geçersiz kılmaları hallettiğinden **yazı tipleri ve renkler** iletişim kutusunda, gereken yalnızca özel renklendirilebilir öğeleri bir ad sağlayın. Bu ad görünür ne olduğunu **görüntü öğeleri** listesi. Renklendirilebilir öğeleri alfabetik sırada görünür. Dil hizmetinizin özel renklendirilebilir öğeleri gruplandırmak için dil adınızla her adı örneğin başlayabilirsiniz **NewLanguage - açıklama** ve **NewLanguage - anahtar sözcüğü**.  
  
> [!CAUTION]
>  Dil adı, mevcut renklendirilebilir öğesi adları ile çarpışmalardan kaçınmak için renklendirilebilir öğesi adını içermelidir. Geliştirme sırasında renklendirilebilir öğelerinizden birini adını değiştirirseniz, renklendirilebilir öğelerinizi erişildiğini ilk kez oluşturulan önbelleğini sıfırlamanız gerekir. Deneysel önbellek dizininde genellikle Visual Studio SDK ile birlikte yüklenen Createexpınstance aracıyla sıfırlayabilir  
>   
>  **C:\Program dosyaları (x86) \Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin**  
>   
>  Önbelleği sıfırlamak için çağrı `CreateExpInstance /Reset`. Createexpınstance hakkında daha fazla bilgi için bkz: [Createexpınstance yardımcı programı](../../extensibility/internals/createexpinstance-utility.md).  
  
 Listesindeki ilk öğe renklendirilebilir öğeleri hiçbir zaman başvuruluyor. İlk öğe için bir renklendirilebilir öğe dizini 0 karşılık gelir ve [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] her zaman varsayılan metin rengini ve bu öğenin öznitelikleri sağlar. Bir yer tutucu renklendirilebilir öğesi listesindeki ilk öğe olarak sağlamak için bu başvurulmayan öğesi uğraşmanızı en kolay yolu olan.  
  
## <a name="implementing-custom-colorable-items"></a>Özel renklendirilebilir öğeler uygulama  
  
1. Tanımlayın örneğin anahtar sözcüğü, işleci ve tanımlayıcı, dil renklendirilmiş gerekir.  
  
2. Bu renklendirilebilir öğeler numaralandırması oluşturun.  
  
3. Bir Ayrıştırıcı veya listelenmiş değerler tarayıcıyla döndürülen belirteç türleri ilişkilendirin.  
  
    Örneğin, belirteç türleri temsil eden değerleri özel renklendirilebilir öğeler aynı değerler olabilir.  
  
4. Uygulamanızda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> yönteminde, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> nesne, öznitelikler listesinde, özel renklendirilebilir öğeler numaralandırma ayrıştırıcı veya tarayıcıdan döndürülen belirteç türleri karşılık gelen değerlerle doldurun.  
  
5. Uygulayan aynı sınıftaki <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> arabirim, uygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> arabirimi ve iki metotlarını <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.  
  
6. Uygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> arabirimi.  
  
7. 24-bit ya da yüksek renk değerleri desteklemek istiyorsanız, ayrıca uygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> arabirimi.  
  
8. Dil hizmeti nesnesinde içeren bir liste oluşturun, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> nesneleri, her renklendirilebilir öğesi ayrıştırıcı veya tarayıcı belirleyebilir.  
  
    Listedeki her öğeye karşılık gelen özel renklendirilebilir öğeler sabit listesi değeri kullanarak erişebilirsiniz. Sabit listesi değerleri listesine bir dizin olarak kullanın. Listedeki ilk öğeye hiç erişilebilir, varsayılan metni karşılık olmadığından, stil [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] her zaman kendini işler. Bunun için bir yer tutucu renklendirilebilir öğesi listesinin başında ekleyerek dengeleyebilirsiniz.  
  
9. Uygulamanızda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> yöntemi, özel renklendirilebilir öğeler listedeki öğe sayısını döndürür.  
  
10. Uygulamanızda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> yöntemi listenizden istenen renklendirilebilir öğeyi döndürür.  
  
    Nasıl uygulayacağınıza dair bir örnek <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> arabirimleri Bkz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski dil hizmetinin modeli](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [Özel düzenleyicilerde söz dizimi renklendirmesi](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Eski dil hizmetinde söz dizimi renklendirmesi](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Söz dizimi renklendirmesi uygulama](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Nasıl yapılır: Yerleşik Renklendirilebilir Öğeleri Kullanma](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

