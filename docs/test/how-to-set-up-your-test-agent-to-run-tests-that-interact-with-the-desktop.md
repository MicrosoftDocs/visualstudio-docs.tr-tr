---
title: Test Aracısı yapılandırma
description: Aracınızı hizmet yerine işlem olarak çalışacak şekilde ayarlayarak masaüstü ile etkileşime geçen otomatikleştirilmiş testlerin nasıl çalıştırılacağını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 09/18/2018
ms.topic: how-to
helpviewer_keywords:
- agents, configuring for interaction with desktop
ms.assetid: 3a94dd07-6d17-402c-ae8f-7947143755c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 13949465677301a336f0a4738e903657dbfe2b7f
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441019"
---
# <a name="how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop"></a>Nasıl yapılır: Masaüstü ile etkileşimi olan testleri çalıştırmak için test aracınızı ayarlama

::: moniker range="vs-2017"
Masaüstüyle etkileşen otomatikleştirilmiş testleri çalıştırmak istiyorsanız, aracınızı hizmet yerine işlem olarak çalışacak şekilde ayarlamanız gerekir. Örneğin, bir test denetleyicisi ve test aracısı kullanarak kodlanmış bir UI testini uzaktan çalıştırmak istiyorsanız veya bir testi çalıştırmak ve çalıştırdığınızda video kaydı yakalamak istiyorsanız, aracınızı bir işlem olarak çalışacak şekilde ayarlamanız gerekir. Visual Studio 'Yu kullanarak test ayarlarınızda rollere aracılar atadığınızda veya Microsoft Test Yöneticisi kullanarak ortamınızda rollere aracılar atadığınızda, masaüstü ile etkileşime geçmek için gereken rollere atanan aracıların kurulumunu değiştirmeniz gerekir.
::: moniker-end
::: moniker range=">=vs-2019"
Masaüstüyle etkileşen otomatikleştirilmiş testleri çalıştırmak istiyorsanız, aracınızı hizmet yerine işlem olarak çalışacak şekilde ayarlamanız gerekir. Örneğin, bir test denetleyicisi ve test aracısı kullanarak kodlanmış bir UI testini uzaktan çalıştırmak istiyorsanız veya bir testi çalıştırmak ve çalıştırdığınızda video kaydı yakalamak istiyorsanız, aracınızı bir işlem olarak çalışacak şekilde ayarlamanız gerekir. Visual Studio 'Yu kullanarak test ayarlarınızda rollere aracılar atadığınızda, masaüstü ile etkileşime geçmek için gereken rollere atanan aracıların kurulumunu değiştirmeniz gerekir.
::: moniker-end

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
> [!WARNING]
> Laboratuvar ortamı ayarlamak için Microsoft Test Yöneticisi kullanıyorsanız, test Aracısı yüklenir. **Ortam oluşturma Sihirbazı** 'nda, kodlanmış UI testlerini çalıştırmak için rollerden birini yapılandırmak istediğinizi belirtebilirsiniz.
:::moniker-end

> [!IMPORTANT]
> Kodlanmış UI testlerini çalıştırmak istediğiniz aracıyı çalıştıran bilgisayar kilitlenemez veya etkin bir ekran koruyucusu olamaz.

Tarayıcıyı başlatan kodlanmış UI testlerini çalıştırıyorsanız, bu tarayıcıyı başlatmak için test aracısının hizmet hesabı kullanılır. Bu hizmet hesabı, bu bilgisayardaki etkin kullanıcının Kullanıcı hesabı ile aynı olmalıdır. Aynı kullanıcı hesabı değilse tarayıcı başlatılmaz.

> [!IMPORTANT]
> Bir yapı tanımının parçası olarak bir tarayıcı başlatan kodlanmış bir UI testi çalıştırıyorsanız, bu tarayıcıyı başlatmak için derleme hizmeti hizmet hesabı kullanılır. Bu hizmet hesabı, bu bilgisayardaki etkin kullanıcının Kullanıcı hesabı ile aynı olmalıdır. Aynı kullanıcı hesabı değilse tarayıcı başlatılmaz.

Masaüstüyle etkileşim kurması gereken bir görevi gerçekleştiren bir role atanan aracıları ayarlamak için aşağıdaki yordamı kullanın.

## <a name="to-set-up-an-agent-to-run-as-a-process"></a>Bir aracıyı işlem olarak çalışacak şekilde ayarlamak için

1. Bir işlem olarak çalıştırmak üzere yüklediğiniz test aracısını yapılandırmak için **Start**  >  **Test Aracısı yapılandırma aracı**'nı Başlat ' a gidin.

   **Test aracısını Yapılandır** iletişim kutusu görüntülenir.

   ![Visual Studio için test aracısını yapılandırma](media/configure-test-agent.png)

2. **Etkileşimli işlem**' i seçin. Test Aracısı hizmet yerine işlem olarak başlatılır. **İleri**’yi seçin.

3. Test Aracısı işlemini çalıştıracak kullanıcı için Kullanıcı adını ve parolayı girin.

   > [!NOTE]
   > - İşlemi başlatmak için eklediğiniz kullanıcının bu aracı için test denetleyicisi için bilgisayarda TeamTestAgentService grubunun bir üyesi olarak da eklenmesi gerekir. Bu Kullanıcı geçerli kullanıcı ise, bu kullanıcıyı test denetleyicisi bilgisayarına eklediğinizde, oturumunuzu kapatmanız veya yeniden başlatmanız gerekir.
   > - Kullanıcı hesaplarında null parolalar desteklenmez.
   > - IntelliTrace 'i veya ağ öykünmesi verilerini ve tanılama bağdaştırıcısını kullanmak istiyorsanız, Kullanıcı hesabının Yöneticiler grubunun bir üyesi olması gerekir. Test aracısını çalıştıran makine Least-Privileged Kullanıcı hesabına sahip bir işletim sistemi çalıştırıyorsa, bunu yönetici olarak da çalıştırmanız gerekir (yükseltilmiş). Aracı Kullanıcı adı aracı hizmetinde değilse, test denetleyicisinde izinler gerektiren bu uygulamayı eklemeye çalışacaktır.
   > - Test denetleyicisini kullanmaya çalışan Kullanıcı, test denetleyicisinin Kullanıcı hesabında olmalıdır, aksi durumda denetleyiciye karşı testleri çalıştıramazlar.

4. Test aracısı olan bir bilgisayarın yeniden başlattıktan sonra testleri çalıştırabilmeniz için, bilgisayarı test aracısı kullanıcısı olarak otomatik olarak oturum açmak üzere ayarlayabilirsiniz. **Otomatik oturum aç '** ı seçin. Bu işlem, Kullanıcı adını ve parolayı kayıt defterindeki şifreli bir biçimde depolar.

   > [!NOTE]
   > Laboratuvar ortamına uzak masaüstü veya konuk tabanlı bağlantı kullanarak bağlıysanız, sık sık, beklenmeyen bağlantıyı kesmeyebilirsiniz. Bağlantının kaybolmasının olası bir nedeni, makinenin ağda otomatik olarak oturum açacak şekilde yapılandırılmadır.

5. BT koruyucunun devre dışı bırakıldığından emin olmak için, bu, masaüstü ile etkileşim kurması gereken otomatikleştirilmiş testleri etkileyebilecek olduğundan, **ekran koruyucunun devre dışı bırakıldığından emin olun**' ı seçin.

   > [!WARNING]
   > Otomatik olarak oturum açtığınızda veya ekran koruyucuyu devre dışı bıraktığınızda güvenlik riskleri vardır. Otomatik oturum açma özelliğini etkinleştirerek, diğer kullanıcıların bu bilgisayarı başlatmasını ve otomatik olarak oturum açtığı hesabı kullanabilmelerini sağlayabilirsiniz. Ekran koruyucusunu devre dışı bırakırsanız, bilgisayar bir kullanıcının bilgisayarın kilidini açmak için oturum açmasını istemez. Bu, bilgisayara fiziksel erişimi olan herkesin bilgisayara erişmesini sağlar. Bu özellikleri bir bilgisayarda etkinleştirirseniz, bu bilgisayarların fiziksel olarak güvenli olduğundan emin olun. Örneğin, bu bilgisayarlar fiziksel olarak güvenli bir laboratuvarda bulunur. **Ekran koruyucunun devre dışı bırakıldığından emin olun**, bu ekran koruyucunuzu etkinleştirmez.

   Aracıyı yeniden hizmet olarak çalışacak şekilde değiştirmek için bu aracı kullanabilir ve **hizmet** seçeneğini belirleyebilirsiniz.

6. Değişikliklerinizi uygulamak için **Ayarları Uygula**' yı seçin.

   Test Aracınızı yapılandırma adımlarının her birinin durumunu gösteren bir **Yapılandırma Özeti** iletişim kutusu görüntülenir.

7. **Yapılandırma Özeti** iletişim kutusunu kapatmak için **Kapat**' ı seçin. Ardından, **Test Aracısı yapılandırma aracı**'nı kapatmak Için yeniden **Kapat** ' ı seçin.

   > [!NOTE]
   > İşlem olarak çalışan bir test aracısı için bilgisayarda çalışan bir bildirim alanı simgesi vardır. Test aracısının durumunu gösterir. Bu aracı kullanarak bir işlem olarak çalışıyorsa aracıyı başlatabilir, durdurabilir veya yeniden başlatabilirsiniz. Test aracısını çalışmıyorsa bir işlem olarak başlatmak için, **Start**  >  **Visual Studio**  >  **Microsoft Visual Studio Test Aracısı**' nı Başlat ' ı seçin.

   ::: moniker range="vs-2017"
   Bu test aracısı için test denetleyicisi Team Foundation Server kaydedilmişse, etkileşimli bir işlem olarak çalışan bir test aracısının durumu, Microsoft Test Yöneticisi için **Laboratuvar merkezindeki** **denetleyiciler** görünümünde görüntülenir. Etkileşimli bir işlem olarak çalıştığını göstermek için önceki bir yıldız simgesiyle listelenir. Bu test aracısını yeniden başlatmak için, **denetleyiciler** görünümü değil, test aracısı için bilgisayarda çalışan aracı kullanmanız gerekir.
   ::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
