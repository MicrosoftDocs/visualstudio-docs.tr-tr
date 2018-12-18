---
title: UML modellerini ve diyagramları düzenleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.modelingproject
- vs.teamarch.UMLModelExplorer
- vs.teamarch.UMLModelExplorer.rootnode
helpviewer_keywords:
- diagrams - modeling
- UML, copy and paste
- UML, models
- UML model
- UML, element properties
- UML
- UML, diagrams
ms.assetid: 87affd40-8127-4ee9-9d3a-ad977abe2ed6
caps.latest.revision: 86
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 92d2be3abfb849b0b5cf5c1c820040b658e2240c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803441"
---
# <a name="edit-uml-models-and-diagrams"></a>UML modellerini ve diyagramları düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oluşturun ve birkaç farklı türde diyagram tarafından sağlanan görünümleri aracılığıyla bir UML modeli Düzenle. Sisteminize göre farklı bakış açıları sağlayarak bu diyagramları anlamanıza ve tasarım ve gereksinim farklı yönlerini tartışmanıza yardımcı olur. Visual Studio şablonları beş en için UML diyagram türleri sık kullanılan sağlar.  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Bu konu, farklı diyagram türleri arasında ortak olan model düzenleme teknikleri açıklar. Diyagramların belirli türlerine özgü daha fazla bilgi için bkz. [uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md).  
  
## <a name="in-this-topic"></a>Bu Konu kapsamında  
  
-   [UML diyagramları bir UML modeli görünümleridir](#Views)  
  
-   [UML modelleme diyagramları oluşturma](#Creating)  
  
-   [UML modelleme diyagramları çizme](#Drawing)  
  
-   [Şekilleri ve bağlayıcıları düzenleme](#Editing)  
  
-   [Modele değişiklikler geri alınıyor](#Undo)  
  
-   [Öğeleri diyagramlar arasında paylaşma](#Sharing)  
  
-   [Öğeleri ve grupları ilgili öğelerin kopyalama](#Copying)  
  
-   [Bir Model öğesi veya görünümlerini silme](#Deleting)  
  
-   [Bir diyagramda metin arama](#Searching)  
  
-   [Sunum için bir diyagram hazırlama](#presentation)  
  
-   [UML tasarımcılarına genişletme](#extensions)  
  
##  <a name="Views"></a> UML diyagramları bir UML modeli görünümleridir  
 Oluşturma ve modelleme projeleri içinde yalnızca UML diyagramları kullanın. Diyagramları ve projeler oluşturma hakkında daha fazla bilgi için bkz. [oluşturma UML modelleme projeleri ve diyagramları](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
-   Bir modelleme projesi, tek bir UML modeli içerir. Projedeki her UML diyagram, UML modelinin bir görünümüdür.  
  
-   Modelde gördüğünüz **UML Model Gezgini**. Üzerinde **mimarisi** menüsünde **Windows**ve ardından **UML Model Gezgini**.  
  
-   Bir diyagramdaki her bir şeklin modelinde bir öğedeki bir görünümüdür. Yeni şekil diyagrama yerleştirdiğinizde, yeni bir öğe modelde oluşturuyorsunuz.  
  
-   Her diyagram, Visual Studio kaydettiğinizde modelin tamamını kaydettiğinde, tüm diyagramları ve model tarafından proje dosyası.  
  
##  <a name="Creating"></a> UML modelleme diyagramları oluşturma  
  
1. Üzerinde **mimarisi** Visual Studio'da menüsünü **yeni UML veya katman diyagramı**.  
  
2. Seçin ve diyagram adlandırın.  
  
3. İçinde **modelleme projesine Ekle**, varolan modelleme projesini seçin ya da seçin **yeni modelleme projesi oluşturma**.  
  
   > [!NOTE]
   >  Modelleme diyagramında bir modelleme projesinin içinde olmalıdır.  
  
   Diyagram, Çözüm Gezgini'nde bir modelleme projesine de ekleyebilirsiniz. Modelleme projesine sağ tıklayın, fareyle **Ekle**ve ardından **yeni öğe**.  
  
#### <a name="to-create-an-empty-uml-modeling-project"></a>Boş bir UML modelleme projesi oluşturmak için  
  
- Üzerinde **dosya** menüsünde **yeni**, tıklayın **proje**ve **yeni proje** iletişim kutusunda, çift **modelleme Projeleri**.  
  
  Modelleme projeleri yönetme hakkında daha fazla bilgi için bkz. [oluşturma UML modelleme projeleri ve diyagramları](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
##  <a name="Drawing"></a> UML modelleme diyagramları çizme  
 Modelleme Diyagramında ilişkileriyle bağlantılı model öğelerinin bir koleksiyonunu görüntüler. Her öğenin bir şekil olarak görüntülenir ve her ilişki iki şekil arasında bir bağlayıcı olarak görüntülenir.  
  
 İki tür öğeleri biri diğeri ilişkiler için araçlar vardır. Örneğin, araç, UML sınıf diyagramı içinde **sınıfı** bir öğe aracıdır ve **ilişkilendirme** ilişki aracıdır.  
  
> [!NOTE]
>  Belirli bir diyagram türlerine özgü bilgileri almak istiyorsanız, bkz. [uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md).  
  
#### <a name="to-create-elements-and-relationships-in-a-uml-modeling-diagram"></a>UML modelleme diyagramında öğeleri ve ilişkileri oluşturmak için  
  
1. Bir model öğesini oluşturmak için araç kutusu öğe aracına tıklayın ve görünmesini istediğiniz yerde Diyagramı'ye tıklayın. Öğe oluşturduktan sonra boyutu ve şekli tutamaçlarını sürükleyerek ayarlayın.  
  
    Bazı durumlarda, yeni bir öğe başka bir öğenin içine yerleştirebilirsiniz. Örneğin, bir UML sınıf diyagramı üzerinde bir sınıf içinde paket yerleştirebilirsiniz.  
  
   > [!NOTE]
   >  Araç kutusunu göremiyorsanız, tıklayın **araç kutusu** üzerinde **görünümü** menüsü.  
  
2. Bir ilişki oluşturmak için bir ilişki Aracı'nı tıklatın, ilişkiyi başlatmak istediğiniz öğeye tıklayın ve ardından son istediğiniz öğeye tıklayın.  
  
    Farklı türlerde ilişkiler başlatabilir veya farklı türde öğeler üzerinde bitmelidir. Örneğin, bir UML sınıf diyagramı üzerinde bir ilişkilendirme ilişkisi başlayamaz veya açıklama öğesi üzerinde bitemez.  
  
   > [!NOTE]
   >  Aynı aracı birkaç kez kullanmak için araca çift tıklayın. İşiniz bittiğinde tıklayın **işaretçi** aracı.  
  
   Bazı tür diyagramlar Basit şekiller çizebilirsiniz. Bu şekilleri modelinin bir parçası değildir ancak dikkat çekmek için diyagramın parçalarını veya farklı alanlara bölmek için bunları kullanabilirsiniz.  
  
##  <a name="Editing"></a> Şekilleri ve bağlayıcıları düzenleme  
 Yeniden boyutlandırmak veya bir şekil renk veya bir bağlayıcıyı yeniden yönlendir, temel alınan model üzerinde hiçbir etkisi yoktur. Ancak, bir şekil diyagramda veya UML Model Gezgini'nde yeniden adlandırdığınızda, karşılık gelen öğe o öğeyi sunan başka bir diyagramları ve UML Model Gezgini'nde yeniden adlandırılır.  
  
> [!NOTE]
>  Kendi seçtiğiniz özellikler öğe veya öğe grup oluşturma yeni araç kutusu öğeleri yapmak için basit bir yolu yoktur. Daha fazla bilgi için [tanımlayan özel bir modelleme araç kutusu öğesi](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
 Aşağıdaki şekil, bir şekil veya adını boyutunu değiştirmek gösterilmektedir.  
  
 ![Bir model öğesini ayarlama](../modeling/media/uml-drawadjust1.png "UML_DrawAdjust1")  
  
> [!TIP]
>  Yerleşik komutları şekilleri düzgünce hizalamak için bir komut dahil değildir. Ancak, kolayca kendi hizalamanızı örnekte kodu kopyalayarak oluşturabilirsiniz [diyagramlar üzerinde bir UML modeli görüntüleme](../modeling/display-a-uml-model-on-diagrams.md).  
  
 Aşağıdaki şekil, yol ve bir bağlayıcı veya etiketlerinden konumunu ayarlamak gösterilmektedir.  
  
 ![Bağlayıcıyı ayarlama](../modeling/media/uml-drawadjust2.png "UML_DrawAdjust2")  
  
#### <a name="to-move-one-end-of-a-connector-to-another-shape"></a>Başka bir şekle bir bağlayıcı ucunu taşımak için  
  
1. Aşağıdakilerden birini yapın:  
  
   - Tuşuna **CTRL** ve sona taşıyın.  
  
     \- veya -  
  
   - Bağlayıcı sağ tıklayın ve ardından **Reconnect**.  
  
2. Taşımak istediğiniz bağlayıcıyı sonuna tıklayın.  
  
3. Bağlayıcısına taşımak istediğiniz şekle tıklayın.  
  
#### <a name="to-change-color-or-other-properties-of-an-element-relationship-or-diagram"></a>Rengini veya öğenin, ilişki, diğer özelliklerini değiştirin veya diyagram  
  
-   Öğesini tıklatın ve alanlar kümesinde **özellikleri** penceresi.  
  
     Göremiyorsanız **özellikleri** penceresi, öğeye sağ tıklayın ve ardından **özellikleri.**  
  
#### <a name="to-zoom-in-and-out-on-a-modeling-diagram"></a>Modelleme Diyagramında yakınlaştırma ve uzaklaştırma için  
  
-   Basılı **CTRL** fare tekerleğini döndürürken anahtar.  
  
     \- veya -  
  
-   Basılı **CTRL + SHIFT**ve ardından sol veya sağ fare düğmesine tıklayın.  
  
     \- veya -  
  
-   Üzerinde **mimari tasarımcıları** araç, artı işaretine tıklayın (**+**) ya da eksi işareti (**-**), veya bir yakınlaştırma düzeyini seçin.  
  
##  <a name="Searching"></a> Bir diyagramda aranıyor  
 Hızlı Bul işlevi, diyagram üzerindeki öğeleri bulabilirsiniz. Ayarlamalısınız **Bak:** için **geçerli belge**.  
  
#### <a name="to-search-for-text-in-a-modeling-diagram"></a>Modelleme Diyagramında metni aramak için  
  
1.  Tuşuna **CTRL + F**.  
  
     \- veya -  
  
     Üzerinde **Düzenle** menüsünde **Bul ve Değiştir**ve ardından **Hızlı Bul**.  
  
    > [!NOTE]
    >  İçinde **Bul ve Değiştir** iletişim kutusunda, gereken bırakın **konum** alan kümesine **geçerli belge**. Diğer seçenekleri desteklenmez.  
  
2.  Bulun ve ardından istediğiniz metni yazın **Sonrakini Bul**.  
  
    > [!NOTE]
    >  Daraltılmış şekil içinde bulmak istediğiniz metin ise şekli vurgulanır. Şekli genişleterek ve ardından **Sonrakini Bul** yeniden.  
  
##  <a name="Undo"></a> Modele değişiklikler geri alınıyor  
 Geri Al ve Yinele kullanarak model ve diyagramlara yaptığınız değişiklikleri **geri** ve **Yinele** komutlarını **Düzenle** menüsü.  
  
 **Her bir modelleme projesi tek bir yığın değişiklikleri var.** Model ve diyagramlara yaptığınız tüm değişiklikler bu yığın üzerinde tutulur. Yığın, bir diyagramdaki odağı değişiklikleri de içerir. Undo komutu değişiklikleri bu yığın üzerinde tersine çevirir.  
  
 Örneğin, bu işlemleri gerçekleştirmek varsayalım: Diyagram1 için; bir değişiklik yapın Odak diyagramı 2'ye değiştirin; Diyagram2'yi değiştirin. Değişiklikleri Geri Al, ilk geri son değişikliği geri; sonraki geri alma odak diyagramı 1'e kaydırır; ve üçüncü geri alma değişikliği diyagramı 1'e geri alacaksınız.  
  
 **Bir diyagram kapanış değişikliklerin yığınını keser.** Bir diyagram kapatırsanız, şemada yapılan değişiklikleri geri al ve model ve diyagramlarını hiçbirini önceki değişiklikler geri alınamıyor.  
  
 **Bir özellik düzenlerken, geri alamazsınız.** Bir özelliği, Özellikler penceresinde ya da bir diyagram üzerindeki bir etikette düzenlerken, yalnızca o özelliğin yaptığınız değişiklikleri geri alabilirsiniz. ENTER tuşuna basarak değişikliğiniz özelliğinde tamamlamak veya ESC tuşuna basarak iptal edin. Ardından model ve diyagramlarını değişiklikleri geri almak mümkün olacaktır.  
  
 **Diyagramı kaydetmeden kapatmak beklediğiniz etkiye sahip olmayabilir.** Bazı değişiklikler yapın ve ardından diyagram kaydetmeden kapatın, modelde yaptığınız değişiklikleri yine de korunur. Bunu kaydetmeden yapmak istiyorsanız tüm modeli kapatmanız önerilir.  
  
##  <a name="Sharing"></a> Öğeleri diyagramlar arasında paylaşma  
 Birden çok kez, diyagramlarında görünür belirli bir örneğini bir model öğesini yapabilirsiniz. Bu sınıfları, arabirimleri, bileşenler, kullanım örnekleri ve aktörler için geçerlidir.  
  
 Bu, farklı diyagramlarda farklı ilişki gruplarını göstermek istiyorsanız yararlıdır. Örneğin, bir diyagram üzerinde müşteri ve adresini sınıflarını arasındaki ilişkilendirmeleri gösterebilirsiniz. Başka bir diyagram üzerinde adres sınıfı yeniden ile posta alanına ilişkisini gösterebilirsiniz.  
  
 Model öğesinin, onun adı gibi özellikleri, herhangi bir diyagram üzerindeki görünümlerini birini seçerek veya UML Model Gezgini'nde seçerek değiştirebilirsiniz.  
  
 Her diyagram türü, bazı model öğe türleri yalnızca gösterebilirsiniz. Örneğin, bir kullanım örneği bir bileşen diyagramı üzerinde gösterilemiyor. Bu nedenle, aşağıdaki yordamlar yalnızca bazı birleşimleri model öğesi ve diyagramı için çalışır.  
  
#### <a name="to-add-a-new-view-of-a-model-element-by-using-uml-model-explorer"></a>UML Model Gezgini kullanarak bir model öğesini yeni bir görünümünü eklemek için  
  
1.  Açmak için **UML Model Gezgini**, **mimarisi** menüsünde **Windows**ve ardından **UML Model Gezgini**.  
  
2.  Model öğesinden sürükleyin **UML Model Gezgini** aynı projede uyumlu bir diyagrama.  
  
     Model öğesinin bir görünümü açılır sağlayan bir şekil, diğer diyagramlara veya aynı diyagram görünümlerini yanı sıra olabilecek.  
  
    > [!NOTE]
    >  Bir sınıf veya bileşeni bir sıralama diyagramına sürüklediğinizde etkisi farklıdır. Bu durumda, bu sınıf ya da bileşen türü olan yeni bir yaşam çizgisi oluşturulur. Daha fazla bilgi için [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md).  
  
#### <a name="to-add-a-new-view-of-a-model-element-by-using-paste-reference"></a>Başvuruyu Yapıştır kullanarak bir model öğesini yeni bir görünümünü eklemek için  
  
1.  Var olan bir öğeye sağ tıklayın ve ardından **kopyalama**.  
  
    -   Aynı anda birkaç öğe kopyalayabilirsiniz. Her öğeye bunları birine sağ tıklayın ve ardından CTRL tuşunu basılı tutarak **kopyalama**.  
  
2.  Uyumlu bir diyagramın boş bir bölümüne sağ tıklayın ve ardından **başvuruyu Yapıştır**.  
  
     Başka bir görünüm aynı öğenin görünür.  
  
    > [!NOTE]
    >  Bu farklıdır **Yapıştır** modelde yeni bir öğe oluşturan komutu. Daha fazla bilgi için [kopyalama öğeleri ve ilişkili öğeleri gruplandırır](#Copying).  
  
> [!NOTE]
>  Zaten bir ilişki ile bağlı olan iki model öğelerini diyagram görünümlerini eklerseniz, ilişkinin bir görünüm de diyagramda görünecektir. Bu görünüm öğelerden birini diyagramından kaldırılması yalnızca tarafından veya ilişkiyi modelden silerek silebilirsiniz.  
  
##  <a name="Copying"></a> Öğeleri ve grupları ilgili öğelerin kopyalama  
 Model öğelerini kopyalayıp ve aralarındaki ilişkilerin birlikte öğelerin grupları kopyalayıp.  
  
> [!NOTE]
>  **Yapıştır** ve **başvuruyu Yapıştır** komutlarının farklı etkileri vardır. **Yapıştırma** özelliklerini aittir kopyalanan öğeler gibi yeni öğeleri oluşturur. **Başvuru yapıştırın** aynı öğelerin yeni görünümler oluşturur.  
  
#### <a name="to-copy-elements-and-their-relationships"></a>Öğeleri ve aralarındaki ilişkiler kopyalamak için  
  
1.  Kopyalamak istediğiniz öğeleri diyagramda, bir veya daha fazla öğe seçin.  
  
    > [!NOTE]
    >  Öğelerin bir grubun bir parçası ilişkiler dışında kopyalanamıyor.  
  
2.  Üzerinde **Düzenle** menüsünde tıklatın **kopyalama**.  
  
3.  Öğeleri başka bir diyagrama kopyalamak istiyorsanız, yeni diyagramı oluşturun veya mevcut diyagramı açın.  
  
4.  Üzerinde **Düzenle** menüsünde tıklatın **Yapıştır**.  
  
    -   Öğelerinin kopyalarını bunlar arasında bağlantı ilişkileri kopyalarını birlikte görünür.  
  
    -   Her yeni öğe yeni bir otomatik olarak oluşturulan adı gerekir.  
  
5.  Konumlar, adları ve diğer yeni öğeleri ve ilişkileri özelliklerini ayarlayın.  
  
> [!NOTE]
>  Örneğin aynı çözümde iki modeli varsa başka bir bir modeldeki bir model öğesine kopyalanamıyor. Ancak, öğeler bir diyagramından diğerine kopyalayabilirsiniz.  
  
#### <a name="to-copy-an-entire-diagram"></a>Tüm bir diyagram kopyalamak için  
  
1. Yeni bir diyagram oluşturun.  
  
2. Tüm öğeleri mevcut bir diyagramı, kopyalamak ve bunları yeni bir tane yapıştırın.  
  
   Çözüm Gezgini'nde yapıştırarak diyagram çoğaltamazsınız.  
  
##  <a name="Deleting"></a> Bir Model öğesi veya görünümlerini silme  
 Bazı tür öğeler, özellikle sınıflandırıcılar, diyagramdan modelden silmeden kaldırılabilir. Sınıflandırıcılar, kullanım örneği diyagramları ve sınıf diyagramları, Bileşen diyagramları görüntülenir başlıca öğeleridir. Bunlar, birden çok diyagramda görünebilir. Bu tür öğeler için iki ayrı komutlar vardır: **diyagramdan Kaldır** ve **modelden silmek**.  
  
 Aksine, bir ilişki diyagramdan sildiğinizde, bu her zaman modelden siliyorsunuz.  
  
> [!NOTE]
>  Öğeleri bir UML diyagram üzerindeki belirli bir türdeki etiketlere sahip. Bu öğeler, bunları çevresinde bir dikdörtgen çizerek seçtiğinizde etiketleri ancak etiketlerin sahibi olan öğeleri seçmek mümkündür. Bu şekilde seçili olan öğeler bir alt kümesi silme desteklenmiyor. Bu öğeleri alt seçmek için basılı **CTRL** her öğe tıklatırken anahtar.  
  
#### <a name="to-remove-a-classifiers-view-from-a-diagram"></a>Sınıflandırıcının görünümünü diyagramdan kaldırmak için  
  
- Diyagramdaki bir öğeye sağ tıklayın ve ardından **diyagramdan Kaldır**.  
  
  \- veya -  
  
- Diyagram üzerinde öğenin tıklayın ve sonra basın **Sil** anahtarı.  
  
  -   Bu öğenin görünümünü kaybolur. Ancak öğe modelde kalır ve yine de içinde bulabilirsiniz **UML Model Gezgini**. Ayrıca aynı öğenin diğer görünümlere kalır.  
  
  -   Bu şekilde sonlanan her bir bağlayıcının diyagramı, ancak kalan modelinde temsil ettiği ilişkisi kaldırılır. İlişkide gördüğünüz **UML Model Gezgini** altında **ilişkileri**, bağladığı her öğe altında.  
  
#### <a name="to-delete-an-element-from-the-model"></a>Modelden bir öğeyi silmek için  
  
-   Ya da öğeye sağ tıklayın, **UML Model Gezgini** veya diyagramındaki ve ardından **modelden silmek**.  
  
    -   Öğe göründüğü her diyagramından silinir.  
  
    -   Bu öğede sonlanan her ilişkinin modelden de silinir.  
  
#### <a name="to-delete-a-relationship-from-the-model"></a>Bir ilişkiyi modelden silmek için  
  
-   İlişkisi diyagram üzerinde ya da buna sağ **UML Model Gezgini**ve ardından **modelden silmek**.  
  
    > [!CAUTION]
    >  Modelden kaldırmadan bir diyagramından bir ilişki kaldırılamıyor.  
  
     İlişkiyi modelden silinir ve göründüğü her diyagramdan silinir.  
  
##  <a name="presentation"></a> Sunum için bir diyagram hazırlama  
 Aşağıdaki özellikler dikkat çekmek için diyagramın belirli bölümlerini açıklamalar ekleyebilir ve ilgilenilen farklı alanlara bir diyagram bölmek için yardımcı olur.  
  
-   Diyagramın herhangi bir bölümü, bir Word, PowerPoint veya başka bir belgeye kopyalayabilirsiniz. Şekilleri ve bağlayıcıları, sağ tıklayın ve ardından seçin **kopyalama**.  
  
-   Herhangi bir şekil veya bağlayıcının rengi değiştirilebilir. Bir veya daha fazla şekilleri seçin ve değiştirme **renk** özelliği. Göremiyorsanız **özellikleri** penceresinde, tuşuna **F4**.  
  
-   Bazı tür diyagramlar üzerinde satırları, dikdörtgenler ve elipsler gelen çizebilirsiniz **Basit şekiller** araç bölümü. Bu şekil, UML modelinin bir parçası oluşturmuyor.  
  
-   Bir alan etiketlemek için bir yorum araç kutusundan sürükleyin ve ardından kendi **saydam** özelliğini **True**. Basit şekiller gibi yorumlar, UML modelinin bir parçası oluşturmuyor ve UML Model Gezgini'nde görünmez.  
  
-   Notlar ve açıklamalar model öğelerine eklemek için açıklamaları oluşturma ve bunları öğelerine bağlayın.  
  
-   Bir sütun veya satır şekilleri diyagram üzerinde düzgünce hizalamak için şekilleri Hizala komutu yükleyebilirsiniz. Bu örnek UML Uzantısı kullanılabilir: [UML: şekiller Hizala komutu](http://code.msdn.microsoft.com/UML-command-to-Align-4139c0d7)  
  
### <a name="to-export-a-diagram-as-an-image"></a>Bir diyagramı görüntü olarak dışarı aktarmak için  
 Daha fazla bilgi için [diyagramlarını görüntü dışarı aktarma](../modeling/export-diagrams-as-images.md).  
  
##  <a name="extensions"></a> UML tasarımcılarına genişletme  
 UML araçlarına yeni işlevler eklemek ve diyagram gösterimi kendi gereksinimlerinize uyarlayın. Daha fazla bilgi için [genişletmek UML modellerini ve diyagramları](../modeling/extend-uml-models-and-diagrams.md).  
  
 Birkaç örnek uzantı yok. Ya da yalnızca yükleyebilir ve bunları kullanın veya kendi uzantılarınızı için kaynak kodlarını temel olarak kullanabilirsiniz. Örnekler şunlardır:  
  
|||  
|-|-|  
|[Şekiller Hizala](http://code.msdn.microsoft.com/UML-command-to-Align-4139c0d7)|Bir diyagram tutuyor yardımcı olan bir menü komutu.|  
|[Belgeleri için bağlantı](http://code.msdn.microsoft.com/Link-UML-elements-to-0adbf5a8)|Herhangi bir UML öğesi başlıkları Word, PowerPoint slaytları, dosyaları herhangi bir tür, UML diyagramları veya diğer UML öğeleri bağlayın. Bağlantı yalnızca sürükleyerek yapılabilir. Daha sonra bağlantılı öğe görmek için öğe çift tıklayabilirsiniz. Örneğin, Word belirtimleri veya ayrıntılı etkinlik diyagramları ve slaytları görsel taslağa dönüştürme işlemleri için kullanım örneklerinize bağlayabilirsiniz.|  
|[Hızlı bir giriş](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a)|Metin girişi kullanarak bir modeli hızlı bir şekilde oluşturun. Fikirlerinizi toplantılarda yakalamak için yararlıdır.|  
|[Stereotip göre renk](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)|Renkleri sınıflar göre stereotip. İçin kendi stereotipler çalışmak için kodu, bir kolayca genişletebilirsiniz.|  
|[Etki alanı modelleme](http://code.msdn.microsoft.com/UML-Domain-Modeling-6df6f7f4)|İşletme modellerini uygun Varsayılanların. İlişkilendirmeleri, oklar olmadan varsayılan olarak gösterilir ve işlemleri sınıflarda görünmez.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML modelleme projeleri ve diyagramları oluşturma](../modeling/create-uml-modeling-projects-and-diagrams.md)   
 [Çözümleme ve mimarinin modelini oluşturma](../modeling/analyze-and-model-your-architecture.md)   
 [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)



