---
title: Seçenekler, Metin Düzenleyici, C/C++, Biçimlendirme
ms.date: 04/30/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- CPP
helpviewer_keywords:
- Text Editor Options dialog box, formatting
- ClangFormat
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: ee7fab1564b39b29ae288e96c7aa77e0da21e88c
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36235147"
---
# <a name="options-text-editor-cc-formatting"></a>Seçenekler, Metin Düzenleyici, C/C++, Biçimlendirme

C veya C++ programlama yaparken Kod düzenleyicisinde varsayılan davranışını değiştirmek için bu özellik sayfalarını kullanın.

[Biçimlendirme C++ özellik sayfaları](media/cpp-formatting.png)

 İçinde bu sayfaya erişmek için **seçenekleri** iletişim kutusunda, sol bölmede, genişletin **metin düzenleyici**, genişletin **C/C++** ve ardından **biçimlendirme** .

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz: [Visual Studio IDE'yi kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-page"></a>Genel sayfası

Bu sayfa, siz yazarken biçimlendirme deyimleri ve blokları için seçenekleri vardır.

**Visual Studio 2017 15.7 ve sonraki sürümleri**: sayfasında de desteği için yapılandırma seçenekleri vardır [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) sürüm 5.0. ClangFormat stili ve bir .clang biçimi veya _clang biçimi dosyasında yapılandırılabilir kurallar kümesi göre kodunuzu biçimlendirmek kolaylaştıran bir yardımcı programdır.

### <a name="configuring-clangformat-options"></a>ClangFormat seçeneklerini yapılandırma

Visual Studio 2017 içinde 15.7 ve sonraki sürümleri, ClangFormat desteği varsayılan olarak etkindir. Tüm projeleriniz uygulamak için bu ortak biçimlendirme kuralları hangisinin seçebilirsiniz: LLVM, Google, Chromium, Mozilla veya WebKit. Özel biçim tanım .clang biçimi veya _clang biçimi dosyası da oluşturabilirsiniz. Proje klasöründe böyle bir dosya varsa, Visual Studio, tüm kaynak kodu dosyaları bu klasörde ve alt klasörlerine biçimlendirmek için kullanır. 

Varsayılan olarak, Visual Studio arka planda çalışır clangformat.exe yazarken biçimlendirme uygular. Çağrılan biçimlendirme komutlarını çalıştırmak için yalnızca el ile belirtebilirsiniz **belgeyi Biçimlendir (Ctrl + K, Ctrl + D)** veya **Biçim Seçimi (Ctrl + K, Ctrl + F)**.


## <a name="indentation-new-lines-spacing-wrapping-pages"></a>Girinti, yeni satırların aralık kaydırma sayfaları

Bu sayfaları çeşitli biçimlendirme özelleştirmeleri etkinleştirir, ancak ClangFormat etkinse, göz ardı edilir.

## <a name="see-also"></a>Ayrıca Bkz.

- [Genel, ortam, Seçenekler iletişim kutusu](../../ide/reference/general-environment-options-dialog-box.md)
- [IntelliSense Kullanma](../../ide/using-intellisense.md)