---
title: Office projelerinde erişilebilirlik
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9c39a68d13e2fd3d4932e169e713ed8534e0d266
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305136"
---
# <a name="accessibility-in-office-projects"></a>Office projelerinde erişilebilirlik
  Microsoft Visual Studio ve Microsoft Office standart erişilebilirlik gereksinimlerini karşılayan özel çözümler oluşturmanıza olanak tanıyan birçok erişilebilirlik özelliği içerir. Microsoft Erişilebilirlik Web için yönergeler yayımlar. Ayrıntılar için bkz [Erişilebilirlik Web sitesi](http://go.microsoft.com/fwlink/?LinkID=37113).  

 Çoğu durumda, Visual Studio'da Office projeleri çözümlerinizi erişilebilir hale getirmek için ayarlayabileceğiniz erişilebilirlik standartlarını veya kullanıma sunan özellikleri karşılayın. Ancak, sınırlı erişilebilirliği olan bazı özellikler vardır.  

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  

## <a name="accessibility-at-design-time"></a>Tasarım zamanında erişilebilirlik  

### <a name="use-shortcut-keys-in-document-level-projects"></a>Belge düzeyinde projelerde kısayol tuşlarını kullanın  
 Microsoft Office Word belgesinden veya Microsoft Office Excel çalışma kitabı Visual Studio'da açık olduğunda, aynı anda yalnızca bir uygulama kısayol tuşu komutlarını alır. Varsayılan olarak, Visual Studio tüm kısayol tuşu komutlarını alır, ancak Word veya Excel belge seçerek odağa sahip olduğunda bildirim ve mesajları alacak yapabileceğiniz **dinamik klavye düzeni** üzerinde **klavye ayarları** sayfası ' ın **seçenekleri** iletişim kutusu. Daha fazla bilgi için [Microsoft Office Word Klavyesi, Microsoft Office Klavyesi ayarları, Seçenekler iletişim kutusu](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) ve [Microsoft Office Excel Klavyesi, Microsoft Office Klavyesi ayarları, Seçenekler iletişim kutusu](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).  

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Belge düzeyi projelere Şeritte kısayol tuşları görüntüleme  
 Visual Studio'da açık bir Word belgesi veya Excel çalışma kitabı olduğunda tuşuna basılamıyor **Alt** sekmeleri ve Şerit üzerindeki denetimleri için kısayol tuşlarını görmek için anahtar. Belge veya çalışma kitabını tasarımcıda açık durumdayken, kısayol tuşlarını görüntülemek için aşağıdaki adımları gerçekleştirin.  

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Tasarımcıda Şerit sekmeler ve denetimler için kısayol tuşlarını görüntülemek için  

1.  Visual Studio'da üzerinde **Araçları** menüsünde tıklatın **seçenekleri**.  

2.  Genişletin **Office Araçları** düğüm ve select **Microsoft Office Excel Klavyesi** veya **Microsoft Office Word Klavyesi**uygun şekilde.  

3.  Seçin **dinamik klavye düzeni**.  

     Visual Studio değişikliğin etkili olması için yeniden başlatmanız gerektiğini belirten bir ileti görüntülenir.  

4.  **Tamam**'ı tıklatın.  

5.  Visual Studio'yu yeniden başlatın ve projenizi yeniden açın.  

6.  Projeniz için belge veya çalışma kitabı Tasarımcısı'nı açın.  

7.  Tuşuna **F6** kısayol tuşları için Şerit görüntülenecek.  

## <a name="accessibility-at-runtime"></a>Çalışma zamanında erişilebilirlik  

### <a name="windows-forms-controls-on-office-documents"></a>Office belgelerindeki Windows Forms denetimleri  
 Windows Forms denetimleri, ekran okuyucular gibi erişilebilirlik Yardımcıları denetimi ile ilgili bilgi sağlamak için erişilebilirlik özellikleri kullanıma sunar. Belge düzeyi özelleştirmesindeki bir Office belgesi üzerinde denetimleri olduğunda bu erişilebilirlik özelliklerinden yararlanabilirsiniz. Daha fazla bilgi için [bir Windows formundaki denetimler için erişilebilirlik bilgileri sağlayan](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).  

 Ancak, Windows Forms denetimlerini bir Excel çalışma kitabı veya Word belgesi üzerinde barındırıldığında zamanında bazı erişilebilirlik sınırlamalar vardır:  

- Başka bir denetimden sekme olamaz.  

- Belgenin yakınlaştırma ayarı % 100 dışında değiştirdiğinizde, bir belge denetimleri devre dışı bırakıldı.  

  Belgelerindeki Windows Forms denetimleri sınırlamaları hakkında daha fazla bilgi için bkz. [sınırlamalar, Windows Forms denetimleri Office belgelerini](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  

### <a name="actions-panes-and-custom-task-panes"></a>Eylemler bölmeleri ve özel görev bölmeleri  
 Bir eylemler bölmesi veya özel görev bölmesi odağa sahip olduğunda, denetimleri bir Windows Forms uygulaması denetimlere eriştiğiniz gibi erişebilirsiniz. İmlecinizi, Eylemler bölmesi ve belge arasında taşımak için basabilirsiniz **F6**.  

 Eylemler bölmesi ve özel görev bölmeleri hakkında daha fazla bilgi için bkz. [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md) ve [özel görev bölmeleri](../vsto/custom-task-panes.md).  

### <a name="display-modes"></a>Görüntü modları  
 Visual Studio görüntü modları ilgili aşağıdaki sınırlamalara sahiptir:  

- Belgenin yakınlaştırma ayarı % 100 dışında değiştirdiğinizde, bir Word belgesi veya Excel çalışma sayfasındaki denetimleri devre dışı bırakıldı.  

- **Yeni proje** iletişim kutusu denetimleri düzgün görüntülenemeyebilir bir kullanıcı bilgisayarın erişilebilirlik seçenekleri değişirse **kullanımı Yüksek Karşıtlık**.  

  Bu sınırlamaların üstesinden gelmek için Büyüteç'i kullanabilirsiniz. Büyüteç'i bir ekran büyütülmüş bir bölümünü görüntüler ayrı bir pencerede Windows içinde görünen aracıdır.  

## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)   
 [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)   
 [Engelli kişiler için erişilebilirlik](/visualstudio/ide/reference/accessibility-for-people-with-disabilities)   
 [Visual Studio'nun erişilebilirlik özellikleri](/visualstudio/ide/reference/accessibility-features-of-visual-studio)  
