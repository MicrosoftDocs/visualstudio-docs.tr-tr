---
title: Sözdizimi özel düzenleyicilerde renklendirme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18e087e82754244b7abda530f733a6047447f4a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139467"
---
# <a name="syntax-coloring-in-custom-editors"></a>Sözdizimi özel düzenleyicilerde renklendirme
Çekirdek Düzenleyicisi'ni de dahil olmak üzere visual Studio ortamı SDK düzenleyicileri dil Hizmetleri belirli söz dizimi öğeleri tanımlamak ve bunları belirli belge görünümü için belirtilen renklerle görüntülemek için kullanın.

## <a name="colorization-requirements"></a>Renklendirme gereksinimleri
 Bir dil hizmetin Renklendirici uygulama tüm düzenleyicileri gerekir:

1.  Bir nesne uygulama kullanmak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> renklendirilen için metin ve bir nesne uygulama yönetmek için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> metin belgesi görünümünü sağlamak için.

2.  Arabirime belirli dil hizmeti dilleri hizmetin tanımlayıcı GUID kullanarak VSPackage'nın hizmet sağlayıcısı sorgulayarak edinin.

3.  Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> nesne uygulama yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Bu yöntem dil hizmetiyle ilişkilendirir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> renklendirilen için metin yönetmek için VSPackage kullanan uygulaması.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Bir dil hizmetin Renklendirici çekirdek Düzenleyici kullanımı
 Bir Renklendirici dil hizmetiyle çekirdek Düzenleyicisi'ni, ayrıştırma ve metin dili hizmetin Renklendirici tarafından işleme bir örneği tarafından ne zaman alınır otomatik olarak çaba başka müdahalesi gerektirmeden gerçekleştirilir.

 IDE saydam:

-   Ayrıştırma ve metin eklendikçe veya uygulamasında değiştiren çözümlemek için gerektiği şekilde Renklendirici çağırır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.

-   Tarafından sağlanan belge görünümü tarafından sağlanan görüntülenmesini sağlar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> uygulama güncelleştirildi ve Renklendirici tarafından döndürülen bilgileri kullanarak yeniden çizilmiş.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Bir dil hizmetin Renklendirici çekirdek olmayan Düzenleyicisi kullanımı
 Non-çekirdek Düzenleyici örnekleri bir dil hizmetin söz dizimi renklendirme hizmetini de kullanabilirsiniz, ancak bunlar açıkça almalı ve hizmetin Renklendirici uygulamak ve kendi belge görünümleri yeniden boyamak.

 Bunu yapmak için bir çekirdek olmayan Düzenleyicisi gerekir:

1.  Bir dil hizmetin Renklendirici nesnesini alın (hangi uygulayan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). VSPackage bu çağırarak gerçekleştirir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> dil hizmetin arabirimde yöntemi.

2.  Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metnin belirli bir aralık renklendirilen istek yöntemi.

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Yöntemi değerleri dizisi döndürür, metindeki her harfi için bir tane span renklendirilen. Ayrıca, açıklama, anahtar sözcüğü veya veri türü gibi colorable öğesinin belirli bir tür olarak metin aralık tanımlar.

3.  Tarafından döndürülen renklendirme bilgileri <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> yeniden çizilmez ve onun metni görüntülemek için.

> [!NOTE]
> Bir dil hizmetin Renklendirici kullanmanın yanı sıra bir VSPackage genel amaçlı Visual Studio ortamı SDK metin renklendirme mekanizması kullanmayı da tercih edebilirsiniz. Bu mekanizma hakkında daha fazla bilgi için bkz: [kullanarak yazı tiplerini ve renkleri](../extensibility/using-fonts-and-colors.md).

## <a name="see-also"></a>Ayrıca Bkz.

- [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Söz Dizimi Renklendirmesi Uygulama](../extensibility/internals/implementing-syntax-coloring.md)
- [Nasıl yapılır: Yerleşik Renklendirilebilir Öğeleri Kullanma](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Özel Renklendirilebilir Öğeler](../extensibility/internals/custom-colorable-items.md)