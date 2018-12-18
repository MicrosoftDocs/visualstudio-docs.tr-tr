---
title: 'Nasıl yapılır: yapılandırmaları oluşturma ve düzenleme'
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- solution build configurations, editing
- build configurations, creating
- solution build configurations, creating
- build configurations, editing
- builds [Visual Studio], setting up
- property pages
- Configuration Manager
- project build configurations, creating
- project build configurations, editing
ms.assetid: 19be121c-148e-4ece-bbfc-d20b08cfc3f7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2d3f6b271eb6b9b663e30953fa597fb7d8cec6ac
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348532"
---
# <a name="how-to-create-and-edit-configurations"></a>Nasıl yapılır: yapılandırmaları oluşturma ve düzenleme

Birkaç derleme yapılandırmaları bir çözüm için oluşturabilirsiniz. Örneğin, test edicilerinizin bulmak ve sorunları gidermek için kullanabileceğiniz bir hata ayıklama derlemesi yapılandırabilirsiniz ve farklı türde yapılar farklı müşterilere dağıttığınız yapılandırabilirsiniz.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz: [Mac için Visual Studio'da oluşturma ve düzenleme yapılandırmaları](/visualstudio/mac/create-and-edit-configurations).

## <a name="create-build-configurations"></a>Derleme yapılandırmaları oluşturma

Kullanabileceğiniz **Configuration Manager** iletişim kutusunu seçin veya mevcut yapı yapılandırmalarını değiştirmek için ya da yenilerini oluşturun.

Açmak için **Configuration Manager** iletişim kutusundaki **Çözüm Gezgini**, çözüm için kısayol menüsünü açın ve ardından **Configuration Manager**.

> [!NOTE]
> Varsa **Configuration Manager** komutu görünmezse kısayol menüsünde, arama altında **derleme** menü çubuğundaki menü. Seçin ya da menü çubuğunda, burada görünmüyorsa **Araçları** > **seçenekleri**ve ardından sol bölmesinde **seçenekleri** iletişim kutusunda, genişletin**Projeler ve çözümler** > **genel**, sağ bölmede seçip **Show Gelişmiş derleme yapılandırmaları** onay kutusu.

İçinde **Configuration Manager** kullanabileceğiniz iletişim kutusu, **etkin çözüm yapılandırması** aşağı açılan listesinin bir çözüm çapında yapı yapılandırması, mevcut bir değiştirme veya yeni oluşturun yapılandırma. Kullanabileceğiniz **etkin çözüm platformu** platform yapılandırma hedefler, mevcut bir değiştirin veya yeni platform Ekle seçmek için aşağı açılan listesi. **Proje bağlamları** bölmesinde çözüm içindeki projeleri listeler. Her proje için bir projeye özgü yapılandırma ve platform seçebilir, var olanları düzenleyin veya yeni bir yapılandırma oluşturmak veya yeni bir platform Ekle. Derleme veya dağıtım çözümü için çözüm genelindeki bir yapılandırma kullandığınızda her proje dahil olup olmadığını gösteren onay kutularını de seçebilirsiniz.

 İstediğiniz yapılandırmaları ayarladıktan sonra bu yapılandırmaları için uygun olan proje özellikleri ayarlayabilirsiniz.

### <a name="to-set-properties-based-on-configurations"></a>Yapılandırmalarına göre özelliklerini ayarlamak için

-   İçinde **Çözüm Gezgini**, bir proje için kısayol menüsünü açın ve ardından **özellikleri**.

     **Özellik sayfaları** penceresi açılır.

     Yapılandırmalarınızı için özellikleri ayarlayabilirsiniz. Örneğin, bir sürüm yapılandırması için kod çözüm yerleşik olarak bulunur ve bu belirttiğinizde bir hata ayıklama yapılandırması için optimize edilmiştir belirtebilirsiniz `DEBUG` koşullu derleme simgesi bulunur. Özellik sayfası ayarları hakkında daha fazla bilgi için bkz: [proje ve çözüm özelliklerini yönetme](../ide/managing-project-and-solution-properties.md).

## <a name="create-and-modify-project-configurations"></a>Oluşturma ve proje yapılandırmalarını değiştirme

### <a name="to-create-a-project-configuration"></a>Bir proje yapılandırması oluşturmak için

1.  Açık **Configuration Manager** iletişim kutusu.

2.  Bir proje seçin **proje** sütun.

3.  İçinde **yapılandırma** açılır listede bu proje için seçme **yeni**.

     **Yeni proje yapılandırması** iletişim kutusu açılır.

4.  İçinde **adı** kutusunda, yeni yapılandırma için bir ad girin.

5.  Varolan bir proje yapılandırma özelliği ayarlarından kullanılacağını **Ayarları Şuradan Kopyala** aşağı açılan listesinde, bir yapılandırma seçin.

6.  Aynı anda çözüm genelindeki bir yapılandırma oluşturmak için seçin **oluştur yeni çözüm yapılandırması** onay kutusu.

### <a name="to-rename-a-project-configuration"></a>Bir proje yapılandırması yeniden adlandırmak için

1.  Açık **Configuration Manager** iletişim kutusu.

2.  İçinde **proje** sütunu yeniden adlandırmak istediğiniz proje yapılandırmasını içeren projeyi seçin.

3.  İçinde **yapılandırma** açılır listede bu proje için seçme **Düzenle**.

     **Proje yapılandırmalarını Düzenle** iletişim kutusu açılır.

4.  Değiştirmek istediğiniz proje yapılandırması adı seçin.

5.  Seçin **Yeniden Adlandır**ve ardından yeni bir ad girin.

## <a name="create-and-modify-solution-wide-build-configurations"></a>Oluşturma ve değiştirme wide çözüm derleme yapılandırmaları

### <a name="to-create-a-solution-wide-build-configuration"></a>Bir çözüm çapında yapı yapılandırması oluşturmak için

1.  Açık **Configuration Manager** iletişim kutusu.

2.  İçinde **etkin çözüm yapılandırması** aşağı açılan listesinde **yeni**.

     **Yeni çözüm yapılandırması** iletişim kutusu açılır.

3.  İçinde **adı** metin kutusunda, yeni yapılandırma için bir ad girin.

4.  Varolan bir çözüm yapılandırması ayarları kullanmak için **Ayarları Şuradan Kopyala** aşağı açılan listesinde, bir yapılandırma seçin.

5.  Proje yapılandırmaları aynı anda oluşturmak isteyip istemediğinizi seçin **yeni proje yapılandırmaları oluşturma** onay kutusu.

### <a name="to-rename-a-solution-wide-build-configuration"></a>Bir çözüm çapında yapı yapılandırması yeniden adlandırmak için

1.  Açık **Configuration Manager** iletişim kutusu.

2.  İçinde **etkin çözüm yapılandırması** aşağı açılan listesinde **Düzenle**.

     **Çözüm yapılandırmalarını Düzenle** iletişim kutusu açılır.

3.  Değiştirmek istediğiniz çözüm yapılandırma adı seçin.

4.  Seçin **Yeniden Adlandır**ve ardından yeni bir ad girin.

### <a name="to-modify-a-solution-wide-build-configuration"></a>Bir çözüm çapında yapı yapılandırmasını değiştirmek için

1.  Açık **Configuration Manager** iletişim kutusu.

2.  İçinde **etkin çözüm yapılandırması** aşağı açılan listesinde, istediğiniz yapılandırmayı seçin.

3.  İçinde **proje bağlamları** bölmesinde, select her proje için **yapılandırma** ve **Platform** ve seçin kullanılıp kullanılmayacağını **Yapı**da görüntülenip görüntülenmeyeceğini **Dağıt** bu.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md)
- [Derleme ve temizleme projeleri ve Visual Studio çözümleri](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Proje ve çözüm özelliklerini yönetme](managing-project-and-solution-properties.md)
- [Yapılandırmaları (Mac için Visual Studio) oluşturma ve düzenleme](/visualstudio/mac/create-and-edit-configurations)