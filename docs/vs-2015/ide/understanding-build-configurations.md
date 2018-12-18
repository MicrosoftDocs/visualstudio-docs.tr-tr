---
title: Derleme yapılandırmalarını anlama | Microsoft Docs
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
- SolutionProperties.ActiveConfig
- vs.build.newprojectconfiguration
- vc.proj.configurationsctrl.multipleconfigs
- vs.build.editsolutionconfigurations
- vs.build.editprojectconfigurations
- vs.multipleconfigurations
- vs.build.newsolutionconfiguration
- VS.ConfigurationManager
- VS.MultipleConfig
helpviewer_keywords:
- solution build configurations, about build configurations
- build configurations
- project build configurations
- build configurations, advanced
- projects [Visual Studio], build configuration
- solutions [Visual Studio], build configuration
ms.assetid: 934c727d-3a22-429c-bd13-3552cecf2e24
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1c7a6304683095b0a3db5c175535d7d28e38eecb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49304141"
---
# <a name="understanding-build-configurations"></a>Derleme Yapılandırmalarını Anlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çözüm ve proje özelliklerini farklı türde yapılar kullanmak üzere farklı yapılandırmaları depolayabilirsiniz. Oluşturma, seçin, değiştirmek veya bir yapılandırmayı silmek için kullanabileceğiniz **Configuration Manager**. Bunu, menü çubuğundan açmak için seçin **derleme**, **Configuration Manager**, veya yazmanız yeterlidir **yapılandırma** içinde **Hızlı Başlat** kutusu. Ayrıca **çözüm yapılandırmaları** listesini **standart** bir yapılandırma seçin veya açmak için araç **Configuration Manager**.  
  
> [!NOTE]
>  Çözüm, araç çubuğundan yapılandırma ayarları bulunamıyor ve erişemiyor **Configuration Manager**, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] geliştirme ayarları uygulanabilir. Daha fazla bilgi için [nasıl yapılır: Visual Basic Geliştirici ayarları uygulanmış ile yapılandırmaları yönetme](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).  
  
 Varsayılan olarak, hata ayıklama ve yayın yapılandırmaları kullanılarak oluşturulan projeleri dahil edilecek [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] şablonları. Uygulamayı hata ayıklama hata ayıklama yapılandırmasını destekler ve bir sürüm yapılandırması dağıtılabilir uygulamanın bir sürümünü oluşturur. Daha fazla bilgi için [nasıl yapılır: ayarlama hata ayıklama ve yayın yapılandırmaları](../debugger/how-to-set-debug-and-release-configurations.md). Ayrıca, özel bir çözüm yapılandırmaları ve proje yapılandırmalarını da oluşturabilirsiniz. Daha fazla bilgi için [nasıl yapılır: yapılandırmaları oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md).  
  
## <a name="solution-configurations"></a>Çözüm yapılandırmaları  
 Bir çözüm yapılandırması, çözümdeki projelerden oluşturulan ve dağıtılan şeklini belirtir. Bir çözüm yapılandırması değiştirmek veya yeni bir tane tanımlamak için **Configuration Manager**altında **etkin çözüm yapılandırması**, seçin **Düzenle** veya **yeni** .  
  
 Her giriş **proje bağlamları** bir çözüm yapılandırması kutusunda çözümde bir proje temsil eder. Her bir birleşimi için **etkin çözüm yapılandırması** ve **etkin çözüm platformu**, her proje nasıl kullanıldığını ayarlayabilirsiniz. (Çözüm platformları hakkında daha fazla bilgi için bkz: [derleme platformlarını anlama](../ide/understanding-build-platforms.md).)  
  
> [!NOTE]
>  Ne zaman yeni bir çözüm yapılandırması tanımlama ve seçme **yeni proje yapılandırmaları oluşturma** onay kutusunu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yeni yapılandırma tüm projeleri için otomatik olarak atar. Benzer şekilde, zaman, yeni bir çözüm platformu tanımlama ve seçme **yeni proje platformları Oluştur** onay kutusunu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yeni platformu tüm projeleri için otomatik olarak atar. Ayrıca, yeni bir platformu hedefleyen bir projeye eklerseniz, Visual Studio, platform çözüm platformları listesine ekler ve tüm projeleri yeniden atar.  
>   
>  Yine de her proje için ayarları değiştirebilirsiniz.  
  
 Etkin çözüm yapılandırmasını, ayrıca IDE bağlamı sağlar. Örneğin, bir proje üzerinde çalışıyorsanız ve belirten yapılandırma, bir mobil cihaz için oluşturulacak **araç kutusu** bir mobil cihaz projesinde kullanılan öğeleri görüntüler.  
  
## <a name="project-configurations"></a>Proje yapılandırmaları  
 Yapılandırma ve platform, bir projenin hedeflediği birlikte, oluşturulduğunda kullanılacak özelliklerini belirtmek için kullanılır. Bir proje özellik tanımları her bir yapılandırma ve platform bileşimi için farklı bir kümesi olabilir. Bir projenin özelliklerini değiştirmek için özellik sayfalarını kullanabilirsiniz. (İçinde **Çözüm Gezgini**, proje için kısayol menüsünü açın ve ardından **özellikleri**.)  
  
 Her bir proje yapılandırması için yapılandırma bağımlı özellikler gerektiği şekilde tanımlayabilirsiniz. Örneğin, belirli bir yapı için hangi proje öğeleri dahil edilecek ayarlayabilirsiniz ve ne çıkış dosyaları oluşturulabilir, bunlar nereye yerleştirilir ve nasıl bunlar iyileştirilir.  
  
 Proje yapılandırmaları önemli ölçüde farklı olabilir. Örneğin, kendi çıktı dosyasını başka bir yapılandırma çalıştırılabilir en yüksek hızda çalıştığını belirtebilir ancak en az alan kaplaması için iyileştirilmiş bir yapılandırma özelliklerini belirtebilirsiniz.  
  
 Proje yapılandırmaları çözümü tarafından depolanan — kullanıcı tarafından — böylece bir takım tarafından paylaşılabilir.  
  
 Proje bağımlılıkları yapılandırma bağımsız olmakla birlikte, yalnızca etkin çözüm yapılandırmasında belirtilen proje oluşturulur.  
  
## <a name="how-visual-studio-assigns-project-configurations"></a>Visual Studio Proje yapılandırmaları atar nasıl  
 Yeni bir çözüm yapılandırması tanımlayın ve var olan bir ayarları kopyalanmaz, Visual Studio varsayılan proje yapılandırmaları atamak için aşağıdaki ölçütleri kullanır. Ölçüt gösterilen sırada değerlendirilir.  
  
1.  Bir proje yapılandırması adı varsa (*\<yapılandırma adı > \<platform adı >*) tam olarak eşleşen yeni bir çözüm yapılandırması, bu yapılandırma adını atanır. Yapılandırma adlarını büyük küçük harfe duyarlı değildir.  
  
2.  Proje yapılandırması adı bölümü yeni çözüm yapılandırması ile eşleşen bir yapılandırma adı varsa, bu yapılandırma veya platformu bölümü eşleşip eşleşmediğini, atanır.  
  
3.  Hala eşleşme yoksa, projeye listelenen ilk yapılandırmayı atanır.  
  
## <a name="how-visual-studio-assigns-solution-configurations"></a>Visual Studio çözüm yapılandırmaları atar nasıl  
 Bir proje yapılandırması oluşturduğunuzda (içinde **Configuration Manager**, seçerek **yeni** açılan menüde **yapılandırma** sütun bu proje için) ve seçin **yeni çözüm yapılandırmaları oluşturma** onay kutusu, Visual Studio projeyi desteklediği her platformda derlemek bir benzer adlı çözüm yapılandırması arar. Bazı durumlarda, Visual Studio, var olan çözüm yapılandırmaları yeniden adlandırır veya yenilerini tanımlar.  
  
 Visual Studio çözüm yapılandırmaları atamak için aşağıdaki ölçütleri kullanır.  
  
-   Bir proje yapılandırması platformu belirtmiyor veya yalnızca tek bir platform belirtir, ardından yeni proje yapılandırmasının adı ile eşleşen bir çözüm yapılandırması bulundu eklendi veya. Bu çözüm yapılandırmasının varsayılan adı, platform adı içermez; şu biçimi alır  *\<proje yapılandırması adı >*.  
  
-   Bir proje birden çok platform destekliyorsa, bir çözüm yapılandırması bulunamadı veya desteklenen her platform için eklendi. Her çözüm yapılandırması adını hem proje yapılandırması adı hem de platform adı içerir ve formundadır  *\<proje yapılandırması adı > \<platform adı >*.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: bir uygulama oluşturma](../ide/walkthrough-building-an-application.md)   
 [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)   
 [Projeler ve çözümler](../ide/solutions-and-projects-in-visual-studio.md)   
 [C/C++ oluşturma başvurusu](http://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d)   
 [Devenv Komut Satırı Anahtarları](../ide/reference/devenv-command-line-switches.md)



