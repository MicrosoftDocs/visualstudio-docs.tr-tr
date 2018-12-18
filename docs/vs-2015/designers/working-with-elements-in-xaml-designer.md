---
title: XAML Tasarımcısı'nda öğelerle çalışma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f0ec7d97ace8f61f209e4664c0de42b883a6a5d0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896958"
---
# <a name="working-with-elements-in-xaml-designer"></a>XAML Tasarımcısı'nda öğelerle çalışma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Öğeleri ekleyebilirsiniz; denetimler, düzenler ve şekiller — uygulamanıza XAML, kod veya XAML Tasarımcısını kullanarak. Bu konuda, Visual Studio veya Visual Studio için Blend, XAML Tasarımcısı'nda öğelerle çalışma açıklar.  
  
## <a name="adding-an-element-to-a-layout"></a>Bir öğe için bir düzen ekleme  
 *Düzen* boyutlandırma ve bir kullanıcı Arabiriminde öğelerin konumlandırmasını, işlemidir. Görsel öğeleri konumlandırmak için bunları bir düzende yerleştirmelisiniz [paneli](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.panel.aspx). A `Panel` koleksiyonu olan bir alt özelliğine sahiptir, [FrameworkElement](http://msdn.microsoft.com/library/windows/apps/br208706.aspx) türleri. Çeşitli kullanabileceğiniz `Panel` alt öğeleri gibi [tuval](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.canvas.aspx), [StackPanel](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.stackpanel.aspx), ve [kılavuz](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx), Düzen kapsayıcıları görev yapacak ve getirin ve öğeleri düzenlemek için bir sayfa üzerinde.  
  
 Varsayılan olarak, bir `Grid` paneli sayfa veya form içinde üst düzey Düzen kapsayıcısı olarak kullanılır. Düzen bölmeleri, denetimleri veya diğer öğeleri içinde üst düzey sayfa düzeni ekleyebilirsiniz.  
  
#### <a name="to-add-an-element-to-a-layout"></a>Bir öğenin bir düzenine eklemek için  
  
-   XAML Tasarımcısı'nda, aşağıdakilerden birini yapın:  
  
    -   Bir öğedeki çift **araç kutusu** (veya araç kutusundan bir öğe seçin ve Enter tuşuna basın).  
  
    -   Bir öğeyi sürükleyin **araç kutusu** çalışma yüzeyine.  
  
    -   İçinde **araç kutusu**, çizim araçlarından birini seçin (örneğin, [elipsin](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.ellipse.aspx) veya [dikdörtgen](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.aspx)) ve sonra etkin panelindeki bir öğesi çizin.  
  
## <a name="changing-the-layering-order-of-elements"></a>Öğeleri katman sırasını değiştirme  
 XAML Tasarımcısı'nda çalışma yüzeyine iki öğe olduğunda, bir öğe katman sırasını diğer önünde görünür. Belge Anahattı öğeleri listesi kısmındaki en öndedir öğesi penceredir (ne zaman dışında **haritadaki** özelliği bir öğe için). Sayfa, form veya Düzen kapsayıcısı için bir öğe eklediğinizde, öğe otomatik olarak etkin kapsayıcı öğe diğer öğeleri önüne yerleştirilir. Öğelerin sırasını değiştirmek için kullanabileceğiniz **sipariş** komutları veya belge ana hattı penceresinin nesne ağacında öğeleri sürükleyin.  
  
#### <a name="to-change-the-layering-order"></a>Katman sırasını değiştirmek için  
  
- Aşağıdakilerden birini yapın:  
  
  - İçinde **belge anahattı** penceresi, istenen katman sırasını oluşturmak için aşağı veya yukarı öğeleri sürükleyin.  
  
  - Belge Anahattı penceresi veya üzerine gelin, katman sırasını değiştirmek istediğiniz çalışma yüzeyi öğe sağ **sipariş**ve sonra aşağıdakilerden birine tıklayın:  
  
    -   **Öne Getir** öğe tüm sipariş öne getirmek için.  
  
    -   **Öne Getir** öğe getirmek için sırada bir düzey iletin.  
  
    -   **Geri gönderme** öğesi geri bir düzey sıraya göndermek için.  
  
    -   **Arkaya Gönder** öğe tüm sırasını geri göndermek için.  
  
    Değişiklik **haritadaki** özelliğinde **Düzen** Özellikler penceresindeki bölümü. Çakışan öğe için **haritadaki** özelliğini belge anahat penceresinde gösterilen öğelerin sırasını üzerinden öncelik alır. Bir alt sahip bir öğe **haritadaki** değeri önde öğeleri çakışma halinde görünür.  
  
## <a name="changing-the-alignment-of-an-element"></a>Bir öğe hizalamasını değiştirme  
 Menü komutlarını kullanarak veya dayama çizgilerine öğeleri sürükleyerek çalışma yüzeyine öğeleri getirebilirsiniz.  
  
 A *snapline* yardımcı olan görsel bir ipucu hizalama uygulamadaki diğer öğeleri göreli öğe olan.  
  
#### <a name="to-align-two-or-more-elements-by-using-menu-commands"></a>İki veya daha fazla öğe, menü komutlarını kullanarak hizalamak için  
  
1.  Hizalamak için kullanmak istediğiniz öğeleri seçin. Tuşuna basarak ve öğeleri seçerken Ctrl tuşunu basılı tutarak birden fazla öğe seçebilirsiniz.  
  
2.  Altında aşağıdaki özelliklerden birini **HorizontalAlignment** içinde **Düzen** Özellikler penceresini bölümünü: **sol**, **Merkezi**, **Sağ**, veya **Esnetme**.  
  
3.  Altında aşağıdaki özelliklerden birini **VerticalAlignment** içinde **Düzen** Özellikler penceresini bölümünü: **üst**, **Merkezi**, **Alt**, veya **Esnetme**.  
  
#### <a name="to-align-two-or-more-elements-by-using-snaplines"></a>Dayama çizgileri kullanarak iki veya daha fazla öğe hizalamak için  
  
-   XAML Tasarımcısı'nda, en az iki öğe içeren bir düzene sürükleyin veya edge başka bir öğe ile hizalanır. böylece öğelerden birini yeniden boyutlandırın.  
  
     Kenarlara hizalandığını, bir *hizalama sınırı* hizalama görünür. Hizalama, kırmızı bir kesikli çizgiye sınırıdır. Hizalama sınırları yalnızca görünür **dayama çizgilerine yaslamayı** etkinleştirilir. Çalışma yüzeyine bir hizalama sınırı gösteren çizim için bkz [XAML Tasarımcısını kullanarak kullanıcı Arabirimi oluşturma](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
## <a name="changing-the-an-elements-margins"></a>Değiştirme bir öğenin kenar boşlukları  
 XAML Tasarımcısı'nda kenar boşlukları, çalışma yüzeyinde bir öğe etrafında boş alan miktarını belirler. Örneğin, kenar boşlukları bir öğenin dış kenarları sınırları arasındaki boşluk miktarını belirtin bir `Grid` öğeyi içeren paneli. Kenar boşlukları da bulunan öğeler arasındaki boşluk miktarını belirtin bir `StackPanel`.  
  
#### <a name="to-change-an-elements-margins-in-the-properties-window"></a>Özellikler penceresinde bir öğenin kenar boşluklarını değiştirmek için  
  
1.  Kenar boşluklarını değiştirmek istediğiniz öğeyi seçin.  
  
2.  Altında **Düzen** Özellikler penceresinde değeri (piksel veya yaklaşık 1/96 inç olan CİHAZDAN bağımsız birimler) herhangi birini değiştirin **kenar boşluğu** özellikleri (**üst**, **Sol**, **sağ**, veya **alt**).  
  
#### <a name="to-change-an-elements-margins-in-the-artboard"></a>Çalışma yüzeyine bir öğenin kenar boşluklarını değiştirmek için  
  
-   Düzen kapsayıcısı göreli öğe kenar boşluklarını değiştirmek için tıklayın *margin donatıcıları* görünen çalışma yüzeyi öğe etrafında öğe seçildiğinde ve içinde bir düzen kapsayıcıdır. Kenar boşluğu donatıcıları gösteren çizim için bkz: [XAML Tasarımcısını kullanarak kullanıcı Arabirimi oluşturma](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
     Kenar boşluğu donatıcısı yatay veya dikey olarak açıksa, bu kenar boşluğu ayarlanmamış. Kenar boşluğu donatıcısı kapalı ise, bu kenar boşluğu ayarlıdır.  
  
     Kenar boşluğu donatıcısı açın ve ters kenar boşluğu ayarlı değil, ters kenar çalışma yüzeyine öğenin konumuna göre doğru değerine ayarlanır. Ters kenar boşlukları için gibi **sol** ve **sağ** kenar boşlukları, en az bir özelliği ayarlandığında her zaman.  
  
    > [!IMPORTANT]
    >  Öğelerin yerleştirilmesi bazı Düzen kapsayıcıları içinde gibi bir <xref:Windows.UI.Xaml.Controls.Canvas>, kenar boşluğu donatıcıları yok. Öğelerin yerleştirilmesi içinde bir <xref:Windows.UI.Xaml.Controls.StackPanel> kenar boşluğu donatıcıları ya da sol ve sağ kenar boşluklarının veya yönünü bağlı olarak üst ve alt kenar boşluklarını sahip `StackPanel`.  
  
## <a name="grouping-and-ungrouping-elements"></a>Gruplandırma ve öğeleri gruplarını çözme  
 XAML Tasarımcısı'nda iki veya daha fazla öğe gruplandırma, yeni bir düzen kapsayıcısı oluşturur ve bu öğeler bu kapsayıcı içinde yerleştirir. İki veya daha fazla öğe birlikte bir düzen kapsayıcısına yerleştirerek kolayca seçin, taşıma ve o gruptaki öğeleri bir öğe olarak varsa dönüştürmenize olanak sağlar. Gruplama, bir gezinti öğesini oluşturan düğmeler gibi bir şekilde birbiriyle ilgili öğeleri tanımlamak için yararlıdır. Öğeleri çözdüğünüzde, basitçe öğeleri içeren düzen kapsayıcısının siliyorsunuz.  
  
#### <a name="to-group-elements-into-a-new-layout-container"></a>Yeni bir düzen kapsayıcısına için Grup öğeleri  
  
1.  Gruplandırmak için kullanmak istediğiniz öğeleri seçin. (Birden fazla öğe seçmek için tuşuna basın ve bunları tıklatırken Ctrl tuşunu basılı tutun.)  
  
2.  Seçili öğeye sağ tıklayın, fareyle **halinde Gruplandır**ve ardından ve grubun yer almasını istediğiniz düzen kapsayıcısı türüne tıklayın.  
  
    > [!TIP]
    >  Seçerseniz <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border>, veya <xref:Windows.UI.Xaml.Controls.ScrollViewer> öğelerinizin gruplandırmak için öğelerin yeni bir yerleştirilir <xref:Windows.UI.Xaml.Controls.Grid> içinde panelinde <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border>, veya <xref:Windows.UI.Xaml.Controls.ScrollViewer>. Öğeleri yalnızca bu düzen kapsayıcıları birinde'ungroup <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border>, veya <xref:Windows.UI.Xaml.Controls.ScrollViewer> silindi ve <xref:Windows.UI.Xaml.Controls.Grid> paneli kalır. Silinecek `Grid` panelinde, öğeleri grubunu tekrar çözün.  
  
#### <a name="to-ungroup-elements-and-delete-the-layout"></a>Öğe grubunu Çöz ve düzenini silmek için  
  
- Grubunu çözmek ve istediğiniz gruba sağ tıklayıp **Ungroup**.  
  
  Gruplandırma veya grubu çözme öğeleri Belge Anahattı penceresi seçili öğelere sağ tıklatıp ayrıca **halinde Gruplandır** veya **Ungroup**.  
  
## <a name="resetting-the-element-layout"></a>Öğesi düzeni sıfırlama  
 Düzeni Sıfırla komutlarını kullanarak, bir öğenin belirli düzen özellikleri için varsayılan değerleri geri yükleyebilirsiniz. Bu komutu kullanarak, tek tek veya topluca kenar boşluğu, hizalama, genişlik, yükseklik ve bir öğenin boyutunu sıfırlayabilirsiniz.  
  
#### <a name="to-reset-the-element-layout"></a>Öğe yerleşimi sıfırlamak için  
  
-   Belge Anahattı penceresi ya da çalışma yüzeyi, öğeye sağ tıklayın, seçin **Düzen**, **sıfırlama** *PropertyName*burada *PropertyName*sıfırlamak istediğiniz özelliktir (veya tercih **Düzen**, **Tümünü Sıfırla** öğesi için düzen özelliklerini sıfırlamak için).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)



