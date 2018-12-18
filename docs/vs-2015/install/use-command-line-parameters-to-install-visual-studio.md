---
title: Visual Studio 2015'i yüklemek için komut satırı parametrelerini kullanma | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: e84d9d7bde30ab781da2f135c94baf74b697e567
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059145"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Visual Studio'yu yüklemek için komut satırı parametrelerini kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 için en son belgeler için bkz. [Visual Studio 2017'yi yüklemek için komut satırı parametreleri kullanmak](https://docs.microsoft.com/visualstudio/install/use-command-line-parameters-to-install-visual-studio).

Bir komut isteminden Visual Studio 2015'i yüklediğinizde, aşağıdaki komut satırı parametrelerini (anahtarlar olarak da bilinir) kullanabilirsiniz.

> [!NOTE]
>  Gerçek yükleyici ve önyükleyici dosyayı kullandığınızdan emin olun. Örneğin, kullandığınızdan emin olun **`vs_enterprise.exe`** vs_enterprise_ yerine*GUID*.exe. Bir Yükleyicisi'nden indirebileceğiniz [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015).

## <a name="list-of-command-line-parameters"></a>Komut satırı parametrelerinin listesi
 Visual Studio komut satırı parametreleri büyük küçük harfe duyarlı değildir.

|Parametre|Açıklama|
|---------------|-----------------|
|**/?**<br /><br /> **/ Help**<br /><br /> **/h**|Komut satırı parametrelerini görüntüler.|
|**/ AddRemoveFeatures**|Yüklü ürüne hangi özelliklerin ekleneceğini veya üründen hangi özelliklerin kaldırılacağını belirtir.|
|**/ AdminFile** *AdminDeployment.xml*|Visual Studio'yu, yönetimsel yükleme için belirttiğiniz veri dosyasını kullanarak yükler.|
|**/ ChainingPackage** *BundleName*|Bu paketi hangi paketin zincirlediğini belirtir. Ayrıca Müşteri Deneyimini Geliştirme kohortu belirtmek için kullanılabilir.|
|**/ CreateAdminFile \<dosya adı >**|/ Adminfile ile kullanılabilecek bir denetim dosyasının oluşturulacağı konumu belirtir|
|**/ CustomInstallPath** *YüklemeDizini*|Tüm yeniden hedeflenebilir paketleri belirttiğiniz dizine yükler.|
|**/ ForceRestart**|Yüklemeden sonra her zaman bilgisayarı yeniden başlatır.|
|**/ tam**|Tüm ürün özelliklerini yükler.|
|**/ Installselectableıtems \<öğe adı 1 > [;\< öğe adı 2 >]**|Yükleyici sihirbazının seçim ekranında işaretlenecek Seçim ağacı öğelerinin listesi.|
|**/ l**<br /><br /> **/ Oturum** *dosya adı*|Günlük dosyası için bir konum belirtir.|
|**/ Layout** *dizini*|Yükleme medyasındaki dosyaları belirttiğiniz dizine kopyalar.|
|**/ NoCacheOnlyMode**|Paket önbelleğinin önceden doldurulmasını engeller.|
|**/ NoRefresh**|Bu ürünün daha yeni sürümleri için onay gerekli veya önerilen güncelleştirilmiş sürümler için engeller.|
|**/ norestart**|Yükleme uygulamasının, yükleme sırasında veya yüklemeden sonra bilgisayarı yeniden başlatmasını engeller. Dönüş kodları bölümüne bakın [Visual Studio Yönetici Kılavuzu](../install/visual-studio-administrator-guide.md) aranacak dönüş kodları.|
|**/ noweb**|Internet'ten yüklemeyi engeller.|
|**/ OverrideFeedUri \<akış dosyasının yolu >**|Yazılım öğelerini açıklayan, yerel, dış akışın yolu|
|**/ ProductKey**<br /><br /> *Ürün anahtarı*|Çizgi içermeyen ve en fazla 25 karakterden oluşan özel bir ürün anahtarı ayarlar.|
|**/ • Uygulamaları zorla kapatır**|Bilgisayarı yeniden başlatmadan önce kullanıcıya sorar.|
|**/q**<br /><br /> **/quiet**<br /><br /> **/s**<br /><br /> **/silent**|Yükleme uygulaması için kullanıcı arabirimini (UI) bastırır. Visual Studio zaten yüklüyse ve bunun dışında bir parametre belirtmezseniz, yükleme uygulaması Bakım modunda çalışır.|
|**/qb**<br /><br /> **/ passive**|İlerleme durumunu gösterir ancak kullanıcı girişini beklemez.|
|**/ Repair**|Visual Studio'yu onarır.|
|**/ SuppressRefreshPrompt**|Yükleme Sihirbazı'nda, bu nedenle, Yükleme Sihirbazı'nı güncelleştirme kullanılabilir iletişim otomatik-tüm gerekli veya önerilen güncelleştirilmiş sürümlerini kabul görüntülenmesini engeller.|
|**/u**<br /><br /> **/ Uninstall**|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]'ı kaldırır.|
|**/ Uninstall/Force**<br /><br /> **/u/Force**|Visual Studio'yu ve diğer ürünlerle paylaşılan tüm özellikleri kaldırır. **Uyarı:** bu parametreyi kullanırsanız, aynı bilgisayarda yüklü diğer ürünler düzgün çalışmamaya başlayabilir.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio Yönetici Kılavuzu](../install/visual-studio-administrator-guide.md)