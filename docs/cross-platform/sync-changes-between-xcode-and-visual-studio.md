---
title: XCode ve Visual Studio arasındaki eşitleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c71a4d7c-120e-4559-a114-3a99c4b860a9
ms.technology: vs-ide-mobile
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xamarin
ms.openlocfilehash: a32d72869a14e22ba8707036cd4b549ef5228d3b
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39379308"
---
# <a name="sync-changes-between-xcode-and-visual-studio"></a>XCode ve Visual Studio arasındaki eşitleme değişiklikleri
Microsoft Visual C++ mobil geliştirme bileşeni için PC ve Mac arasındaki iş eşitlenmesi uzak yetenekleri içerir Visual Studio ve Mac makinelerinizin birlikte kullanıldığında, iOS projenizi XCode içinde açmak için kullanabileceğiniz Visual Studio'da Uygulama projeleri için yeni seçenekler kullanılabilir kodunuzu XCode ile Visual Studio arasında taşıma ve geçici XCode proje dizinini Temizle.

 Uzak makine seçenekleri kullanmak için projenizin bir iOS uygulaması projesinin olmalıdır ve Visual Studio Mac ile eşleştirilmek Önkoşullar ve Mac ile eşleştirme hakkında yönergeler için bkz [yükleme ve yapılandırma araçları kullanarak iOS derleme](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="the-remote-machine-menu"></a>Uzak makine menüsü
 İçinde **Çözüm Gezgini**, bağlam menüsünü görüntülemek için bir iOS uygulaması projesine sağ tıklayın. Seçin **uzak makine** uzak seçeneklerini göstermek için öğesi.

 ![Çözüm Gezgini'nde uzak makine menü öğesi](../cross-platform/media/cppmdd_u2_remotemachine_menu.jpg "CPPMDD_U2_RemoteMachine_Menu")

 Bu komutlar, projenizi, Xcode'da açın yerel değişiklikleri veya projenin bütünü Visual Studio ile XCode arasında taşıma ve geçici dosyalar uzak makinede temiz olanak tanır.

### <a name="open-in-xcode"></a>Xcode'da Aç
 Visual Studio, XCode projesinde açmak için **uzak makine** alt seçin **Xcode'da açın** eşleştirilmiş uzak makinede Seçili projeyi açmak için. Vcremote sunucunun, Mac'te XCode açmak ve projenin bir kopyasını içeren, Mac'te oluşturulan geçici bir dizine gitmek için kullanılır. Visual Studio projesi için kullanılan geçici dizini gösteren bir iletişim kutusu görüntüler. Uzak makinede gerçekleştirilen eylemleri de gösterilir **çıkış** Visual Studio'daki. Bunları görmek için seçmeniz gerekebilir **Visual C++ uzak makine** içinde **çıktıyı Göster** en üstündeki açılan **çıkış** penceresi.

 ![Çıkış penceresi, uzak makine eylemleri gösterir. ](../cross-platform/media/cppmdd_u2_remotemachine_output.png "CPPMDD_U2_RemoteMachine_Output")

 Mac'inizde, kod ve kaynakları, film şeritleri ve eylemleri düzenlemek için XCode araçları kullanabilirsiniz. Visual Studio'da iOS uygulaması projenizin "Açılan içindeki değişiklikleri uzak makinede yapılabilir göstermek için XCode ile" açıklanıyor. Düzenlemeleriniz tamamlandıktan sonra uzak konumdan çekme veya artımlı çekme uzak komutlarının değişiklikleri geri Visual Studio projenize kopyalamak için kullanabilirsiniz.

### <a name="push-to-remote-and-incremental-push-to-remote"></a>Uzak ve artımlı anında iletme uzaktan gönderin
 Visual Studio'da iOS uygulaması projeniz değişiklikler yaptıysanız anında iletme uzaktan ve uzak komutları için artımlı gönderin eşleştirilmiş uzak makineye değiştirilen proje dosyalarını taşımak için kullanılabilir. Uzak komut gönderme tüm proje dosyaları uzak makineye kopyalar. Artımlı anında uzaktan komut için yalnızca değiştirilen dosyalar uzak makineye kopyalar. Küçük değişiklikler ile büyük projeleri için artımlı komut süreyi ve bant genişliği kaydedebilirsiniz.

 Mac bilgisayarınızda, Visual Studio'daki proje dosyaları kopyalamak için **Çözüm Gezgini**, bağlam menüsünü açmak için iOS uygulama projesine sağ tıklayın. Seçin **uzak makine** ve seçmeniz **uzak konuma itme** veya **uzaktan için artımlı gönderin** Mac için Visual Studio'dan proje dosyalarını kopyalamak

### <a name="pull-from-remote-and-incremental-pull-from-remote"></a>Uzak konumdan artımlı ve uzakta çekme isteneceğini
 Xcode'da projenize herhangi bir değişiklik yaptıktan sonra değişiklikleri geri projeleri eşitlenmiş şekilde tutmanızı sağlayacak Visual Studio'ya taşıyın.

 Mac bilgisayarınızda, Visual Studio'daki proje dosyaları kopyalamak için **Çözüm Gezgini**, bağlam menüsünü açmak için iOS uygulama projesine sağ tıklayın. Seçin **uzak makine** ve seçmeniz **çekme uzaktan** veya **uzak konumdan artımlı çekme** proje dosyaları, Mac için Visual Studio kopyalamak için.

### <a name="clean-remote"></a>Uzak öğeyi Temizle
 Uzaktan temizleme komutu, uzak makinedeki geçici proje dizininde bulunan dosyaları silmek için kullanabilirsiniz. Herhangi bir kaynak dosyaları veya derleme ürünler dahil olmak üzere, dizinin içeriklerini Mac'inizde kaldırılır Geri çekme uzaktan veya artımlı çekme uzaktan kullanarak uzaktan temizleme komutu kullanmadan önce Visual Studio için tutmak istediğiniz herhangi bir değişiklik eşitlendiğinden emin olun.

 Uzak makinede Visual Studio'da geçici proje dizini temizlemek için **Çözüm Gezgini**, bağlam menüsünü açmak için iOS uygulama projesine sağ tıklayın. Seçin **uzak makine** ve **temiz uzak** Mac'inizdeki proje dizini dosyaların kaldırmak için