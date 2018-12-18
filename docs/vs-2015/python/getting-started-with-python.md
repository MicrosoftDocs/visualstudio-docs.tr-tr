---
title: Python ile çalışmaya başlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 5cb04bb01aaa6eb06c5e3c50aa13ab51c136678c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49275294"
---
# <a name="getting-started-with-python"></a>Python’ı Kullanmaya Başlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Python araçları için Visual Studio (PTVS), ücretsiz olduğundan, [açık kaynaklı](https://github.com/Microsoft/ptvs) güçlü bir Python geliştirme deneyimi yaşayın Visual Studio için eklenti.  
  
## <a name="python-the-language"></a>Python dil
  
Python birçok üniversiteler, uzmanları, uygulama çalıştırıcılara, sıradan geliştiriciler ve profesyonel geliştiriciler, uygulamaları, web siteleri ve bulut hizmetleri üzerinde çalışan tarafından kullanılan popüler bir programlama dilidir.

Python programlama dili olarak verilmiştir:
  
- Güvenilir.
- Genellikle, hızlı programlar betik, app komut dosyası, Masaüstü uygulamaları, web sunucuları, web hizmetleri ve bilimsel bilgi işleme için de kullanışlıdır.
- Öğrenmesi kolay ve (birçok üniversiteler kullanın, tanıtım programlama kursları) iyi kodlamayı teşvik etmek için iyi bir tasarım sahiptir.
- Esnek, kesinlik temelli, işlevsel ve nesne yönelimli programlama stilleri destekleme.
- Ücretsiz ve açık kaynak.
- Tüm önemli işletim sistemleri de çalışır.  
- Çok sayıda ücretsiz, kullanışlı ve iyi tasarlanmış kitaplıkları tarafından desteklenmiyor.  
- Belgeler, örnekler ve güçlü Geliştirici topluluğu çok sayıda tarafından desteklenmiyor.  

Dili hakkında daha fazla bilgi edinmek için başlayın [yeni başlayanlar için Python](https://www.python.org/about/gettingstarted/) python.org üzerinde.

Python kendisini yüklemek için ziyaret [ https://www.python.org/download/ ](https://www.python.org/download/).
 
  
## <a name="python-tools-for-visual-studio"></a>Visual Studio için Python Araçları
  
Yükleyebilmek için Visual Studio için Python Tools [visualstudio.com](https://www.visualstudio.com/en-us/explore/python-vs), aşağıdaki özellikleri sağlar:  
  
- Birden çok yorumlayıcılarını desteği: çeşitli sürümlerini CPython, IronPython ve IPython  
- Python kodu bir klasör yapısı örtük olarak seçer ve uygulama kodu, test kodu, web sayfaları, JavaScript, derleme betikleri ve VS. belirleyebilmeniz açık denetim de izin veren bir proje sistemi.  
- Konsol, web, Azure, veri bilimi ve diğer proje türleri için proje şablonları.    
- Python (aşağıya bakın) için Azure SDK'sı    
- Sözdizimi renklendirme, otomatik tamamlama, kodunuzu ve kitaplıkları, imza Yardımı, sınıf görünümü, yeniden düzenleme tanımı, tüm başvuruları Bul, Git ve daha fazla arasında gibi zengin düzenleme ve kod kavrama özellikleri.    
- Etkileşimli (REPL) penceresi
- Ipython ile veri görselleştirmeleri.
- IronPython ve .NET/WPF desteği.    
- Zengin hata ayıklama Visual Studio projesi, bir var olan yürütülebilir, karma mod hata ayıklama, uzaktan Linux/Windows/Mac için hata ayıklama ve etkileşimli pencereye hata ayıklama olanağı.   
- Profil oluşturma Araçları'nı tıklatın.  
- Test Araçları.  
  
Aşağıdaki kaynaklar, başlamanıza yardımcı olur:

- [Yükleme kılavuzu](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)    
- [Başlatılan ve kapsamlı kısa videolar alma](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)  
- Yükleme ve özellikleri Tanıtımı (27 dk.)])https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Belgeler](https://github.com/Microsoft/PTVS/wiki)  


Visual Studio şu anda temelde katıştırılmış bir Python yorumlayıcısı programla anlamına gelir ve Python kullanarak tek başına yürütülebilir dosya oluşturmak için Araçlar sağlamaz unutmayın. Ancak Python topluluk içinde çeşitli araç üzerinde açıklandığı şekilde bunun için vardır [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython da destekler yerel bir uygulama içinde gömülen blog gönderisi konusunda açıklandığı gibi [gömülebilir ZIP dosyasını kullanarak CPython'ın](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/).
  
## <a name="building-ui-with-python"></a>Python ile kullanıcı arabirimini oluşturma  

Python ile bir kullanıcı Arabirimi oluşturmak için ana sunan [Qt proje](https://www.qt.io/qt-for-application-development/), bilinen Python için bağlamaları ile [PySide (resmi bağlama)](http://wiki.qt.io/PySide) (Ayrıca bkz: [PySide indirir](https://download.qt.io/official_releases/pyside/.)) ve [PyQt](https://wiki.python.org/moin/PyQt). Şu anda, herhangi belirli kullanıcı Arabirimi geliştirme araçları Visual Studio'da Python desteği içermez.

## <a name="azure-sdk-for-python"></a>Python için Azure SDK
  
Destekleyen Windows, Mac ve Linux, Python için Azure SDK'sını kullanmak ve Microsoft Azure hizmetlerini yönetmek kolay hale getirir. Ayrıntılar için aşağıdaki kaynaklara bakın: 

- SDK yüklemek için kullanın [Python paket dizinini](https://pypi.python.org/pypi/azure) veya takip [yüklemeniz Python ve SDK'sı](https://azure.microsoft.com/documentation/articles/python-how-to-install/) Azure belgeleri. 
- [Python Geliştirici Merkezi için Azure SDK'sı](https://azure.microsoft.com/develop/python/) yüklemesinden Yardım belgelerine öğreticiler ile çok sayıda sahiptir.  Bazı önemli noktalar izleyin:  
- Nasıl yapılır kılavuzları:
  - [Depolama blobu](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [Depolama kuyruğu](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [Depolama tablosu](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Service Bus kuyrukları](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [Hizmet veri yolu konuları/abonelikleri](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [Hizmet Yönetimi](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>Bilimsel bilgi işleme

Tüm Python veri Bilimcisi kitaplıklarına ek olarak, Visual Studio için Python araçları, Ipython ve Ipython not defterleri Azure'da barındırılan destekler.

Ipython ve bilimsel hesaplama kitaplıkları (matplotlib, scipy, numpy, vb.) almakla öneririz [California Üniversitesi, Irvine](http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack).  
  
## <a name="see-also"></a>Ayrıca Bkz.  

[PTVS kullanmaya Başlarken: Visual Studio'yu ayarlama](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[PTVS ile çalışmaya başlama: Başlat (Projeler) kodlama](../python/getting-started-with-ptvs-start-coding-projects.md)
[PTVS ile çalışmaya başlama: kod düzenleme](../python/getting-started-with-ptvs-editing-code.md) 
 [PTVS kullanmaya Başlarken: hata ayıklama](../python/getting-started-with-ptvs-debugging.md)
[PTVS kullanmaya Başlarken: etkileşimli Python](../python/getting-started-with-ptvs-interactive-python.md)
[alma PTVS kullanmaya başladı: azure'da bir Web sitesi oluşturma](../python/getting-started-with-ptvs-building-a-website-in-azure.md)

