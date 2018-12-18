---
title: Hata ayıklama sayfası, Proje Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f16abf5fbf21678187a22efc9a368df7785057ab
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49271368"
---
# <a name="debug-page-project-designer"></a>Hata Ayıklama Sayfası, Proje Tasarımcısı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
> [!WARNING]
>  Bu konu, Windows Store uygulamaları için geçerli değil. Bkz: [(VB, C#, C++ ve XAML) bir hata ayıklama oturumunu başlatmada](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) Windows geliştirme Merkezi'nde.  
  
 Kullanım **hata ayıklama** sayfasının **Proje Tasarımcısı** davranışı Visual Basic veya C# projesinde hata ayıklama özelliklerini ayarlamak için.  
  
 Erişim için **hata ayıklama** sayfasında, içinde bir proje düğümü seçin **Çözüm Gezgini**. Üzerinde **proje** menüsünde seçin _ProjectName_**özellikleri**. Zaman **Proje Tasarımcısı** görünen tıklayın **hata ayıklama** sekmesi.  
  
## <a name="configuration-and-platform"></a>Yapılandırma ve Platform  
 Aşağıdaki seçenekler, görüntülenecek veya değiştirilecek platform ve yapılandırmayı seçmenize olanak sağlar.  
  
 **Yapılandırma**  
 Hangi yapılandırma ayarlarının görüntüleneceğini veya değiştirileceğini belirtir. Ayarları **hata ayıklama** (varsayılan), **yayın**, veya **yapılandırmalarında**. Daha fazla bilgi için [hata ayıklama ve dağıtım proje yapılandırmalarını](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 **Platform**  
 Platform ayarlarının görüntüleneceğini veya değiştirileceğini belirtir. Seçimleri içerebilir **herhangi bir CPU** (varsayılan), **x64**, ve **x86**. Daha fazla bilgi için [hata ayıklama ve dağıtım proje yapılandırmalarını](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
## <a name="start-action"></a>Başlatma eylemi  
 **Başlangıç eylemi** uygulamanın hataları ayıklanırken başlatılacak öğe belirtir: Proje, özel bir program, bir URL veya hiçbir şey. Varsayılan olarak, bu seçeneği ayarlamak **başlangıç projesi**. **Başlatma eylemi** ayarını **hata ayıklama** sayfa değerini belirler `StartAction` özelliği.  
  
 **Projeyi Başlat**  
 Yürütülebilir dosyası (Windows uygulaması ve konsol uygulaması projeleri) uygulamanın hataları ayıklanırken başlatılacak belirtmek için bu seçeneği belirleyin. Bu seçenek varsayılan olarak seçilidir.  
  
 **Harici program Başlat**  
 Uygulamanın hataları ayıklanırken belirli bir programı başlaması gerektiğini belirtmek için bu seçeneği belirleyin.  
  
 **Tarayıcı URL'si ile başlayın**  
 Uygulamanın hataları ayıklanırken belirli bir URL erişilmesi gerektiğini belirtmek için bu seçeneği belirleyin.  
  
## <a name="start-options"></a>Başlatma seçenekleri  
 **Komut satırı bağımsız değişkenleri**  
 Bu metin kutusunda, hata ayıklama için kullanılacak komut satırı bağımsız değişkenleri girin.  
  
 **Çalışma dizini**  
 Bu metin kutusunda, projeyi başlatılacak dizini girin. Veya Gözat düğmesine tıklayın (**...** ) için bir dizin seçin.  
  
 **Uzak makine kullanma**  
 Uzak bir bilgisayardan bir uygulamada hata ayıklamak için bu onay kutusunu seçin ve metin kutusunda bir uzak bilgisayara yolunu girin.  
  
## <a name="enable-debuggers"></a>Hata ayıklayıcıları etkinleştir  
 **Yönetilmeyen kodun hata ayıklamasını etkinleştir**  
 Bu seçenek yerel kodun Hata Ayıklamasının desteklenip desteklenmediğini belirtir. COM nesneleri çağrıları yapıyorsanız veya projenizi çağıran ve yerel kodda yazılmış özel bir program başlatma ve yerel kod hata ayıklama, bu onay kutusunu işaretleyin. Yönetilmeyen kodun hata ayıklamasını devre dışı bırakmak için bu onay kutusunu temizleyin. Bu onay kutusu varsayılan olarak işaretli değildir.  
  
 **SQL Server hata ayıklamayı etkinleştir**  
 Seçin veya etkinleştirin veya Visual Basic uygulamanızdan SQL yordamlarının hata ayıklama devre dışı bırakmak için bu onay kutusunu temizleyin. Bu onay kutusu varsayılan olarak işaretli değildir.  
  
 **Visual Studio barındırma işlemini etkinleştir**  
 Visual Studio barındırma işlemini etkinleştirmek için bu onay kutusunu seçin. Bu onay kutusu varsayılan olarak seçilidir. Daha fazla bilgi için [barındırma süreci (vshost.exe)](../../ide/hosting-process-vshost-exe.md).  
  
 Bir güvenlik bölgesinde hata ayıklamak için bu seçeneği etkinleştirin ve **bu uygulama için seçili izin kümesi ile hata ayıklama** içinde [Gelişmiş Güvenlik Ayarları iletişim kutusu](../../ide/reference/advanced-security-settings-dialog-box.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da hata ayıklama](../../debugger/debugging-in-visual-studio.md)   
 [Hata ayıklama yapılandırması proje ayarları C#](../../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Hata ayıklama yapılandırması proje ayarları bir Visual Basic](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Hata ayıklama özellikleri yönetme](http://msdn.microsoft.com/en-us/92474d16-e7fe-4fac-9287-6bd6b3a7eb68)   
 [Nasıl yapılır: sınırlı izinler ile ClickOnce uygulamasında hata ayıklama](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Nasıl Yapılır: Yapılandırmaları Oluşturma ve Düzenleme](../../ide/how-to-create-and-edit-configurations.md)



