---
title: Eski dil hizmetindeki hızlı bilgi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ffdfe9bfb9063828a90dd9cdf3452ca3684ff0a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132165"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Eski dil hizmetindeki hızlı bilgi
IntelliSense Hızlı bilgileri kullanıcı tanımlayıcısını şapka yerleştirir ve seçer bu tanımlayıcıyı hakkında bilgileri kaynağında gösterir **hızlı bilgi** gelen **IntelliSense** menüsü veya fare tutar İmleç üzerinden tanımlayıcısı. Bu tanımlayıcı bilgiler görüntülenecek araç ipucu neden olur. Bu bilgiler, genel tanımlayıcı türü oluşur. Hata ayıklama altyapısı etkin olduğunda, bu bilgileri geçerli değeri içerebilir. Dil hizmeti yalnızca tanımlayıcıları işlerken hata ayıklama altyapısı ifade değer sağlıyor.  
  
 Eski dil hizmetler bir VSPackage bir parçası olarak uygulanır, ancak dil hizmet özellikleri uygulamak için daha yeni MEF uzantıları kullanmak için bir yoludur. Daha fazla bilgi bulmak için bkz: [izlenecek yol: Quıckınfo araç ipuçlarını görüntüleme](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).  
  
> [!NOTE]
>  Yeni Düzenleyicisi API mümkün olan en kısa sürede kullanmaya başlamanızı öneriyoruz. Bu dil hizmetinizin performansını ve yeni Düzenleyicisi özelliklerden yararlanmak sağlar.  
  
 Yönetilen paket framework (MPF) dil hizmet sınıfları, IntelliSense Hızlı bilgileri araç ipucu görüntülemek için tam destek sağlar. Yapmanız gereken tek şey görüntülenmesi ve hızlı bilgi özelliğini etkinleştirmek için metin girin.  
  
 Görüntülenecek metni çağırılarak alınır <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi ayrıştırıcı ayrıştırma neden değerini <xref:Microsoft.VisualStudio.Package.ParseReason>. Bu nedenle türü bilgileri (veya ne olursa olsun hızlı bilgi araç ipucunda görüntülenecek uygundur) elde etmek için ayrıştırıcı söyler belirtilen konumda tanımlayıcısı için <xref:Microsoft.VisualStudio.Package.ParseRequest> nesnesi. <xref:Microsoft.VisualStudio.Package.ParseRequest> Nesnesidir ne geçirilmedi <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi.  
  
 Ayrıştırıcının konumda kadar her şeyi ayrıştırma gerekir <xref:Microsoft.VisualStudio.Package.ParseRequest> tüm tanımlayıcılar türlerini belirlemek için nesne. Ardından ayrıştırıcı tanımlayıcı ayrıştırma isteği konumda almanız gerekir. Son olarak, ayrıştırıcı için bu kimlikle ilişkili araç ipucu veri geçmelidir <xref:Microsoft.VisualStudio.Package.AuthoringScope> söz konusu nesne metinden dönebilmeniz nesne <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> yöntemi.  
  
## <a name="enabling-the-quick-info-feature"></a>Hızlı bilgi özelliğini etkinleştirme  
 Hızlı bilgi özelliğini etkinleştirmek için ayarlamalısınız `CodeSense` ve `QuickInfo` parametrelerinin adlı <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Bu öznitelikler <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> ve <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> özellikleri.  
  
## <a name="implementing-the-quick-info-feature"></a>Hızlı bilgi özellik uygulama  
 <xref:Microsoft.VisualStudio.Package.ViewFilter> Sınıfı IntelliSense hızlı bilgi işlem işler. Zaman <xref:Microsoft.VisualStudio.Package.ViewFilter> sınıfı alır <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> komutu, sınıf çağrıları <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi ayrıştırma nedeni ile <xref:Microsoft.VisualStudio.Package.ParseReason> ve düzeltme zaman konumunu <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> komutu gönderildi. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Yöntemi ayrıştırıcısı belirtilen konum kadar kaynak ayrıştırma ve hızlı bilgi araç ipucunda görüntülenecek belirlemek için belirtilen konumda tanımlayıcı ayrıştırılamıyor.  
  
 Çoğu ayrıştırıcıları tüm kaynak dosyasının ilk bir ayrıştırma yapın ve sonuçları bir ayrıştırma ağacı depolayın. Tam ayrıştırma zaman aktarılan <xref:Microsoft.VisualStudio.Package.ParseReason> geçirilir <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi. Ayrıştırma, diğer tür ardından istenen bilgileri almak için Ayrıştırma Ağacı'nı kullanabilirsiniz.  
  
 Örneğin, ayrıştırma neden değerini <xref:Microsoft.VisualStudio.Package.ParseReason> kaynak konumundaki tanımlayıcı bulabilir ve arayın türü bilgilerini elde etmek için ayrıştırma ağacı. Bu tür bilgiler sonra geçirilir <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıfı ve tarafından döndürülen <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> yöntemi.