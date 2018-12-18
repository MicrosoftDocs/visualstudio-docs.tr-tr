---
title: Sözdizimi eski dil hizmetinde renklendirme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 172f06f4e30f1320b6e17332cb2b54af91f7ed01
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136061"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Eski dil hizmetinde renklendirme sözdizimi

Visual Studio renklendirme hizmeti dil öğeleri tanımlamak ve bunları bir düzenleyicide belirtilen renklerle görüntülemek için kullanır.

## <a name="colorizer-model"></a>Renklendirici modeli
 Dil hizmeti uygulayan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> sonra düzenleyiciler tarafından kullanılan arabirim. Bu uygulama, aşağıdaki çizimde gösterildiği gibi ayrı bir nesne dil hizmetinden geçerlidir:

 ![SVC Renklendirici grafiği](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
>  Hizmet renklendirme söz dizimi renklendirme metin için genel Visual Studio mekanizması ayrıdır. Genel hakkında daha fazla bilgi için [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] renklendirme, destekleme mekanizması bkz [kullanarak yazı tiplerini ve renkleri](../../extensibility/using-fonts-and-colors.md).

 Renklendirici yanı sıra dil hizmeti Düzenleyicisi tarafından özel colorable öğeleri sağlayan reklam tarafından kullanılan özel colorable öğeler sağlayabilir. Bunu uygulayarak yapmak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> arabirimini uygulayan nesnedeki <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> arabirimi. Düzenleyici çağırdığında özel colorable öğe sayısını döndürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> Yöntemi Düzenleyicisi'ni çağırdığında ayrı bir özel colorable öğe döndürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> yöntemi.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> Yöntemi uygulayan bir nesne döndürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> arabirimi. Dil hizmeti 24 bit ya da yüksek renk değerleri destekliyorsa, uygulamalıdır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> aynı nesneye arabirimde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> arabirimi.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Bir VSPackage dil hizmeti Renklendirici nasıl kullanır

1.  VSPackage dil hizmeti aşağıdakileri yapmak için VSPackage gerektirir uygun dil hizmeti almanız gerekir:

    1.  Bir nesne uygulama kullanmak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> renklendirilen için metni almak için arabirim.

         Metin, uygulayan bir nesne kullanarak genellikle görüntülenir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> arabirimi.

    2.  Dil hizmeti VSPackage GUID dil hizmeti için hizmet sağlayıcısı sorgulayarak alın. Dil Hizmetleri kayıt defterinde dosya uzantısı ile tanımlanır.

    3.  Dil hizmeti ile ilişkilendirmek <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> çağırarak kendi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> yöntemi.

2.  VSPackage şimdi elde edilir ve Renklendirici nesne aşağıdaki şekilde kullanın:

    > [!NOTE]
    > Çekirdek Düzenleyicisi'ni VSPackages bir dil hizmetin Renklendirici nesneleri açıkça almak zorunda kalmazsınız. Uygun dil hizmeti çekirdek Düzenleyici örneği alır almaz, burada gösterilen tüm renklendirme görevleri gerçekleştirir.

    1.  Uygulayan dil hizmetin Renklendirici nesnesini alın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>, ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> çağırarak arabirimleri <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> dil hizmetin yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> nesnesi.

    2.  Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metin belirli bir aralığa Renklendirici bilgilerini elde etmek için yöntem.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> değer, bir renklendirilen metin aralığı içinde her karakter dizisi döndürür. Çekirdek Düzenleyicisi tarafından tutulan varsayılan colorable öğesi listesini ya da dil hizmeti kendisi tarafından tutulan özel colorable öğesi listesini colorable öğesi listesini dizin değerlerdir.

    3.  Tarafından döndürülen renklendirme bilgileri <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> seçili metni görüntülemek için yöntem.

> [!NOTE]
>  Bir dil hizmeti Renklendirici kullanmanın yanı sıra bir VSPackage mekanizması renklendirme genel amaçlı Visual Studio metin de kullanabilirsiniz. Bu mekanizma hakkında daha fazla bilgi için bkz: [kullanarak yazı tiplerini ve renkleri](../../extensibility/using-fonts-and-colors.md).

## <a name="in-this-section"></a>Bu Bölümde
 [Söz dizimi renklendirme uygulama](../../extensibility/internals/implementing-syntax-coloring.md) Discusses bir düzenleyici nasıl eriştiğini bir dil hizmetin söz dizimi renklendirme ve dil hizmet sözdizimi renklendirmesi desteklemek için uygulamanız gerekir.

 [Nasıl yapılır: kullanım yerleşik Colorable öğeleri](../../extensibility/internals/how-to-use-built-in-colorable-items.md) dil hizmetinden yerleşik colorable öğelerin nasıl kullanılacağı gösterilmektedir.

 [Özel Colorable öğeler](../../extensibility/internals/custom-colorable-items.md) nasıl özel colorable öğeler uygulanacağını anlatır.

## <a name="see-also"></a>Ayrıca Bkz.

- [Yazı tipleri ve renkler kullanarak](../../extensibility/using-fonts-and-colors.md)