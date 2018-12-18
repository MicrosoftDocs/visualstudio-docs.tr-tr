---
title: 'Nasıl yapılır: yapılandırmaları oluşturma ve düzenleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f171c337f73db495b7b71aded24f669b6e613a07
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887793"
---
# <a name="how-to-create-and-edit-configurations"></a>Nasıl Yapılır: Yapılandırmaları Oluşturma ve Düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Birkaç derleme yapılandırmaları bir çözüm için oluşturabilirsiniz. Örneğin, test edicilerinizin bulmak ve sorunları gidermek için kullanabileceğiniz bir hata ayıklama derlemesi yapılandırabilirsiniz ve farklı türde yapılar farklı müşterilere dağıttığınız yapılandırabilirsiniz.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-build-configurations"></a>Derleme yapılandırmaları oluşturma  
 Kullanabileceğiniz **Configuration Manager** derleme yapılandırmaları seçin veya mevcut değiştirmek için iletişim kutusu veya yenilerini de oluşturabilirsiniz.  
  
#### <a name="to-open-the-configuration-manager-dialog-box"></a>Configuration Manager iletişim kutusunu açmak için  
  
- İçinde **Çözüm Gezgini**, çözüm için kısayol menüsünü açın ve ardından **Configuration Manager**.  
  
  > [!NOTE]
  >  Varsa **Configuration Manager** komutu görünmezse kısayol menüsünde, arama altında **derleme** menü çubuğundaki menü. Seçin ya da menü çubuğunda, burada görünmüyorsa **Araçları**, **seçenekleri**ve ardından sol bölmesinde **seçenekleri** iletişim kutusunda **projeler ve Çözümleri**, **genel**, sağ bölmede seçip **Show Gelişmiş derleme yapılandırmaları** onay kutusu.  
  
   İçinde **Configuration Manager** kullanabileceğiniz iletişim kutusu, **etkin çözüm yapılandırması** aşağı açılan listesinin bir çözüm çapında yapı yapılandırması, mevcut bir değiştirme veya yeni oluşturun yapılandırma. Kullanabileceğiniz **etkin çözüm platformu** platform yapılandırma hedefler, mevcut bir değiştirin veya yeni platform Ekle seçmek için aşağı açılan listesi. **Proje bağlamları** bölmesinde çözüm içindeki projeleri listeler. Her proje için bir projeye özgü yapılandırma ve platform seçebilir, var olanları düzenleyin veya yeni bir yapılandırma oluşturmak veya yeni bir platform Ekle. Derleme veya dağıtım çözümü için çözüm genelindeki bir yapılandırma kullandığınızda her proje dahil olup olmadığını gösteren onay kutularını de seçebilirsiniz.  
  
  İstediğiniz yapılandırmaları ayarladıktan sonra bu yapılandırmaları için uygun olan proje özellikleri ayarlayabilirsiniz.  
  
#### <a name="to-set-properties-based-on-configurations"></a>Yapılandırmalarına göre özelliklerini ayarlamak için  
  
-   İçinde **Çözüm Gezgini**, bir proje için kısayol menüsünü açın ve ardından **özellikleri**.  
  
     **Özellik sayfaları** penceresi açılır.  
  
     Yapılandırmalarınızı için özellikleri ayarlayabilirsiniz. Örneğin, bir sürüm yapılandırması için kod çözüm yerleşik olarak bulunur ve bu belirttiğinizde bir hata ayıklama yapılandırması için optimize edilmiştir belirtebilirsiniz `DEBUG` koşullu derleme simgesi bulunur. Özellik sayfası ayarları hakkında daha fazla bilgi için bkz: [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
## <a name="creating-and-modifying-project-configurations"></a>Oluşturma ve proje yapılandırmalarını değiştirme  
  
#### <a name="to-create-a-project-configuration"></a>Bir proje yapılandırması oluşturmak için  
  
1.  Açık **Configuration Manager** iletişim kutusu.  
  
2.  Bir proje seçin **proje** sütun.  
  
3.  İçinde **yapılandırma** açılır listede bu proje için seçme **yeni**.  
  
     **Yeni proje yapılandırması** iletişim kutusu açılır.  
  
4.  İçinde **adı** kutusunda, yeni yapılandırma için bir ad girin.  
  
5.  Varolan bir proje yapılandırma özelliği ayarlarından kullanılacağını **Ayarları Şuradan Kopyala** aşağı açılan listesinde, bir yapılandırma seçin.  
  
6.  Aynı anda çözüm genelindeki bir yapılandırma oluşturmak için seçin **oluştur yeni çözüm yapılandırması** onay kutusu.  
  
#### <a name="to-rename-a-project-configuration"></a>Bir proje yapılandırması yeniden adlandırmak için  
  
1.  Açık **Configuration Manager** iletişim kutusu.  
  
2.  İçinde **proje** sütunu yeniden adlandırmak istediğiniz proje yapılandırmasını içeren projeyi seçin.  
  
3.  İçinde **yapılandırma** açılır listede bu proje için seçme **Düzenle**.  
  
     **Proje yapılandırmalarını Düzenle** iletişim kutusu açılır.  
  
4.  Değiştirmek istediğiniz proje yapılandırması adı seçin.  
  
5.  Seçin **Yeniden Adlandır**ve ardından yeni bir ad girin.  
  
## <a name="creating-and-modifying-solution-wide-build-configurations"></a>Derleme yapılandırmaları oluşturma ve çözüm çapında değiştirme  
  
#### <a name="to-create-a-solution-wide-build-configuration"></a>Bir çözüm çapında yapı yapılandırması oluşturmak için  
  
1.  Açık **Configuration Manager** iletişim kutusu.  
  
2.  İçinde **etkin çözüm yapılandırması** aşağı açılan listesinde **yeni**.  
  
     **Yeni çözüm yapılandırması** iletişim kutusu açılır.  
  
3.  İçinde **adı** metin kutusunda, yeni yapılandırma için bir ad girin.  
  
4.  Varolan bir çözüm yapılandırması ayarları kullanmak için **Ayarları Şuradan Kopyala** aşağı açılan listesinde, bir yapılandırma seçin.  
  
5.  Proje yapılandırmaları aynı anda oluşturmak isteyip istemediğinizi seçin **yeni proje yapılandırmaları oluşturma** onay kutusu.  
  
#### <a name="to-rename-a-solution-wide-build-configuration"></a>Bir çözüm çapında yapı yapılandırması yeniden adlandırmak için  
  
1.  Açık **Configuration Manager** iletişim kutusu.  
  
2.  İçinde **etkin çözüm yapılandırması** aşağı açılan listesinde **Düzenle**.  
  
     **Çözüm yapılandırmalarını Düzenle** iletişim kutusu açılır.  
  
3.  Değiştirmek istediğiniz çözüm yapılandırma adı seçin.  
  
4.  Seçin **Yeniden Adlandır**ve ardından yeni bir ad girin.  
  
#### <a name="to-modify-a-solution-wide-build-configuration"></a>Bir çözüm çapında yapı yapılandırmasını değiştirmek için  
  
1.  Açık **Configuration Manager** iletişim kutusu.  
  
2.  İçinde **etkin çözüm yapılandırması** aşağı açılan listesinde, istediğiniz yapılandırmayı seçin.  
  
3.  İçinde **proje bağlamları** bölmesinde, select her proje için **yapılandırma** ve **Platform** ve seçin kullanılıp kullanılmayacağını **Yapı**da görüntülenip görüntülenmeyeceğini **Dağıt** ..  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md)   
 [Projeleri ve Visual Studio çözümleri oluşturma ve temizleme](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [NIB nasıl yapılır: Proje özelliklerini ve yapılandırma ayarlarını değiştirme](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)



