---
title: Bir test aracısını Yapılandır
ms.date: 09/18/2018
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring for interaction with desktop
ms.assetid: 3a94dd07-6d17-402c-ae8f-7947143755c9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: f657babf33c315be2760cf59f3ec57525643f70e
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894579"
---
# <a name="how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop"></a>Nasıl yapılır: test aracınızı masaüstüyle etkileşim kuran testleri çalıştırmak için ayarlama

Masaüstü ile etkileşmesi gereken otomatik testleri çalıştırmak istiyorsanız, aracınızı hizmet yerine işlem olarak çalıştırmak için ayarlamanız gerekir. Örneğin, uzaktan test denetleyicisi ve test aracısı kullanarak kodlanmış UI testi çalıştırmak istediğiniz ya da bir test çalıştırın ve video, çalıştırdığınızda kaydını yakalamak istiyorsanız, aracınızı işlem olarak çalışacak şekilde ayarlamanız gerekir. Visual Studio kullanarak test ayarlarınızda rollere aracılar atadığınızda, veya rollere aracılar için ortamınızda Microsoft Test Yöneticisi'ni kullanarak atadığınızda, masaüstüyle etkileşimde olması gereken rollere atanmış her aracı için kurulumu değiştirmeniz gerekir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!WARNING]
> Bir laboratuvar ortamı ayarlamak için Microsoft Test Yöneticisi'ni kullanırsanız, test aracısını yükler. Belirleyebilirsiniz **ortam oluşturma Sihirbazı'nı** kodlanmış UI testleri çalıştıracak rollerden birini yapılandırmak istediğiniz.

> [!IMPORTANT]
> Kodlanmış UI testlerini çalıştırmak istediğiniz aracıyı çalıştıran bilgisayar kilitlenemez veya etkin ekran koruyucusu olamaz.

Tarayıcıyı başlatan kodlanmış UI testleri çalıştırıyorsanız, test aracısı hizmet hesabı bu tarayıcı başlatmak için kullanılır. Bu hizmet hesabı bu bilgisayardaki etkin kullanıcının kullanıcı hesabı ile aynı olmalıdır. Aynı kullanıcı hesabı değilse, tarayıcı başlatılmaz.

> [!IMPORTANT]
> Yapı tanımının bir parçası tarayıcıyı başlatan kodlanmış UI testi çalıştırıyorsanız, yapı hizmeti için hizmet hesabı bu tarayıcı başlatmak için kullanılır. Bu hizmet hesabı bu bilgisayardaki etkin kullanıcının kullanıcı hesabı ile aynı olmalıdır. Aynı kullanıcı hesabı değilse, tarayıcı başlatılmaz.

Masaüstü ile etkileşime gerek duyan bir görevi gerçekleştiren bir role atanan aracıları ayarlamak için aşağıdaki yordamı kullanın.

## <a name="to-set-up-an-agent-to-run-as-a-process"></a>Bir aracıyı işlem olarak çalışacak şekilde ayarlamak için

1. Bir işlem olarak çalıştırmak için yüklediğiniz test aracısını yapılandırmak için Git **Başlat** > **Test Aracısı Yapılandırma Aracı**.

   **Test aracısını Yapılandır** iletişim kutusu görüntülenir.

   ![Visual Studio için test aracısını Yapılandır](media/configure-test-agent.png)

2. Seçin **etkileşimli işlem**. Test aracısı hizmet yerine işlem olarak başlatılacak. Seçin **sonraki**.

3. Test aracısı işleminin çalıştırılacağı kullanıcı için kullanıcı adını ve parolasını girin.

   > [!NOTE]
   > - İşlemi başlatmak için eklediğiniz kullanıcı, aynı zamanda bu aracı için test denetleyicisi için bilgisayarda TeamTestAgentService grubunun bir üyesi olarak eklenmelidir. Bu kullanıcıyı test denetleyicisi bilgisayarına eklediğinizde bu kullanıcı geçerli kullanıcıysa, kapatma veya yeniden başlatmanız gerekir.
   > - Null parolalar kullanıcı hesapları için desteklenmez.
   > - IntelliTrace'i veya ağ öykünmesi veri ve tanılama bağdaştırıcısını kullanmak istiyorsanız, kullanıcı hesabının Yöneticiler grubunun bir üyesi olması gerekir. Test aracısını çalıştıran makine en az ayrıcalıklı kullanıcı hesabı olan bir işletim sistemi çalıştırıyorsa, bu yönetici olarak da çalıştırmanız gerekir (yükseltilmiş). Aracı kullanıcı adı Aracı hizmeti içinde değilse, bunu eklemek test denetleyicisi üzerinde izinler gerektirir dener.
   > - Test denetleyicisini kullanmaya çalışan kullanıcı test denetleyicisinin kullanıcı hesabında olmalıdır ya da denetleyiciye karşı testleri çalıştırmak mümkün olmayacaktır.

4. Bir test aracısı olan bilgisayarın bilgisayarı yeniden başlattıktan sonra testleri çalıştıracağından emin olmak için bilgisayarı otomatik olarak test aracısı kullanıcısı oturum açmak için ayarlayabilirsiniz. Seçin **otomatik olarak oturum açma**. Bu kullanıcı adını ve parolasını şifrelenmiş bir biçimde kayıt defterinde depolar.

   > [!NOTE]
   > Uzak Masaüstü veya konuk tabanlı bağlantı kullanarak laboratuar ortamına bağlandığında, karşılaşabileceğiniz sık sık beklenmedik bağlantı kesilmeleriyle. Bağlantının kopmasının Olası nedenlerden biri, makine otomatik olarak ağda oturum açmak için yapılandırılmasıdır.

5. Masaüstüyle etkileşimde olması gereken otomatikleştirilmiş testleri engelleyebilmesi yüzünden ekran koruyucunun devre dışı bırakıldığından emin olmak için seçin **olun ekran koruyucu devre dışı**.

   > [!WARNING]
   > Otomatik olarak oturum açın veya ekran koruyucuyu devre dışı güvenlik riskleri vardır. Otomatik oturum açmayı etkinleştirerek, diğer kullanıcıların bilgisayarı başlatmasını ve otomatik olarak oturum hesabını kullanabilmelerini sağlar. Ekran koruyucu devre dışı bırakırsanız, bilgisayar kullanıcının oturum açmak bilgisayarın kilidini açmak istemeyebilir. Bu, herkesin bilgisayara fiziksel erişimi olan bilgisayara erişmesini sağlar. Bu özellikleri bir bilgisayarda etkinleştirirseniz, bu bilgisayarların fiziksel olarak güvenli olduğundan emin olun. Örneğin, bu bilgisayarların fiziksel olarak güvenli laboratuarda bulunur. Silerseniz **olun ekran koruyucu devre dışı**, bu ekran koruyucunuzu etkinleştirmez.

   Aracıyı geri hizmet olarak çalıştırmak için bu aracı kullanabilirsiniz ve **hizmet**.

6. Yaptığınız değişiklikleri uygulamak için seçin **ayarlarını uygula**.

   A **Yapılandırma Özeti** iletişim kutusu, her test aracınızı yapılandırmak için gereken adımları durumunu gösteren görüntülenir.

7. Kapatmak için **Yapılandırma Özeti** iletişim kutusunda **kapatmak**. Ardından **kapatmak** kapatmak için tekrar **Test Aracısı Yapılandırma Aracı**.

   > [!NOTE]
   > Bir işlem olarak çalışan bir test aracısı için bilgisayar üzerinde çalışan bir bildirim alanı simgesi vardır. Bu test aracısı durumunu gösterir. Başlat, Durdur veya bu aracı kullanarak bir işlem olarak çalışıyorsa aracıyı yeniden başlatın. Çalışır durumda değilse test aracısını bir işlem olarak başlatmak için seçin **Başlat** > **Visual Studio** > **Microsoft Visual Studio Test aracısı**.

   Bu test aracısın test denetleyicisi Team Foundation Server ile kayıtlıysa, etkileşimli bir işlem olarak çalışan bir test aracısı durumunu görüntülenen **denetleyicileri** görünümünde **Laboratuvar Merkezi**Microsoft Test Yöneticisi için. Etkileşimli bir işlem olarak çalıştığını göstermek için bir önceki yıldız simgesiyle listelenir. Bu test aracısını yeniden başlatmak için test aracısı için bilgisayarda çalışan aracı kullanmanız gerekir ve **denetleyicileri** görünümü.

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)