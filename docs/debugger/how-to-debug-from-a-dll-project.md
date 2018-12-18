---
title: 'Nasıl yapılır: DLL projesinde hata ayıklama | Microsoft Docs'
ms.custom: ''
ms.date: 10/10/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e006bbd27acc0fa88cfee1b22cb435acba1e282e
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388260"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio-c-c-visual-basic-f"></a>Nasıl yapılır: Visual Studio'da bir DLL projesinden hata ayıklama (C#, C++, Visual Basic F#)

DLL projesinde hata ayıklama yollarından biri, çağıran uygulama DLL proje özelliklerinde belirtmektir. Ardından, DLL projesinden kendisini hata ayıklamaya başlayabilirsiniz. Çalışmak bu yöntem için uygulama, yapılandırmadan biri ile aynı konumda aynı DLL'nin çağırmanız gerekir. Bu sürüm, uygulamayı bulur ve farklı bir DLL sürümünü yükler, kesme noktalarınız içermez. DLL'lerinde hata ayıklama diğer yöntemleri için bkz. [hata ayıklama DLL projelerinde](../debugger/debugging-dll-projects.md).
  
Yönetilen uygulamanızın yerel bir DLL çağırır veya yerel uygulamanızı yönetilmiş DLL'ye çağrı, DLL hem çağıran uygulama hata ayıklama yapabilirsiniz. Daha fazla bilgi için [nasıl yapılır: karışık modda hata ayıklama](../debugger/how-to-debug-in-mixed-mode.md).   

Yerel ve yönetilen DLL projelerinde arama uygulamaları belirtmek için farklı ayarları vardır. 

## <a name="specify-a-calling-app-in-a-native-dll-project"></a>Çağıran bir uygulama içinde yerel bir DLL projesi belirtin  
  
1. C++ DLL projesinde seçin **Çözüm Gezgini**. Seçin **özellikleri** simgesi, tuşuna **Alt**+**Enter**, veya sağ tıklayıp seçin **özellikleri**.
   
1. İçinde  **\<Proje > özellik sayfaları** iletişim kutusunda, emin **yapılandırma** pencerenin üst kısmındaki alanı **hata ayıklama**. 
   
1. Seçin **yapılandırma özellikleri** > **hata ayıklama**.  
   
1. İçinde **başlatmak için hata ayıklayıcı** listesinde **yerel Windows hata ayıklayıcı** veya **uzaktan Windows hata ayıklayıcı**.  
   
1. İçinde **komut** veya **uzaktan komut** kutusunda, tam yolunu ve dosya arama uygulaması aşağıdaki gibi ekleyin bir *.exe* dosya.
   
   ![Özellikler penceresi hata ayıklama](../debugger/media/dbg-debugging-properties-dll.png "hata ayıklama Özellikler penceresi")  
   
1. Tüm gerekli program bağımsız değişkenleri eklemek **komut satırı bağımsız değişkenlerini** kutusu.  
   
1. Seçin **Tamam**.

## <a name="specify-a-calling-app-in-a-managed-dll-project"></a>Çağıran bir uygulama içinde yönetilen bir DLL projesi belirtin  
  
1. C# veya Visual Basic DLL projesini seçin **Çözüm Gezgini**. Seçin **özellikleri** simgesi, tuşuna **Alt**+**Enter**, veya sağ tıklayıp seçin **özellikleri**.
   
1. Emin olun **yapılandırma** pencerenin üst kısmındaki alanı **hata ayıklama**.
   
1. Altında **başlangıç eylemi**:
   
   - .NET Framework dll dosyaları için seçin **harici program Başlat**, çağıran bir uygulama adı ve tam yolunu ekleyin.
     
   - Ya da seçin **Başlat tarayıcı URL ile** ve yerel bir ASP.NET uygulamasının URL'sini girin. 
   
   - .NET Core DLL'ler **hata ayıklama** özellikleri sayfasında farklıdır. Seçin **yürütülebilir** gelen **başlatma** açılır listesinde ve ardından tam yolunu ve çağıran uygulamada adını ekleyin **yürütülebilir** alan. 
   
1. Tüm gerekli komut satırı bağımsız değişkenleri eklemek **komut satırı bağımsız değişkenleri** veya **uygulamanın bağımsız değişkenleri** alan.
   
   ![C# hata ayıklama özellikleri penceresi](../debugger/media/dbg-debugging-properties-dll-csharp.png "C# hata ayıklama Özellikler penceresi") 
   
1. Kullanım **dosya** > **seçili öğeleri Kaydet** veya **Ctrl**+**S** değişiklikleri kaydedin.

## <a name="debug-from-the-dll-project"></a>DLL projesinde hata ayıklama  
 
1. DLL projesinde kesme noktaları ayarlayın.

1. DLL projesini sağ tıklatın ve seçin **başlangıç projesi olarak ayarla**. 

1. Emin **çözümleri yapılandırma** ayarlanmış **hata ayıklama**. Tuşuna **F5**, yeşil tıklayın **Başlat** ok ya da seçin **hata ayıklama** > **hata ayıklamayı Başlat**.

Hata ayıklama, kesme noktaları isabet etmiyor, DLL dosyanızı çıkış emin olun (varsayılan olarak,  *\<Proje > \Debug* klasör) çağıran uygulama çağırma konumdur.
  
## <a name="see-also"></a>Ayrıca bkz.  
 [DLL projelerinde hata ayıklama](../debugger/debugging-dll-projects.md)   
 [Hata ayıklama yapılandırması proje ayarları C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)