---
title: Bir .NET Framework sürümünü hedefleme
ms.date: 02/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- .NET Framework version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3673d3c57a33d99c3c26dd22cd5c2b7b8959e7d6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059476"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Nasıl yapılır: .NET Framework sürümü hedefleme

Bu belge, bir sürümünü hedefleyecek şekilde açıklar varolan bir Visual Basic içinde hedeflenen sürümün nasıl değiştirileceğini ve bir proje oluşturduğunuzda, .NET Framework'ün C#, veya Visual F# proje.

> [!IMPORTANT]
> C++ projeleri için hedef sürümü değiştirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: hedef framework ve platform araç takımını değiştirmek](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="to-target-a-version-when-you-create-a-project"></a>Projenizi oluştururken bir sürümü hedeflemek için

Bir proje oluşturduğunuzda, kullanılabilir .NET Framework sürümlerinin hangi sürümlerinin yüklü olduğunu ve seçili şablonda bağlıdır **yeni proje** iletişim kutusu.

1. Menü çubuğunda, **dosya** > **yeni** > **proje**.

1. Yüklü Şablonlar listesinde oluşturmak istediğiniz proje türünü seçin ve proje için bir ad girin.

1. Gelen **Framework** altındaki açılır listede **yeni proje** iletişim kutusunda, projenizin hedeflemesini istediğiniz .NET Framework sürümünü seçin.

    Çerçeve listesi yalnızca seçtiğiniz şablon için geçerli olan sürümler gösterilmektedir. .NET Core gibi bazı proje türleri, .NET Framework gerektirmez. Böyle durumlarda, **Framework** açılır listede gizlenir.

    ![Framework açılan yeni proje iletişim kutusunda](media/vside-newproject-framework.png)

1. Seçin **Tamam** düğmesi.

## <a name="to-change-the-targeted-version"></a>Hedeflenen sürümü değiştirmek için

Visual Basic'te .NET Framework'ün hedeflenen sürümünü değiştirebilirsiniz C#, veya Visual F# bu yordamı izleyerek proje.

C++ projeleri için hedef sürümü değiştirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: hedef framework ve platform araç takımını değiştirmek](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

1. İçinde **Çözüm Gezgini**, değiştirin ve ardından istediğiniz projenin kısayol menüsünü **özellikleri**.

    ![Visual Studio Çözüm Gezgini özellikleri](../ide/media/vs_slnexplorer_properties.png)

1. Sol sütununda **özellikleri** penceresinde seçin **uygulama** sekmesi.

    ![Visual Studio uygulama özellikleri uygulama sekmesi](../ide/media/vs_slnexplorer_properties_applicationtab.png)

    > [!NOTE]
    > Bir UWP uygulaması oluşturduktan sonra hedeflenen Windows ya da .NET Framework sürümü değiştirilemiyor.

1. İçinde **hedef Framework'ü** listesinde, istediğiniz sürümü seçin.

1. Görüntülenen doğrulama iletişim kutusunda seçin **Evet** düğmesi.

    Projenin yüklemesi kaldırılır. Yeniden yüklediğinde, seçtiğiniz .NET Framework sürümünü hedefler.

    > [!NOTE]
    > Kodunuz hedeflediğinizden farklı bir .NET Framework sürümüne başvurular içeriyorsa, kodu derlediğinizde veya çalıştırdığınızda hata iletileri görülebilir. Bu hataları gidermek için başvuruları değiştirmeniz gerekir. Bkz: [.NET Framework hedefleme hatalarının sorunlarını giderme](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio çoklu sürüm desteğine genel bakış](../ide/visual-studio-multi-targeting-overview.md)
- [.NET Framework hedefleme hatalarının sorunlarını giderme](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)
- [Uygulama sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Uygulama sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Nasıl yapılır: hedef framework ve platform araç takımını (C++) değiştirme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)