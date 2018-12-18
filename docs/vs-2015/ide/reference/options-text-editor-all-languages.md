---
title: Seçenekler, metin düzenleyici, tüm diller | Microsoft Docs
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
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- vs.toolsoptionspages.text_editor.all_languages.scrollbars
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 987e0339f2d27405c81ce05b6a30181a1469be7b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884179"
---
# <a name="options-text-editor-all-languages"></a>Seçenekler, Metin Düzenleyici, Tüm Diller
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Bu iletişim kutusu Kod Düzenleyicisi'nin varsayılan davranışını değiştirmenizi sağlar. Bu ayarları temel üzerine Kod düzenleyicisinde, HTML Tasarımcısı'nın kaynak görünümü gibi diğer düzenleyiciler için de geçerlidir. Bu iletişim kutusunu açmak için seçmeniz **seçenekleri** gelen **Araçları** menüsü. İçinde **metin düzenleyici** klasörünü genişletin **tüm diller** alt seçip **genel**.  
  
> [!CAUTION]
>  Bu sayfa, tüm geliştirme diller için varsayılan seçenekleri ayarlar. Bu iletişim kutusunda bir seçenek sıfırlama genel seçenekleri tüm dillerde hangi seçenekler burada seçilen için sıfırlar olduğunu unutmayın. Yalnızca bir dilin metin düzenleyici seçenekleri değiştirmek için bu dil için alt klasörü genişletin ve seçeneği sayfalarını seçin.  
  
 Bazı programlama dilleri, ancak diğerleri genel seçenekler sayfalarındaki seçeneği seçildiğinde, gri bir onay işareti görüntülenir.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="statement-completion"></a>Deyim Tamamlama  
 Üyeleri otomatik Listele  
 Yazarken düzenleyicide açılan listesi kullanılabilir üyeler, özellikler, değerleri veya yöntemleri seçili olduğunda, IntelliSense tarafından görüntülenir. Öğeyi kodunuza eklemek için açılır listeden herhangi bir öğeyi seçin. Bu seçenek belirlendiğinde **Gelişmiş üyeleri Gizle** seçeneği.  
  
 Gelişmiş üyeleri Gizle  
 Seçili olduğunda, yalnızca en sık kullanılan öğe görüntüleyerek açılır deyim tamamlama listeleri kısaltır. Diğer öğeler listeden filtrelenir.  
  
 Parametre bilgileri  
 Seçili olduğunda, geçerli bildirimi ya da yordamın eksiksiz sözdizimi düzenleyicisinde, tüm kullanılabilir parametrelerinin ile ekleme noktası altında görüntülenir. Atayabileceğiniz bir sonraki parametreyi kalın olarak gösterilir.  
  
## <a name="settings"></a>Ayarlar  
 Sanal boşluğu etkinleştir  
 Bu seçeneği seçildiğinde ve **sözcük kaydırmayı** olan temizlenmiş, herhangi bir kod düzenleyicisi ve türü bir satır bitiminin ötesinde tıklayabilirsiniz. Bu özellik, kodunuzun yanında tutarlı bir noktada açıklamaları konumlandırmak için kullanılabilir.  
  
 Sözcük kaydırma  
 Seçili olduğunda, yatay olarak görüntülenebilir Düzenleyicisi alan genişletir bir satır herhangi bir kısmını sonraki satırda otomatik olarak görüntülenir. Bu seçenek belirlendiğinde **sözcük kaydırma için görsel karakterleri Göster** seçeneği.  
  
> [!NOTE]
>  **Sanal adres alanı** özelliğin açık kapalı durumdayken **sözcük kaydırma** açıktır.  
  
 Sözcük kaydırma için görsel karakterleri Göster  
 Seçili olduğunda, burada bir uzun satır ikinci satıra sarmalar dönüş ok göstergesi görüntülenir.  
  
 ![LineBreakSymbol ekran](../../ide/reference/media/linebreak.gif "linebreak")  
  
 Bu göstergeler görüntülemeyecek tercih ederseniz bu seçeneği temizleyin.  
  
> [!NOTE]
>  Bu anımsatıcı okları kodunuza eklenmez ve yazdırılmaz. Bunlar yalnızca başvuru amaçlıdır.  
  
 Seçim olduğunda Kes veya Kopyala komutlarını boş satırlara Uygula  
 Bu seçenek, ekleme noktasını boş bir satıra yerleştirin, hiçbir şey seçin ve ardından kopyaladığınızda veya Kes Düzenleyicisi davranışını ayarlar.  
  
- Bu seçenek belirlendiğinde, boş satır kopyaladığınız veya Kes. Ardından yapıştırırsanız, yeni, boş bir satır eklenir.  
  
- Bu seçenek işaretli değilse, Cut komutu boş satırları kaldırır. Ancak, Panodaki veriler korunur. Ardından Paste komutu kullanırsanız, bu nedenle, en son Pano'ya kopyalanan içeriği yapıştırılır. Daha önce hiçbir şey kopyalandı, hiçbir şey yapıştırılır.  
  
  Bir satır boş olmadığında bu ayar Kopyala veya Kes üzerinde etkisi yoktur. Hiçbir şey seçili ise, tüm satırı kopyaladığınız veya Kes. Ardından yapıştırırsanız, tüm satırı ve kendi endline karakter yapıştırılan metin.  
  
> [!TIP]
>  Boşluklar, sekmeler ve uçları göstergelerini görüntüleme ve bu nedenle, tamamen boş satırları girintili satırları ayırt etmek için **Gelişmiş** gelen **Düzenle** menüsünü seçip **görünümü beyaz Alanı**.  
  
## <a name="display"></a>Ekran  
 Satır numaraları  
 Bu onay kutusu seçildiğinde, her kod satırının yanındaki satır numarası görüntülenir.  
  
> [!NOTE]
>  Bu satır numaraları kodunuza eklenmez ve yazdırılmaz. Bunlar yalnızca başvuru amaçlıdır.  
  
 Tek tıkla URL gezinmesini etkinleştir  
 Bir URL'yi Düzenleyici üzerinden geçerken seçili olduğunda, fare imlecini işaret eden bir ele değiştirir. Belirtilen sayfayı, Web tarayıcınızda görüntülemek için URL tıklayabilirsiniz.  
  
 Gezinti çubuğu  
 Bu onay kutusu seçildiğinde, görüntüler **gezinti çubuğu** üst kısmında, Kod Düzenleyicisi. Kendi açılan **nesneleri** ve **üyeleri** liste üyelerini, select, kodunuzun belirli bir nesne seçmenizi sağlar ve Kod Düzenleyicisi'nde seçilen üye bildirimi gider.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Seçenekler, metin düzenleyici, tüm diller, sekmeler](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 [Genel, ortam, Seçenekler iletişim kutusu](../../ide/reference/general-environment-options-dialog-box.md)   
 [IntelliSense Kullanma](../../ide/using-intellisense.md)



