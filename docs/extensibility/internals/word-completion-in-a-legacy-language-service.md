---
title: Eski dil hizmetinde Sözcük tamamlama | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 55fbe636c77d77b3b4f61f9f56a4fa91fe49a090
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879083"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Sözcük Tamamlama
Kısmen belirlenmiş bir Word eksik karakter Sözcük tamamlama doldurur. Yalnızca bir olası tamamlanma varsa, sözcük tamamlama karakter girildiğinde tamamlandı. Kısmi sözcüğün birden fazla olasılığını eşleşiyorsa tamamlanabilir listesi görüntülenir. Bir tamamlama karakter tanımlayıcıları için kullanılmayan herhangi bir karakter olabilir.  
  
 Eski dil Hizmetleri bir VSPackage'ı bir parçası olarak uygulanır, ancak dil hizmeti özellikleri uygulamak için daha yeni MEF uzantıları kullanmaktır. Daha fazla bilgi için bkz. [düzenleyiciyi ve dil hizmetlerini genişletme](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Yeni bir düzenleyici API hemen kullanmaya başlamak öneririz. Bu dil hizmetinizin performansını ve yeni düzenleyici özellikleri yararlanmanıza olanak tanır.  
  
## <a name="implementation-steps"></a>Uygulama adımları  
  
1. Kullanıcı seçtiğinde **tam sözcük** gelen **IntelliSense** menüsünde <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> komut dil hizmetine gönderilir.  
  
2. <xref:Microsoft.VisualStudio.Package.ViewFilter> Sınıfı komut ve çağrılarını yakalar <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> yöntemi ayrıştırma nedeni ile <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
3. <xref:Microsoft.VisualStudio.Package.Source> Sınıfı ardından çağrıları <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> olası sözcük tamamlamaları ve araç ipucu sözcükler listesi kullanarak sonra görüntüler listesini almak için yöntemi <xref:Microsoft.VisualStudio.Package.CompletionSet> sınıfı.  
  
    Eşleşen tek bir sözcük ise <xref:Microsoft.VisualStudio.Package.Source> sınıfı word tamamlar.  
  
   Alternatif olarak, tarayıcı tetikleme değerini döndürürse <xref:Microsoft.VisualStudio.Package.TokenTriggers> bir tanımlayıcının ilk karakteri yazıldığında <xref:Microsoft.VisualStudio.Package.Source> sınıfı, bunu algılar ve çağıran <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> yöntemi ayrıştırma nedeni ile <xref:Microsoft.VisualStudio.Package.ParseReason>. Bu durumda ayrıştırıcı bir üye seçimi karakterin varolup olmadığını algılamak ve bu üye listesini sağlamanız gerekir.  
  
## <a name="enabling-support-for-the-complete-word"></a>Tam sözcük desteğini etkinleştirme  
 Sözcük tamamlama kümesi desteğini etkinleştirmek için `CodeSense` geçirilen parametre adlı <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> dil paket ile ilişkili kullanıcı özniteliği. Bu ayarlar <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> özelliği <xref:Microsoft.VisualStudio.Package.LanguagePreferences> sınıfı.  
  
 Ayrıştırma neden değeri için yanıt bildirimleri listesi, ayrıştırıcı döndürmelidir <xref:Microsoft.VisualStudio.Package.ParseReason>, sözcük tamamlama çalışılacak.  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>Tam sözcük ParseSource yöntemi uygulama  
 Sözcük tamamlama <xref:Microsoft.VisualStudio.Package.Source> sınıf çağrıları <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metodunda <xref:Microsoft.VisualStudio.Package.AuthoringScope> olası sözcük eşleşme listesini almak için sınıf. Türetilen bir sınıfta listenin uygulamalıdır <xref:Microsoft.VisualStudio.Package.Declarations> sınıfı. Bkz: <xref:Microsoft.VisualStudio.Package.Declarations> uygulanmalı yöntemleri hakkında ayrıntılar için sınıf.  
  
 Listede yalnızca tek bir sözcük, varsa sonra <xref:Microsoft.VisualStudio.Package.Source> sınıfı kısmi sözcük yerine bu sözcüğü otomatik olarak ekler. Listede birden fazla sözcük varsa <xref:Microsoft.VisualStudio.Package.Source> sınıfı sunan bir araç ipucu listesi, kullanıcının uygun seçeneği seçebilirsiniz.  
  
 Aynı zamanda örneğe bakmaktır bir <xref:Microsoft.VisualStudio.Package.Declarations> sınıfı uygulamasında [eski dil hizmetinde üye tamamlama](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).