---
title: 'Öğretici 1: Resim Görüntüleyici oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0cdc926121212a8082fac126e4ab91b753df7dee
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884972"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Eğitmen 1: Resim Görüntüleyici Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu öğreticide, bir dosyadan resim yükleyen ve pencerede görüntüleyen bir program oluşturun. Düğmeler ve resim kutuları, form üzerindeki özellikleri ayarlamak ve sorunsuz formu yeniden boyutlandırmak için kapsayıcıları kullanma gibi denetimleri Sürüklemeyi öğrenin. Ayrıca, kod yazmaya başlayın. Aşağıdakilerin nasıl yapıldığını öğreneceksiniz:  
  
- Yeni bir proje oluşturun.  
  
- Test (hata ayıklama) bir uygulama.  
  
- Bir forma onay kutuları ve düğmeler gibi temel denetimler ekleyin.  
  
- Düzenleri kullanarak form üzerinde denetimleri yerleştirin.  
  
- Ekleme **açık dosya** ve **renk** bir forma iletişim kutuları.  
  
- IntelliSense ve kod parçacıkları kullanarak kod yazın.  
  
- Olay işleyicisi yöntemleri yazın.  
  
  İşiniz bittiğinde, programınız aşağıdaki resim gibi görünecektir.  
  
  ![Bu öğreticide oluşturduğunuz resim](../ide/media/express-pictureviewerdone.png "Express_PictureViewerDone")  
  Bu öğreticide oluşturduğunuz resim  
  
  Örnek tamamlanmış bir sürümünü indirmek için bkz [eksiksiz resim görüntüleyici Öğreticisi örneği](http://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).  
  
  ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo")bu konunun video sürümü için bkz. [nasıl ı: Resim Görüntüleyici oluşturma Visual Basic'te?](http://go.microsoft.com/fwlink/?LinkId=205207) veya [nasıl ı: Resim Görüntüleyici oluşturma C#?](http://go.microsoft.com/fwlink/?LinkId=205198).  
  
> [!NOTE]
>  Bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar olduğundan bu videolarda Visual Studio'nun önceki bir sürümü kullanın. Ancak, kavramlar ve yordamlar benzer şekilde Visual Studio'nun geçerli sürümünde çalışır. Visual C# ve Visual Basic hem de Bu öğreticide ele alınmaktadır; bu nedenle kullandığınız programlama diline özgü bilgilere odaklanın.  
>   
>  Visual Basic için kod görmek için **VB** sekmesinde kod blokları üstündeki ve Visual C# kodunu görmek için **C#** sekmesi. Visual C++ hakkında bilgi almakla ilgileniyorsanız bkz [Başlarken](../misc/getting-started-with-visual-cpp-in-visual-studio-2015.md) ve [C++ dil Eğitmeni](http://www.cplusplus.com/doc/tutorial/).  
>   
>  Visual C# veya Visual Basic uygulamaları için Windows Store yazma öğrenmek istiyorsanız [C# veya Visual Basic kullanarak ilk Windows Store uygulamasını oluşturma](http://msdn.microsoft.com/library/windows/apps/hh974581.aspx). Windows Store için JavaScript uygulamaları oluşturma hakkında daha fazla bilgi için bkz: [JavaScript kullanarak ilk Windows Store uygulamasını oluşturma](http://msdn.microsoft.com/library/windows/apps/br211385.aspx).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[1. Adım: Windows Forms Uygulaması Projesi Oluşturma](../ide/step-1-create-a-windows-forms-application-project.md)|Bir Windows Forms uygulaması projesi oluşturarak başlayın.|  
|[2. Adım: Programınızı Çalıştırma](../ide/step-2-run-your-program.md)|Önceki adımda oluşturduğunuz Windows Forms uygulama programını çalıştırın.|  
|[3. Adım: Form Özelliklerinizi Ayarlama](../ide/step-3-set-your-form-properties.md)|Yolu kullanarak formunuzun görünüşünü değiştirin **özellikleri** penceresi.|  
|[4. Adım: TableLayoutPanel Denetimi ile Formunuzu Düzenleme](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Ekleme bir `TableLayoutPanel` form denetimi.|  
|[5. Adım: Formunuza Denetimler Ekleme](../ide/step-5-add-controls-to-your-form.md)|Denetimleri gibi ekleme bir `PictureBox` denetimi ve bir `CheckBox` form denetimi. Formunuza düğmeler ekleyin.|  
|[6. Adım: Düğme Denetimlerinizi Adlandırma](../ide/step-6-name-your-button-controls.md)|Düğmelerinizi daha anlamlı olarak yeniden adlandırın.|  
|[7. Adım: Formunuza İletişim Kutusu Bileşenleri Ekleme](../ide/step-7-add-dialog-components-to-your-form.md)|Ekleme bir **OpenFileDialog** bileşeni ve bir **ColorDialog** formunuza bileşen.|  
|[8. Adım: Resim Göster Düğmesi Olay İşleyicisi için Kod Yazma](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|IntelliSense aracını kullanarak kod yazın.|  
|[9. Adım: Kodunuzu Gözden Geçirme, Açıklama ve Test Etme](../ide/step-9-review-comment-and-test-your-code.md)|Gözden geçirin ve kodunuzu test edin. Gerektiği gibi açıklamaları ekleyin.|  
|[10. Adım: Ek Düğmeler ve Onay Kutusu için Kod Yazma](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Diğer düğmelerin ve IntelliSense kullanarak onay kutusu iş yapmak için kod yazın.|  
|[11. Adım: Programınızı Çalıştırma ve Diğer Özellikleri Deneme](../ide/step-11-run-your-program-and-try-other-features.md)|Programınızı çalıştırmak ve arka plan rengini ayarlayın. Renkleri, yazı tiplerini ve kenarlıkları değiştirme gibi diğer özellikleri deneyin.|



