---
title: 'Hata ayıklama hazırlığı: Visual C++ proje türleri | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- project templates, debugging
- Visual C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 802b34d47501d3538008838f9bb6ddec93ac827a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752392"
---
# <a name="debugging-preparation-visual-c-project-types"></a>Hata Ayıklama Hazırlığı: Visual C++ Proje Türleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde oluşturan temel proje türlerinde hata ayıklama işlemini açıklamaktadır [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] proje şablonları.  
  
 Proje türlerine çıktılarını DLL'leri oluşturma halinde gruplandırılır Not [DLL projelerinde hata ayıklama](../debugger/debugging-dll-projects.md) paylaştıkları genel özellikleri nedeniyle.  
  
##  <a name="BKMK_In_this_topic"></a> Bu konudaki  
 [Önerilen özellik ayarları](#BKMK_Recommended_Property_Settings)  
  
 [Win32 projeleri](#BKMK_Win32_Projects)  
  
- [Bir C veya C++ Win32 uygulamasında hata ayıklamak için](#BKMK_To_debug_a_C_or_C___Win32_application)  
  
- [Hata ayıklama yapılandırmasını el ile ayarlamak için](#BKMK_To_manually_set_a_Debug_configuration)  
  
  [Windows Forms uygulamaları (.NET)](#BKMK_Windows_Forms_Applications___NET_)  
  
##  <a name="BKMK_Recommended_Property_Settings"></a> Önerilen özellik ayarları  
 Bazı özellikler tüm yönetilmeyen hata ayıklama senaryoları için aynı şekilde ayarlamanız gerekir. Aşağıdaki tablolarda, önerilen özellik ayarları gösterilmiştir. Burada listelenmeyen ayarlar, yönetilmeyen farklı proje türleri arasında değişebilir. Daha fazla bilgi için [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)  
  
### <a name="configuration-properties-124-cc-124-optimization-node"></a>Yapılandırma özellikleri &#124; C/C++ &#124; iyileştirme düğümü  
  
|Özellik adı|Ayar|  
|-------------------|-------------|  
|**En iyi duruma getirme**|Kümesine **devre dışı (/ 0 d).** Oluşturulan yönergeler doğrudan sizin kaynak kodunuza karşılık gelmediğinden en iyi duruma getirilmiş kod hatalarını ayıklamak için zordur. Programınızda, yalnızca en iyi duruma getirilmiş kodda görüntülenen bir hata bulursanız, bu ayarı açabilirsiniz, ancak gösterilen kodun **ayrıştırılmış kodu** penceresi, kaynak kodunuzda gördüğünüz eşleşmeyebilir en iyi duruma getirilmiş kaynaktan oluşturulur Windows. Adımlama gibi diğer özellikleri beklendiği gibi çalışmayabilir.|  
  
### <a name="configuration-properties-124-linker-124-debugging-node"></a>Yapılandırma özellikleri &#124; bağlayıcı &#124; hata ayıklama düğümü  
  
|Özellik adı|Ayar|  
|-------------------|-------------|  
|**Hata ayıklama bilgileri üret**|Her zaman bu seçeneği ayarlamalısınız **Evet (/ DEBUG)** hata ayıklama sembolleri ve hata ayıklama için gereken dosyaları oluşturmak için. Uygulama üretime gittiğinde, off olarak ayarlayabilirsiniz.|  
  
 [Bu konudaki](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Win32_Projects"></a> Win32 projeleri  
 Win32, C veya C++ ile yazılmış geleneksel Windows programları uygulamalardır. Bu tür bir uygulamada hata ayıklama [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oldukça basittir.  
  
 MFC ve ATL Projelerimi Win32 uygulamaları içerir. Windows API'larını kullanın ve MFC veya ATL kullanabilir, ancak ortak dil çalışma zamanı (CLR) kullanmayın. Ancak, CLR kullanan yönetilen kodu çağrısı olabilir.  
  
 Aşağıdaki yordam, içinden bir Win32 Proje hatalarını ayıklamaya açıklanmaktadır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Dışında uygulamayı başlatmak için bir Win32 uygulamasında hata ayıklamak için başka bir yolu olan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve ekleyebilir. Daha fazla bilgi için [çalışan işlemlere ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
###  <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Bir C veya C++ Win32 uygulamasında hata ayıklamak için  
  
1.  Projeyi Visual Studio'da açın.  
  
2.  Üzerinde **hata ayıklama** menüsünde seçin **Başlat**.  
  
3.  İçinde açıklanan teknikleri kullanarak hata ayıklama [hata ayıklayıcı temel bilgileri](../debugger/debugger-basics.md).  
  
###  <a name="BKMK_To_manually_set_a_Debug_configuration"></a> Hata ayıklama yapılandırmasını el ile ayarlamak için  
  
1. Üzerinde **görünümü** menüsünü tıklatın **özellik sayfaları**.  
  
2. Tıklayın **yapılandırma özellikleri** zaten değilse, açmak için düğümü  
  
3. Seçin **genel**, değerini ayarlayıp **çıkış** için satır **hata ayıklama**.  
  
4. Açık **C/C++** düğüm ve select **genel**.  
  
    İçinde **hata ayıklama** satır derleyici tarafından oluşturulacak hata ayıklama türünü belirtin. Seçtiğiniz değerler **Program veritabanı (/Zi)** veya **Düzenle ve devam et (/zı) için Program veritabanı**.  
  
5. Seçin **iyileştirme**hem de **iyileştirme** satır, select **devre dışı (/ 0d)** aşağı açılan listeden.  
  
    Oluşturulan yönergeler doğrudan sizin kaynak kodunuza karşılık gelmediğinden en iyi duruma getirilmiş kod hatalarını ayıklamak için zordur. Programınızda, yalnızca en iyi duruma getirilmiş kodda görüntülenen bir hata bulursanız, bu ayarı açabilirsiniz, ancak ayrıştırma penceresinde gösterilen kodun kaynak pencerelerinizi gördüğünüz eşleşmeyebilir en iyi duruma getirilmiş kaynaktan oluşturulduğunu unutmayın. Adımlama gibi özellikleri, kesme noktaları ve yürütme yanlış noktası gösterilecek olasıdır.  
  
6. Açık **bağlayıcı** düğüm ve select **hata ayıklama**. İlk **Oluştur** satır, select **Evet (/ DEBUG)** aşağı açılan listeden. Her zaman hata ayıklaması yapıyorsanız bu ayarlar.  
  
   Daha fazla bilgi için[C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
   [Bu konudaki](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Windows_Forms_Applications___NET_"></a> Windows Forms uygulamaları (.NET)  
 **Windows Forms uygulaması (.NET)** şablon oluşturur bir [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] Windows Forms uygulaması. Daha fazla bilgi için [nasıl yapılır: bir Windows uygulaması projesi oluşturmak](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Bu tür bir uygulamada hata ayıklama [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yönetilen Windows Forms uygulamalarında benzer.  
  
 Proje şablonuyla bir Windows Forms projesi oluşturduğunuzda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hata ayıklama ve yayın yapılandırmaları için gereken ayarları otomatik olarak oluşturur. Gerekirse, bu ayarları değiştirip değiştiremeyeceğini  **\<proje adı > özellik sayfaları** iletişim kutusu. Daha fazla bilgi için [hata ayıklama ve yayın yapılandırmaları](../debugger/how-to-set-debug-and-release-configurations.md).  
  
 Daha fazla bilgi için [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 Dışında uygulamayı başlatmak için bir Windows Forms uygulamasında hata ayıklamak için başka bir yolu olan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve ekleyebilir. Daha fazla bilgi için [bir çalışan bir Program veya birden çok programları ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 [Bu konudaki](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı temel bilgileri](../debugger/debugger-basics.md)   
 [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Çalışan bir Program veya birden çok programlara ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Hata ayıklama ve yayın yapılandırmaları](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Nasıl yapılır: bir Windows uygulaması projesi oluşturma](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)



