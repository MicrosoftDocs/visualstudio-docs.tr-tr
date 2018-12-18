---
title: Görüntüleme veri değerlerinin veri ipuçlarında Kod Düzenleyicisi'nde | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37fc58a68f8cf482ac6a2bbab3ecb47c28d60904
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799450"
---
# <a name="view-data-values-in-data-tips--in-the-code-editor"></a>Veri İpuçları'ndaki veri değerlerini kod düzenleyicide görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DataTips, hata ayıklama sırasında programınızdaki değişkenleri hakkında daha fazla bilgi görüntülemek için kullanışlı bir yol sağlar. DataTips, sadece kesme modunda ve yalnızca yürütme geçerli kapsamdaki değişkenler çalışın.  
  
 İçinde [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]DataTips sabitlenmiş kaynak dosyada belirli bir konuma veya tüm üstüne Kaydır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] windows.  
  
### <a name="to-display-a-datatip-in-break-mode-only"></a>Bir DataTip (sadece kesme modunda) görüntülemek için  
  
1. Bir kaynak penceresinde, fare işaretçisini geçerli kapsamdaki herhangi bir değişken üzerine getirin.  
  
    Bir DataTip görünür.  
  
   > [!NOTE]
   >  Veri ipuçları, her zaman yürütmesi askıya alınır ve imleç değil geldiği yerde bağlamında değerlendirilir. Geçerli bağlam içinde bir değişken olarak aynı ada sahip başka bir işlev bir değişkende üzerine gelin, diğer işlev değişkenin değeri geçerli bağlamda değişkeninin değeri olarak görüntülenir.  
  
2. Fare işaretçisi kaldırdığınızda DataTip kaybolur. Açık kalması DataTip sabitlemek için tıklayın **kaynağına PIN** simgesi, veya  
  
   - Bir değişken üzerinde sağ tıklatın ve ardından **kaynağına PIN**.  
  
     Hata ayıklama oturumu sona erdiğinde sabitlenmiş DataTip kapatır.  
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>Bir DataTip kaldırın ve kolaylaştırmak için Kaydır  
  
-   Sabitlenmiş bir DataTip içinde tıklayın **kaynağından Unpın** simgesi.  
  
     Raptiye simgesini sabitlenmemiş konuma değişir. DataTip artık açık pencerelerin kayar. Hata ayıklama oturumu sona erdiğinde kayan DataTip kapatır.  
  
### <a name="to-repin-a-floating-datatip"></a>Kayan bir DataTip Görselden için  
  
-   Bir DataTip içinde Raptiye simgesine tıklayın.  
  
     Raptiye simgesini sabitlenmiş konumuna değiştirir. Kaynak penceresi dışında DataTip ise Raptiye simgesini devre dışıdır ve DataTip sabitlenemez.  
  
### <a name="to-close-a-datatip"></a>Bir DataTip kapatmak için  
  
-   Fare işaretçisini bir DataTip üzerinde getirin ve ardından **Kapat** simgesi.  
  
### <a name="to-close-all-datatips"></a>Tüm veri ipuçlarını kapatmak için  
  
-   Üzerinde **hata ayıklama** menüsünde tıklatın **Temizle tüm veri ipuçlarını**.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>Belirli bir dosya için tüm veri ipuçlarını kapatmak için  
  
-   Üzerinde **hata ayıklama** menüsünde tıklatın **Temizle tüm veri ipuçlarını sabitlenmiş için** *dosya*.  
  
## <a name="expanding-and-editing-information"></a>Genişletme ve bilgilerini düzenleme  
 DataTips, bir dizi, yapı veya üyelerini görüntülemek için bir nesne genişletmek için kullanabilirsiniz. Bir DataTip değişkeninden değerini de düzenleyebilirsiniz.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>Bir değişken öğeleri görmek için genişletin  
  
-   Fare işaretçisini bir DataTip içinde yerleştirin **+** değişken adından önce gelen oturum.  
  
     Öğeleri ağaç biçiminde göstermek için değişkeni genişletir.  
  
     Değişken genişletildiğinde klavyenizde yukarı ve aşağı taşımak için ok tuşlarını kullanabilirsiniz. Alternatif olarak, fare kullanabilirsiniz.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>Bir DataTip kullanarak bir değişkenin değerini düzenlemek için  
  
1.  Bir DataTip içinde değere tıklayın. Bu salt okunur değerleri için devre dışıdır.  
  
2.  Yeni bir değer yazın ve ENTER tuşuna basın.  
  
## <a name="making-a-datatip-transparent"></a>Bir DataTip saydam hale getirme  
 Bir DataTip kod görmek istiyorsanız, DataTip geçici olarak saydam olarak yapabilirsiniz. Bu sabitlenmiş veya kayan DataTips için geçerli değildir.  
  
#### <a name="to-make-a-datatip-transparent"></a>Bir DataTip saydam yapmak için  
  
-   Bir DataTip içinde CTRL tuşuna basın.  
  
     CTRL tuşunu basılı tutun sürece DataTip saydam olarak kalır.  
  
## <a name="visualizing-complex-data-types"></a>Karmaşık veri türlerini Görselleştirme  
 Bir değişken adı bir veya daha fazla bir DataTip içinde bir Büyüteç simgesinin yanında, [oluşturma özel Görselleştiriciler](../debugger/create-custom-visualizers-of-data.md) değişken veri türü için kullanılabilir. Görselleştirici, genellikle grafik daha anlamlı bir şekilde bilgileri görüntülemek için kullanabilirsiniz.  
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>Görselleştirici kullanarak değişkenlerin içeriğini görüntülemek için  
  
-   Veri türü için varsayılan Görselleştirici seçmek için büyüteç simgesini tıklayın.  
  
     veya  
  
     Veri türü için uygun görselleştiriciler bir listesinden seçmek için Görselleştirici yanındaki açılır oka tıklayın.  
  
     Görselleştirici bilgileri görüntüler.  
  
## <a name="adding-information-to-a-watch-window"></a>Bir Gözcü penceresi için bilgi ekleme  
 Bir değişken izlemek devam etmek istiyorsanız, bir değişkene ekleyebilirsiniz **Watch** bir DataTip penceresinde.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>İzle penceresine bir değişken eklemek için  
  
-   Bir DataTip sağ tıklayın ve ardından **Gözcü Ekle**.  
  
     Değişken eklenir **Watch** penceresi. Birden çok destekleyen bir sürüm kullanıyorsanız **Watch** windows, değişkenin eklendiği **Watch 1.**  
  
## <a name="importing-and-exporting-datatips"></a>İçeri aktarma ve veri ipuçlarını dışarı aktarma  
 Bir iş arkadaşınızla paylaşılabilir veya bir metin düzenleyicisi kullanarak düzenlenebilir bir XML dosyasına veri ipuçlarını dışarı aktarabilirsiniz.  
  
#### <a name="to-export-datatips"></a>Veri ipuçlarını dışarı aktarmak için  
  
1.  Hata Ayıklama menüsünde **veri ipuçlarını dışarı aktar**.  
  
     **Veri ipuçlarını dışarı aktar** iletişim kutusu görüntülenir.  
  
2.  XML dosyasını, dosyasında için bir ad yazın istediğiniz konuma gitmek için standart dosya teknikleri kullanın **dosya adı** kutusuna ve ardından **Tamam**.  
  
#### <a name="to-import-datatips"></a>Veri ipuçlarını içeri aktarmak için  
  
1.  Hata Ayıklama menüsünde **alma DataTips**.  
  
     **Alma DataTips** iletişim kutusu görüntülenir.  
  
2.  İletişim kutusunu açıp istediğiniz XML dosyasını bulmak için kullanın **Tamam**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)   
 [Nasıl yapılır: QuickWatch iletişim kutusunu kullanın](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Özel Görselleştiriciler oluşturma](../debugger/create-custom-visualizers-of-data.md)   
 [Nasıl yapılır: hata ayıklayıcı Windows sayısal biçimini değiştirme](http://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)



