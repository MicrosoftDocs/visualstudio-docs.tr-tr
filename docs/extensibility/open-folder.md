---
title: Visual Studio açık klasör genişletilebilirlik genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: dcb2d1d922b4ebd4943c42c478400c5873af9cc4
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36302982"
---
# <a name="open-folder-extensibility"></a>Açık klasör genişletilebilirliği

[Klasörünü Aç](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) özelliği sağlar açmak kullanıcıların herhangi bir Visual Studio Proje ya da çözüm dosyaları gerek kalmadan codebase. Klasör Aç özellikler kullanıcılar Visual Studio'dan gibi bekler sağlar:

* Çözüm Gezgini tümleştirme ve arama
* Düzenleyici renklendirme
* Git gezinme
* Dosyaları aramada Bul

.NET ve C++ geliştirme ettirilmesi gibi iş yükleri ile kullanıldığında, kullanıcılar ayrıca alın:

* Zengin IntelliSense
* Dile özgü işlevi

Açık klasörüyle uzantısı yazarlar Zengin özellikleri herhangi bir dil için oluşturabilirsiniz. Kullanıcının bir kullanıcı herhangi bir dosyada codebase yapı, hata ayıklama ve sembol arama desteği için API'ler vardır. Geçerli Extender'larının kodu projeleri veya bir çözüm yedekleme olmadan anlamak için mevcut Visual Studio özelliklerine güncelleştirebilirsiniz.

## <a name="an-api-without-project-systems"></a>Proje sistemleri olmadan bir API

Tarihsel olarak, Visual Studio, yalnızca bir çözüm ve proje sistemleri kullanarak projeleri dosyalarında anladım. Proje sistemi yüklenen bir proje için işlevselliği ve kullanıcı etkileşimler sorumludur. Proje içeriğinin başka proje bağımlılıkları görsel gösterimi, proje dosyaları, içerir ve arka plandaki değişikliği proje dosyası bilir. Bu hiyerarşileri ve diğer bileşenler, kullanıcı adına çalışır özellikleri aracılığıyla olmadığı. Tümü olarak kullanılabilecek kod temeli iyi bir proje ve çözüm yapısında sunulur. Komut dosyası dili ve Linux için C++ ile yazılmış açık kaynak kodu iyi verilebilir. Açık klasörüyle Visual Studio, kullanıcıların kendi kaynak kodu ile etkileşmek için yeni bir yol sağlar.

Açık klasörü altında apı'leridir `Microsoft.VisualStudio.Workspace.*` ad alanı ve Extender'larının üretmek ve veri veya açık klasördeki dosyalar geçici eylemlerini kullanmak kullanılabilir. Uzantıları dahil olmak üzere birçok alanlar için işlevselliği sağlamak için bu API'leri kullanabilirsiniz:

- [Çalışma alanları](workspaces.md) - açık klasörü noktası genişletilebilirlik başlayarak olduğunu çalışma ve API'lerini.
- [Dosya içerikleri ve eylemleri](workspace-file-contexts.md) -dosya dosya bağlamları sağlanan belirli bir kod gösterimi.
- [Dizin oluşturma](workspace-indexing.md) - toplamak ve klasör Aç çalışma alanları hakkında veri kalır.
- [Dil Hizmetleri](workspace-language-services.md) -Klasör Aç çalışma alanları halinde dil services tümleştirme.
- [Yapı](workspace-build.md) -yapı Klasör Aç çalışma alanları için destek.

Aşağıdaki türler kullanan özellikler Klasör Aç desteklemek için yeni API benimsemeyi gerekir:

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Geri bildirim, yorumlar, sorunları

Klasörü açın ve `Microsoft.VisualStudio.Workspace.*` apı'leridir etkin geliştirme aşamasındadır. Beklenmeyen davranışları görürseniz, ilgi sürüm için bilinen sorunlar bakın. [Geliştirici topluluğu](https://developercommunity.visualstudio.com) oy verin ve sorunları oluşturmak için önerilen yerdir. Her görüş için sorununuzu ayrıntılı bir açıklaması öneririz. İçin geliştirirken Visual Studio sürümü, (ne uyguladık ve ile etkileşim) kullandığınız API'leri, beklenen sonucu ve gerçek sonucunu içerir. Mümkünse, devenv.exe işlemin dökümünü içerir. GitHub'ın sorun geri Bu bildirimde için izleme kullanın ve ilgili belgelere.

## <a name="next-steps"></a>Sonraki adımlar

* [Çalışma alanları](workspaces.md) -API Klasör Aç çalışma hakkında bilgi edinin.