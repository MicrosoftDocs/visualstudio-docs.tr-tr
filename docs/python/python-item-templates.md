---
title: Python projeleri için öğe şablonları
description: Başvuru listesini Ekle kullanılabilir olan Python proje öğesi şablonları > Visual Studio'da yeni öğe iletişim kutusu.
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5fc08a190dfe146002dc4180f8c9a1fb680a5fb9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065794"
---
# <a name="python-item-templates"></a>Python öğe şablonları

Öğe şablonları Python projelerinde kullanılabilir **proje** > **Yeni Öğe Ekle** menü komutu veya **Ekle**  >  **Yeni öğe** bağlam menüsü komutu **Çözüm Gezgini**.

![Yeni Öğe Ekle iletişim kutusu](media/project-item-templates.png)

Öğe için sağladığınız adı kullanarak, bir şablon genellikle bir veya daha fazla dosya ve klasör içindeki şu anda seçilen projede oluşturur (Bu klasöre seçer otomatik olarak bağlam menüsünü açmak için bir klasöre sağ tıklayarak). Öğe ekleme bunu içerir Visual Studio Proje ve öğe görünür **Çözüm Gezgini**.

Aşağıdaki tabloda, her öğe şablonu bir Python projesindeki etkisini kısaca açıklanır:

| Şablon | Hangi şablon oluşturur |
| --- | --- |
| **Boş Python dosyası** | Boş bir dosya ile *.py* uzantısı. |
| **Python sınıfı** | A *.py* tek bir boş Python sınıf tanımını içeren dosya. |
| **Python paketi** | İçeren bir klasörün bir  *\_ \_init\_\_.py* dosya. |
| **Test Jednotky Pythonu** | A *.py* tek birim testi dosyasını temel alarak `unittest` , çağrı birlikte iş çerçevesini `unittest.main()` dosyasında testleri çalıştırmak için. |
| **HTML sayfası** | Bir *.html* oluşan bir basit sayfa yapısı dosyasıyla bir `<head>` ve `<body>` öğesi. |
| **JavaScript** | Boş bir *.js* dosya. |
| **Stil sayfası** | A *.css* için boş bir stil içeren dosya `body`. |
| **Metin dosyası** | Boş bir *.txt* dosya. |
| **Django 1.9 uygulama**<br/>**Django 1.4 uygulama** | İçinde anlatıldığı gibi bir Django uygulaması çekirdek dosyalarını içeren uygulamanın adı taşıyan bir klasör [öğrenin Django Visual Studio'da, adım 2-2](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) Django 1.9 için. Django 1.4 için *geçişler* klasöründe *admin.py* dosyasını ve *apps.py* dosyası dahil değildir. |
| **Okno WPF v Ironpythonu** | İki yan yana dosyasından oluşan bir WPF penceresi: bir *.xaml* tanımlayan dosyası bir `<Window>` boş ile `<Grid>` öğesi ve ilişkili bir *.py* XAML kullanarak dosya yükleyen dosyası `wpf` kitaplığı. Genellikle, IronPython proje şablonlarından birini kullanarak oluşturulan bir proje içinde kullanılır. Bkz: [yönetme Python projeleri - proje şablonları](managing-python-projects-in-visual-studio.md#project-templates). |
| **Web rolü destek dosyaları** | A *bin* (seçilen klasördeki projesinde) bağımsız olarak proje kök klasöründe. Klasör varsayılan dağıtım betiğini içerir ve bir *web.config* Azure bulut hizmeti web rolleri için dosya. Şablon da içeren bir *readme.html* ayrıntılarını açıklayan dosya. |
| **Çalışan rolü destek dosyaları** | A *bin* (seçilen klasördeki projesinde) bağımsız olarak proje kök klasöründe. Klasörü ile birlikte varsayılan dağıtım veya başlatma betiği içeren bir *web.config* Azure bulut hizmeti çalışan rolleri için bir dosya. Şablon da içeren bir *readme.html* ayrıntılarını açıklayan dosya. |
| **Web.config Pro Azure (Fastcgı)** | A *web.config* dosyasının kullanarak uygulamalar için girdiler içeren bir [WSGI](https://wsgi.readthedocs.io/en/latest/) gelen bağlantıları işlemek için nesne. Bu dosya, IIS çalıştıran web sunucusunun köküne genellikle dağıtılır. Daha fazla bilgi için [bir uygulama IIS'yi](configure-web-apps-for-iis-windows.md). |
| **Web.config Pro Azure (HttpPlatformHandler)** | A *web.config* bir yuvada gelen bağlantıları için dinlemek uygulamaları girişlerini içeren dosya. Bu dosya, genellikle Azure App Service gibi bir IIS web sunucusunda kök dağıtılır. Daha fazla bilgi için [bir uygulama IIS'yi](configure-web-apps-for-iis-windows.md). |
| **Azure statik dosyaları web.config** | A *web.config* tipik olarak eklenen dosya bir *statik* bu klasör için işleme Python devre dışı bırakmak için klasöründen (veya diğer klasör içeren statik öğeleri). Bu yapılandırma dosyası yukarıdaki Fastcgı veya HttpPlatformHandler yapılandırma dosyalarından biri ile birlikte çalışır. Daha fazla bilgi için [bir uygulama IIS'yi](configure-web-apps-for-iis-windows.md). |
| **Azure uzaktan hata ayıklama web.config** | Kullanım (uzaktan üzerinde Azure App Service'te artık desteklenmeyen Windows için hata ayıklama için kullanılan). |

## <a name="see-also"></a>Ayrıca bkz.

- [Python projeleri - proje şablonlarını yönetme](managing-python-projects-in-visual-studio.md#project-templates)
- [Python web projesi şablonları](python-web-application-project-templates.md)
- [Azure App Service’e yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md)
