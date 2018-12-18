---
title: C++ ile çalışmaya başlama
description: ''
ms.custom: mvc
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
author: corob-msft
ms.author: corob
manager: douge
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: 406b3c24cf3c46b694afc8ab24c0ddca11b434ee
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53160003"
---
# <a name="get-started-with-c-in-visual-studio"></a>Visual Studio'da C++ kullanmaya başlama

Birçok Visual Studio ile C++ uygulamaları geliştirirken kullanabileceğiniz iletişim kutuları ve araçları sahibi bu hızlı başlangıcı tamamlayın. Bir "Hello, World" Oluştur-tümleşik geliştirme ortamında (IDE) çalışma hakkında daha fazla bilgi edinirken konsol uygulaması stili.

## <a name="prerequisites"></a>Önkoşullar

Bu hızlı başlangıcı tamamlamak için C++ ile ilgili bilgi sahibi olmanız gerekmez, ancak bazı genel programlama ve hata ayıklama kavramlarını bilmelisiniz. Visual Studio belgeleri c++'ta nasıl programlama yapılacağı öğretmek değildir. İyi bir kılavuzdur c++ öğrenme kaynakları [başlama](https://isocpp.org/get-started) ISO C++ sitesinde sayfasında.

Örneği takip etmek için bir kopyasını bir Visual Studio 2017 sürüm 15.3 veya üzeri ile ihtiyacınız **C++ ile masaüstü geliştirme** iş yükü yüklenmiş. Yükleme hızlı bir kılavuz için bkz: [Visual Studio'da C++ yükleme desteği](/cpp/build/vscpp-step-0-installation).

## <a name="create-a-console-app"></a>Bir konsol uygulaması oluşturma

Henüz çalışmıyorsa, Visual Studio'yu başlatın.

![Visual C ile IDE&#43; &#43; uygulanan ayarları](../ide/media/get-started-cpp-ide-layout.png)

Visual Studio'yu açtıktan sonra IDE üç temel bölümlerini görebilirsiniz: windows, menüler ve araç çubuklarını ve ana pencere alanını aracı. Araç pencereleri ve uygulama penceresinin sol tarafında sabitlenir. **Hızlı başlatma** standart araç kutusu ve menü çubuğu üstünde bulunur. Pencerenin ortasına içeren **başlangıç sayfası**. Bir çözüm veya projeyi açtığınızda, düzenleyiciler ve tasarımcılar Bu alanda görüntülenir. Uygulama geliştirirken zamanınızın çoğunu bu Orta alanda harcanır.

Visual Studio kullanan *projeleri* bir uygulama için kod düzenleme ve *çözümleri* projelerinizi düzenlemek için. Bir proje, tüm seçenekleri, yapılandırmaları ve uygulamalarınızı oluşturmak için kullanılan kuralları içerir. Tüm proje dosyaları ve dış dosyaları arasındaki ilişki da yönetir. Uygulamanızı oluşturmak için ilk olarak, yeni proje ve çözüm oluşturun.

### <a name="to-create-a-console-app-project"></a>Bir konsol uygulaması projesi oluşturmak için

1. Menü çubuğunda, **Dosya > Yeni > Proje** açmak için **yeni proje** iletişim kutusu.

   ![Menü çubuğunda, Dosya > Yeni > Proje](../ide/media/get-started-cpp-file-new-project-menu.png)

1. İçinde **yeni proje** iletişim kutusunda **yüklü > Visual C++** zaten seçili değilse. Orta bölmede seçin **Windows konsol uygulaması** şablonu. İçinde **adı** düzenleme kutusu, girin *HelloApp*.

   ![Yeni Proje iletişim uygulama projenizi oluşturmak için kullanın](../ide/media/get-started-cpp-new-project-dialog.png)

   İletişim kutusu bileşenleri yükledikten ve Visual Studio iş yüklerine bağlı olarak farklı bir seçenek olabilir. Visual Studio yükleyiciyi yeniden çalıştırın ve yüklemek gereken Visual C++ proje şablonları görmüyorsanız **C++ ile masaüstü geliştirme** iş yükü. Bunu doğrudan yapabilirsiniz **yeni proje** iletişim. Yükleyiciyi başlatın, tercih **açık Visual Studio yükleyicisi** iletişim kutusundaki bağlantı.

1. Seçin **Tamam** uygulama projesi ve çözümü oluşturmak için.

   HelloApp projeyi ve çözümü, bir Windows konsol uygulaması için temel dosyalar oluşturulur ve otomatik olarak yüklenen **Çözüm Gezgini**. *HelloApp.cpp* dosyası Kod Düzenleyicisi'nde açılır. Bu öğelerin görünür **Çözüm Gezgini**:

   ![Çözüm Gezgini'nde çözüm dosyaları](../ide/media/get-started-cpp-solution-explorer.png)

## <a name="add-code-to-the-app"></a>Kod uygulamaya ekleme

Ardından, word görüntülenecek kod konsol penceresinde "Hello" ekleyin.

### <a name="to-edit-code-in-the-editor"></a>Kod Düzenleyicisi'nde düzenlemek için

1. İçinde *HelloApp.cpp* dosya, satırından önce boş bir satıra girin `return 0;` ve sonra bu kodu girin:

   ```cpp
   cout << "Hello\n";
   ```

   Altında kırmızı dalgalı çizgi görünür `cout`. İşaretçi geldiğinizde, bir hata iletisi görüntülenir.

   ![Cout hata metni](../ide/media/get-started-cpp-intellisense-error.png)

   Hata iletisi ayrıca görünür **hata listesi** penceresi. Bu pencere seçerek görüntüleyebilirsiniz **Görüntüle > hata listesi** menü çubuğundaki.

   ![Hata Listesi penceresindeki hata](../ide/media/get-started-cpp-error-list.png)

   Kodunuz için bir bildirim eksik [std::cout](/cpp/standard-library/iostream), içinde bulunan  *\<iostream >* üst bilgi dosyası.

1. Eklenecek *iostream* üst bilgi, sonra bu kodu girin `#include "stdafx.h"`:

   ```cpp
   #include <iostream>
   using namespace std;
   ```

   Büyük olasılıkla kod girildiği gibi görünen bir kutu fark. Bu kutu otomatik tamamlama önerileri, girdiğiniz karakterleri için içerir. C++ IntelliSense, sınıf veya arabirim üyeleri ve parametre bilgileri de dahil olmak üzere kodlama istemleri sağlar gereksinimlerimizim bir parçasıdır. Önceden tanımlanmış kod bloklarını olan kod parçacıklarını da kullanabilirsiniz. Daha fazla bilgi için [IntelliSense kullanarak](../ide/using-intellisense.md) ve [kod parçacıkları](../ide/code-snippets.md).

   ![Sabit Kod Düzenleyicisi'nde](../ide/media/get-started-cpp-cout-fix.png)

   Altında kırmızı dalgalı çizgi `cout` hatayı düzeltmeniz kaybolur.

1. Değişiklikleri dosyaya kaydetmek için basın **Ctrl + S**.

## <a name="build-the-app"></a>Uygulama oluşturma

Kodunuzu derlemek kolay bir işlemdir. Menü çubuğunda, **Yapı > Çözümü Derle**. Visual Studio HelloApp çözümü oluşturur ve ilerleme raporları **çıkış** penceresi.

   ![HelloApp çözümü oluşturun](../ide/media/get-started-cpp-build-solution.gif)

## <a name="debug-and-test-the-app"></a>Hata ayıklama ve uygulamayı test etme

"Hello" sözcüğünü konsol penceresinde görünür olup olmadığını görmek için HelloApp ayıklayabilirsiniz.

### <a name="to-debug-the-app"></a>Uygulamanın hatalarını ayıklamak için

Hata ayıklayıcıyı başlatmak için **hata ayıklama > hata ayıklamayı Başlat** menü çubuğundaki.

![Hata ayıklama komutu hata ayıklama menüsünden başlayın.](../ide/media/get-started-cpp-start-debugging-menu.png)

Hata ayıklayıcıyı başlatır ve kodu çalıştırır. Konsol penceresi (bir komut istemi gibi görünüyor ayrı bir pencerede) için birkaç saniye görüntülenir ancak hata ayıklayıcı çalışmayı durdurduğunda hızla kapatır. Metin görmek için program yürütme durdurmak için bir kesme noktasını ayarlamanız gerekir.

### <a name="to-add-a-breakpoint"></a>Bir kesme noktası eklemek için

1. Düzenleyicide, imleç satıra `return 0;`. Menü çubuğunda, **hata ayıklama > iki durumlu kesme noktası**. Bir kesme noktası ayarlamak için sol kenar boşluğunda de tıklayabilirsiniz.

     ![Hata ayıklama menüsünden kesim noktasını Değiştir komutu](../ide/media/get-started-cpp-toggle-breakpoint-menu.png)

     Düzenleyici penceresinin en sol kenar boşluğunda, kod satırının yanında kırmızı bir daire görünür.

     ![Kesme noktası penceresinin kenar boşluğundaki gösterilir](../ide/media/get-started-cpp-breakpoint-set.png)

1. Hata ayıklamayı başlatmak için basın **F5**.

   Hata ayıklayıcıyı başlatır, word gösteren bir konsol penceresi görünür **Hello**.

   ![Konsol penceresinde Hello metin](../ide/media/get-started-cpp-helloapp-window.png)

1. Hata ayıklamayı durdurmak için basın **Shift + F5**.

Konsol projesi hata ayıklama hakkında daha fazla bilgi için bkz. [konsol projeleri](../debugger/debugging-preparation-console-projects.md).

## <a name="build-a-release-version-of-the-app"></a>Uygulama sürümü oluşturma

Her şeyin çalıştığını doğruladığınıza göre uygulamanın bir yayın derlemesini hazırlayabilirsiniz. Yayın bırakın daha küçük, daha hızlı kod oluşturmak için derleyici en iyi duruma getirme seçenekleri kullanın ve hata ayıklama bilgileri oluşturur.

### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Çözüm dosyalarını temizlemek ve yayın sürümünü oluşturmak için

1. Menü çubuğunda, **Yapı > çözümü Temizle** Ara dosyaları ve önceki derlemeler sırasında oluşturulan çıktı dosyalarını silmek için.

   ![Derle menüsünde çözümü Temizle komutu](../ide/media/get-started-cpp-clean-solution-menu.png)

1. HelloApp çözüm yapılandırmasını değiştirmek için **hata ayıklama** için **yayın**, araç çubuğunda, çözüm yapılandırmaları denetimi açılan menüyü seçin ve ardından **yayın**.

   ![Uygulamanın yayın sürümünü oluşturma](../ide/media/get-started-cpp-set-release-configuration.png)

1. Çözümü oluşturun. Menü çubuğunda, **Yapı > Çözümü Derle**.

Bu derleme tamamlandığında, kopyalama ve herhangi bir komut istemi penceresinde çalıştırın bir uygulama oluşturdunuz. Bu çok bunu yapabilirsiniz, ancak büyük şeyler için geçididir.

Bu hızlı başlangıcı tamamladığınızda Tebrikler!

## <a name="see-also"></a>Ayrıca bkz.

- [C++ Masaüstü geliştirmesi için Visual Studio IDE kullanma](/cpp/ide/using-the-visual-studio-ide-for-cpp-desktop-development)
- [İzlenecek yol: Basit bir uygulama oluşturacaksınız C# veya Visual Basic](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)
- [Visual Studio için üretkenlik ipuçları](../ide/productivity-tips-for-visual-studio.md)
