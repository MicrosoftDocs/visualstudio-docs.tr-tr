---
title: Derleme öncesi olay sonrası derleme olay komut satırı iletişim kutusu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEventsBuilder
- vb.ProjectPropertiesBuildEventsBuilder
helpviewer_keywords:
- $(SolutionExt)
- $(ProjectDir)
- $(TargetPath)
- $(ProjectExt)
- $(TargetFileName)
- $(PlatformName)
- $(SolutionName)
- macros, build events
- $(SolutionPath)
- $(ProjectPath)
- $(ProjectFileName)
- $(DevEnvDir)
- $(TargetName)
- $(TargetDir)
- $(SolutionDir)
- $(TargetExt)
- $(OutDir)
- $(ConfigurationName)
- $(SolutionFileName)
- $(ProjectName)
- build events, macros
ms.assetid: d49b2c57-24bf-4fb2-8351-5c4b6cca938f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e27a7e624607009e986d301fa802fdbe1597a3c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947979"
---
# <a name="pre-build-eventpost-build-event-command-line-dialog-box"></a>Derleme Öncesi Olay/Derleme Sonrası Olay Komut Satırı İletişim Kutusu
Oluşturma öncesi veya sonrası olayları yazabilirsiniz [derleme olayları sayfası, Proje Tasarımcısı (C#)](../../ide/reference/build-events-page-project-designer-csharp.md) doğrudan Düzenle kutusu veya öncesi ve sonrası derleme makroları kullanılabilir makroları listesinden seçebilirsiniz.

> [!NOTE]
> Oluşturma öncesi olaylar proje güncel olduğundan ve hiçbir derleme tetiklenir çalıştırmayın.


## <a name="ui-element-list"></a>UI öğe listesi
 **Komut satırı düzenleme kutusu**

 Oluşturma öncesi veya sonrası derleme için çalıştırılacak olayları içerir.

> [!NOTE]
> Ekleme bir `call` .bat dosyaları çalıştıran tüm sonrası derleme komutları önce deyim. Örneğin, `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat`.


 **Makroları**

 Komut satırı düzenleme kutusuna eklemek için makrolar listesini görüntülemek için düzenleme kutusuna genişletir.

 **Makro tablosu**

 Kullanılabilir makroları ve değerini listeler. Makrolar Aşağıda her bir açıklaması için bkz. Komut satırı düzenleme kutusuna eklemek için bir anda yalnızca bir makro seçebilirsiniz.

 **Ekle**

 Düzenleme kutusu makrosu tabloda seçilen makrosu komut satırını ekler.

### <a name="macros"></a>Makrolar
 Bu makroları birini dosyaları için konumlarını belirtin ya da birden çok seçimin durumunda giriş dosyasının gerçek adını almak için kullanabilirsiniz. Bu makrolar büyük küçük harfe duyarlı değildir.

|Makrosu|Açıklama|
|-----------|-----------------|
|`$(ConfigurationName)`|Geçerli proje yapılandırması, örneğin, "Hata ayıklama" adı.|
|`$(OutDir)`|Çıktı dosyası dizini proje dizine göreli yolu. Bu çıktı dizini özelliği için değer çözümler. Eğik içeren '\\'.|
|`$(DevEnvDir)`|Yükleme dizini, Visual Studio'nun (sürücü ve yol ile tanımlanan); eğik içeren '\\'.|
|`$(PlatformName)`|Şu anda hedeflenen platform adı. Örneğin, "AnyCPU".|
|`$(ProjectDir)`|(Sürücü ve yol ile tanımlanan); projenin dizini eğik içeren '\\'.|
|`$(ProjectPath)`|(Sürücü, yol, bir taban adına ve dosya uzantısı ile tanımlanır) projenin mutlak bir yol adı.|
|`$(ProjectName)`|Projenin temel adı.|
|`$(ProjectFileName)`|(Temel adı ve dosya uzantısı ile tanımlanır) proje dosya adı.|
|`$(ProjectExt)`|Projenin dosya uzantısı. İçerdiği '.' önce dosya uzantısı.|
|`$(SolutionDir)`|(Sürücü ve yol ile tanımlanan); çözüm dizini eğik içeren '\\'.|
|`$(SolutionPath)`|(Sürücü, yol, bir taban adına ve dosya uzantısı ile tanımlanır) çözümü mutlak bir yol adı.|
|`$(SolutionName)`|Çözümün temel adı.|
|`$(SolutionFileName)`|(Temel adı ve dosya uzantısı ile tanımlanır) çözüm dosya adı.|
|`$(SolutionExt)`|Çözüm dosya uzantısı. İçerdiği '.' önce dosya uzantısı.|
|`$(TargetDir)`|(Sürücü ve yol ile tanımlanan) derleme için birincil çıkış dosyasının dizin. Eğik içeren '\\'.|
|`$(TargetPath)`|(Sürücü, yol, bir taban adına ve dosya uzantısı ile tanımlanır) derleme için birincil çıkış dosyasının mutlak bir yol adı.|
|`$(TargetName)`|Derleme için birincil çıkış dosyasının temel adı.|
|`$(TargetFileName)`|(Temel adı ve dosya uzantısı olarak tanımlanan) derleme için birincil çıkış dosyasının dosya adı.|
|`$(TargetExt)`|Derleme için birincil çıkış dosyasının dosya uzantısı. İçerdiği '.' önce dosya uzantısı.|

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio'da Özel Derleme Olayları Belirtme](../../ide/specifying-custom-build-events-in-visual-studio.md)
- [Derleme Olayları Sayfası, Proje Tasarımcısı (C#)](../../ide/reference/build-events-page-project-designer-csharp.md)
- [Nasıl Yapılır: Derleme Olayları Belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Nasıl Yapılır: Derleme Olayları Belirtme (C#)](../../ide/how-to-specify-build-events-csharp.md)