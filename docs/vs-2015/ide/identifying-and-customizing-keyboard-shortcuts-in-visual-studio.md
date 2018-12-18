---
title: Klavye Kısayollarını Tanımlama ve Özelleştirme
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
- VS.ToolsOptionsPages.Environment.Keyboard
helpviewer_keywords:
- keyboard shortcuts [Visual Studio], customizing
- importing shortcut keys [Visual Studio]
- shortcut key combinations [Visual Studio]
- commands [Visual Studio], shortcut keys
- custom shortcut keys [Visual Studio]
- customizing keyboard shortcuts [Visual Studio]
- exporting shortcut keys [Visual Studio]
ms.assetid: d2774be2-60a4-4d6f-95f1-79d0d9e55b56
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac425903ade4dbf90f094376927d46629b1c675d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53054005"
---
# <a name="identifying-and-customizing-keyboard-shortcuts-in-visual-studio"></a>Visual Studio'daki Klavye Kısayollarını Tanımlama ve Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio komutları için kısayollar tanımlayabilir, bu kısayolları özelleştirebilir ve başkalarının kullanması için dışarı aktarabilirsiniz. Birçok kısayol her zaman aynı komutları çağırır, ancak kısayolun davranışı aşağıdaki koşullara göre değişebilir:

- Visual Studio'yu ilk kez çalıştırdığınızda seçtiğiniz varsayılan ortam ayarları (örneğin, Genel Geliştirme veya Visual C#).

- Kısayolun davranışını özelleştirip özelleştirmediğiniz.

- Kısayolu seçtiğiniz anda içinde bulunduğunuz bağlam. Örneğin F2 kısayolu, Ayarlar Tasarımcısı'nı kullanıyorsanız Edit.EditCell komutunu, Ekip Gezgini'ni kullanıyorsanız File.Rename komutunu çağırır.

  Ayarları, özelleştirme ve bağlam bağımsız olarak her zaman bulabilir ve klavye kısayolu Değiştir **seçenekleri** iletişim kutusu. Birkaç düzine komutlar için varsayılan klavye kısayolları da arayabilirsiniz [sık kullanılan komutlar için varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md), ve (genel geliştirmeye göre tüm varsayılan kısayolların eksiksiz bir listesini bulabilirsiniz Ayarları) içinde [varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md).

  **Bu konudaki**

- [Klavye kısayolu tanımlama](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_identify)

- [Klavye kısayolunu özelleştirme](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_assign)

- [Özel klavye kısayollarını paylaşma](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_transfer)

  Bir komuta Genel bağlamda kısayol atanmış ve diğer bağlamlarda atanmamışsa, ilgili kısayol her zaman bu komutu çağırır. Ancak bir kısayol, Genel bağlamda bir komuta ve özel bağlamda farklı bir komuta atanabilir. Böyle bir komutu özel bağlamda kullanırsanız, özel bağlama ilişkin komutu çağırır (Genel bağlama ilişkin komutu çağırmaz).

> [!NOTE]
>  Ayarlarınıza ve Visual Studio sürümünüze göre, menü komutlarının adları ve konumları ve iletişim kutularında görünen seçenekler değişik olabilir. Bu konuda dayanır **genel geliştirme ayarları**.

##  <a name="bkmk_identify"></a> Klavye kısayolu tanımlama

1.  Menü çubuğunda, **Araçları**, **seçenekleri**.

2.  Genişletin **ortam**ve ardından **klavye**.

     ![Seçenekler iletişim kutusunda görüntüleme klavye kısayolları](../ide/media/optionskeyboard.png "OptionsKeyboard")

3.  İçinde **içeren komutları göster** kutusuna, boşluk olmadan komutun adını bir kısmını veya tamamını girin.

     Örneğin, için komutları bulabilirsiniz **solutionexplorer**.

4.  Listede doğru komutu seçin.

     Örneğin, seçebileceğiniz **View.SolutionExplorer**.

5.  Komutun bir klavye kısayolu varsa görünür **seçili komut için kısayollar** listesi.

     ![Belirtilen komut için bir kısayol görüntülemek](../ide/media/viewshortcut.png "ViewShortcut")

##  <a name="bkmk_assign"></a> Klavye kısayolunu özelleştirme

1.  Menü çubuğunda, **Araçları**, **seçenekleri**.

2.  Genişletin **ortam** klasörünü ve ardından **klavye**.

     ![Seçenekler iletişim kutusunda görüntüleme klavye kısayolları](../ide/media/optionskeyboard.png "OptionsKeyboard")

3.  İçinde **içeren komutları göster** kutusuna, boşluk olmadan komutun adını bir kısmını veya tamamını girin.

     Örneğin, için komutları bulabilirsiniz **solutionexplorer**.

4.  Listede, klavye kısayolu atamak istediğiniz komutu seçin.

5.  İçinde **kullanım yeni kısayolu şunun içinde** listesinde, kısayolu kullanmak istediğiniz özellik alanını seçin.

     Örneğin, seçebileceğiniz **genel** kısayolun her bağlamda çalışmasını istiyorsanız. Başka bir düzenleyicide Genel olarak eşlenmemiş herhangi bir kısayolu kullanabilirsiniz. Aksi takdirde düzenleyici kısayolu geçersiz kılar.

    > [!NOTE]
    >  Bir klavye kısayolunu parçası olarak şu tuşları atayamazsınız **genel**: yazdırma ekran/Sys Rq, kaydırma Lock, Pause/Break, sekme, Caps Lock, INSERT, Home, End, Page Up, Page Down, Windows logosu tuşu, uygulama anahtarı, herhangi bir ok anahtarları veya Enter; Num Lock, Delete veya sayısal tuş takımındaki; temizleyin veya Ctrl + Alt + Delete.

6.  İçinde **kısayol tuşlarına basın** kutusunda, kullanmak istediğiniz kısayolu girin.

    > [!NOTE]
    >  Bir harfi; Alt tuşu, Ctrl tuşu veya her ikisiyle birden birleştiren bir kısayol oluşturabilirsiniz. Ayrıca Shift tuşu ve bir harfi; Alt tuşu, Ctrl tuşu veya her ikisiyle birden birleştiren bir kısayol da oluşturabilirsiniz.

     Bir kısayol zaten başka bir komuta atanmışsa görünür **şu anda kullandığı kısayolunu** kutusu. Bu durumda, farklı birini denemden önce kısayolu silmek için Geri Al tuşunu seçin.

     ![Bir komut için farklı bir kısayol belirtin](../ide/media/reassignshortcut.png "ReassignShortcut")

7.  Seçin **atama** düğmesi.

    > [!NOTE]
    >  Bir komut için farklı bir kısayol belirtirseniz **atama** düğmesine ve ardından **iptal** düğmesi, iletişim kutusu kapanır, ancak değişiklik geri alınır.

##  <a name="bkmk_transfer"></a> Özel klavye kısayollarını paylaşma
 Özel klavye kısayollarınızı bir dosyaya dışarı aktararak ve verileri içeri aktarabilmeleri için bu dosyayı başkalarına vererek, klavye kısayollarınızı paylaşabilirsiniz.

#### <a name="to-export-only-keyboard-shortcuts"></a>Yalnızca klavye kısayollarını dışarı aktarmak için

1.  Menü çubuğunda, **Araçları**, **içeri ve dışarı aktarma ayarları**.

2.  Seçin **seçili ortam ayarlarını dışarı aktar**ve ardından **sonraki** düğmesi.

3.  Altında **hangi ayarları dışarı aktarmak istiyor musunuz?** temizleyin **tüm ayarlar** onay kutusunu işaretleyin, genişletme **seçenekleri**ve ardından **ortam**.

4.  Seçin **klavye** onay kutusunu işaretleyin ve ardından **sonraki** düğmesi.

     ![Dışarı aktarma, yalnızca klavye kısayollarını özelleştirilmiş](../ide/media/exportshortcuts.png "ExportShortcuts")

5.  İçinde **ne ayarlar dosyanızı adlandırın istiyor musunuz?** ve **ayarlarımı bu dizinde Store** kutularında ya da varsayılan değerleri bırakın veya farklı değerler belirtin ve ardından  **Son** düğmesi.

     Varsayılan olarak kısayollarınız %USERPROFILE%\Documents\Visual Studio 2013\Settings klasöründe bulunan bir dosyaya kaydedilir. Dosyanın adı ayarları dışarı aktardığınız tarihi yansıtır ve uzantısı .vssettings olur.

#### <a name="to-import-only-keyboard-shortcuts"></a>Yalnızca klavye kısayollarını içeri aktarmak için

1.  Menü çubuğunda, **Araçları**, **içeri ve dışarı aktarma ayarları**.

2.  Seçin **seçili ortam ayarlarını içeri aktarma** seçenek düğmesini ve ardından **sonraki** düğmesi.

3.  Seçin **Hayır, sadece yeni ayarları, geçerli ayarlarımı alma** seçenek düğmesini ve ardından **sonraki** düğmesi.

4.  Altında **ayarlarım**, içeri aktarma veya seçmek istediğiniz kısayolları içeren dosyayı seçin **Gözat** doğru dosyayı bulmak için düğme.

5.  Seçin **sonraki** düğmesi.

6.  Altında **hangi ayarları içeri aktarmak istiyor musunuz?** temizleyin **tüm ayarlar** onay kutusunu işaretleyin, genişletme **seçenekleri**ve ardından **ortam**.

7.  Seçin **klavye** onay kutusunu işaretleyin ve ardından **son** düğmesi.

     ![İçeri aktarma, yalnızca klavye kısayollarını özelleştirilmiş](../ide/media/importshortcuts.png "ImportShortcuts")

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'nun Erişilebilirlik Özellikleri](../ide/reference/accessibility-features-of-visual-studio.md)
