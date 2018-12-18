---
title: Unity için Visual Studio Araçları ile çalışmaya başlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
caps.latest.revision: 12
author: conceptdev
ms.author: crdun
manager: ghogen
ms.openlocfilehash: 9ed6cb4127ba57c6b9b84a32996968dbf9fac4fe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762718"
---
# <a name="getting-started-with-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları ile Başlarken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bu bölümde, Unity için Visual Studio Araçları yükleme ve Unity projeniz Visual Studio ile çalışmak için yapılandırma öğreneceksiniz.  
  
> [!IMPORTANT]
>  5.2 Unity Proje kurulumu kolaylaştırır Unity 2.1 Visual Studio Araçları için yerleşik desteği ekler. Bu yararlanmak için Unity sürüm 5.2.0 gerekir ya da Windows ve Visual Studio Araçları 2.1 veya üzeri bir sürüm Unity için daha yüksek.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Unity için Visual Studio Araçları kullanmak için ihtiyacınız olacak:  
  
-   Bir sürümünü **Visual Studio** , Visual Studio Community, Professional, Premium veya Enterprise gibi uzantıları destekler. Visual Studio Community'yi ücretsiz indirebilirsiniz.  
  
     [Visual Studio Community'yi indirin](http://www.visualstudio.com/downloads/download-visual-studio-vs)  
  
-   **Unity** sürüm 4.0.0 veya üzeri; **Unity** sürüm 5.2.0 veya sürüm 2.1 veya üzeri Unity için Visual Studio Araçları için yerleşik destek avantajlarından yararlanmak için daha yüksek.  
  
     [Unity'yi indirin](https://unity3d.com/get-unity/download)  
  
## <a name="install-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları yükleme  
 İndirin ve Unity için Visual Studio Araçları, Visual Studio Gallery'den yükleyin. Visual Studio sürümünüz için doğru paketi yüklemeniz gerekir. VSTU Unity 5.2 veya üzeri için yerleşik destek avantajlarından yararlanmak sürüm 2.1 veya üzeri Unity için Visual Studio Araçları'nı yüklediğinizden emin olun.  
  
-   Visual Studio 2015 Community, Visual Studio 2015 Professional veya Visual Studio 2015 Enterprise için:  
  
     [Unity için Visual Studio 2015 Araçları'nı indirin](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)  
  
-   Visual Studio 2013 Community, Visual Studio 2013 Professional veya Visual Studio 2013 Premium için:  
  
     [Unity için Visual Studio 2013 Araçları'nı indirin](https://visualstudiogallery.msdn.microsoft.com/20b80b8c-659b-45ef-96c1-437828fe7cf2)  
  
-   Visual Studio 2012 Professional veya Visual Studio 2012 Premium için:  
  
     [Unity için Visual Studio 2012 araçlarını indirin](https://visualstudiogallery.msdn.microsoft.com/7ab11d2a-f413-4ed6-b3de-ff1d05157714)  
  
-   Visual Studio 2010 Professional veya Visual Studio 2010 Premium için:  
  
     [Unity için Visual Studio 2010 Araçları'nı indirin](https://visualstudiogallery.msdn.microsoft.com/6e536faa-ce73-494a-a746-6a14753015f1)  
  
> [!NOTE]
>  Visual Studio'nun Express sürümleri, Unity için Visual Studio Araçları gibi uzantıları desteklemez. Visual Studio Community, Visual Studio'nun Unity ve diğer uzantılar için Visual Studio Araçları destekleyen ücretsiz bir sürümüdür. Çoğu kullanıcı için Visual Studio Community Express daha iyi bir seçimdir.  
  
## <a name="your-first-unity-project-with-visual-studio-tools-for-unity"></a>İlk Unity projenize Unity için Visual Studio Araçları ile  
 Artık ihtiyaç duyduğunuz her şeyi sahip olduğunuza göre Visual Studio ile ilk Unity projeniz için hazırsınız demektir. Unity projenize Unity'nın hangi sürümleri bağlı olarak farklı ayardır ve Unity için Visual Studio Araçları yüklenir. Unity ve yüklemiş olduğunuz Unity için Visual Studio Araçları sürümü için aşağıdaki adımları izleyin.  
  
### <a name="unity-52-and-higher-requires-vstu-21-or-higher"></a>5.2 ve daha yüksek unity (VSTU 2.1 veya üzeri gerekir)  
 Unity 5.2 ile başlayarak, artık Visual Studio Araçları unitypackage projelerinizle aktarmanız gerekir. Projenizi bu unitypackage aktarırsa, Unity 5.2 yoksayar ve Unity için Visual Studio Araçları yüklü konumundan doğrudan yükler.  
  
#### <a name="1---create-a-unity-project"></a>1 - Unity projesi oluşturma  
 Zaten Unity ile deneyimli, yeni bir proje oluşturun ya da kendi yükler. Unity için Visual Studio Araçları Unity önceki bir sürümü ile kullanılacak Visual Studio Araçları unitypackage içeri aktarılan bir proje, yüklemekte olduğunuz, UnityVS dizini silerek bunu kaldırmanız önerilir.  
  
 Aksi takdirde, Unity için yeniyseniz, temel bir öğretici video ile küçük başlatın. Örnek projeler ile başlayabilirsiniz ve kendi oyununuzu Unity ile oluşturmak için gelen edinebilirsiniz dersleri öğreticiler bulmak için Unity edinin sayfasını ziyaret edin. Unity bilgi sayfası, birkaç farklı oyunları için izleme kolay öğreticiler vardır.  
  
 [Öğretici: Unity bilgi sayfası](http://unity3d.com/learn/tutorials/modules)  
  
#### <a name="2---configure-unity-editor-to-use-visual-studio-tools-for-unity"></a>2 - Unity için Visual Studio Araçları kullanmak için Unity Editor'ı yapılandırma  
 Projenizi Unity için Visual Studio Araçları kullanmak üzere etkinleştirmek için Visual Studio, dış betik Düzenleyicisi ayarlamanız yeterlidir. Unity Editor'ana menüsündeki seçin **düzenleme Tercihler'i**; ardından **Unity tercihleri** iletişim kutusunda seçin **dış Araçları**. Ardından, ayarlamak **dış betik Düzenleyicisi** kullanmak istediğiniz Visual Studio sürümünün özelliği (Unity için Visual Studio Araçları, Visual Studio'nun bu sürümü için de yüklenmelidir) ve emin **Düzenleyicisiekleme** özelliği ayarlanmış.  
  
 Unity şimdi etkinleştirildi için Visual Studio Araçları için yerleşik destekleyen emin olmak için bkz: **hakkında Unity** iletişim. Unity Düzenleyicisi, ana menüsündeki seçin **Yardım, hakkında Unity.** Unity için Visual Studio Araçları yüklenir ve yapılandırılır. doğru ise sol alt köşesinde görüntülenen bir ileti görürsünüz **hakkında Unity** iletişim.  
  
 Son olarak, bir yapı hedefi aracılığıyla ayarlayın sağlayın **Build Settings** sayfası ve, **betik hata ayıklamasını** etkinleştirilir.  
  
 ![Hata ayıklama için Unity derleme ayarlarını yapılandırın. ](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
#### <a name="3---launch-visual-studio-from-the-unity-editor"></a>3 - Visual Studio Unity Düzenleyicisi'nden başlatın  
 Unity 5.2 ile başlayan **Visual Studio Araçları** uzantısı menüsü artık Visual Studio'yu başlatın veya Unity için Visual Studio Araçları'nı yapılandırmak için gerekli. Dış betik düzenleyici olarak Visual Studio yapılandırıldıktan sonra bunun yerine, yalnızca Visual Studio'da Unity editor ve kodunuzu betik dosyasından açılacak seçin.  
  
### <a name="previous-versions-of-unity-pre-52"></a>Unity (pre-5.2) önceki sürümleri  
 Unity 5.2 önce Unity için Visual Studio Araçları için yerleşik destek yoktu. Visual Studio Araçları unitypackage almak ve Unity için Visual Studio Araçları kullanmak için diğer proje ayarlarını yapılandırmak bunun yerine, her proje vardı.  
  
#### <a name="1---create-a-unity-project"></a>1 - Unity projesi oluşturma  
 Zaten Unity ile deneyimli, yeni bir proje oluşturun ya da kendi yükler. Yeni bir proje başlatıyorsanız oluşturduğunuzda Visual Studio Araçları unitypackage içeri aktarın.  
  
 Aksi takdirde, Unity için yeniyseniz, temel bir öğretici video ile küçük başlatın. Örnek projeler ile başlayabilirsiniz ve kendi oyununuzu Unity ile oluşturmak için gelen edinebilirsiniz dersleri öğreticiler bulmak için Unity edinin sayfasını ziyaret edin. Unity bilgi sayfası, birkaç farklı oyunları için izleme kolay öğreticiler vardır.  
  
 [Öğretici: Unity bilgi sayfası](http://unity3d.com/learn/tutorials/modules)  
  
#### <a name="2---configure-unity-editor-to-use-visual-studio-tools-for-unity"></a>2 - Unity için Visual Studio Araçları kullanmak için Unity Editor'ı yapılandırma  
 Var olan bir Unity projeden başlatıyorsanız veya projeyi oluşturduğunuzda Visual Studio Araçları unitypackage içeri aktarmadıysanız, unitypackage artık almanız gerekir. Unity Düzenleyicisi, ana menüsündeki seçin **varlıklar, içeri aktarma paketi, Visual Studio 2015 Araçları** (yüklediğiniz Visual Studio sürümü için bir seçenek görmeniz gerekir).  
  
 ![VSTU paket Unity projenize içeri aktarın. ](../cross-platform/media/vstu-configure-unity-import-vstu.png "vstu_configure_unity_import_vstu")  
  
 Son olarak, bir yapı hedefi aracılığıyla ayarlayın sağlayın **Build Settings** sayfası ve, **betik hata ayıklamasını** etkinleştirilir.  
  
 ![Hata ayıklama için Unity derleme ayarlarını yapılandırın. ](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
#### <a name="3---launch-visual-studio-from-unity-editor"></a>3 - Visual Studio Unity Düzenleyicisi'nden başlatın  
 Son adım, Visual Studio Unity'de başlamaktır. Bu, projeniz için bir Visual Studio çözümü oluşturur ve ardından Visual Studio'da açılır.  
  
 Unity Editor'ana menüsündeki seçin **Visual Studio Araçları, Visual Studio'da açın**.  
  
 ![Unity projenizi Visual Studio'da açın. ](../cross-platform/media/vstu-configure-open-in-visual-studio.png "vstu_configure_open_in_visual_studio")  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Çalışmak ve Unity projenizde Visual Studio hata ayıklama hakkında bilgi edinmek için [Unity için Visual Studio araçları kullanarak](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Unity giriş sayfası](http://unity3d.com)

