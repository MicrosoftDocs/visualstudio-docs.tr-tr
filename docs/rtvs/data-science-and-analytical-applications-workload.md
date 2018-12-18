---
title: Veri bilimi ve analitik uygulamalar iş yükü
description: 'Visual Studio Thsi iş yükü Python, R, F # ve onların ilgili çalışma zamanı dağıtımları Anaconda dahil olmak üzere bir araya getirir.'
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 3d9815c72a500f9edd3b01f76dae3411ac0ee50f
ms.sourcegitcommit: 4c60bcfa2281bcc1a28def6a8e02433d2c905be6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42624294"
---
# <a name="install-data-science-support-in-visual-studio"></a>Visual Studio'da veri bilimi desteğini yükleme

Seçin ve Visual Studio yükleyicisi yüklemek, veri bilimi ve analitik uygulamalar iş yükü, üç diller ve onların ilgili çalışma zamanı dağıtımları bir araya getirir:

- [R ve Microsoft R istemcisi](../rtvs/index.md)
- [Python ve Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [F # .NET framework ile](/dotnet/fsharp/)

![Visual Studio Yükleyicisi'nde veri bilimi ve analitik uygulamalar iş yükü](media/data-science-workload.png)

R ve Python için veri bilimi kullanılan birincil komut dosyası dilleri ikisidir. Her iki dil öğrenmek kolaydır ve paketlerin zengin bir ekosisteme tarafından desteklenir. Bu paketleri, çok çeşitli veri alma, temizleme, model eğitiminin, dağıtım ve çizim gibi senaryolar adresi. F # Ayrıca, çok çeşitli veri işleme görevleri için uygun bir güçlü işlevsellik öncelikli .NET dilidir.

<!--Note link on the image because this one is large -->
[![R, Python ve F # ile Visual Studio'nun ekran görüntüleri](media/data-science-workload-screens.png)](media/data-science-workload-screens.png#lightbox)

## <a name="workload-options"></a>İş yükü seçenekleri

Varsayılan olarak, iş yükünü Visual Studio Yükleyicisi'nde iş yükü için Özet bölümünde değiştirebilirsiniz aşağıdaki seçenekleri yükler:

- F # dil desteği
- Python:
  - Python dil desteği
  - [Anaconda3 64 bit](https://www.continuum.io) (kapsamlı veri bilimi kitaplıkları ile bir Python yorumlayıcısı içerir bir Python distro)
  - Python web desteği
  - Cookiecutter şablonu desteği
- R:
  - R dil desteği
  - R geliştirme araçları için çalışma zamanı desteği
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (Microsoft'un tam olarak uyumlu, topluluk tarafından desteklenen İnterpret R ile daha hızlı hesaplama tek düğümler ve kümeler üzerindeki ScaleR kitaplıklarında. Öğesinden herhangi bir R kullanabilirsiniz [CRAN](https://cran.r-project.org/).)

F # diğer iş yükleri bir dizi dahil edilmiştir ve Python iş yükü kendi sahip, veri bilimi ve analitik uygulamalar, ancak yalnızca iş yükü şu anda r içerir Ancak, iş yükü bağımsız R yükleyebilirsiniz. Üzerinde **tek tek bileşenler** sekmesinde Yükleyicisi'nde, aşağıdaki R seçeneklerini belirtin:

- **Geliştirme etkinlikleri** > **R dil desteği**
- **Geliştirme etkinlikleri** > **Microsoft R Client**
- **Derleyiciler, derleme araçları ve çalışma zamanları** > **R geliştirme araçları için çalışma zamanı desteği**

## <a name="sql-server-integration"></a>SQL Server tümleştirmesi

Hem R hem de Python'un doğrudan SQL Server içinde Gelişmiş analiz yapmak için SQL Server kullanılmasını destekler. R desteği, SQL Server 2016 ve sonraki sürümlerinde; Python desteği, SQL Server 2017 CTP 2.0 kullanılabilir ve üzerinde desteklenir.

Aşağıdaki avantajları, verileriniz zaten nerede kodunuzu çalıştırarak keyfini çıkarın:

- **Veri taşıma saydamlığından**: verileri veritabanından uygulamanızı veya model için taşıma yerine, R ve Python uygulamaları veritabanında oluşturabilirsiniz. Bu özellik, güvenlik, uyumluluk, idare, bütünlük ve çok büyük miktarda veri moving'e ilgili benzer sorunları çok sayıda engelleri ortadan kaldırır. Bir istemci makinesi belleğe sığması uygulanamadı veri kümeleri de kullanabilir.

- **Kolay dağıtım**: bilgisayarınızda bir R veya Python modeli hazır sonra bir T-SQL komut dosyası ekleme ibarettir Üretim dağıtımı gelir. Herhangi bir SQL istemci uygulama herhangi bir dilde yazılmış bir saklı yordam çağrısı aracılığıyla zeka ve modelleri yararlanabilirsiniz. Belirli bir R veya Python tümleştirmeler gereklidir.

- **Kurumsal düzeyde performans ve ölçek**: bellek içi tablo ve sütun dizinleri yüksek performanslı ölçeklenebilir API'leri ile RevoScaleR ve RevoScalePy paketleri depolamak gibi SQL Server'ın gelişmiş özelliklerini kullanabilirsiniz. Veri taşıma saydamlığından çoğalan veya uygulamanın performansını artırmak istediğiniz istemci bellek kısıtlamaları kaçının anlamına gelir.

- **Zengin genişletilebilirlik**: yükleme ve herhangi bir en son open source R veya Python paketleri SQL Server'ın çok büyük miktarda verileri SQL Server üzerinde derin öğrenme ve yapay ZEKA uygulamaları oluşturmak için çalıştırın. SQL Server'da bir paket yükleme, yerel makinenizde bir paket yüklemek kadar basittir.

- **Hiçbir ek ücret ödemeden geniş kullanılabilirlik**: R ve Python tümleştirmeler SQL Server 2017 ve sonraki tüm sürümlerinde kullanılabilir Express edition dahil. (R desteği, kullanılabilir SQL Server 2016 ve üzeri içindir.)

SQL Server Tümleştirme tam olarak yararlanmak için Visual Studio yükleyicisini kullanma **veri depolama ve işleme** yüküyle **SQL Server veri Araçları** seçeneği. İkinci seçeneği, SQL IntelliSense, sözdizimi vurgulama ve dağıtımını sağlar.

![Veri depolama ve işleme iş yükü](media/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Veri depolama ve işleme iş yükü seçenekleri](media/data-storage-workload-options.png)

Daha fazla bilgi için:

- [SQL Server ve R ile çalışma](integrating-sql-server-with-r.md)
- [Veritabanı SQL Server 2016 (blog) R ile Gelişmiş analiz](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
- [SQL Server 2017 Python: Gelişmiş veritabanında machine learning (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>Ek hizmetler ve SDK'lar

Veri bilimi ve analitik uygulamalar iş yükü doğrudan nedir ek olarak, Azure not defterleri hizmet ve Python için Azure SDK'sı ayrıca veri bilimi için yararlıdır.

Python için Azure SDK'sını kullanma ve uygulamaları Windows, Mac ve Linux üzerinde çalışan Microsoft Azure hizmetlerini yönetmenize daha kolay hale getirir. Daha fazla bilgi için [Python için Azure SDK'sı](../python/azure-sdk-for-python.md)

Azure Not Defterleri (şu anda önizlemede), Jupyter not defterleri bulutta Microsoft Azure üzerinde çalışan ücretsiz çevrimiçi erişim sağlar. Hizmet, Python, R ve F # başlamanıza yardımcı olmak için örnek not defterlerini içerir. Ziyaret[notebooks.azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Ekran görüntüleri, Azure not defterleri ile R örnek giriş](media/data-science-workload-notebooks.png)](media/data-science-workload-notebooks.png#lightbox)
