---
title: Hizmet verme yönergeleri için yalıtılmış kabuk uygulamaları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a795e5dc71183550e660f8ce7d67f1a41bddbcf4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726787"
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Yalıtılmış kabuk uygulamaları için hizmet verme yönergeleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio yalıtılmış Kabuk uygulaması dağıttığınızda, yüklendikten sonra uygulamanız için yazılım güncelleştirmeleri sağlamak mümkün olması gerekir. Bunu yapmak için uygulamanızı Microsoft Installer (MSI) dosyası kullanarak yüklemeniz gerekir. Bu tür bir yükleme tarafından Web yeniden dağıtılması Microsoft tarafından sağlanan yazılım güncelleştirmeleri indirmek ve özel müdahalesi olmadan müşterileriniz tarafından tüketilen sağlar.  
  
## <a name="servicing-requirements"></a>Bakım gereksinimlerini  
 Yalıtılmış Kabuk yüklemenizi güncelleştirmeleri yükleme programınızı aşağıdaki üç ölçütleri karşıladığından emin olarak izin verebileceğiniz emin olabilirsiniz.  
  
### <a name="redistribute-by-using-an-msi"></a>MSI kullanarak yeniden Dağıt  
 Uygulamanızı yeniden dağıtmak için bir MSI kullanmanız gerekir, çünkü bir MSI ürün kimliğini korur ve emin olun, uygulama istemci bilgisayardaki fiziksel bir konuma sahip. Birleştirme modülleri (.msm dosyaları), bu tür güvence sağlamaz ve kullanılmamalıdır.  
  
### <a name="accounting-for-custom-actions"></a>Hesap için özel eylemler  
 Standart olmayan yükleme yönergeleri bir yükleyici programı özel eylemlerdir. Özel Eylemler dosya konumları, kayıt defteri ayarları, kullanıcı ayarlarını veya diğer yükleme öğeleri gibi parametreleri değiştirin. Özel Eylemler ile veri yükleme sırasında düzenleme.  
  
 Bir yükleme programındaki özel eylemler kullandığınızda, her zaman yükle özel eylem kullanıcı uygulamayı kaldırırken eylemi geri almak için karşılık gelen bir özel eylem gereken emin olmanız gerekir. Karşılık gelen sağlamak için Kurulum programı başarısız özel eylem kaldırırsanız, uygulamanız kaldırarak kısmen yüklü bırakır.  
  
-   Yazılım güncelleştirmeleri bu sürümleri değiştirin ya da karma değeri, bir dosya veya karma değerleri belirli bir sürümüne bağımlı olan özel bir eylem başarısız olur. Bu durumda, özel bir eylem bu değerleri el ile güncelleştirmeniz gerekir. Ürün sürümleri arasında paylaşılan bir dosya veya karma değerleri sürümleri, ek bir sorun meydana gelir. Bu bağımlılık, mümkün olduğunda kaçının.  
  
### <a name="accounting-for-shared-files"></a>Paylaşılan dosyalar için hesap oluşturma  
 Paylaşılan dosyalar, aynı ada sahip ve aynı konuma göre birden çok ürünlerin yüklenir. Bu ürün sürümü, stok tutma birimini (SKU) veya her ikisi de farklı olabilir ve ürünlerin belirli bir bilgisayarda birlikte bulunabilir. Ancak, paylaşılan dosyalar, çeşitli nedenlerle hizmet sorunları oluşturun:  
  
-   Paylaşılan dosyalar güncelleştiriliyor, bir uygulama için bir güncelleştirme henüz güncelleştirilmemiş ikinci bir uygulama tarafından kullanılan bir dosya sürümü değişebilir için uygulama uyumluluğu sorunlarına neden olabilir. Dosyaları paylaşma ürünleri için yükleyicileri paylaşılan dosyalara başvuruları sayısı. Bu nedenle, bir ürünü kaldırmadan yüklü örnek sayısını azaltma dışında paylaşılan dosyalar etkilemez.  
  
-   Hızlı düzeltme Mühendisliği (QFE) Yükleyici QFE yükleyici hizmet ürünleri sürümlerine dosyaların sürümlerine geri döner. Bu işlem, potansiyel olarak güncelleştirilen bir paylaşılan dosya teslim bir uygulama keser.

