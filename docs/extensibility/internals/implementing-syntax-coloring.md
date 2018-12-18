---
title: Sözdizimi renklendirmesi uygulama | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5502bd30378130e5977d427acb9df5b73226a05b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131861"
---
# <a name="implementing-syntax-coloring"></a>Sözdizimi renklendirmesi uygulama
Dil hizmeti söz dizimi renklendirme sağladığında, ayrıştırıcı metin satırının colorable öğelerini bir diziye dönüştürür ve belirteç türleri colorable bu öğeler karşılık gelen döndürür. Ayrıştırıcının colorable öğeler listesine ait belirteç türleri döndürmelidir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] colorable her öğe için uygun belirteç türü Renklendirici nesne tarafından atanan öznitelikleri göre kod penceresi görüntüler.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Bir Ayrıştırıcı arabirimi belirtmiyor ve ayrıştırıcı uygulamasıdır tamamen size kalmıştır. Ancak, varsayılan ayrıştırıcı uygulama Visual Studio dil paketi projede sağlanır. Yönetilen kod için yönetilen paket framework (MPF) metin renklendirme için tam destek sağlar.  
  
 Eski dil hizmetler bir VSPackage bir parçası olarak uygulanır, ancak dil hizmet özellikleri uygulamak için daha yeni MEF uzantıları kullanmak için bir yoludur. Söz dizimi renklendirme uygulamak için yeni yolu hakkında daha fazla bilgi için bkz: [izlenecek yol: Metin vurgulama](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
>  Yeni Düzenleyicisi API mümkün olan en kısa sürede kullanmaya başlamanızı öneriyoruz. Bu dil hizmetinizin performansını ve yeni Düzenleyicisi özelliklerden yararlanmak sağlar.  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Bir düzenleyici metin renklendirme tarafından izlenen adımları  
  
1.  Çağırarak Renklendirici düzenleyiciyi alır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> nesnesi.  
  
2.  Düzenleyici çağrıları <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> Renklendirici Renklendirici dışında tutulması için her bir satır durumunu gerekip gerekmediğini belirlemek için yöntem.  
  
3.  Renklendirici Renklendirici dışında tutulması durumuna gerektiriyorsa, Düzenleyicisi'ni çağırır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> ilk satırı durumunu almak için yöntem.  
  
4.  Arabelleği her satır için Düzenleyicisi'ni çağırır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> yöntemi aşağıdaki adımları gerçekleştirir:  
  
    1.  Metin satırının belirteçlere metni dönüştürmek için bir tarayıcı geçirilir. Her belirteç, belirteç metni ve belirteç türü belirtir.  
  
    2.  Belirteç türü colorable öğeleri listesinde bir dizine dönüştürülür.  
  
    3.  Belirteç bilgileri sağlayacak şekilde dizinin her öğesi satırdaki karakter karşılık gelen bir dizide doldurmak için kullanılır. Dizide saklanan colorable öğeleri listeye dizinler değerlerdir.  
  
    4.  Satırın sonundaki durumu, her satır için döndürülür.  
  
5.  Düzenleyicisi Renklendirici sürdürülmesi durumuna gerektiriyorsa, bu satır için durumu önbelleğe alır.  
  
6.  Döndürülen bilgileri kullanarak metin satırının Düzenleyicisi işler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> yöntemi. Bu, aşağıdaki adımları gerektirir:  
  
    1.  Satırda her bir karakter için colorable öğe dizini alın.  
  
    2.  Varsayılan colorable öğeleri kullanıyorsanız, düzenleyicinin colorable öğeleri listesi erişin.  
  
    3.  Aksi takdirde, dil hizmetin çağrısı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> colorable öğesi elde etmek için yöntemi.  
  
    4.  Bilgileri colorable öğesi metni görüntü oluşturmak için kullanın.  
  
## <a name="managed-package-framework-colorizer"></a>Yönetilen paket Framework Renklendirici  
 Yönetilen paket framework (MPF) bir Renklendirici uygulamak için gereken tüm sınıflar sağlar. Dil hizmet sınıfınızı alması gerektiğini <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı ve gerekli yöntemleri uygulayın. Tarayıcı ve ayrıştırıcı uygulayarak sağlamalısınız <xref:Microsoft.VisualStudio.Package.IScanner> arabirim ve bu arabirimden örneği döndürür <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> yöntemi (uygulanmalı yöntemlerden birini <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı). Daha fazla bilgi için bkz: [söz dizimi renklendirme eski dil hizmetindeki](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: yerleşik Colorable öğelerini kullanma](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Özel Colorable öğeler](../../extensibility/internals/custom-colorable-items.md)   
 [Eski dil hizmeti geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)