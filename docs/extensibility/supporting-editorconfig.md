---
title: Visual Studio'da EditorConfig desteklemek için bir dil hizmeti genişletme | Microsoft Docs
ms.custom: ''
ms.date: 11/22/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2aa80903b3e5ea2723ec576fa463161b8d003c93
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139480"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Dil hizmetiniz için EditorConfig destekleme

[EditorConfig](http://editorconfig.org/) dosyaları bir proje başına temelinde girinti boyutu gibi ortak metin düzenleyici seçenekleri açıklayan olanak tanır. EditorConfig dosyaları için Visual Studio'nun desteği hakkında daha fazla bilgi için bkz: [EditorConfig kullanarak taşınabilir Düzenleyici ayarları oluşturmak](../ide/create-portable-custom-editor-options.md).

Visual Studio dil hizmet uyguladığınızda çoğu durumda EditorConfig Evrensel özellikleri desteklemek için ek bir iş gereklidir. Çekirdek Düzenleyicisi'ni otomatik olarak bulur ve kullanıcıların dosyaları açmak ve uygun bir metin arabelleği ve görünüm seçeneklerini ayarlar .editorconfig dosyasını okur. Ancak, sekmeler ve alanları gibi düzenlemeleri için genel ayarları kullanmak yerine uygun bağlamsal metin Görünüm seçeneğini kullanmak için bazı dil hizmetler tercih. Bu durumlarda, dil hizmeti EditorConfig dosyaları destekleyecek şekilde güncelleştirilmesi gerekir.

Bir genel değiştirerek EditorConfig dosyaları desteklemek için bir dil hizmeti güncelleştirmek için gereken değişiklikler şunlardır _dile özgü_ seçeneğini bir _bağlamsal_ seçeneği:

## <a name="indent-style"></a>Girinti stili

Dile özgü seçenekleri | Bağlamsal seçenekleri
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|! textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>! textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Girinti boyutu

Dile özgü seçenekleri | Bağlamsal seçenekleri
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Sekme boyutu

Dile özgü seçenekleri | Bağlamsal seçenekleri
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Ayrıca bkz.

[EditorConfig kullanarak taşınabilir Düzenleyici ayarları oluştur](../ide/create-portable-custom-editor-options.md)  
[Düzenleyici ve dil Hizmetleri genişletme](../extensibility/extending-the-editor-and-language-services.md)