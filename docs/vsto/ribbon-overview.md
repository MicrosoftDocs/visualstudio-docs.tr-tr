---
title: Şerite Genel Bakış
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, multiple Ribbons
- Ribbon [Office development in Visual Studio], about Ribbon
- toolbars [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], multiple Ribbons
- toolbars [Office development in Visual Studio]
- custom Ribbon, multiple Ribbons
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 51de8b5fbc4e21b4dabaf34f526b85f0b98623db
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846373"
---
# <a name="ribbon-overview"></a>Şerite Genel Bakış
  Şerit, bunlar daha kolay olacak şekilde ilgili komutları düzenlemek için bir yoldur. Komutlar, Şerit üzerindeki denetimleri olarak görünür. Denetimler halinde düzenlenir *grupları* uygulama penceresinin üst kenarındaki yatay bir çubuk boyunca. Sekmelerde ilgili gruplar halinde düzenlenir.  
  
 Microsoft Office sistemi önceki sürümlerinde menüleri ve araç çubuklarını kullanarak erişilen özelliklerin çoğu, Şerit kullanarak artık erişilebilir. Daha fazla bilgi için teknik makaleye bakın [2007 Microsoft Office sistemi için kullanıcı arabirimi Geliştirici bakış](http://go.microsoft.com/fwlink/?LinkID=70860).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="customize-the-microsoft-office-ribbon"></a>Microsoft Office Şerit özelleştirme  
 Şerit özelleştirmek için aşağıdaki Şerit öğeleri birini Office projenize ekleyin:  
  
- **Şerit (Görsel Tasarımcı)**  
  
- **Şerit (XML)**  
  
  Örneğin, Excel şeridinde özelleştirmek için Şerit öğesi bir Excel VSTO eklentisi projesine ekleyin.  
  
### <a name="ribbon-visual-designer-item"></a>Şerit (Görsel Tasarımcı) öğesi  
 **Şerit (Görsel Tasarımcı)** öğesi bir Şerit tasarlayıp kolaylaştıran gelişmiş araçlar sağlar. Kullanım **Şerit (Görsel Tasarımcı)** şeridi aşağıdaki yollarla özelleştirmek için öğe:  
  
- Şerite özel ya da yerleşik sekmeleri ekleyin.  
  
- Özel gruplar için yerleşik veya özel bir sekme ekleyin.  
  
  > [!NOTE]  
  >  Bir yerleşik bir sekmeyi veya grup zaten bir Microsoft Office uygulamasının Şerit üzerinde var olan bir örneğidir. Örneğin, **veri** Excel yerleşik bir sekmede sekmesidir. **Bağlantıları** grup yerleşik bir gruptur üzerinde **veri** sekmesi.  
  
- Özel denetimler için özel bir grup ekleyin.  
  
- Özel Backstage görünümüne denetimler ekleme.  
  
  Bir Şerit kullanarak özelleştirme hakkında daha fazla bilgi için **Şerit (Görsel Tasarımcı)** öğesi için bkz: [Şerit Tasarımcısı](../vsto/ribbon-designer.md).  
  
### <a name="ribbon-xml-item"></a>Şerit (XML) öğesi  
 Kullanım **Ribbon (XML)** şeridi tarafından desteklenmeyen bir biçimde özelleştirmek istiyorsanız öğesi **Şerit (Görsel Tasarımcı)** öğesi. Kullanım **Ribbon (XML)** şeridi aşağıdaki yollarla özelleştirmek için öğe:  
  
- Ekleme *yerleşik* özel sekme veya yerleşik bir sekmeyi grupları.  
  
- Yerleşik denetimler için özel bir grup ekleyin.  
  
- Olay işleyicileri yerleşik denetimlerin geçersiz kılmak için özel kod ekleyin.  
  
- Hızlı Erişim Araç çubuğunu özelleştirme.  
  
- Bir Şerit özelleştirme VSTO yetkili bir kimlik kullanarak eklentisi arasında paylaşma  
  
  Şerit kullanarak özelleştirme hakkında daha fazla bilgi için **Ribbon (XML)** öğesi için bkz: [Ribbon XML](../vsto/ribbon-xml.md).  
  
## <a name="export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Bir Şerit Şerit Tasarımcısından Şerit XML'ine verebilir.  
 Şerit Tasarımcısı kullanarak Şerit oluşturma ve ardından şeridi şekilde özelleştirmek istediğinize karar verin, **Şerit (Görsel Tasarımcı)** öğesi desteklemiyor, Şerit XML biçimine dışa aktarabilirsiniz.  
  
 Visual Studio otomatik olarak oluşturur bir **Ribbon (XML)** öğesi ve Şerit üzerindeki her denetim için Ribbon XML dosyasındaki öğeleri ve öznitelikleri ile doldurur.  
  
 Bulunan özelliklerin tümünü **özellikleri** penceresi Şerit Tasarımcısı Şerit XML dosyasına aktarılır.  Örneğin, Visual Studio değeri vermez **görüntü** veya **metin** özelliği. Görüntü atamak veya bir denetimin metnini ayarlamak için dışarı aktarılan projenin Şerit kod dosyasını bir geri çağırma yöntemi oluşturma olmasıdır. Visual Studio geri çağırma yöntemleri dışarı aktarma işleminin bir parçası otomatik olarak oluşturmaz.  
  
 Ek olarak, değiştirilmeden varsayılan özellik değerleri sonuçta elde edilen Ribbon XML dosyasında görünmez.  
  
 Şeridi XML'ye Aktar hakkında daha fazla bilgi için bkz. [nasıl yapılır: Şerit Şerit Tasarımcısından Şerit XML'ine dışarı](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).  
  
### <a name="update-the-code"></a>Kodu güncelleştirme  
 Yeni bir Şerit kod dosyası eklenir **Çözüm Gezgini**. Bu dosya, Şerit XML sınıfını içerir. Geri çağırma yöntemleri oluşturmalısınız `Ribbon Callbacks` bir düğmeye tıklanması gibi kullanıcı eylemlerini işlemek için bu sınıfın bölge. Kodunuzu olay işleyicilerindeki bu geri çağırma yöntemlerine taşıyın ve Ribbon genişletilebilirliği (RibbonX) programlama modeliyle çalışmak için kodu değiştirin. Daha fazla bilgi için [Ribbon XML](../vsto/ribbon-xml.md).  
  
 Ayrıca kodu eklemelisiniz `ThisAddIn`, `ThisWorkbook`, veya `ThisDocument` kılan sınıf `CreateRibbonExtensibilityObject` Office uygulamasına sınıf yöntemi ve Şerit XML döndürür.  
  
 Daha fazla bilgi için [Ribbon XML](../vsto/ribbon-xml.md).  
  
## <a name="add-multiple-ribbon-items-to-a-project"></a>Birden çok Şerit öğeleri bir projeye ekleyin.  
 Birden fazla Şerit öğesi tek bir projeye ekleyebilirsiniz. Bu, aşağıdaki iki görevden herhangi birini gerçekleştirmek istiyorsanız yararlıdır:  
  
-   Outlook için Şerit oluşturma *denetçiler*. Daha fazla bilgi için [Outlook için Şerit özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md).  
  
    > [!NOTE]  
    >  Bir denetçi kullanıcılar bir e-posta iletisi oluşturmak gibi belirli görevleri gerçekleştirdiğinde, açılan bir penceredir.  
  
-   Çalışma zamanında görüntülemek için hangi Şerit'i seçin.  
  
### <a name="select-which-ribbons-to-display-at-runtime"></a>Çalışma zamanında görüntülemek için hangi şeritler seçin  
 Bir projenin birden fazla Şerit içerebileceğinden, çalışma zamanında görüntülemek üzere hangi Şerit seçebilirsiniz.  
  
 Çalışma zamanında görüntülemek için Şerit'i seçmek için geçersiz kılma `CreateRibbonExtensibilityObject` yönteminde `ThisAddin`, `ThisWorkbook`, veya `ThisDocument` proje ve dönüş görüntülemek istediğiniz Şerit sınıfı. Aşağıdaki örnek adlı bir alanın değerini denetler `myCondition` ve uygun Şerit döndürür.  
  
> [!NOTE]  
>  Bu örnekte kullanılan sözdizimi kullanılarak oluşturulmuş bir Şerit döndürür **Şerit (Görsel Tasarımcı)** öğesi. Söz dizimi kullanılarak oluşturulan bir Şerit döndüren bir **Ribbon (XML)** madde biraz farklıdır. Döndürme hakkında daha fazla bilgi için bir **Ribbon (XML)** öğesi için bkz: [Ribbon XML](../vsto/ribbon-xml.md).  
  
 Aşağıdaki kodu ekleyin:  
  
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.cs#1)]  
  
### <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Şerit özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md)|Microsoft Office uygulamasının Şerit özelleştirme, ekleme işlemi gösterilmektedir bir **Şerit (Görsel Tasarımcı)** veya **Ribbon (XML)** bir Office projesi için öğesi.|  
|[Şerit Tasarımcısı](../vsto/ribbon-designer.md)|Bir Microsoft Office uygulamasının Şeritine özel sekmeler, gruplar ve denetimler eklemek için Şerit Tasarımcısını nasıl kullanabileceğinizi açıklar.|  
|[İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Şerit Tasarımcısını kullanarak özel bir Şerit sekmesi oluşturma işlemi gösterilmektedir. Ekleme ve özel sekmedeki denetimleri konumlandırma Şerit Tasarımcısı'nı kullanabilirsiniz.|  
|[Şerit nesne modeline genel bakış](../vsto/ribbon-object-model-overview.md)|Almak ve çalışma zamanında Şerit denetimlerinin özelliklerini ayarlamak için kullanabileceğiniz sağlam biçimde yazılmış nesne modeline genel bakış sağlar.|  
|[İzlenecek yol: çalışma zamanında Şerit denetimlerini güncelleştirme](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Şerit nesne modeline Şerit Office uygulamasına yüklendikten sonra Şerit denetimlerini güncelleştirme için nasıl kullanılacağını gösterir.|  
|[Outlook için Şerit özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md)|Microsoft Office Outlook'ta Şeritteki özelleştirmeye yönelik yönergeler sağlar.|  
|[InfoPath için Şerit özelleştirme](../vsto/customizing-a-ribbon-for-infopath.md)|Microsoft Office InfoPath Şerit özelleştirmeye yönelik rehberlik sağlar.|  
|[Şerit, çalışma zamanında erişme](../vsto/accessing-the-ribbon-at-run-time.md)|Göster, gizleme ve Şerit değiştirebilir ve bir özel görev bölmesi, Eylemler bölmesi veya Outlook form bölgesi denetimlerinden kodu çalıştırmak kullanıcıların gösterilmektedir.|  
|[Nasıl yapılır: Şeritteki sekmenin konumunu değiştirme](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Şerit sekme sırasını değiştirme işlemi gösterilmektedir.|  
|[Nasıl yapılır: yerleşik bir sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md)|Yerleşik bir sekmeye grup ve denetim ekleme işlemi gösterilmektedir.|  
|[Nasıl yapılır: Backstage görünümüne denetimler ekleme](../vsto/how-to-add-controls-to-the-backstage-view.md)|' A tıkladığınızda açılan menüye denetimler eklemek gösterilmektedir **dosya**.|  
|[Nasıl yapılır: Şerit grubuna iletişim kutusu başlatıcısı ekleme](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Herhangi bir Şerit grubuna iletişim kutusu başlatıcısı ekleme gösterir.|  
|[Nasıl yapılır: Şerit Şerit Tasarımcısından Şerit XML'ine verebilir.](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Şerit Tasarımcısından Şerit XML'ine dışa aktararak Gelişmiş yollarla şeridi özelleştirme işlemi gösterilmektedir.|  
|[Şerit XML](../vsto/ribbon-xml.md)|Şerit XML kullanarak Şerit nasıl özelleştirebileceğinizi açıklar.|  
|[İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Kullanarak özel bir Şerit sekmesi oluşturma işlemini gösterir **Ribbon (XML)** öğesi.|  
  
  