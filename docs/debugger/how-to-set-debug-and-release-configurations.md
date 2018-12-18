---
title: Ayarlama hata ayıklama ve dağıtım yapılandırmalarını | Microsoft Docs
ms.custom: ''
ms.date: 10/05/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.builds
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a65a3331c210bdfb4143ff890180fdc7d663229
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257231"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Hata ayıklama ayarlayabilir ve yayın yapılandırmaları Visual Studio'da

Visual Studio projeleri ayrı sürümü ve hata ayıklama yapılandırması, programınız için. Hata ayıklama sürümünün hata ayıklama ve yayın sürümünü son sürüm dağıtımı oluşturun.

Hata ayıklama yapılandırmasında programınızı tam sembolik hata ayıklama bilgileri ve en iyileştirme olmadan derlenir. Kaynak kodu ve oluşturulan yönergeler arasındaki ilişki daha karmaşık olacağından en iyileştirme hata ayıklama, karmaşık hale getirir.

Programınızın sürüm yapılandırması simgesel hata ayıklama bilgisi ve tamamen en iyileştirilmiştir. Hata ayıklama bilgisi .pdb dosyaları oluşturulabilir [derleyici seçeneklerine bağlı olarak](#BKMK_symbols_release) kullanılan. .Pdb dosyaları oluşturmak, daha sonra yayım sürümünüzde hata ayıklama varsa yararlı olabilir.

Derleme yapılandırmaları hakkında daha fazla bilgi için bkz. [anlayın derleme yapılandırmaları](../ide/understanding-build-configurations.md).

Derleme yapılandırmasını değiştirebilirsiniz **derleme** menüsünde, araç çubuğundan veya projenin özellik sayfalarındaki. Dile özgü proje özellik sayfaları. Aşağıdaki yordam, menü ve araç, yapı yapılandırmasını değiştirme işlemi gösterilmektedir. Farklı dillerde projelerde derleme yapılandırmasını değiştirme hakkında daha fazla bilgi için bkz. [Ayrıca bkz:](#see-also) bölümüne bakın.

## <a name="change-the-build-configuration"></a>Derleme yapılandırmasını değiştirin

Yapı yapılandırmasını ya da değiştirmek için:

* Gelen **derleme** menüsünde **Configuration Manager**, ardından **hata ayıklama** veya **yayın**.

veya

* Ya da araç çubuğunda **hata ayıklama** veya **yayın** gelen **çözüm yapılandırmaları** listesi.

  ![araç çubukları oluşturma yapılandırma](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="BKMK_symbols_release"></a>Bir derleme için Sembol (.pdb) dosyalarını oluşturmak (C#, C++, Visual Basic F#)

Sembol (.pdb) dosyalarını ve hangi oluşturulacak seçebilirsiniz, hata ayıklama bilgilerini dahil etmek için. Çoğu proje türleri için hata ayıklama için varsayılan olarak, derleyici sembol dosyalarını oluşturur ve proje türüne ve Visual Studio sürümü tarafından diğer varsayılan ayarları farklı sırada yayın oluşturur.

> [!IMPORTANT]
> Hata ayıklayıcı, yalnızca yürütülebilir dosya oluşturulduğunda, oluşturulan .pdb dosyasıyla tam olarak eşleşen bir yürütülebilir dosya için bir .pdb dosyasını yükler (yani, .pdb özgün olmalı veya özgün .pdb'nin kopyasını olmalıdır). Daha fazla bilgi için [neden Visual Studio gerektiriyor hata ayıklayıcı sembol birlikte oluşturuldukları ikili dosyalarla tam olarak eşleşen dosyaları?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

Her proje türü, bu seçenekleri ayarlamak için farklı bir yol olabilir.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Bir C#, ASP.NET veya Visual Basic projesi için Sembol dosyaları oluştur

C# veya Visual Basic hata ayıklama yapılandırmaları için proje ayarları hakkında ayrıntılı bilgi için bkz: [hata ayıklama yapılandırması proje ayarları bir C#](../debugger/project-settings-for-csharp-debug-configurations.md) veya [hata ayıklama YapılandırmasıbirVisualBasicprojeayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. Çözüm Gezgini'nde projeyi seçin.

2. Seçin **özellikleri** simgesi (veya basın **Alt + Enter**).

3. Yan bölmede seçin **derleme** (veya **derleme** Visual Basic'te).

4. İçinde **yapılandırma** listesinde **hata ayıklama** veya **yayın**.

5. Seçin **Gelişmiş** düğme (veya **Gelişmiş derleme seçenekleri** düğme Visual Basic'te).

6. İçinde **hata ayıklama bilgileri** listesi (veya **hata ayıklama bilgileri üret** Visual Basic'te liste), seçin **tam**, **yalnızca Pdb**, veya **Taşınabilir**.

   Taşınabilir en son platformlar arası .NET Core için biçimdir. Seçenekler hakkında daha fazla bilgi için bkz. [Gelişmiş derleme Ayarları iletişim kutusu (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

   ![C# derlemeleri için pdb oluşturma](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. Projenizi yapılandırın.

   Derleyici sembol dosyaları aynı klasörde yürütülebilir dosyası ya da ana çıkış dosyası oluşturur.

### <a name="generate-symbol-files-for-a-c-project"></a>Sembol dosyaları için bir C++ projesi oluşturma

1. Çözüm Gezgini'nde projeyi seçin.

2. Seçin **özellikleri** simgesi (veya basın **Alt + Enter**).

3. İçinde **yapılandırma** listesinde **hata ayıklama** veya **yayın**.

4. Yan bölmede seçin **bağlayıcı > hata ayıklama**, ilgili seçenekleri seçin **hata ayıklama bilgisi Oluştur**.

   C++ hata ayıklama yapılandırmaları için proje ayarları hakkında ayrıntılı bilgi için bkz: [hata ayıklama yapılandırması proje ayarları bir C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

5. Seçeneklerini yapılandırmak **Program veritabanı dosyaları üretmek**.

   Çoğu C++ projelerinde varsayılan değerdir `$(OutDir)$(TargetName).pdb`, çıktı klasöründe .pdb dosyaları oluşturur.

   ![C++'ta yapılar için pdb oluşturma](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. Projenizi yapılandırın.

   Derleyici sembol dosyaları aynı klasörde yürütülebilir dosyası ya da ana çıkış dosyası oluşturur.

## <a name="see-also"></a>Ayrıca bkz:
 
[Visual Studio hata ayıklayıcısında simge (.pdb) dosyalarını ve kaynak dosyaları belirtin](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
[Hata ayıklayıcısı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)<br/>
[C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
[C# hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
[Visual Basic hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
[Nasıl yapılır: yapılandırmaları oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md)
