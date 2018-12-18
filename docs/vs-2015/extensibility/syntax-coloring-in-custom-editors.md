---
title: Özel düzenleyicilerde söz dizimi renklendirmesi | Microsoft Docs
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
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cc4d7f01a813332665a753a8a2aad54bea8a6980
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778676"
---
# <a name="syntax-coloring-in-custom-editors"></a>Özel Düzenleyicilerde Söz Dizimi Renklendirmesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çekirdek Düzenleyici dahil olmak üzere visual Studio ortamı SDK düzenleyicileri, belirli bir söz dizimi öğeleri tanımlamak ve bunları belirtilen belge görünümü için belirtilen renklerle görüntülemek için dil hizmetlerini kullanın.  
  
## <a name="colorization-requirements"></a>Renklendirme gereksinimleri  
 Bir dil hizmetin Renklendirici uygulama tüm düzenleyicileri gerekir:  
  
1.  Bir nesneyi uygulama kullanmak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> metin renklendirilmiş ve bir nesneyi uygulama yönetmek için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> metin belgesi bir görünümünü sağlamak için.  
  
2.  VSPackage'nın hizmet sağlayıcısı dilleri hizmetin tanımlayıcı GUID kullanarak sorgulayarak arabirime belirli dil hizmeti edinin.  
  
3.  Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> nesneyi uygulama yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Bu yöntem dil hizmeti ile ilişkilendirir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> renklendirilmiş için metin yönetmek için VSPackage'ı kullanan bir uygulama.  
  
## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Bir dil hizmetin Renklendirici çekirdek Düzenleyicisi kullanımı  
 Bir dil hizmeti ile bir Renklendirici çekirdek Düzenleyicisi, ayrıştırma ve metin tarafından bir dil hizmetin Renklendirici işleme bir örneği tarafından ne zaman elde otomatik olarak kazandırabileceği hakkında daha fazla müdahalesi gerektirmeden gerçekleştirilir.  
  
 IDE şeffaf bir şekilde:  
  
-   Ayrıştırma ve eklendiğinde veya değiştirildiğinde uygulamasında gibi metin analiz etmek için gerektiği şekilde Renklendirici çağırır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.  
  
-   Tarafından sağlanan belge görünümü tarafından sağlanan görüntü sağlar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> uygulama güncelleştirildi ve Renklendirici tarafından döndürülen bilgileri kullanarak yeniden çizilmesini.  
  
## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Bir dil hizmetin Renklendirici çekirdek olmayan Düzenleyicisi kullanımı  
 Temel olmayan Düzenleyicisi örnekleri bir dil hizmetin söz dizimi renklendirme hizmetini de kullanabilirsiniz, ancak bunlar açıkça almalı ve hizmetin Renklendirici uygulamak ve kendi belge görünümleri repaint.  
  
 Bunu yapmak için bir çekirdek olmayan düzenleyiciye gerektirir:  
  
1.  Bir dil hizmetin Renklendirici nesnesini alın (uygulayan `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). Çağırarak gerçekleştirir Bu, VSPackage <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> dil hizmetin arabirimi yöntemi.  
  
2.  Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metnin belirli bir aralık renklendirilmiş istemek için yöntemi.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Bir metindeki her harfi için span renklendirilmiş, yöntem değerlerin dizisini döndürür. Ayrıca, açıklama, anahtar sözcüğü veya veri türü gibi renklendirilebilir öğesinin belirli bir tür olarak metin aralığı tanımlar.  
  
3.  Tarafından döndürülen renklendirme bilgileri <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> repaint ve metnini görüntülemek için.  
  
> [!NOTE]
>  Bir dil hizmetin Renklendirici kullanmanın yanı sıra, genel amaçlı Visual Studio ortamı SDK metin renklendirmesi mekanizmasının kullanılması bir VSPackage'ı seçebilirsiniz. Bu mekanizma hakkında daha fazla bilgi için bkz. [kullanarak yazı tipleri ve renkler](../extensibility/using-fonts-and-colors.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski dil hizmetinde söz dizimi renklendirmesi](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Söz dizimi renklendirmesi uygulama](../extensibility/internals/implementing-syntax-coloring.md)   
 [Nasıl yapılır: yerleşik renklendirilebilir öğeleri kullanma](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Özel Renklendirilebilir Öğeler](../extensibility/internals/custom-colorable-items.md)

