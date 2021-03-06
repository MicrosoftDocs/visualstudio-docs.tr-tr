---
title: Visual Studio çözümünün parçası olmayan bir uygulamada hata ayıklama
titleSuffix: ''
description: Visual Studio çözümünün bir parçası olmayan bir uygulamada hata ayıklamayı öğrenin. Visual Studio hata ayıklayıcısını iliştirebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/21/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f201121eb65f7c045ac42783ac71b2d49fafd802
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155009"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Visual Studio çözümünün parçası olmayan bir uygulamada hata ayıklama (C++, C#, Visual Basic, F #)

Visual Studio çözümünün parçası olmayan bir uygulamada (*. exe* dosyası) hata ayıklamak isteyebilirsiniz. Bu bir [açık klasör](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) projesi veya sizin ya da başka birinin uygulamayı Visual Studio dışında oluşturmuş olabileceği gibi, başka bir yerde de uygulamayı oluşturmuş olabilirsiniz.

- Visual Studio 'da (proje veya çözüm dosyası olmayan) bir açık klasör projesi için, bkz. [kodunuzu çalıştırma ve hata ayıklama](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md#run-and-debug-your-code) veya C++ için, [launch.vs.jsile hata ayıklama parametrelerini yapılandırma](/cpp/build/open-folder-projects-cpp#configure-debugging-parameters-with-launchvsjson).

- Visual Studio 'da mevcut olmayan bir uygulama için, hata ayıklamanın her bir yolu, uygulamayı Visual Studio dışında başlatmak ve sonra Visual Studio hata ayıklayıcısında **Işleme Ekle** ' yi kullanarak buna eklemektir. Daha fazla bilgi için bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

   Bir uygulamaya eklemek için birkaç saniye sürecek el ile adımlar gerekir. Bu gecikme nedeniyle, iliştirme bir başlatma sorununa hata ayıklamasına veya Kullanıcı girişini beklememe ve hızlı bir şekilde sona ermeyen bir uygulamaya yardımcı olmaz.

   Bu durumlarda, uygulama için bir Visual Studio EXE projesi oluşturabilir veya var olan bir C#, Visual Basic veya C++ çözümüne aktarabilirsiniz. Tüm programlama dilleri EXE projelerini desteklemez.

>[!IMPORTANT]
>Visual Studio 'da yerleşik olmayan bir uygulama için hata ayıklama özellikleri, uygulamaya iliştirip bir Visual Studio çözümüne eklemeye bakılmaksızın sınırlıdır.
>
>Kaynak kodunuz varsa, en iyi yaklaşım kodu bir Visual Studio projesine içeri aktarmalıdır. Sonra, uygulamanın hata ayıklama derlemesini çalıştırın.
>
>Kaynak kodunuz yoksa ve uygulamanın, uyumlu bir biçimde [hata ayıklama bilgileri](../debugger/how-to-set-debug-and-release-configurations.md) yoksa, kullanılabilir hata ayıklama özellikleri çok az olabilir.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>Mevcut bir uygulama için yeni bir EXE projesi oluşturmak için

1. Visual Studio 'da **Dosya**  >  **Aç**  >  **Proje**' yi seçin.

1. **Proje Aç** Iletişim kutusunda **dosya adı**' nın yanındaki açılan listede, önceden seçili değilse, **tüm proje dosyaları**' nı seçin.

1. *. Exe* dosyasına gidin, seçin ve **Aç**' ı seçin.

   Dosya, yeni, geçici bir Visual Studio çözümünde görüntülenir.

1. **Hata ayıklama menüsünden hata** **ayıklamayı Başlat** gibi bir yürütme komutu seçerek uygulamada hata ayıklamayı başlatın.

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>Bir uygulamayı var olan bir Visual Studio çözümüne aktarmak için

1. Visual Studio 'da bir C++, C# veya Visual Basic çözümü açıkken **Dosya**  >  **ekleme**  >  **Varolan proje**' yi seçin.

1. **Proje Aç** Iletişim kutusunda **dosya adı**' nın yanındaki açılan listede, önceden seçili değilse, **tüm proje dosyaları**' nı seçin.

1. *. Exe* dosyasına gidin, seçin ve **Aç**' ı seçin.

   Dosya, geçerli çözüm altında yeni bir proje olarak görünür.

1. Yeni dosya seçili **olduğunda hata ayıklama menüsünden hata** **ayıklamayı Başlat** gibi bir yürütme komutu seçerek uygulamada hata ayıklamayı başlatın.

### <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcısı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)
- [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)
- [DBG dosyaları](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))
