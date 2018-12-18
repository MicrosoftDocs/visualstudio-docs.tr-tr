---
title: Visual Studio 2015'i kaldırma | Microsoft Docs
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
- uninstalling
- uninstalling visual studio
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
caps.latest.revision: 9
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 71e1318444c0b03ee5b2b9024c13bfbeb51b5c41
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53050140"
---
# <a name="uninstall-visual-studio"></a>Visual Studio'yu kaldırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 için en son belgeler için bkz. [kaldırma Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/uninstall-visual-studio).

Bu sayfada Visual Studio 2015, tümleşik paketimiz geliştiriciler için üretkenlik araçları'nın önceki bir sürümünü kaldırma aracılığıyla size yol gösterir.

##  <a name="uninstalling"></a>
#### <a name="to-uninstall-visual-studio-by-using-the-standard-uninstallation-method"></a>Visual Studio'yu "standart" kaldırma yöntemini kullanarak kaldırmak için

1. İçinde **Denetim Masası**, **programlar ve Özellikler** kaldırın ve ardından istediğiniz ürün sürümünü seçin **değişiklik**.

2. Kurulum sihirbazında **kaldırma**, seçin **Evet**ve ardından sihirbazda kalan yönergeleri izleyin.

   Bu standart veya varsayılan yöntem bazı bırakır ilk yüklemesi Visual Studio'nun ilk olarak yüklediyseniz (örneğin, Microsoft .NET Framework, Microsoft Visual C++ yeniden dağıtılabilir dosyaları, Microsoft SQL Server, vb.) öğeleri.   Biz bu diğer birçok uygulama bunlara bağımlı olduğundan yüklü bırakın. Bunları da kaldırmak istiyorsanız, ancak girdisini seçerek **programlar ve Özellikler**ve her tek tek kaldırabilirsiniz.

#### <a name="to-uninstall-visual-studio-and-all-other-related-files-that-is-to-uninstall-almost-everything"></a>Visual Studio ve diğer ilgili dosyaları kaldırmak için (diğer bir deyişle, neredeyse her şeyi kaldırmak)

1.  Visual Studio'nun .exe dosyasını (örneğin, "vs_enterprise.exe" bulun).

    > [!NOTE]
    >  Dosya Örneğin, "%ProgramData%\Package Cache", bir alt klasöründe olmalıdır: C:\ProgramData\Package önbellek\\{37e19555-e88d-4aed-9d42-82d0784d2b79} \vs_enterprise.exe

2.  Kullanarak .exe dosyasını çalıştırın. / uninstall/force komut satırı parametrelerini.

     Örneğin, ```vs_enterprise.exe /uninstall /force```, hangi kaldırılır Visual Studio ve çoğu geride bıraktığı temel bileşenleri, içinde bir varsayılan kaldırma. Ancak, ek içeriğin tümünü Visual Studio eklentileri kaldırmaz ve uzantıları (örneğin, Visual Studio güncelleştirmeleri ve diğer isteğe bağlı bileşenler) yükleyebilirsiniz.

    > [!TIP]
    > Alternatif olarak, "**Total Uninstaller**" Visual Studio her şeyi kaldırmak için aracı veya Visual Studio güncelleştirmelerinin yüklemiş olabilirler. Diğer bir deyişle, tüm Visual Studio 2013 veya sonraki sürümü. Daha fazla bilgi için bkz. [Visual Studio Uninstaller aracına](https://github.com/Microsoft/VisualStudioUninstaller/releases) GitHub üzerinde.

#### <a name="to-uninstall-visual-studio-in-silent-or-passive-modes-that-is-to-uninstall-from-source"></a>Visual Studio'yu Sessiz ya da pasif modda kaldırmak için (diğer bir deyişle, kaynaktan kaldırmak)

1.  Visual Studio'nun yüklü olduğu bilgisayarda Windows komut istemini açın.

2.  Aşağıdaki parametreleri girin:

     *DVDRoot* \\< yükleme dosyası\> \</quiet&#124;/passive > [/ norestart] / uninstall

#### <a name="to-roll-back-to-a-previous-version-or-release-of--visual-studio"></a>Bir önceki sürümü veya Visual Studio'nun geri almak için

1. Bu konuda listelenen yöntemlerden istediğinizi kullanarak Visual Studio'yu kaldırın.

   > [!WARNING]
   >  Visual Studio'nun (veya bir Visual Studio güncelleştirmesinin) geçerli bir sürümünün kaldırılması ve ardından önceki bir sürümünün yüklenmesi beklendiği gibi çalışmayabilir.
   >
   >  Sonucu bağımlı olduğu sürüm veya sürüm Visual Studio'nun bilgisayarınızda yüklü, bileşenleri hangi sürümlerinin yüklendiğine, hangi ürünlerin bağımlılıkları ya da Visual Studio sürüm veya bileşenleri, sahip ve son olarak, üzerinde hangi eski Visual Studio sürümünü yüklemek ya da yeniden planlayın.  Tüm bu değişkenler nedeniyle, standart kaldırma genellikle çalışmayabilecek bileşenler önceki Visual Studio sürümleri veya sürümler ile kalır.
   >
   >  Bu nedenle, en iyi sonuçlar için kullanmanızı öneririz [Visual Studio Uninstaller aracına](https://github.com/Microsoft/VisualStudioUninstaller/releases).

2. Yükleme veya kullanmak istediğiniz Visual Studio'nun önceki sürümünü yeniden yükleyin.

   Visual Studio'nun önceki bir sürümünü yüklüyor olsanız bile, Kurulum programı varsa sürüm veya daha yeni bir sürümünü kullanmak yine de deneyebilirsiniz. Daha ayrıntılı bilgi için bkz. [nasıl yapılır: bir belirli Visual Studio'nun sürümünü yükleme](../install/how-to-install-a-specific-release-of-visual-studio.md) konu.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'yu yükleyin](https://msdn.microsoft.com/library/e2h7fzkw.aspx)