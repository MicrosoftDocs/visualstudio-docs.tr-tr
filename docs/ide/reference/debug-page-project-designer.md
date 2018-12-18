---
title: Hata Ayıklama Sayfası, Proje Tasarımcısı
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e7bc849a48161fdf1763517f90514dfb464b74e
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37090029"
---
# <a name="debug-page-project-designer"></a>Hata Ayıklama Sayfası, Proje Tasarımcısı

Kullanım **hata ayıklama** sayfasında **Proje Tasarımcısı** davranışı bir Visual Basic veya C# projesinde hata ayıklama özelliklerini ayarlamak için.

Erişim için **hata ayıklama** sayfası, proje düğümü seçin **Çözüm Gezgini**. Üzerinde **proje** menüsünde seçin  **\<ProjectName > Özellikler**. Zaman **Proje Tasarımcısı** görünen tıklatın **hata ayıklama** sekmesi.

> [!NOTE]
> Bu konu, UWP uygulamaları için geçerli değil. Bkz: [(VB, C#, C++ ve XAML) bir hata ayıklama oturumu Başlat](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) UWP uygulamalar için.

## <a name="configuration-and-platform"></a>Yapılandırması ve platformu

Aşağıdaki seçenekler yapılandırma ve görüntülemek veya değiştirmek için platform seçmenize olanak tanır.

**Yapılandırma**

Görüntülemek veya değiştirmek için hangi yapılandırma ayarlarını belirtir. Ayarları **hata ayıklama** (varsayılan), **sürüm**, veya **tüm yapılandırmaları**.

**Platform**

Görüntülemek veya değiştirmek için hangi platform ayarlarını belirtir. Seçimleri içerebilir **herhangi bir CPU** (varsayılan), **x64**, ve **x86**.

## <a name="start-action"></a>Eylemi Başlat

**Eylemi Başlat** uygulama hata ayıklaması başlattığınızda öğeyi belirtir: Proje, özel bir program, bir URL veya hiçbir şey. Varsayılan olarak, bu seçeneği ayarlanmış **başlangıç projesi**. **Eylemi Başlat** ayarı **hata ayıklama** sayfa belirler değerini `StartAction` özelliği.

**Başlangıç projesi**

Uygulama hata ayıklaması olduğunda çalıştırılabilir dosyanın (Windows uygulaması ve konsol uygulaması projeleri) başlaması gerektiğini belirtmek için bu seçeneği belirleyin. Bu seçenek varsayılan olarak seçilidir.

**Dış program Başlat**

Uygulama hata ayıklaması sırasında belirli bir programı başlaması gerektiğini belirtmek için bu seçeneği belirleyin.

**URL ile tarayıcıyı başlatın**

Uygulama hata ayıklaması sırasında belirli bir URL erişilmesi gerektiğini belirtmek için bu seçeneği belirleyin.

## <a name="start-options"></a>Başlatma seçenekleri

**Komut satırı bağımsız değişkenleri**

Bu metin kutusunda, hata ayıklama için kullanılacak komut satırı bağımsız değişkenleri girin.

**Çalışma dizini**

Bu metin kutusunda projenin başlatılacak dizini girin. Veya Gözat düğmesine (**...** ) bir dizin seçin.

**Uzak makine kullanın**

Uzak bir bilgisayardan uygulama hatalarını ayıklamak için bu onay kutusunu seçin ve metin kutusuna bir uzak bilgisayara yolunu girin.

## <a name="debugger-engines"></a>Hata ayıklayıcı motorları

**Yerel kod hata ayıklamayı etkinleştir**

Bu seçenek yerel kodda hata ayıklama desteklenip desteklenmediğini belirtir. COM nesnelerine çağrıları yapıyorsanız veya projenizin çağıran yerel kodda yazılan özel bir programı başlatın ve yerel kod hata ayıklama, bu onay kutusunu seçin. Yönetilmeyen kod hata ayıklama devre dışı bırakmak için bu onay kutusunu temizleyin. Bu onay kutusu varsayılan olarak işaretli değildir.

**SQL Server hata ayıklamayı etkinleştir**

Seçin veya etkinleştirmek veya SQL yordamları, Visual Basic uygulamasında hata ayıklama devre dışı bırakmak için bu onay kutusunu temizleyin. Bu onay kutusu varsayılan olarak işaretli değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da hata ayıklama](../../debugger/debugging-in-visual-studio.md)
- [Proje ayarları için C# hata ayıklama yapılandırmaları](../../debugger/project-settings-for-csharp-debug-configurations.md)
- [Hata ayıklama yapılandırması proje ayarları bir Visual Basic](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Nasıl yapılır: Sınırlı İzinler ile ClickOnce Uygulamasında Hata Ayıklama](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [Nasıl Yapılır: Yapılandırmaları Oluşturma ve Düzenleme](../../ide/how-to-create-and-edit-configurations.md)