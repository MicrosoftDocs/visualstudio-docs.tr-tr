---
title: Eski dil hizmeti Features1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0c931147d20454a920e20cec61e1f6000a9b043d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131746"
---
# <a name="legacy-language-service-features"></a>Eski dil hizmeti özellikleri
Yönetilen paket framework (MPF) dil hizmeti bir veya daha fazla destekleyebilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sözdizimi vurgulama, IntelliSense ve kesme noktası doğrulama gibi özellikleri. Her bir özelliğin diğer bağımsız olarak uygulanabilir ancak tüm bir Ayrıştırıcıyı ve yalnızca bir tarayıcı gerektiren sözdizimi vurgulama dışında bir tarayıcı gerektirir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Eski Dil Hizmetinde Ayraç Eşleştirme](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 Dil çifti olarak da bilinen eşleşen Ayraç eşleştirme desteklemek için gerekli olan açıklar.  
  
 [Eski Dil Hizmetinde Koda Açıklama Ekleme](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 Yorum oluşturma ve seçili kodunu uncommenting desteklemek için gerekli olan açıklar.  
  
 [Eski Dil Hizmetinde Özel Belge Özellikleri](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 Bir kaynak dosyasında katıştırılmış belge özelliklerini desteklemek için gerekli olan açıklar.  
  
 [Eski Dil Hizmetinde Ana Hat Oluşturma](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 Gizli bölgeler uygulama anahat oluşturma desteklemek için gerekli olan açıklar.  
  
 [Eski Dil Hizmetinde Kodu Yeniden Biçimlendirme](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 Yeniden biçimlendirme kodu desteklemek için gerekli olan açıklar.  
  
 [Eski Dil Hizmetinde Kod Parçacıkları için Destek](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 Eklenir ve düzenlenebilir kesimlerin kodunun kod parçacıkları desteklemek için gerekli olan açıklar.  
  
 [Eski dil hizmetindeki parametre bilgisi](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 Yöntem yazıldığı gibi bir yöntem imzası görüntüleme için IntelliSense parametre bilgisi işlemi desteklemek için gerekli olan açıklar.  
  
 [Eski Dil Hizmetinde Hızlı Bilgiler](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 Tanımlayıcı hakkında bilgi görüntülemek için IntelliSense Hızlı bilgileri işlemi desteklemek için gerekli olan açıklar.  
  
 [Eski Dil Hizmetinde Üye Tamamlama](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 Bir ad alanı üyesi bir listeden seçmek için IntelliSense üye tamamlama işlemi desteklemek için gereken açıklar.  
  
 [Eski Dil Hizmetinde Sözcük Tamamlama](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 Kısmen yazılan sözcükler tamamlamak için IntelliSense tam sözcüğü işlemi desteklemek için gerekli olan açıklar.  
  
 [Eski Dil Hizmetinde Otomatik Değişkenler Penceresi için Destek](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 Bir dil hizmeti desteklemek için yapabileceğiniz açıklanır **otomobiller** hata ayıklarken penceresi.  
  
 [Eski Dil Hizmetinde Otomatik Değişkenler Penceresi için Destek](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Nasıl kullanılacağını açıklar **gezinti çubuğu** herhangi bir tür veya üye bu görünümde gösterilen dosyasında Hızlı gezinme sağlamak için Düzenleyicisi görünümünün üstte...  
  
 [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 Kaynak kodu sözdizimi vurgulama desteklemek için gerekli olan açıklar.  
  
 [Eski Dil Hizmetinde Kesme Noktalarını Doğrulama](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 Bir dil hizmeti bir hata ayıklayıcı dışında doğrulama kesme noktaları desteklemek için yapabileceklerinizi açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Eski Dil Hizmeti Ayrıştırıcısı ve Tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Ayrıştırıcı ve yönetilen paket framework kullanan bir dil hizmetin tüm özelliklerini uygulamak için gereken tarayıcı açıklar.  
  
 [Eski dil hizmeti uygulama](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Bir dil hizmeti MPF kullanarak uygulamak için gereken nedir açıklar.  
  
 [Eski dil hizmeti kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Bir dil MPF tabanlı hizmete kaydolmak için gereken adımları açıklar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [IntelliSense Kullanma](../../ide/using-intellisense.md)  
 Nasıl IntelliSense dil başvuruları erişmek kolaylaştırır açıklanmaktadır.  
  
 [Eski dil hizmeti uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Yönetilen paket framework (MPF) tam özellikli dil hizmeti yönetilen koda uygulanması için nasıl kullanılacağı hakkında bilgi sağlar.