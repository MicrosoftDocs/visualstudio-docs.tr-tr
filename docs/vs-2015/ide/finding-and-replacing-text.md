---
title: Metin bulma ve değiştirme | Microsoft Docs
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
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- find, text
- Find in Files dialog box
- find
- text searches, finding and replacing text
- Replace dialog box
- text, finding and replacing
- find, symbol
- find and replace
- replace
- find text
- replacing text
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4bbe1456632b2707ca548582bb278f7646ec540
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273448"
---
# <a name="finding-and-replacing-text"></a>Metin Bulma ve Değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bul ve Visual Studio Kod Düzenleyicisi ve belirli metin temelli çıktı pencerelerinde metni gibi değiştirin **sonuçları Bul** kullanarak windows **Bul ve Değiştir** denetim veya **Bul / Dosyalarda Değiştir**. Ayrıca arama ve bazı XAML Tasarımcısı ve Windows Forms Tasarımcısı gibi tasarımcı pencerelerinde ve araç pencerelerinde de değiştirme  
  
 Geçerli belgede, geçerli çözüm veya özel bir klasör kümesi için arama kapsamını belirleyebilirsiniz. Ayrıca, bir çoklu dosya aramaları için dosya adı uzantıları kümesi de belirtebilirsiniz. .NET normal ifadelerini kullanarak arama sözdizimini özelleştirebilirsiniz.  
  
 Bul ve Değiştir normal ifadeler için bkz: [Visual Studio'da normal ifadeler kullanarak](../ide/using-regular-expressions-in-visual-studio.md).  
  
> [!TIP]
>  **Bul/komut** kutusu araç çubuğu denetimi olarak hala kullanılabilir, ancak artık varsayılan olarak görünür. Görüntüleyebileceğiniz **Bul/komut** kutusunu **Düğme Ekle veya Kaldır** üzerinde **standart** araç çubuğu ve ardından **Bul**. Daha fazla bilgi için [Bul/komut kutusu](../ide/find-command-box.md).  
  
## <a name="find-and-replace-control"></a>Bul ve Değiştir denetimi  
 **Bul ve Değiştir** denetimi kod düzenleyici penceresinin sağ alt köşesinde görünür. **Bul ve Değiştir** denetimi belirtilen arama dizesinin geçerli belgede her geçtiği yeri hemen vurgular. Seçim yaparak başka bir oluşumdan diğerine gidebilirsiniz **Sonrakini Bul** düğmesini veya **Öncekini Bul** arama denetimin üzerindeki düğme.  
  
 Yanındaki düğmeyi seçerek değiştirme seçeneklerine erişebilirsiniz **Bul** metin kutusu. Aynı anda bir tane değişiklik yapmaya karar **Değiştir** düğmesinin yanındaki **değiştirin** metin kutusu. Tüm eşleşmeleri değiştirmek için seçin **Tümünü Değiştir** düğmesi.  
  
 Eşleşmeler için vurgulama rengini değiştirmek için seçin **Araçları** menüsünde **seçenekleri**ve ardından **ortam**seçip **yazı tipleri ve renkler** . İçinde **ayarlarını göster** listesinden **metin düzenleyici**ve ardından **görüntü öğeleri** listesinden **Vurgu Bul (uzantı)**.  
  
### <a name="searching-tool-windows"></a>Aracı Windows arama  
 Kullanabileceğiniz **bulmak** gibi kod veya metin pencerelerinde denetim **çıkış** windows, ve **sonuçları Bul** seçerek windows **Bul ve Değiştir**üzerinde **Düzenle** menüsü ya da (CTRL + F).  
  
 Bul denetiminin bir sürümü bazı araç pencerelerinde de kullanılabilir. Örneğin, artık denetim listesini filtreleyebilirsiniz **araç kutusu** arama kutusuna metin girerek penceresi. Şimdi bunların içeriğini aramanıza olanak veren diğer araç pencereleri dahil **Çözüm Gezgini**, **özellikleri** penceresinde ve **Takım Gezgini**, diğerlerinin yanı sıra.  
  
## <a name="findreplace-in-files"></a>Dosyalarda Bul/Değiştir  
 **Dosyalarda Bul/Değiştir** gibi çalışır **Bul ve Değiştir** denetimi aramanız için bir kapsam tanımlayabilmenizdir. Yalnızca geçerli açık dosya Düzenleyicisi'nde arama yapabilirsiniz, ancak aynı zamanda arayabilirsiniz bütün açık belgeleri, tüm çözümü, geçerli proje ve seçili klasör kümelerini. Dosya adı uzantısına göre de arayabilirsiniz. Erişim için **dosyalarda Bul/Değiştir** iletişim kutusunda **Bul ve Değiştir** üzerinde **Düzenle** menü (veya CTRL + SHIFT + F).  
  
 Seçeneğini belirlediğinizde **Tümünü Bul**, **sonuçları Bul** penceresi açılır ve aramanız için eşleşmeleri listeler. Listede bir sonuç seçerek ilişkili dosyayı görüntüler ve eşleşmeyi vurgular. Dosyayı düzenlemek için açık değilse, bunu sekmenin sağ tarafındaki bir önizleme sekmesinde de açılır. Kullanabileceğiniz **Bul** arama denetimi **sonuçları Bul** listesi.  
  
### <a name="creating-custom-search-folder-sets"></a>Özel arama klasörü kümeleri oluşturma  
 Seçerek bir arama kapsamı tanımlayabilirsiniz **arama klasörlerini Seç** düğmesine (gibi görünüyor **...** ) yanındaki **konum** kutusu. İçinde **arama klasörlerini Seç** iletişim kutusunda, aranacak klasörler kümesi belirtebilirsiniz ve daha sonra yeniden belirtim kaydedebilirsiniz. Yalnızca sürücüsünü yerel makineye eşlediğiniz uzak makinede klasörler belirtebilirsiniz.  
  
### <a name="creating-custom-component-sets"></a>Özel bileşen kümeleri oluşturma  
 Seçerek bileşen kümelerini arama Kapsamınız olarak tanımlayabilirsiniz **özel bileşen kümesini Düzenle** düğmesinin yanındaki **konum** kutusu. Yüklü .NET veya COM bileşenlerini, çözümünüze veya (.dll, .tlb, .olb, .exe veya .ocx) herhangi bir derleme veya tür kitaplığı dahil Visual Studio projeleri belirtebilirsiniz. Başvurular aramak için seçin **başvurularda bak** kutusu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da Normal İfadeler Kullanma](../ide/using-regular-expressions-in-visual-studio.md)



