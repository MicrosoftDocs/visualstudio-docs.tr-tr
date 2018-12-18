---
title: Çağrı yığınının görsel haritasını oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/26/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- call stacks, code maps
- Call Stack window, mapping calls
- debugging [Visual Studio], diagramming the call stack
- call stacks, mapping
- Call Stack window, visualizing
- debugging code visually
- debugging [Visual Studio], mapping the call stack
- call stacks, visualizing
- debugging, code maps
- Call Stack window, tracing calls visually
- Call Stack window, show on code map
- debugging [Visual Studio], tracing the call stack visually
- debugging [Visual Studio], visualizing the call stack
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ede973d96ffe21fb9406bb471400ffa8e2b69251
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389584"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging"></a>Hata ayıklama sırasında çağrı yığınının görsel haritasını oluşturma 

Hata ayıklarken çağrı yığınını görsel olarak izlemek için bir kod Haritası oluşturun. Kodun ne yaptığını, böylece hata bulmaya odaklanabilirsiniz izlemek için harita üzerinde not alabilirsiniz.

Bir kılavuz için şu videoyu izleyin: [Video: (kanal 9) kod Haritası hata ayıklayıcı Tümleştirmesi ile görsel olarak hata ayıklama](http://go.microsoft.com/fwlink/?LinkId=293418)

Komutlar ve kod haritaları ile kullanabileceğiniz Eylemler ayrıntıları için bkz: [göz atma ve yeniden düzenleme kod eşlemeleri](../modeling/browse-and-rearrange-code-maps.md).

>[!IMPORTANT]
>Oluşturabileceğiniz kod eşlemeleri yalnızca [Visual Studio Enterprise sürümünde](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

Bir kod Haritası hızlı bir bakış şu şekildedir:

 ![Kod haritalarına çağrı yığınları ile hata ayıklama](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

##  <a name="MapStack"></a> Çağrı yığınını eşleme

1. Bir Visual Studio Enterprise'da C#, Visual Basic, C++, JavaScript veya X seçerek hata ayıklamaya başlayın, proje ++ **hata ayıklama** > **hata ayıklamayı Başlat** ya basarak **F5**.
   
1. Uygulamanız Kesme moduna girdiğinde ya da bir işleve sonra seçin **hata ayıklama** > **kod Haritası**, veya basın **Ctrl**+**kaydırma** +**`**.

   Geçerli çağrı yığını yeni bir kod haritası üzerinde turuncu renkte görüntülenir:

   ![Bkz: kod haritasında çağrı yığınını](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

Kodu haritalayarak güncelleştirmeleri otomatik olarak hata ayıklama devam ederken. Harita öğelerini veya Düzen değiştiriliyor kodu herhangi bir şekilde etkilemez. Haritadaki herhangi bir şeyi rahatça yeniden adlandırabilir, taşıyabilir veya kaldırabilirsiniz.

Bir öğe hakkında daha fazla bilgi için üzerine gelin ve öğenin ipucuna bakın. Belirleyebilirsiniz **gösterge** araç çubuğunda her simgenin ne anlama geldiğini öğrenebilirsiniz.

![Kod Haritası gösterge](../debugger/media/debuggermap_showlegend.png "kod Haritası gösterge")

>[!NOTE]
>İleti **diyagram kodu daha eski bir sürümünü temel alıyor olabilir** kodun üstünde harita anlamına gelir haritayı son güncelleştirmenizden sonra kod değişmiş olabilir. Örneğin, harita üzerindeki bir çağrı artık kodda bulunmayabilir. İletiyi kapatın ve haritayı yeniden güncelleştirmeden önce çözümü yeniden oluşturmayı deneyin.

## <a name="map-external-code"></a>Dış kod eşleme

Varsayılan olarak, yalnızca kendi kodunuzu harita üzerinde görüntülenir. Harita üzerinde harici kodu görmek için:
  
- Sağ **çağrı yığını** penceresi ve select **harici kodu Göster**:
  
  ![Çağrı yığını penceresini kullanarak dış kod görüntüleme](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")
- Ya da seçimini **yalnızca benim kodumu etkinleştir** Visual Studio'daki **Araçları** (veya **hata ayıklama**) > **seçenekleri**  >   **Hata ayıklama**:
  
  ![Seçenekler iletişim kutusunu kullanarak dış Kodu Göster](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

## <a name="control-the-maps-layout"></a>Haritanın düzenini denetleme

Haritanın düzenini değiştirerek, herhangi bir şekilde kod etkilemez. 

Haritanın düzenini denetlemek için seçin **Düzen** menüsünü harita araç çubuğunda. 

İçinde **Düzen** menüsünü şunları yapabilirsiniz:

-   Ekran düzenini değiştirin.
-   Harita kaldırarak otomatik olarak yeniden düzenleme Durdur **otomatik olarak hata ayıklama sırasında Düzen**.
-   Kaldırarak öğeleri eklediğinizde, eşlemeyi olabildiğince az yeniden düzenlemek **artan düzen**.

##  <a name="MakeNotes"></a> Kodla ilgili notlar alın

Kodda neler olduğunu izlemek için yorum ekleyebilirsiniz. 

Açıklama eklemek için kod Haritası'nda sağ tıklayıp **Düzenle** > **yeni açıklama**, ardından bir açıklama yazın. 

Bir açıklamaya yeni bir satır eklemek için basın **Shift**+**Enter**.

 ![Kod haritasında çağrı yığını için açıklama ekleme](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

##  <a name="UpdateMap"></a> Sonraki çağrı yığını ile eşlemeyi güncelleyin

Harita, uygulamanızı sonraki kesme noktasına ya da adım bir işleve çalıştırma gibi yeni çağrı yığınları otomatik olarak ekler.

![Sonraki çağrı yığını ile güncelleştirme kod Haritası](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

Eşlemeyi otomatik olarak yeni çağrı yığınları eklemesini durdurmayı seçin ![Show çağrı yığınını kod haritasında otomatik olarak](../debugger/media/debuggermap_automaticupdateicon.gif "Show çağrı yığınını kod haritasında otomatik olarak") kod harita araç çubuğunda. Harita, varolan çağrı yığınlarını vurgulamaya devam eder. Geçerli çağrı yığınını eşlemeye el ile eklemek için basın **Ctrl**+**Shift**+**`**. 

##  <a name="AddRelatedCode"></a> Eşlemeye ilgili kodu ekleyin

Bir eşlem içinde kendinizi göre C# veya Visual Basic, alanlar, özellikler ve kodda neler olduğunu izlemek için diğer yöntemler gibi öğeleri ekleyebilirsiniz. 

Kodda bir yöntem tanımına gitmek için bir eşlem içindeki bir yöntemi çift tıklatın veya seçin ve basın **F12**, sağ tıklatın ve seçin **tanıma**.

![Kod haritasında bir yöntem için kod tanımı Git](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

Haritaya izlemek istediğiniz öğeleri eklemek, bir yönteme sağ tıklayın ve izlemek istediğiniz öğeleri seçin. En son eklenen öğeler yeşil görünür.

![Metoda çağrı yığınını kod haritasında ilgili alanları](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

>[!NOTE]
>Varsayılan olarak, öğeleri haritaya ekleme sınıfı, ad alanı ve derlemeye gibi üst düğümleri gruplandırma ekler. Seçerek bu özelliği kapatıp açabilirsiniz **dahil üst** düğmesine basarak veya kod harita araç çubuğunda **Ctrl** öğeleri eklerken.

![Çağrı yığınını kod Haritası üzerinde bir yöntemi alanları gösterin](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

Daha fazla kod görmek için haritayı oluşturmaya devam edin.

 ![Bir alanı kullanan yöntemlerine bakın: çağrı yığınını kod Haritası](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![Çağrı yığınını kod haritasında bir alanı kullanan yöntemleri](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

##  <a name="FindBugs"></a> Eşlemeyi kullanarak hataları bulun
 Kodunuzu görselleştirmeniz, hataları daha hızlı şekilde bulmanıza yardımcı olabilir. Örneğin, çizim bir uygulamada bir hata araştırdığınızı varsayın. Bir çizgi çizip geri almayı denediğinizde, başka bir çizgi çizinceye kadar hiçbir şey olmaz.

 Kesme noktaları ayarlamak için `clear`, `undo`, ve `Repaint` yöntemleri, hata ayıklamayı başlatmak ve bunun gibi bir harita oluşturur:

 ![Başka bir çağrı yığınını kod Haritası eklemek](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Harita çağrısında tüm kullanıcı hareketlerine dikkat edin `Repaint`, dışında `undo`. Yaramamasının nedeni `undo` hemen işe yaramaz.

 Hata düzeltip uygulamayı çalıştırmaya devam etmenizin ardından harita yeni çağrısından ekler `undo` için `Repaint`:

 ![Yeni yöntemi çağrısı için çağrı yığınını kod haritasında eklemek](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="share-the-map-with-others"></a>Haritayı başkalarıyla paylaşabilir

Bir haritayı dışarı aktarabilir, Microsoft Outlook ile başkalarına gönderebilir, çözümünüze kaydedebilir ve sürüm denetimine iade.

Paylaşma veya eşleme kaydetmek için kullanın **paylaşmak** kod Haritası araç. 

![Paylaşım çağrı yığınını kod Haritası başkalarıyla](../debugger/media/debuggermap_sharewithothers.png "başkalarıyla paylaşımı çağrı yığınını kod Haritası")

## <a name="see-also"></a>Ayrıca bkz.
[Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)

[Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)

[Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)

[Kod haritalarına göz atma ve bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)
