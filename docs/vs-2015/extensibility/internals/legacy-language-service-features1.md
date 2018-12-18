---
title: Eski dil hizmeti özellikleri1 | Microsoft Docs
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
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bb66895066d0af1259c3509c40ec9fa4458e3f79
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774074"
---
# <a name="legacy-language-service-features"></a>Eski dil hizmeti özellikleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir yönetilen paket framework (MPF) dil hizmeti bir veya daha fazla destekleyebilir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] söz dizimi vurgulama, IntelliSense ve kesme noktası doğrulama gibi özellikler. Her bir özellik diğerlerinden bağımsız olarak uygulanabilir ancak tüm bir ayrıştırıcı ve yalnızca bir tarayıcı gerektiren söz dizimi vurgulama dışında bir tarayıcı gerektirir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Eski Dil Hizmetinde Ayraç Eşleştirme](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 Dil çifti olarak da bilinen eşleşen Ayraç eşleştirme desteklemek için gereken açıklar.  
  
 [Eski Dil Hizmetinde Koda Açıklama Ekleme](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 Yorum ve seçili kodu uncommenting desteklemek için gereken açıklar.  
  
 [Eski Dil Hizmetinde Özel Belge Özellikleri](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 Kaynak dosyada gömülü bir belge özellikleri desteklemek için gereken açıklar.  
  
 [Eski Dil Hizmetinde Ana Hat Oluşturma](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 Gizli bölgeler uygulaması ana hat oluşturmayı desteklemek için gereken açıklar.  
  
 [Eski Dil Hizmetinde Kodu Yeniden Biçimlendirme](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 Kodu yeniden biçimlendirme desteklemek için gereken açıklar.  
  
 [Eski Dil Hizmetinde Kod Parçacıkları için Destek](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 Eklenir ve düzenlenebilir kod parçalarını olan kod parçacıkları desteklemek için gereken açıklar.  
  
 [Eski Dil Hizmetinde Parametre Bilgileri](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 Yöntem yazıldığı gibi bir yöntem imzasını görüntülemek için IntelliSense parametre bilgisi işlemi desteklemek için gereken açıklar.  
  
 [Eski Dil Hizmetinde Hızlı Bilgiler](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 Bir tanımlayıcı hakkında bilgi görüntülemek için IntelliSense hızlı bilgi işlemi desteklemek için gereken açıklar.  
  
 [Eski Dil Hizmetinde Üye Tamamlama](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 Bir ad alanı üyesi bir listeden seçmek için IntelliSense üye tamamlama işlemi desteklemek için gereken açıklar.  
  
 [Eski Dil Hizmetinde Sözcük Tamamlama](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 Kısmen yazılan sözcükleri tamamlama tam sözcük IntelliSense işlemi desteklemek için gereken açıklar.  
  
 [Eski Dil Hizmetinde Otomatik Değişkenler Penceresi için Destek](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 Dil hizmeti desteklemek için neler yapabileceğinizi açıklayan **Otolar** ayıklarken penceresi.  
  
 [Eski Dil Hizmetinde Otomatik Değişkenler Penceresi için Destek](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Nasıl kullanılacağını açıklar **gezinti çubuğu** sayfanın üst kısmında, herhangi bir tür veya üye bu görünümde gösterilen dosyasındaki gezinmenin hızlı gerçekleşmesini sağlamak için düzenleyici görünümü...  
  
 [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 Kaynak kodunun söz dizimi vurgulama desteklemek için gereken açıklar.  
  
 [Eski Dil Hizmetinde Kesme Noktalarını Doğrulama](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 Dil hizmeti bir hata ayıklayıcı dışında doğrulama kesme noktalarını desteklemek için neler yapabileceğinizi açıklayan.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Eski Dil Hizmeti Ayrıştırıcısı ve Tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Yönetilen paket çerçevesini kullanan bir dil hizmetinin tüm özellikleri uygulamak için gerekli olan tarayıcı ve ayrıştırıcı açıklar.  
  
 [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Dil hizmeti MPF uygulamak için gereken açıklar.  
  
 [Eski Dil Hizmeti Kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Bir dil MPF tabanlı hizmetiyle kaydetmek için gerekli adımları açıklayan [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [IntelliSense Kullanma](../../ide/using-intellisense.md)  
 Açıklayan nasıl IntelliSense dili başvuruları şekilde erişmek çok kolay hale getirir.  
  
 [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Yönetilen kodda bir tam özellikli dil hizmeti uygulamak için yönetilen paket çerçevesini (MPF) kullanma hakkında bilgi sağlar.

