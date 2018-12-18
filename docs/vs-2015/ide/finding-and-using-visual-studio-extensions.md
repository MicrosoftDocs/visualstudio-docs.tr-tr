---
title: Bulma ve uzantıları kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
caps.latest.revision: 47
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8de9a0394c72043bc54dd6fa0632d3ed3e6edfd5
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062806"
---
# <a name="finding-and-using-visual-studio-extensions"></a>Visual Studio Uzantıları’nı bulma ve kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio uzantıları Visual Studio içinde çalıştırın ve yeni veya geliştirilmiş Visual Studio özellikleri sağlayan kod paketlerdir. Visual Studio uzantıları hakkında daha fazla bilgi bulabilirsiniz: [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 Kullanabileceğiniz **Uzantılar ve güncelleştirmeler** iletişim kutusunda, Web siteleri ve diğer konumlardan Visual Studio uzantılarını ve örneklerini yüklemek ve etkinleştirmek, devre dışı bırakmak, güncelleştirmek veya bunları kaldırmak için. (**Araçları / Uzantılar ve güncelleştirmeler**, veya tür **uzantıları** içinde **hızlı başlatma** pencere). İletişim kutusu, yüklü örnekler ve uzantılar için güncelleştirmeleri de gösterir. Ayrıca, Web sitelerinden uzantıları indirmesi veya diğer geliştiricilerden alın.

> [!NOTE]
>  Visual Studio 2015'ten başlayarak, Visual Studio Galerisi üzerinde barındırılan uzantıları otomatik olarak güncelleştirilir.  Bu ayarı yoluyla değiştirebilirsiniz **Uzantılar ve güncelleştirmeler** iletişim.  Bölümüne **otomatik uzantı güncelleştirmeleri** altındaki ayrıntılar için.

## <a name="finding-visual-studio-extensions"></a>Visual Studio uzantıları bulma
 Uzantılardan yükleyebileceğiniz [Visual Studio Galerisi](http://go.microsoft.com/fwlink/?LinkID=178891) veya [örnek Galerisi](http://go.microsoft.com/fwlink/?LinkId=245175) Microsoft Web sitesinde. Uzantılar; denetimler, örnekler, şablonlar, araçlar veya Visual Studio'ya işlevsellik katan diğer bileşenler olabilir. Visual Studio, VSIX paketi biçimindeki uzantıları destekler; bu proje şablonları içerir, öğe şablonları, **araç kutusu** öğeleri, yönetilen uzantı çerçevesi (MEF) bileşenleri ve VSPackages. Ayrıca indirin ve MSI tabanlı uzantılar yükleyin ancak **Uzantılar ve güncelleştirmeler** iletişim kutusunu etkinleştirin veya devre dışı. Visual Studio Galerisi VSIX hem de MSI uzantıları içerir.

## <a name="installing-or-uninstalling-visual-studio-extensions"></a>Visual Studio uzantıları yükleme veya kaldırma
 İçinde **Uzantılar ve güncelleştirmeler**, yüklemek istediğiniz uzantıyı bulun. (Adı veya uzantı adının bir kısmını biliyorsanız, içinde arama yapabilirsiniz **Visual Studio Galerisi'nde Ara** penceresi.) Tıklayın **indirme**, ardından **yükleme**. Uzantıyı yüklemek için Visual Studio'yu yeniden başlatmanız gerekir.

 Bağımlılıkları olan bir uzantıyı yüklemeye çalışırsanız, yükleyici bunların yüklenmiş olup olmadığını denetler. Bunlar yüklü değilse **Uzantılar ve güncelleştirmeler** iletişim kutusunda uzantıyı yükleyebilmeniz için önce yüklenmesi gereken bağımlılıklar listelenmiştir.

 Bir uzantıyı kullanmayı bırakmak isterseniz devre dışı bırakabilir veya kaldırabilirsiniz. Bir uzantı devre dışı bırakıldığında yüklü kalır, ancak etkin değildir. Yalnızca VSIX uzantılarını devre dışı bırakabilirsiniz; MSI kullanarak yüklenmiş uzantıları sadece kaldırılabilir. Uzantı bulun ve tıklatın **kaldırma** veya **devre dışı**. Devre dışı bırakılmış bir uzantıyı kaldırmak için Visual Studio'yu yeniden başlatmanız gerekir.

## <a name="per-user-and-administrative-extensions"></a>Kullanıcı Başına ve Yönetim Uzantıları
 Uzantıların çoğu kullanıcı başına uzantılar ve yüklenmiş **%LocalAppData%\Microsoft\VisualStudio\\< Visual Studio sürümü\>\Extensions\\**  klasör. Bazı uzantılar yönetimsel uzantıları ve yüklenmiş **\<Visual Studio yükleme klasörü > \Common7\IDE\Extensions\\** klasör.

 Hata veya kötü amaçlı kod içerebilecek uzantıları karşı sisteminizi korumak için yalnızca Visual Studio normal kullanıcı izinleriyle çalıştırıldığında yüklemek için kullanıcı başına uzantılar kısıtlayabilirsiniz. Başka bir deyişle, Visual Studio Yönetici kullanıcı izinleriyle çalıştırdığınızda kullanıcı başına uzantılar devre dışı bırakılır. Bunu yapmak için Git **Uzantılar ve güncelleştirmeler** seçenekler sayfası (**Araçlar / Seçenekler**, **ortam**, **Uzantılar ve güncelleştirmeler**, veya yalnızca tür **uzantısı** içinde **hızlı başlatma** pencere). NET **bağımsız kullanıcı uzantılarının yönetici olarak çalışırken yük** onay kutusunu işaretleyin ve ardından Visual Studio'yu yeniden başlatın.

## <a name="automatic-extension-updates"></a>Otomatik uzantı güncelleştirmeleri
 Kullanıcı başına uzantılar, yeni bir sürümü Visual Studio galerisinde kullanılabilir olduğunda otomatik olarak güncelleştirilir.  Uzantının yeni sürümünü algılanır ve arka planda ve sonraki yeniden başlatmada Visual Studio'nun yüklü, uzantının yeni sürümünü çalıştırırsınız.

 Yalnızca kullanıcı başına uzantılar otomatik olarak güncelleştirilebilir.  Tüm kullanıcılar güncelleştirilmez ve aracılığıyla yeni sürümleri yine de el ile yüklemek için yüklenen yönetim uzantıları **Uzantılar ve güncelleştirmeler** iletişim **güncelleştirmeleri** düğümü. Hangi uzantıların uzantının Ayrıntılar bölmesinde otomatik olarak güncelleştirilecek gördüğünüz **Uzantılar ve güncelleştirmeler** iletişim.

 Otomatik Güncelleştirmeler devre dışı bırakmak istiyorsanız, tüm uzantıları veya yalnızca belirli uzantılara özelliği devre dışı bırakabilirsiniz.

-   Tüm uzantılar için Otomatik Güncelleştirmeler devre dışı bırakmak için **Uzantılar ve güncelleştirmeler ayarlarınızı değiştirin** bağlantısını **Uzantılar ve güncelleştirmeler** iletişim kaldırın **otomatik olarak güncelleştir Uzantıları**.

-   Belirli bir uzantı için Otomatik Güncelleştirmeler devre dışı bırakmak için işareti kaldırın **bu uzantıyı otomatik olarak güncelleştir** seçeneği uzantının ayrıntıları bölmesinde sağ alt tarafında **Uzantılar ve güncelleştirmeler** iletişim.

> [!NOTE]
>  Visual Studio 2015 güncelleştirme 2'de başlayarak, belirtebilirsiniz (içinde **Araçlar / Seçenekler / ortam / Uzantılar ve güncelleştirmeler**) kullanıcı başına uzantılar, tüm kullanıcı uzantıları veya hem de (varsayılan ayar) için Otomatik Güncelleştirmeler isteyip istemediğinizi.

## <a name="sample-master-copies-and-working-copies"></a>Örnek ana kopyalar ve çalışma kopyaları
 Çevrimiçi bir örneği yüklediğinizde, çözüm iki konumda depolanır:

- Belirtilen konumda bir çalışma kopyası depolanır **yeni proje** iletişim kutusu.

- Ayrı bir ana kopya bilgisayarınızda depolanır.

  Kullanabileceğiniz **Uzantılar ve güncelleştirmeler** iletişim kutusu örneklerle ilgili şu görevleri gerçekleştirebilirsiniz:

- Yüklediğiniz örneklerin ana kopyalarını listeleyin.

- Bir örneğin ana kopyasını devre dışı bırakın veya kaldırın.

- Örnek Paketleri (bir teknoloji veya özellik ile ilgili örnek koleksiyonları) yükleyin.

- Tek tek çevrimiçi örnekleri yükleyin. (Ayrıca bunu yapabilirsiniz **yeni proje** iletişim kutusu.)

- Yüklü örnekler için kaynak kodu değişiklikleri yayımlandığında güncelleştirme bildirimlerini görüntüleyin.

- Bir güncelleştirme bildirimi olduğunda yüklü bir örneğin ana kopyasını güncelleştirin.

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Uzantılar ve Güncelleştirmeler İletişim Kutusunu Kullanmadan Yükleme
 .vsix dosyalarında paketlenmiş uzantılar Visual Studio Galerisi dışındaki konumlarda bulunabilir. **Uzantılar ve güncelleştirmeler** iletişim kutusunda, bu dosyaları silemese ancak dosyasına çift veya dosyasını seçme ve ENTER tuşuna basmak .vsix dosyasını yükleyebilirsiniz. Bundan sonra yalnızca yönergeleri izleyin. Uzantı yüklendiğinde, kullanabileceğiniz **Uzantılar ve güncelleştirmeler** etkinleştirmek, devre dışı bırakmak veya kaldırmak için iletişim kutusu.

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Uzantılar tarafından desteklenmeyen uzantı türleri ve güncelleştirmeler iletişim kutusu
 Visual Studio Microsoft Installer (MSI) tarafından yüklenen Uzantıları desteği devam eder ancak ile **Uzantılar ve güncelleştirmeler** yapmadan iletişim kutusu.

> [!TIP]
>  MSI tabanlı uzantı bir extension.vsixmanifest dosyası içeriyorsa, uzantı görünür **Uzantılar ve güncelleştirmeler** iletişim kutusu.
