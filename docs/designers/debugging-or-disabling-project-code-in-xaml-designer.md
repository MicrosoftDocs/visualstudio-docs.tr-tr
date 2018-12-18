---
title: XAML Tasarımcısı’nda proje kodu hatalarını ayıklama veya proje kodunu devre dışı bırakma
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 191d180a68edd439c729fa963b607c992ff3c00e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816817"
---
# <a name="debug-or-disable-project-code-in-xaml-designer"></a>XAML Tasarımcısı’nda proje kodu hatalarını ayıklama veya proje kodunu devre dışı bırakma

Çoğu durumda, İşlenmeyen özel durumları **XAML** Tasarımcısı özellikleri veya yöntemleri farklı değerler döndürür veya tasarımcıda uygulamanız çalıştığında zaman farklı bir şekilde iş erişmeye çalışan proje kodunu tarafından kaynaklanabilir. Visual Studio'nun başka bir örnek proje kodunda hata ayıklama tarafından bu özel durumları çözmek veya Tasarımcısı'nda proje kodu devre dışı bırakarak özel durumlar geçici olarak engelleyin.

Proje kodu içerir:

-   Özel denetimler ve kullanıcı denetimleri

-   Sınıf kitaplıkları

-   Değer dönüştürücüler

-   Proje koddan oluşturulan tasarım zamanı verilerine karşı bağlamaları

Visual Studio, proje kodunu devre dışı bırakıldığında, yer tutucuları gösterir. Örneğin, Visual Studio veriler artık kullanılabilir olduğu bir bağlama veya artık çalışan bir denetim için bir yer tutucu için özellik adını gösterir.

![İşlenmeyen özel durum iletişim kutusu](../designers/media/xaml_unhandledexception.png)

## <a name="to-determine-if-project-code-is-causing-an-exception"></a>Proje kodu bir özel durum neden olup olmadığını belirlemek için

1.  İşlenmeyen özel durum iletişim kutusunda seçin **tasarımcıyı yeniden yüklemek için burayı tıklatın** bağlantı.

2.  Menü çubuğunda **hata ayıklama** > **hata ayıklamayı Başlat** oluşturun ve uygulamayı çalıştırın.

     Uygulama oluşturur ve başarıyla çalıştığından, tasarım zamanı özel durum Tasarımcısı'nda çalışan proje kodunu nedeni olabilir.

## <a name="to-debug-project-code-running-in-the-designer"></a>Tasarımcıda çalışan proje kodu hatalarını ayıklamak için

1.  İşlenmeyen özel durum iletişim kutusunda seçin **çalışan proje kodunu devre dışı bırakmak ve tasarımcıyı yeniden yüklemek için burayı tıklatın** bağlantı.

2.  Windows Görev Yöneticisi'nde seçin **Görevi Sonlandır** çalışmakta olan tüm örneklerini Visual Studio XAML Tasarımcısı'nı kapatmak için düğme.

     ![Görev Yöneticisi'nde XAML Tasarımcısı örnekleri](../designers/media/xaml_taskmanager.png)

3.  Visual Studio'da kod veya hata ayıklamak istediğiniz denetimi içeren XAML sayfası açın.

4.  Visual Studio'nun yeni bir örneğini açın ve ardından projenizi ikinci bir örneğini açın.

5.  Proje kodunuzda bir kesme noktası ayarlayın.

6.  Menü çubuğunda, Visual Studio, yeni bir örneğini seçin **hata ayıklama** > **iliştirme**.

7.  İçinde **iliştirme** iletişim, **kullanılabilir işlemler** listesinde **XDesProc.exe**ve ardından **iliştirme** düğmesi.

     ![XAML Tasarımcısı işlemi](../designers/media/xaml_attach.png)

     XAML Tasarımcısı'nda Visual Studio ilk örneğinin işlemidir.

8.  Visual Studio menü çubuğunda, ilk örneğini seçin **hata ayıklama** > **hata ayıklamayı Başlat**.

     Artık tasarımcıda çalıştıran kodunuzla geçebilirsiniz.

## <a name="to-disable-project-code-in-the-designer"></a>Tasarımcısı'nda proje kodu devre dışı bırakmak için

-   İşlenmeyen özel durum iletişim kutusunda seçin **çalışan proje kodunu devre dışı bırakmak ve tasarımcıyı yeniden yüklemek için burayı tıklatın** bağlantı.

-   Alternatif olarak, araç çubuğunda **XAML Tasarımcısı**, seçin **proje kodunu devre dışı bırak** düğmesi.

     ![Proje kodunu devre dışı bırak düğmesi](../designers/media/xaml_disablecode.png)

     Proje kodu tekrar etkinleştirmeniz için düğmesine geçiş yapabilirsiniz.

    > [!NOTE]
    > ARM veya X64 hedefleyen projeler için işlemcileri, Visual Studio Tasarımcısı'nda proje kodu çalıştırılamaz böylece **proje kodunu devre dışı bırak** Tasarımcısı'nda düğmesi devre dışı.

-   İki seçenekten birini yeniden ve tüm ilişkili proje kodunu devre dışı bırakmak Tasarımcı neden olur.

    > [!NOTE]
    > Proje kodunu devre dışı bırakmak için tasarım zamanı veri kaybına neden olabilir. Tasarımcıda çalışan kodda hata ayıklamak için kullanılan bir alternatiftir.

## <a name="control-display-options"></a>Denetim görüntüleme seçenekleri

> [!NOTE]
> **Denetim görüntüleme seçenekleri** yalnızca Windows 10 Fall Creators Update (derleme 16299) hedefleyen Evrensel Windows platformu uygulamaları için kullanılabilir veya üzeri. **Denetimi görüntüleme seçeneklerini** özelliği Visual Studio 2017 15,9 veya sonraki bir sürümü kullanılabilir. 

XAML Tasarımcısı'nda, yalnızca Windows SDK platform denetimlerini görüntülemek için Denetim görüntüleme seçeneklerini değiştirebilirsiniz. Bu XAML tasarımcının güvenilirliğini artırabilir.

Denetim görüntüleme seçeneklerini değiştirmek için Tasarımcı penceresinin sol alt simgeyi tıklatın ve ardından altındaki bir seçenek belirleyin **denetimi görüntüleme seçeneklerini**:

![Denetim görüntüleme seçenekleri](../designers/media/control_display_options.png)

Seçtiğinizde, **yalnızca görüntü platformu denetimleri**, SDK'larından gelen tüm özel denetimleri, müşteri kullanıcı denetimleri ve daha fazla değil işleme tamamen. Bunun yerine, bunlar denetimin konumunu ve boyutunu göstermek için geri dönüş denetimleri tarafından değiştirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ve Visual Studio için Blend, XAML tasarım](../designers/designing-xaml-in-visual-studio.md)
