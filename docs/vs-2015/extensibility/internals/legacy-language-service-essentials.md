---
title: Eski dil hizmeti temel bileşenleri | Microsoft Docs
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
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c878c4fe124d0443ab5f926a03a378b5b4af014
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753628"
---
# <a name="legacy-language-service-essentials"></a>Eski Dil Hizmeti Temel Bileşenleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir programlama dili, Visual Studio ile tümleştirmek için bir dil hizmeti sağlamanız gerekir. Bu konu eski dil Hizmetleri kullanılabilen özellikleri açıklar.  
  
 Eski dil Hizmetleri bir VSPackage'ı bir parçası olarak uygulanır, ancak dil hizmeti özellikleri uygulamak için daha yeni MEF uzantıları kullanmaktır. Dil hizmeti uygulamak için en yeni yolu hakkında daha fazla bilgi için bkz: [düzenleyici ve dil hizmeti uzantıları](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Yeni bir düzenleyici API hemen kullanmaya başlamak öneririz. Bu dil hizmetinizin performansını ve yeni düzenleyici özellikleri yararlanmanıza olanak tanır.  
  
 Eski dil Hizmetleri aşağıdaki özellikleri sağlar:  
  
|Özellik|Açıklama|  
|-------------|-----------------|  
|Söz dizimi renklendirmesi|Farklı renk ve yazı tipi stillerini farklı bir dil öğelerini görüntülemek Düzenleyici görünümü neden olur. Bu ayrım, dosyaları okuyup kolaylaştırabilir.<br /><br /> Genel bilgi için bkz. [eski dil hizmetinde söz dizimi renklerini](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Yönetilen paket çerçevesini (MPF)'deki bu özellik hakkında daha fazla bilgi için bkz: [eski dil hizmetinde söz dizimi renklendirme](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|  
|Deyim tamamlama|Bir deyim ya da kullanıcı yazmaya başlayıp anahtar sözcüğü tamamlar. Deyim tamamlama, daha az yazarak ve daha az hata olasılığını daha kolay zor ifadelerini girin kullanıcılara yardımcı olur.<br /><br /> Genel bilgi için bkz. [eski dil hizmetinde deyim tamamlama](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> MPF'deki bu özellik hakkında daha fazla bilgi için bkz: [eski dil hizmetinde Sözcük tamamlama](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|  
|Ayraç eşleştirme|Küme ayraçları gibi eşleştirilmiş karakterler vurgular. Ne zaman kullanıcı bir kapatma karakteri gibi türleri "}", ayraç Eşleştirme vurgular karakteri gibi açma karşılık gelen "{". Bu özellik, birkaç karakterini düzeyleri olduğunda, kullanıcıları kapsayan karakterleri çiftlerinin doğru olduğunu onaylayın yardımcı olur.<br /><br /> MPF'deki bu özellik hakkında daha fazla bilgi için bkz: [eski dil hizmetinde Ayraç eşleştirme](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|  
|Parametre bilgisi araç ipuçları|Kullanıcı şu anda yazarak aşırı yüklenmiş yöntem imzaları olası bir listesini görüntüler.<br /><br /> Genel bilgi için bkz. [eski dil hizmetinde parametre bilgisi](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> MPF'deki bu özellik hakkında daha fazla bilgi için bkz: [eski dil hizmetinde parametre bilgisi](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|  
|Hata işaretçileri|Dalgalı kırmızı alt çizgi, olarak da bilinen bir dalgalı sözdizimsel olarak yanlış metin altında görüntüler. Hata işaretçileri, genellikle kullanıcıların yazılmış anahtar sözcükler, kapatılmamış parantezler, geçersiz karakterler ve benzer hatalar haberdar olmak için kullanılır.<br /><br /> MPF sınıflarda, hata işaretçileri otomatik olarak işlenir <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> yöntemi <xref:Microsoft.VisualStudio.Package.AuthoringSink> sınıfı.|  
  
 Bu özelliklerin çoğu, kaynak kodu ayrıştırmak için dil hizmeti gerektirir. Belirteç oluşturma ve kod derleyici veya yorumlayıcı ayrıştırma sık yeniden kullanabilirsiniz.  
  
 Aşağıdaki özellikleri, programlama dili için destek ile ilgili ancak dil Hizmetleri bir parçası değildir:  
  
|Özellik|Açıklama|  
|-------------|-----------------|  
|İfade değerlendiricisi|Destekler [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] görüntülenecek kesme noktalarını doğrulama ve ifadelerin listesi sağladığı tarafından hata ayıklayıcı **Otolar** hata ayıklama penceresine.<br /><br /> Daha fazla bilgi için [hata ayıklama için dil hizmeti desteği](../../extensibility/internals/language-service-support-for-debugging.md).|  
|Sembol tarama araçlarını|Destekler **Nesne Tarayıcısı**, **sınıf görünümü**, **çağrı tarayıcısı**, ve **sembol sonuçları Bul**.|

