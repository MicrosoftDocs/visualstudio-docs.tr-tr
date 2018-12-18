---
title: 'Nasıl yapılır: projeleri hedef platformlar için yapılandırma'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2152f90d244ed283250bf8ea6a42a39b545f9c09
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847987"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Nasıl yapılır: projeleri hedef platformlar için yapılandırma

Visual Studio uygulamalarınızı 64 bit platformlar da dahil olmak üzere, farklı platformları hedeflemek için ayarlamanıza olanak tanır. Visual Studio 64-bit platform desteği hakkında daha fazla bilgi için bkz. [64-bit uygulamalar](/dotnet/framework/64-bit-apps).

## <a name="target-platforms-with-the-configuration-manager"></a>Configuration Manager ile hedef platformlar

**Configuration Manager** projenizle hedef hızla yeni bir platform eklemek bir yol sağlar. Visual Studio'ya dahil edildi platformlardan birini seçerseniz, seçilen platform için projenizi yaratmanız için projeniz için özellikleri değiştirilmiştir.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Bir 64 bit platformları hedefleyen bir proje yapılandırma

1.  Menü çubuğunda, **derleme** > **Configuration Manager**.

2.  İçinde **etkin çözüm platformu** listesinde, hedef çözümü için 64 bit platform seçin ve ardından **Kapat** düğmesi.

    1.  İstediğiniz platform görünmüyorsa **etkin çözüm platformu** listesinde **yeni**.

         **Yeni çözüm platformu** iletişim kutusu görüntülenir.

    2.  İçinde **yazın veya seçin yeni platformu** listesinde **x64**.

        > [!NOTE]
        >  Yapılandırmanızı yeni bir ad verin, ayarlarını değiştirmeniz gerekebilir **Proje Tasarımcısı** doğru platformunu hedeflemek için.

    3.  Geçerli bir platform yapılandırmasını ayarlar kopyalamak istiyorsanız, bunu seçin ve ardından **Tamam** düğmesi.

64-bit platformu hedefleyen tüm projeler için özellikler güncelleştirilir ve projenin sonraki derleme için 64-bit platformlarda iyileştirilir.

## <a name="target-platforms-in-the-project-designer"></a>Proje Tasarımcısı'nda Hedef platformlar

**Proje Tasarımcısı** ayrıca projenizle farklı platformları hedeflemek için bir yol sağlar. Listede bulunan platformlardan birini seçilirken **yeni çözüm platformu** iletişim kutusunda, çözümünüz için çalışmıyor, özel yapılandırma adı oluşturmak ve ayarlarını değiştirmeyi **Proje Tasarımcısı**  doğru platformunu hedeflemek için.

Bu görevi gerçekleştirmek, kullandığınız programlama diline göre değişir. Daha fazla bilgi için aşağıdaki bağlantılara bakın:

- İçin [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projeleri için bkz: [/Platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

- İçin [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projeleri için bkz: [derleme sayfası, Proje Tasarımcısı (C#)](../ide/reference/build-page-project-designer-csharp.md).

- İçin [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projeleri için bkz: [/CLR (ortak dil çalışma zamanı derlemesi)](/cpp/build/reference/clr-common-language-runtime-compilation).

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme platformlarını anlama](../ide/understanding-build-platforms.md)
- [/ Platform (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [64-bit uygulamalar](/dotnet/framework/64-bit-apps)
- [Visual Studio IDE 64 Bit desteği](../ide/visual-studio-ide-64-bit-support.md)
