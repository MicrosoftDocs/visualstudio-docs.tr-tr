---
title: 'Önceki .NET Framework sürümleri için F # hedef'
description: "F # kullanarak Visual Studio'da .NET Framework'ün daha eski bir sürümü hedefleme hakkında bilgi edinin."
ms.date: 07/11/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: troubleshooting
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2cb32f37bde0a55da081105cbee52a8744db2b88
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38978505"
---
# <a name="target-older-versions-of-net-f"></a>Hedef eski sürümlerini .NET (F #)

.NET Framework 2.0 kullanan denerseniz, Windows 8.1 Visual Studio yüklü olduğunda 3.0 veya 3.5 bir F # proje aşağıdaki hata görünebilir:

**Bu proje 2.0 F # çalışma zamanının gerektirir, ancak bu çalışma zamanı yüklü değil.**

Bu hata koşulları altında aşağıdaki birleşimi bilinmektedir:

- Windows 8.1 Visual Studio yüklenmiş.

- Visual Studio yüklemeden önce .NET Framework 3.5 etkinleştirme kaydetmedi.

- Projeniz .NET Framework 2.0, 3.0 veya 3.5 hedefler.

Visual Studio yükleme sırasında .NET Framework'ün yüklü sürümlerini algılar. .NET Framework 3.5 yalnızca yüklü ve etkin değilse visual Studio 2.0 F # çalışma zamanı yükler.

## <a name="resolve-the-error"></a>Hatayı çözün

Bu hatayı gidermek için şunlardan birini yapabilirsiniz:

- Hedef .NET Framework'ün daha yeni bir sürümü.

- Windows 8.1 üzerinde .NET Framework 3.5 etkinleştirin ve ardından Visual Studio yüklemesini onararak F # 2.0 çalışma zamanını yükleyin. Bunu yapmak için adımları izleyin.

### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Windows 8.1 üzerinde .NET Framework 3.5 etkinleştirmek için

1. Üzerinde **Başlat** ekranında, yazın **Denetim Masası**.

   Siz yazarken **Denetim Masası** simgesi görünür altında **uygulamaları** başlığı.

2. Seçin **Denetim Masası** simgesini seçin **programlar** simgesini seçip **kapatma Windows özelliklerini aç veya Kapat** bağlantı.

3. Emin olun **.NET Framework 3.5 (.NET 2.0 ve 3.0 içerir)** onay kutusunun seçili olduğundan ve ardından **Tamam** düğmesi. .NET Framework'ün isteğe bağlı bileşenler için herhangi bir alt düğüm için onay kutularını işaretleyin gerek yoktur.

   Zaten yapmadıysanız, .NET Framework 3.5 etkinleştirilir.

### <a name="to-install-the-f-20-runtime"></a>F # 2.0 çalışma zamanı yüklemek için

İzleyin [onarım Visual Studio 2017 için adımları](../install/repair-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F # Kılavuzu (.NET Framework)](/dotnet/fsharp/)
- [Visual Studio'da F #](fsharp-visual-studio.md)