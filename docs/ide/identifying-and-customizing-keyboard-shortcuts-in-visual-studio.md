---
title: Klavye kısayollarını tanımlama ve özelleştirme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 61ea8d6ee9243f79fe250872820643904bb2367a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062997"
---
# <a name="identify-and-customize-keyboard-shortcuts-in-visual-studio"></a>Tanımlamak ve Visual Studio'daki klavye kısayollarını özelleştirme

Visual Studio komutları için kısayollar tanımlayabilir, bu kısayolları özelleştirebilir ve başkalarının kullanması için dışarı aktarabilirsiniz. Birçok kısayol her zaman aynı komutları çağırır, ancak kısayolun davranışı aşağıdaki koşullara göre değişebilir:

- Visual Studio'yu ilk kez çalıştırdığınızda seçtiğiniz varsayılan ortam ayarları (örneğin, Genel Geliştirme veya Visual C#).

- Kısayolun davranışını özelleştirip özelleştirmediğiniz.

- Kısayolu seçtiğiniz anda içinde bulunduğunuz bağlam. Örneğin, **F2** kısayol çağırır `Edit.EditCell` kullanıp kullanmadığınızı komutu **ayarlar Tasarımcısı** ve `File.Rename` kullanıp kullanmadığınızı komutu **TakımGezgini**.

Ayarları, özelleştirme ve bağlam bağımsız olarak her zaman bulabilir ve klavye kısayolu Değiştir **seçenekleri** iletişim kutusu. Birkaç düzine komutlar için varsayılan klavye kısayolları da arayabilirsiniz [sık kullanılan komutlar için klavye kısayolları varsayılan](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md), tüm varsayılan kısayolların eksiksiz bir listesini bulabilirsiniz (temel **genel Geliştirme Ayarları**) içinde [varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Bir komuta Genel bağlamda kısayol atanmış ve diğer bağlamlarda atanmamışsa, ilgili kısayol her zaman bu komutu çağırır. Ancak bir kısayol, Genel bağlamda bir komuta ve özel bağlamda farklı bir komuta atanabilir. Böyle bir komutu özel bağlamda kullanırsanız, özel bağlama ilişkin komutu çağırır (Genel bağlama ilişkin komutu çağırmaz).

> [!NOTE]
> Ayarlarınıza ve Visual Studio sürümünüze göre, menü komutlarının adları ve konumları ve iletişim kutularında görünen seçenekler değişik olabilir. Bu konuda dayanır **genel geliştirme ayarları**.

## <a name="identify-a-keyboard-shortcut"></a>Klavye kısayolu tanımlama

1. Menü çubuğunda, **Araçları** > **seçenekleri**.

2. Genişletin **ortam**ve ardından **klavye**.

   ![Seçenekler iletişim kutusundaki görüntüleme klavye kısayolları](../ide/media/optionskeyboard.png)

3. İçinde **içeren komutları göster** kutusuna, boşluk olmadan komutun adını bir kısmını veya tamamını girin.

   Örneğin, için komutları bulabilirsiniz `solutionexplorer`.

4. Listede doğru komutu seçin.

    Örneğin, seçebileceğiniz `View.SolutionExplorer`.

5. Komutun bir klavye kısayolu varsa görünür **seçili komut için kısayollar** listesi.

   ![Belirtilen komut için bir kısayol görüntüleyin](../ide/media/viewshortcut.png)

## <a name="customize-a-keyboard-shortcut"></a>Klavye kısayolunu özelleştirme

1. Menü çubuğunda, **Araçları** > **seçenekleri**.

2. Genişletin **ortam** klasörünü ve ardından **klavye**.

3. İsteğe bağlı: adı, boşluk olmadan komut bir kısmını veya tamamını girerek komutların listesini filtrelemek **içeren komutları göster** kutusu.

4. Listede, klavye kısayolu atamak istediğiniz komutu seçin.

    İçinde **kullanım yeni kısayolu şunun içinde** listesinde, kısayolu kullanmak istediğiniz özellik alanını seçin.

    Örneğin, seçebileceğiniz **genel** kısayolun her bağlamda çalışmasını istiyorsanız. Başka bir düzenleyicide Genel olarak eşlenmemiş herhangi bir kısayolu kullanabilirsiniz. Aksi takdirde düzenleyici kısayolu geçersiz kılar.

    > [!NOTE]
    > Bir klavye kısayolunu parçası olarak şu tuşları atayamazsınız **genel**: yazdırma ekran/Sys Rq, kaydırma Lock, Pause/Break, sekme, Caps Lock, INSERT, Home, End, Page Up, Page Down, Windows logosu tuşu, uygulama anahtarı, herhangi bir ok anahtarları veya Enter; Num Lock, Delete veya sayısal tuş takımındaki; temizleyin Ctrl + Alt + Delete tuş bileşimi.

6. İçinde **kısayol tuşlarına basın** kutusunda, kullanmak istediğiniz kısayolu girin.

    > [!NOTE]
    > Bir harf ile birleştiren bir kısayol oluşturabilirsiniz **Alt** anahtar **Ctrl** tuşu veya her ikisi de. Birleştiren bir kısayol da oluşturabilirsiniz **Shift** anahtarı ve bir harf ile **Alt** anahtar **Ctrl** tuşu veya her ikisi de.

     Bir kısayol zaten başka bir komuta atanmışsa görünür **şu anda kullandığı kısayolunu** kutusu. Bu durumda, seçin **geri** başka bir denemeden önce kısayolu silmek için anahtar.

    ![Bir komut için farklı bir kısayol belirtin](../ide/media/reassignshortcut.png)

7. Seçin **atama** düğmesi.

    > [!NOTE]
    > Bir komut için farklı bir kısayol belirtirseniz **atama** düğmesine ve ardından **iptal** düğmesi, iletişim kutusu kapanır, ancak değişiklik geri alınır.

## <a name="share-custom-keyboard-shortcuts"></a>Özel klavye kısayollarını paylaşma

Özel klavye kısayollarınızı bir dosyaya dışarı aktararak ve verileri içeri aktarabilmeleri için bu dosyayı başkalarına vererek, klavye kısayollarınızı paylaşabilirsiniz.

### <a name="to-export-only-keyboard-shortcuts"></a>Yalnızca klavye kısayollarını dışarı aktarmak için

1. Menü çubuğunda, **Araçları** > **içeri ve dışarı aktarma ayarları**.

2. Seçin **seçili ortam ayarlarını dışarı aktar**ve ardından **sonraki** düğmesi.

3. Altında **hangi ayarları dışarı aktarmak istiyor musunuz?** temizleyin **tüm ayarlar** onay kutusunu işaretleyin, genişletme **seçenekleri**ve ardından **ortam**.

4. Seçin **klavye** onay kutusunu işaretleyin ve ardından **sonraki** düğmesi.

    ![Yalnızca özel klavye kısayollarını dışarı aktarma](../ide/media/exportshortcuts.png)

5. İçinde **ne ayarlar dosyanızı adlandırın istiyor musunuz?** ve **ayarlarımı bu dizinde Store** kutularında ya da varsayılan değerleri bırakın veya farklı değerler belirtin ve ardından  **Son** düğmesi.

    Varsayılan olarak, kısayollarınızı bir dosyaya kaydedilir *%USERPROFILE%\Documents\Visual Studio 2017\Settings* klasör. Dosyanın adı ayarları dışarı aktardığınız ve uzantı tarihi yansıtır *.vssettings*.

### <a name="to-import-only-keyboard-shortcuts"></a>Yalnızca klavye kısayollarını içeri aktarmak için

1. Menü çubuğunda, **Araçları** > **içeri ve dışarı aktarma ayarları**.

2. Seçin **seçili ortam ayarlarını içeri aktarma** seçenek düğmesini ve ardından **sonraki** düğmesi.

3. Seçin **Hayır, sadece yeni ayarları, geçerli ayarlarımı alma** seçenek düğmesini ve ardından **sonraki** düğmesi.

4. Altında **ayarlarım**, içeri aktarma veya seçmek istediğiniz kısayolları içeren dosyayı seçin **Gözat** doğru dosyayı bulmak için düğme.

5. Seçin **sonraki** düğmesi.

6.  Altında **hangi ayarları içeri aktarmak istiyor musunuz?** temizleyin **tüm ayarlar** onay kutusunu işaretleyin, genişletme **seçenekleri**ve ardından **ortam**.

7. Seçin **klavye** onay kutusunu işaretleyin ve ardından **son** düğmesi.

    ![Yalnızca özel klavye kısayollarını içeri aktarma](../ide/media/importshortcuts.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'nun erişilebilirlik özellikleri](../ide/reference/accessibility-features-of-visual-studio.md)