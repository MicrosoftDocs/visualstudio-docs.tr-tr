---
title: Otomatik test için rolleri için bir Test denetleyicisi ve Test aracısı atama
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- testing, walkthroughs, test controller and test agents
- test agent, walkthrough
- walkthroughs [Visual Studio ALM] testing
- test controller, walkthrough
- walkthroughs, test controller and test agents
ms.assetid: 57ed43ae-4e67-4139-8aec-3e9fceb0a745
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 021693266278bd705678c22d2c3f07e534901e5a
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895346"
---
# <a name="assign-roles-to-a-test-controller-and-test-agent"></a>Bir test denetleyicisi ve test aracısına roller atama

Bu yönerge, oluşturmak ve Visual Studio kullanarak birçok makine üstünden sınamayı dağıtmak için bir test denetleyicisi ve test aracısı'nı kullanan bir test ayarı yapılandırmak nasıl gösterir. Ayrıca, bu yönerge test ayarına tanılama ve veri bağdaştırıcılarının ekleneceğini gösterir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Önkoşullar

-   Birim testleri veya kodlanmış UI testleri test ayarıyla çalıştırmak için oluşturun.

-   Bir test denetleyicisi ve test aracılarını yükleyin. Bir test denetleyicisi yüklemek ve test aracıları hakkında daha fazla bilgi için bkz: [yüklemek ve test denetleyicisilerinin](../test/lab-management/install-configure-test-agents.md).

## <a name="to-create-and-configure-a-test-setting"></a>Oluşturma ve bir test ayarı yapılandırmak için

1.  İçinde **Çözüm Gezgini**, sağ **çözüm öğeleri** işaret **Ekle**ve ardından **yeni öğe**.

     **Yeni Öğe Ekle** iletişim kutusu görüntülenir.

2.  İçinde **yüklü şablonlar** bölmesinde seçin **Test ayarları**.

3.  İçinde **adı** kutusuna **TestSettingDistributedTestWalkthrough**.

4.  Seçin **ekleme**.

     Yeni test *TestSettingDistributedTestWalkthrough.testsettings* dosya görünür **Çözüm Gezgini**altında **çözüm öğeleri** klasör.

     **Test ayarları** iletişim kutusu görüntülenir. **Genel** sayfası seçili.

     Şimdi, düzenleme ve test ayarları değerlerini kaydedin.

    > [!NOTE]
    > Oluşturduğunuz her test ayarları için bir seçenek olarak listelendiğini **Etkin Test ayarlarını seçin** ve **Test Ayarlarını Düzenle** seçeneklerinden **Test** menüsü.

5.  Altında **adı**, test ayarları adını yazın.

6.  Altında **açıklama**, türü **Dağıtılmış test ayarları**.

7.  Bırakın **varsayılan adlandırma düzeni** seçili.

## <a name="to-assign-roles-to-a-test-controller-and-test-agents"></a>Bir test denetleyicisi ve test aracılarına roller atamak için

1.  Seçin **rolleri**.

     **Rolleri** sayfası görüntülenir.

2.  Testinizi uzaktan çalıştırmak için kullanın **Test yürütme yöntemi** aşağı açılan listesinden **uzaktan yürütme**.

3.  İçinde **denetleyicisi** aşağı açılan listesinde, bilgisayar adını yazın [test denetleyicinizin](../test/lab-management/install-configure-test-agents.md).

    > [!NOTE]
    > Bu ilk kez denetleyici eklediğiniz ise, aşağı açılan listesinde hiçbir denetleyicisi vardır. Liste diğer test ayarlarında belirttiğiniz önceki denetleyiciler tarafından doldurulur.

4.  Altında **rolleri**, seçin **Ekle**.

5.  Altındaki vurgulanmış satıra **adı** sütununa, **Dağıtılmış test**.

## <a name="to-assign-a-diagnostic-and-data-adapter-to-your-test-setting"></a>Test ayarınıza tanılama ve veri bağdaştırıcısı atamak için

1.  Seçin **veri ve tanılama**.

     **Veri ve tanılama** sayfası görüntülenir.

2.  Altında **rol**, doğrulayın **Dağıtılmış test** rolü seçilir.

3.  Altında **select rol için veri ve tanılama**seçin **IntelliTrace** ve **sistem bilgileri** bağdaştırıcıları.

     Bu bağdaştırıcılar ve bir test ayarında kullanabileceğiniz diğer bağdaştırıcılar hakkında daha fazla bilgi için bkz. [birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

4.  Seçin **konakları**.

5.  (İsteğe bağlı) Makinenizde Microsoft Windows 64-bit sürümünde çalışıyorsa ve test kullanarak derlenmiş **herhangi bir CPU** yapılandırmasını **Testi 32 bit veya 64 bit işlem içinde çalıştırmak** aşağı açılan listesinden **64-bit makine üzerindeki 64 bit işlem içinde testler**.

    > [!TIP]
    > Maksimum esneklik için test projelerinizi derlemelisiniz **herhangi bir CPU** yapılandırma. Daha sonra hem 32-bit hem de 64 bit aracıların çalıştırabilirsiniz. İle test projelerini derlemek için herhangi bir avantaj sağlamaz **64-bit** yapılandırma.

6.  Yeni test ayarlarını kaydetmek için seçin **Uygula**.

7.  Seçin **Kapat**.

8.  Test menüsünde **Etkin Test ayarlarını seçin** seçip **TestSettingDistributedTestWalkthrough.testsettings**.

9. Testinizi her zamanki şekilde çalıştırın.

     Test denetleyicisi birim testleri ve kodlanmış UI testlerini işlerken, test denetleyicisi testleri 100 gruplara böler ve bunları bir test aracısı makineye gönderir. Örneğin, 250 birim testiniz ve üç test aracınız varsa, ilk 100 birim testi agent1'e gönderilir, sonraki 100 birim testi agent2 gönderilir ve kalan 50 birim testleri ise Aracı3'e gönderilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)