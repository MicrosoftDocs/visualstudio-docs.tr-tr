---
title: XAML Tasarımcısı'nda proje kodu devre dışı bırakma veya hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2507b509ee33957845f010f7c18404d257ad4a38
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837587"
---
# <a name="debugging-or-disabling-project-code-in-xaml-designer"></a>XAML Tasarımcısı'nda proje kodu devre dışı bırakma veya hata ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çoğu durumda, özellikleri veya yöntemleri farklı değerler döndürür veya Uygulama Tasarımcısı'nda çalışırken farklı şekillerde çalışır erişmeye çalışan proje kodu tarafından işlenmemiş özel durumlar XAML Tasarımcısı'nda neden olabilir. Visual Studio'nun başka bir örnek proje kodunda hata ayıklama tarafından bu özel durumları çözmek veya geçici olarak Tasarımcısı'nda proje kodu devre dışı bırakarak engelleyin.  
  
 Proje kodu içerir:  
  
- Özel denetimler ve kullanıcı denetimleri  
  
- Sınıf kitaplıkları  
  
- Değer dönüştürücüler  
  
- Proje koddan oluşturulan tasarım zamanı verilerine karşı bağlamaları  
  
  Visual Studio Proje kodunu devre dışı bırakıldığında, yer tutucuları gösterir veriler kullanılabildiği artık; bir bağlama için özellik adı gibi veya artık çalışan bir denetim için bir yer tutucu.  
  
  ![İşlenmeyen özel durum iletişim](../designers/media/xaml-unhandledexception.png "XAML_UnhandledException")  
  
#### <a name="to-determine-if-project-code-is-causing-an-exception"></a>Proje kodu bir özel durum neden olup olmadığını belirlemek için  
  
1.  İşlenmeyen özel durum iletişim kutusunda seçin **tasarımcıyı yeniden yüklemek için burayı tıklatın** bağlantı.  
  
2.  Menü çubuğunda **hata ayıklama**, **hata ayıklamayı Başlat** oluşturun ve uygulamayı çalıştırın.  
  
     Uygulama oluşturur ve başarıyla çalıştığından, tasarım zamanı özel durum Tasarımcısı'nda çalışan proje kodunu nedeni olabilir.  
  
#### <a name="to-debug-project-code-running-in-the-designer"></a>Tasarımcıda çalışan proje kodu hatalarını ayıklamak için  
  
1.  İşlenmeyen özel durum iletişim kutusunda seçin **çalışan proje kodunu devre dışı bırakmak ve tasarımcıyı yeniden yüklemek için burayı tıklatın** bağlantı.  
  
2.  Windows Görev Yöneticisi'nde seçin **Görevi Sonlandır** çalışmakta olan tüm örneklerini Visual Studio XAML Tasarımcısı'nı kapatmak için düğme.  
  
     ![XAML Tasarımcısı örnekleri Görev Yöneticisi'nde](../designers/media/xaml-taskmanager.png "XAML_TaskManager")  
  
3.  Visual Studio'da kod veya hata ayıklamak istediğiniz denetimi içeren XAML sayfası açın.  
  
4.  Visual Studio'nun yeni bir örneğini açın ve ardından projenizi ikinci bir örneğini açın.  
  
5.  Proje kodunuzda bir kesme noktası ayarlayın.  
  
6.  Menü çubuğunda, Visual Studio, yeni bir örneğini seçin **hata ayıklama**, **iliştirme**.  
  
7.  İçinde **iliştirme** iletişim, **kullanılabilir işlemler** listesinde **XDesProc.exe**ve ardından **iliştirme** düğmesi.  
  
     ![XAML Tasarımcısı işlem](../designers/media/xaml-attach.png "XAML_Attach")  
  
     XAML Tasarımcısı'nda Visual Studio ilk örneğinin işlemidir.  
  
8.  Visual Studio'nun ilk örnekte, menü çubuğunda **hata ayıklama**, **hata ayıklamayı Başlat**.  
  
     Artık tasarımcıda çalıştıran kodunuzla geçebilirsiniz.  
  
#### <a name="to-disable-project-code-in-the-designer"></a>Tasarımcısı'nda proje kodu devre dışı bırakmak için  
  
-   İşlenmeyen özel durum iletişim kutusunda seçin **çalışan proje kodunu devre dışı bırakmak ve tasarımcıyı yeniden yüklemek için burayı tıklatın** bağlantı.  
  
-   Alternatif olarak, XAML Tasarımcısı araç çubuğunda **proje kodunu devre dışı bırak** düğmesi.  
  
     ![Proje kodunu devre dışı bırak düğmesi](../designers/media/xaml-disablecode.png "XAML_DisableCode")  
  
     Proje kodu tekrar etkinleştirmeniz için düğmesine geçiş yapabilirsiniz.  
  
    > [!NOTE]
    >  ARM veya X64 hedefleyen projeler için işlemcileri, Visual Studio Tasarımcısı'nda proje kodu çalıştırılamaz böylece **proje kodunu devre dışı bırak** Tasarımcısı'nda düğmesi devre dışı.  
  
-   İki seçenekten birini tasarımcıyı yeniden yüklemek neden olur ve ardından tüm ilişkili proje kodunu devre dışı bırakır.  
  
    > [!NOTE]
    >  Proje kodunu devre dışı bırakmak için tasarım zamanı veri kaybına neden olabilir. Tasarımcıda çalışan kodda hata ayıklamak için kullanılan bir alternatiftir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio ve Visual Studio İçin Blend Uygulamalarında XAML Tasarlama](../designers/designing-xaml-in-visual-studio.md)





