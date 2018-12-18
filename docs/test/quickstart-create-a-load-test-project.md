---
title: Web performansı ve yük testi projesi oluşturma
ms.date: 03/14/2018
ms.topic: quickstart
helpviewer_keywords:
- load testing, quickstart
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 30e67768b502228ba8cba5acd813ec829624a822
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057580"
---
# <a name="quickstart-create-a-load-test-project"></a>Hızlı Başlangıç: Yük testi projesi oluşturma

10 dakikalık bu hızlı başlangıçta, oluşturma ve bir web performansı ve yük testi projesi Visual Studio'da çalıştırma öğreneceksiniz. Yük testleri, web performans veya bir sunucu aynı anda erişen birçok kullanıcının benzetimini yapmak için birim testleri yürütün.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="software-requirements"></a>Yazılım gereksinimleri

Yalnızca Web performans ve yük testi projelerini Visual Studio Enterprise sürümünde kullanılabilir.

## <a name="install-the-load-testing-component"></a>Yük testi bileşeni yükle

Yoksa zaten web performansı ve yük testi araçları bileşeninin yüklü ise, Visual Studio yükleyicisi yüklemeniz gerekir.

1. Açık **Visual Studio yükleyicisi** gelen **Başlat** Windows menüsü. Ayrıca, Visual Studio'dan erişebildiğinizi **yeni proje** iletişim kutusu, seçerek veya **Araçları** > **araçları ve özellikleri Al** menü çubuğundan.

1. İçinde **Visual Studio yükleyicisi**, seçin **tek tek bileşenler** sekmesini ve ekranı aşağı kaydırarak **hata ayıklama ve test** bölümü. Seçin **Web performansı ve yük testi Araçları**.

   ![Web performansı ve yük testi araçları bileşeni](media/web-perf-load-testing-tools-component.png)

1. Seçin **Değiştir** düğmesi.

   Web performansı ve yük testi araçları bileşeni yüklenir.

## <a name="create-a-load-test-project"></a>Bir yük testi projesi oluşturma

Bu bölümde, bir C# yük testi projesi oluşturacağız. Tercih ederseniz, Visual Basic yük testi projesi oluşturabilirsiniz.

1. Visual Studio'yu açın ve seçin **dosya** > **yeni** > **proje** menü çubuğundan.

   **Yeni proje** iletişim kutusu açılır.

1. İçinde **yeni proje** iletişim kutusunda **yüklü** ve **Visual C#** ve ardından **Test** kategorisi. Seçin **Web performansı ve yük testi projesi** şablonu.

   ![Web performansı ve yük testi projesi şablonu](media/web-perf-load-test-project-template.png)

1. Varsayılan adı kullanın ve ardından istemiyorsanız, proje için bir ad girin **Tamam**.

   Visual Studio projeyi oluşturup dosyaları görüntüler **Çözüm Gezgini**. Projeyi başlangıçta adlı bir web testi dosyası içeren *WebTest1.webtest*.

## <a name="add-a-load-test-to-the-project"></a>Bir yük testi projeye Ekle

1. Sağ tıklama menüsünden veya proje düğümünün kısayol menüsünü **Çözüm Gezgini**, seçin **Ekle** > **yük testi**.

   **Yeni Yük Testi Sihirbazı** açılır.

1. Seçin **şirket içi yük testi** seçeneğini ve ardından **sonraki**. Bulut tabanlı yük testi hakkında daha fazla bilgi [burada](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts).

   ![Yeni Yük Testi Sihirbazı - ilk sayfa](media/load-test-wizard-page-1.png)

1. Seçin **sonraki** adımına ulaşana kadar sihirbazı takip **bir yük testi senaryosuna testleri ekleme ve test karışımını düzenleme** sayfası. Seçin **Ekle** düğmesi.

   **Test Ekle** iletişim kutusu açılır.

1. Altında **kullanılabilir testler**seçin **WebTest1'i**seçip için taşıyabiliyor için sağ ok **Seçili testler** kutusu. Seçin **Tamam** düğmesi.

   ![Testleri iletişim kutusu Ekle](media/add-tests-dialog-box.png)

1. Geri **Yeni Yük Testi Sihirbazı**, seçin **son** düğmesi.

   Yük testi projenize eklenir ve yük testi dosyası düzenleyici penceresinde açılır.

## <a name="run-the-load-test"></a>Yük testi çalıştırma

Çok fazla yapmak değil ancak çalıştıralım, yine de bir yük testi oluşturduk.

Sağ tıklama menüsünü ya da Yük Testi Düzenleyicisi'nde açık olan bağlam menüsünden seçin **yük testi Çalıştır**.

![Yük testi menüsünden çalıştırın](media/run-load-test.png)

Yük testi çalışmaya başlar. **Test sonuçları** test ediyor ve Yük Testi Çözümleyicisi düzenleyici penceresinde görüntülenen pencerede gösterilir. Varsayılanları kabul beş dakika olmalıdır, test, tamamlandıktan sonra düzenleyicide bir özeti gösterilir. Seçebileceğiniz **grafikleri**, **tabloları**, veya **ayrıntı** yük testi sonuçlarıyla ilgili farklı bilgi almak için.

![Yük Testi Çözümleyicisi penceresi](media/load-test-analyzer.png)

## <a name="next-steps"></a>Sonraki adımlar

Basit yük testi projesi oluşturduğunuza göre sıradaki adım senaryoları, sayaç kümeleri, yapılandırma ve çalıştırma ayarları olacak.

> [!div class="nextstepaction"]
> [Test Ayarlarını Düzenle](edit-load-tests.md)
