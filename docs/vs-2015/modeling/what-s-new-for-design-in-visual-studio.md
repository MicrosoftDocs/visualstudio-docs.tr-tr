---
title: Hangi&#39;tasarım için Yenilikler
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
ms.assetid: 36ab5c17-6dc0-4075-a28e-a0fa49b11260
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 666402a0488fdfd0e09e12e711c9b74b2f3b2fd1
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068120"
---
# <a name="whats-new-for-design-in-visual-studio"></a>Visual Studio tasarımındaki yenilikler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Visual Studio'nun bu sürümü daha iyi anlamanıza ve kod tasarlamanıza yardımcı olması için aşağıdaki geliştirmeleri içerir.

 **Kod haritaları ve bağımlılık grafikleri**

 Kodunuzdaki belirli bağımlılıkları anlamak istediğinizde, Visual Studio Enterprise kod haritaları oluşturarak bunları görselleştirin. Ardından, kodunuzun yanında görüntülenen haritayı kullanarak bu ilişkilere gidebilirsiniz. Kod haritaları de yardımcı olabilir, kod içindeki yerinizi çalışmak veya kodunuzun tasarımı hakkında daha fazla bilgi edinirken daha az kod okumanız için kodu, hata ayıklama sırasında izler.

 Son (RTM) sürümünde kod öğeleri ve bağlantılarına yönelik kısayol menülerini çok daha kolay seçme, düzenleme, grupları yönetme ve Grup içeriklerinin düzenini değiştirmek için ilgili bölümlere komutları gruplandırma tarafından kullanılacak yaptık. Ayrıca test projelerinin diğer projelerden farklı bir stilde görüntülendiğini ve haritadaki öğelere yönelik simgeleri daha uygun sürümlere güncelleştirdik, dikkat edin.

 ![Seçili öğeleri yeni bir kod haritasında Göster](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 Diğer iyileştirmeler şunlardır:

- **Gelişmiş yukarıdan aşağıya diyagramlar**. Orta ve büyük ölçekli Visual Studio çözümleri, daha kullanışlı bir kod eşlemeleri, çözümünüz için almak için artık basitleştirilmiş bir mimari menüsü kullanabilirsiniz. Böylece bunları bağlam içinde görebilir ve, çözümü yapılandırırken yaptığınız çalışmadan yararlanarak çözümünüzün derlemeleri çözüm klasörleri tarafından gruplanır. Proje ve bütünleştirilmiş kod başvuruları ve bağlantı türleri görüntülenir hemen görürsünüz. Ayrıca, çözümünüze dışında bulunan derlemeler daha kompakt şekilde gruplanır.

- **Test projeleri farklı stillere sahip olabilir ve filtrelenebilir**. Farklı stillere çünkü haritasında test projelerini daha kolay ve hızlı bir şekilde artık tanımlayabilirsiniz. Uygulamanın çalışma koduna odaklanabilmeniz için bunlar da filtrelenebilen.

- **Basitleştirilmiş dış bağımlılık bağlantıları**. Bağımlılık bağlantıları artık System.Object, System.ValueType, System.Enum ve kod haritanızda dış bağımlılıkların görmeyi kolaylaştırır ve System.Delegate öğesinden devralmayı temsil eder.

- **' Ayrıntıya-bağımlılık bağlantılarının ' işleminde filtreler dikkate**. Bağımlılık bağlantısına yapılan katkıları anlamak için genişletirken, kullanışlı bir NET diyagram alırsınız. Diyagram daha az dağınıktır ve bağlantı filtreleme seçeneklerini seçmiş olduğunuz hesaba katar ' dir.

- **Kod öğeleri, bağlamları ile birlikte bir kod haritasına eklenir**. Diyagramları artık bağlamları (gerektiğinde filtreleyebileceğiniz, derleme ve çözüm klasörüne kadar) ile birlikte sürükleyip kod öğelerini Çözüm Gezgini, sınıf görünümü, Nesne Tarayıcısı daha kullanışlı diyagramlar elde filtreleyebileceğiniz; veya, Çözüm Gezgini'nde öğeleri ve seçerek kod haritasında göster.

- **Reaktif kod haritalarını daha hızlı alma**. Sürükleyip bırakma işlemleri anında sonuç verir ve düğümler arasındaki bağlantılar, düğümü genişletme veya daha fazla düğüm isteme gibi sonraki kullanıcı tarafından başlatılan işlemleri etkilemeden çok daha hızlı bir şekilde oluşturulur. Tüm olağandışı durumlar çözümü oluşturmadan kod haritaları oluşturduğunuzda — zaman derlemeleri oluşturulmadı gibi — şimdi işlenir.

- **Çözümünüzü yeniden oluşturmayı atlama.** Diyagram oluştururken veya düzenlerken daha iyi performans sağlar.

- **Kod öğesi düğümlerini ve gruplarını filtreleme**. Hızlı bir şekilde, gösterme veya gizleme kod öğelerini kategorilerine veya kod öğelerini çözüm klasörleri, derlemeler, ad alanları, proje klasörleri ve türleri tarafından gruplandırma etsek düzelten.

- **Diyagramların okunmasını kolaylaştırmak için ilişkileri filtreleme**. Bağlantı filtrelemesi artık filtre penceresiyle çalışılmasını daha az sezgisel önceki sürümlere kıyasla getiren, çapraz grup bağlantıları için de geçerlidir.

- **Sınıf Görünümü ve Nesne Tarayıcısı'ndan diyagramlar oluşturma**. Sürükleyip dosyaları ve yeni veya mevcut bir haritayı derlemeleri sınıf görünümü ve Nesne Tarayıcısı windows.

  Bkz: [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md).

  **Bu sürümdeki diğer tasarım ve modelleme değişiklikleri:**

- **Katman diyagramları**. Sınıf Görünümü ve Nesne Tarayıcısı'nı kullanarak bu diyagramları güncelleştirin. Yazılım tasarımı gerekliliklerini yerine getirmek için yazılımınız için istenen bağımlılıkları açıklamak için katman diyagramları kullanın. Kodun bu tasarım ile tutarlı bu sınırlamaları karşılamayan kodu bularak ve sonraki kodu bu temele göre doğrulayarak tutun.

- **UML diyagramları**. Artık koddan UML sınıf diyagramları ve sıra diyagramları oluşturamazsınız. Ancak yine de yeni UML öğelerini kullanarak bu diyagramları oluşturur.

- **Mimari Gezgini**. Mimari Gezgini artık diyagramları oluşturmak için de kullanabilirsiniz. Ancak Çözüm Gezgini'ni kullanmaya devam edebilirsiniz.

##  <a name="VersionSupport"></a> Mimari ve Modelleme Araçları sürüm desteği

Visual Studio 2015, birkaç sürümlerinde kullanılabilir. Bunların tümü, mimari ve Modelleme Araçları için destek sağlar. Aşağıdaki tabloda her bir aracı kullanılabilirliğini gösterir.

|**Özelliği**|**Enterprise**|**Professional**|**Topluluk**|**Express**|
|-----------------|--------------------|----------------------|-------------------|-----------------|
|**Kod haritaları**|Evet|Yalnızca okuma ve kod haritaları filtreleme, yeni genel düğüm ekleme ve bir seçim yeni yönlendirilmiş grafik oluşturma destekler.|-|-|
|**UML sınıf diyagramları**|Evet|-|-|-|
|**UML sıralı diyagramlar**|Evet|-|-|-|
|**UML Kullanım örneği diyagramları**|Evet|-|-|-|
|**UML etkinlik diyagramları**|Evet|-|-|-|
|**UML Bileşen diyagramları**|Evet|-|-|-|
|**Katman diyagramları**|Evet|-|-|-|
|**Yönlendirilmiş grafikleri** (DGML diyagramları)|Evet|Evet|-|-|
|**Kod kopyası**|Evet|-|-|-|