---
title: Bir Azure bulut hizmeti ya da sanal makineyi hata ayıklama
description: Bir bulut hizmeti veya sanal makine Visual Studio'da hata ayıklama
author: mikejo5000
manager: douge
ms.assetid: 945e06e0-2100-41af-b218-72347367ddab
ms.topic: conceptual
ms.custom: seodec18
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.prod: visual-studo-dev15
ms.technology: vs-ide-debug
ms.openlocfilehash: 78be27daf7dfe77d88508dec929e896e884f81b2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063791"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Bir Azure bulut hizmeti veya sanal makinesinde Visual Studio'da hata ayıklama

Visual Studio, Azure bulut Hizmetleri ve sanal makineler hata ayıklama için farklı seçenekler sunar.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>Yerel bilgisayarınızda, bir bulut hizmetinde hata ayıklama

Zamandan tasarruf edebilirsiniz ve Azure kullanarak para işlem bulut hizmetinizi yerel bir makinede hata ayıklamak için öykünücü. Dağıtmadan önce bir hizmet yerel olarak hata ayıklama tarafından güvenilirlik ve performans işlem süresi için ödeme yapmadan artırabilir. Ancak, bazı hatalar yalnızca bir bulut hizmeti Azure'da çalıştırıldığında meydana gelebilir kendisi. Hizmetinizi yayımlayın ve ardından bir rol örneği için hata ayıklayıcının uzak hata ayıklama etkinleştirirseniz, bu hataları ayıklayabilirsiniz.

Öykünücü, Azure işlem hizmetini taklit eder ve test ve bulut hizmetinizi dağıtmadan önce hata ayıklama için yerel ortamınızda çalışır. Öykünücü, rol örneklerinizin yaşam döngüsü işler ve yerel depolama gibi sanal kaynaklara erişim sağlar. Hata ayıklama veya hizmetinizi Visual Studio'dan çalıştırma öykünücü bir arka plan uygulama otomatik olarak başlatılır ve sonra hizmetinizi öykünücüye dağıtır. Öykünücüyü hizmetinizi yerel ortamda çalıştığında görüntülemek için kullanabilirsiniz. Tam sürümünü ya da öykünücüsü'nün express sürümü çalıştırabilirsiniz. (Azure 2.3 ile başlayarak, öykünücüsü'nün express sürümü varsayılandır.) Bkz: [çalıştırın ve bir bulut hizmeti yerel olarak hata ayıklamak için Emulator Express kullanarak](vs-azure-tools-emulator-express-debug-run.md).

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>Bulut hizmetinizi yerel bilgisayarınızda hata ayıklamak için

1. Menü çubuğunda, **hata ayıklama**, **hata ayıklamayı Başlat** Azure bulut hizmeti projenizi çalıştırmak için. Alternatif olarak, F5 tuşuna basabilirsiniz. İşlem öykünücüsü başlatılıyor bir ileti görürsünüz. Öykünücü başlatıldığında sistem tepsisi simgesi, onaylar.

    ![Sistem tepsisindeki Azure öykünücüsü](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. Bildirim alanında Azure simgesi için kısayol menüsünü açarak işlem öykünücüsü kullanıcı arabirimini görüntülemek ve ardından **Göster işlem öykünücüsü kullanıcı Arabiriminde**.

    Sol bölmede kullanıcı arabiriminin işlem öykünücüsü ve her hizmet çalışan rolü örnekleri için şu anda dağıtılan hizmetler gösterilmektedir. Hizmet veya yaşam döngüsü, günlüğe kaydetme ve tanılama bilgileri sağ bölmede gösterilecek roller seçebilirsiniz. Odağı dahil penceresinin üst kenar boşluğunda yerleştirirseniz, sağ bölmede doldurmak üzere genişletir.

3. Komutları üzerinde seçerek uygulama adımlayın **hata ayıklama** menü ve kodunuzda kesme noktaları ayarlama. Uygulama hata ayıklayıcı adım adım olarak bölmeleri uygulamanın geçerli durumuyla güncelleştirilir. Uygulama dağıtımı hata ayıklamayı durdurduğunuzda silinir. Uygulamanız bir web rolü içerir ve web tarayıcı başlatmak için başlatma eylemi özelliğini ayarladınız, Visual Studio web uygulamanızı tarayıcıda başlatır. Hizmet yapılandırmasının bir rolün örnekleri sayısını değiştirirseniz, bulut hizmetinizi durdurmak ve ardından bu yeni rol örneklerini ayıklayabilirsiniz, hata ayıklamayı yeniden başlatın.

    **Not:** çalıştırılırken veya hata ayıklama hizmetinizi durdurduğunuzda, yerel işlem öykünücüsü ve depolama öykünücüsü durduruldu değildir. Bunları açıkça bildirim alanından durdurmanız gerekir.

## <a name="debug-a-cloud-service-in-azure"></a>Azure bulut hizmetinde hata ayıklama

Bulut hizmetinizi böylece gerekli hizmetlerinin (örneğin, msvsmon.exe) rol örneklerinizin çalışan sanal makineleri üzerinde yüklü olduğu dağıttığınızda bir bulut hizmeti uzak bir makineden hata ayıklamak için bu işlevi açıkça etkinleştirmeniz gerekir. Hizmet yayımlandığında, uzaktan hata ayıklama etkinleştirmediyseniz, uzaktan hata ayıklama etkin olan hizmet yeniden yayımlamanız gerekir.

Bir bulut hizmeti için uzaktan hata ayıklama etkinleştirirseniz, performans göstermesi veya ek ücrete tabi değildir. Hizmeti kullanan istemciler olumsuz yönde etkilenebilir, çünkü bir üretim hizmetine üzerinde uzaktan hata ayıklama kullanmayın.

> [!NOTE]
> Bir bulut hizmeti Visual Studio'dan yayımladığınızda, etkinleştirebilirsiniz **IntelliTrace** .NET Framework 4 veya .NET Framework 4.5 hedefleyen herhangi bir rol içinde bu hizmet için. Kullanarak **IntelliTrace**, bir rol örneğinde geçmişte gerçekleşen olayları inceleyin ve bu süre bağlamdan yeniden. Bkz: [IntelliTrace ve Visual Studio ile yayımlanan bulut hizmeti hata ayıklama](http://go.microsoft.com/fwlink/?LinkID=623016) ve [kullanarak IntelliTrace](https://msdn.microsoft.com/library/dd264915.aspx).

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>Bir bulut hizmeti için uzaktan hata ayıklamayı etkinleştirmek için

1. Azure projesi için kısayol menüsünü açın ve ardından **Yayımla**.

2. Seçin **hazırlama** ortam ve **hata ayıklama** yapılandırma.

    Yalnızca bir kılavuz budur. Bir üretim ortamında test ortamlarınızı çalıştırmayı seçebilirsiniz. Ancak, üretim ortamına uzaktan hata ayıklama etkinleştirirseniz kullanıcılar olumsuz yönde etkileyebilir. Sürüm yapılandırmasını seçebilirsiniz, ancak hata ayıklama yapılandırması hata ayıklamayı kolaylaştırır.

    ![Hata ayıklama yapılandırmasını seçin](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. Her zamanki adımları izleyin, ancak seçin **etkinleştirme uzaktan hata ayıklayıcı tüm roller için** onay kutusunu **Gelişmiş ayarlar** sekmesi.

    ![Hata ayıklama yapılandırması](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>Azure'daki bir bulut hizmeti eklemek için

1. Sunucu Gezgini'nde, bulut hizmetinizin düğümünü genişletin.

2. Ekleyin ve ardından istediğiniz rol veya rol örneği için kısayol menüsünü açın **hata ayıklayıcı iliştirmek**.

    Rol hatalarını ayıklıyorsanız Visual Studio hata ayıklayıcı bu rolün her örneğine ekler. Hata ayıklayıcı, kodun o satırına çalıştırır ve bu Kesme noktasının koşulları karşılayan ilk rol örneği için bir kesme noktasında keser. Örneği, yalnızca bu örneği ve yalnızca o belirli örnekte bu kod satırı çalıştırır ve kesme noktasının koşullara uyan bir kesme noktasında sonları hata ayıklayıcı iliştirileceği hata ayıklama durumunda.

    ![Hata ayıklayıcının](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. Hata ayıklayıcı örneğine ekler sonra zamanki gibi hata ayıklayın. Hata ayıklayıcı, uygun ana bilgisayar işlemine rolünüz için otomatik olarak ekler. Rolü nedir bağlı olarak, hata ayıklayıcı, w3wp.exe, WaWorkerHost.exe veya WaIISHost.exe ekler. Hata ayıklayıcının bağlı olduğu işlemini doğrulamak için Sunucu Gezgininde örneği genişletin. Bkz: [Azure rol mimarisi](http://blogs.msdn.com/b/kwill/archive/2011/05/05/windows-azure-role-architecture.aspx) Azure'un işlediği hakkında daha fazla bilgi.

    ![Kod türünü seç iletişim kutusu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. Hata ayıklayıcının bağlı olduğu işlemleri tanımlamak için seçme hata ayıklama, Windows, işlemleri menü çubuğunda, işlemleri iletişim kutusunu açın. (Klavye: Ctrl + Alt + Z) Belirli bir işlem ayırmak için kısayol menüsünü açın ve ardından **ayırma işlemi**. Sistemlerde veya sunucu Gezgini'nde örneği düğümünü bulun, işlemi bulun, kısayol menüsünü açın ve ardından **ayırma işlemi**.

    ![Hata Ayıklama İşlemleri](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> Uzun kesme noktaları uzak durur önlemek hata ayıklama. Azure işlem yanıt vermiyor olarak birkaç dakikadan fazla durdurulur ve bu örneğe trafik göndermeyi durdurur değerlendirir. Uzun süre durdurursanız, msvsmon.exe işlemden ayırır.

Tüm işlemlerden hata ayıklayıcı örneği veya rolü içinde ayırmak için rol ya da hata ayıklama ve ardından örneği için kısayol menüsünü açın **ayırma hata ayıklayıcı**.

## <a name="limitations-of-remote-debugging-in-azure"></a>Azure'da uzaktan hata ayıklama sınırlamaları

Azure SDK 2.3 ' uzaktan hata ayıklama aşağıdaki sınırlamalara sahiptir:

* Uzaktan hata ayıklama etkin olan, herhangi bir rol 25 örnekten daha fazlasını olan bir bulut hizmeti yayımlanamıyor.
* Hata ayıklayıcı için 30400 30424, 31400 için 31424 ve 32400 için 32424 bağlantı noktalarını kullanır. Bu bağlantı noktalarından birini kullanmayı denerseniz, hizmetinizi yayımlama mümkün olmayacaktır ve aşağıdaki hata iletilerinden biri için Azure etkinlik günlüğü'nde görünür:

  * .Cscfg dosyası .csdef dosyası karşı doğrulanırken bir hata oluştu.
    Uç noktası için ayrılmış bir bağlantı noktası aralığı 'range' Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector 'role' rolünün bir zaten tanımlı bir bağlantı veya aralığı ile çakışıyor.
  * Ayırma başarısız oldu. Lütfen daha sonra yeniden deneyin, VM boyutunu veya rol örneklerinin sayısını azaltmayı deneyin veya farklı bir bölgeye dağıtmayı deneyin.

## <a name="debugging-azure-virtual-machines"></a>Azure sanal makineleri hata ayıklama

Visual Studio'da Sunucu Gezgini kullanarak Azure sanal makinelerinde çalışan programlar ayıklayabilirsiniz. Azure sanal makinesinde uzaktan hata ayıklama etkinleştirdiğinizde, Azure sanal makinede uzaktan hata ayıklama uzantısı yükler. Ardından, sanal makine üzerindeki işlemleri ekleyin ve normalde yaptığınız gibi hata ayıklama.

> [!NOTE]
> Azure resource manager yığınından oluşturulan sanal makineler, Visual Studio 2015'te Cloud Explorer'ı kullanarak uzaktan ayıklanabilir. Daha fazla bilgi için [bulut Gezgini ile Azure kaynaklarını yönetme](vs-azure-tools-resources-managing-with-cloud-explorer.md).

### <a name="to-debug-an-azure-virtual-machine"></a>Bir Azure sanal makinesi hata ayıklamak için

1. Sunucu Gezgini'nde, sanal makine düğümünü genişletin ve sanal makinenin hata ayıklamak istediğiniz düğümü seçin.

2. Bağlam menüsünü açın ve seçin **Etkinleştir'hata ayıklama**. Sanal makinede hata ayıklamayı etkinleştirmek istiyorsanız emin olup olmadığınız sorulduğunda **Evet**.

    Azure uzaktan hata ayıklama uzantısı hata ayıklamayı etkinleştirmek için sanal makineye yükler.

    ![Sanal makine hata ayıklamayı etkinleştir komutu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Azure etkinlik günlüğü](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. Uzak hata ayıklama uzantısı'nın yükleme işlemini tamamladıktan sonra sanal makinenin bağlam menüsünü açın ve seçin **Debugger Ekle...**

    Azure sanal makinede işlemlerin bir listesini alır ve bunları işleme İliştir işlem iletişim kutusu gösterir.

    ![Hata ayıklayıcısı Ekle komutu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. İçinde **iliştirme** iletişim kutusunda **seçin** yalnızca istediğiniz hata ayıklanacak kod türlerini göstermek için sonuç listesinde sınırlamak için. 32 bit veya 64 bit yönetilen kod, yerel kod veya her ikisi de ayıklayabilirsiniz.

    ![Kod türünü seç iletişim kutusu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. Sanal makine üzerinde hata ayıklayın ve ardından istediğiniz işlemleri seçin **iliştirme**. Örneğin, w3wp.exe işlemi, sanal makinede bir web uygulamasında hata ayıklamak istiyorsanız seçebilirsiniz. Bkz: [hata ayıklama bir veya daha fazla işlem Visual Studio'da](https://msdn.microsoft.com/library/jj919165.aspx) ve [Azure rol mimarisi](http://blogs.msdn.com/b/kwill/archive/2011/05/05/windows-azure-role-architecture.aspx) daha fazla bilgi için.

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>Bir web projesi ve hata ayıklama için bir sanal makine oluşturma

Azure projenizi yayımlamadan önce hata ayıklama ve test senaryolarını destekleyen ve test etme ve programları izleme yükleyebileceği bağımsız bir ortamda test etmek yararlı. Bu tür testler yollarından biri, uygulamanızı bir sanal makinede uzaktan hata ayıklama sağlamaktır.

Visual Studio ASP.NET projeleri uygulamayı test etmek için kullanabileceğiniz yararlı bir sanal makine oluşturmak için bir seçenek sunar. Sanal makine, PowerShell, Uzak Masaüstü ve WebDeploy gibi yaygın olarak gerekli uç noktaları içerir.

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>Bir web projesi ve hata ayıklama için bir sanal makine oluşturmak için

1. Visual Studio'da yeni bir ASP.NET Web uygulaması oluşturun.

2. Yeni ASP.NET projesi iletişim kutusunda Azure bölümünde seçin **sanal makine** açılan liste kutusunda. Bırakın **uzak kaynaklar Oluştur** onay kutusu seçili. Seçin **Tamam** devam etmek için.

    **Azure'da sanal makine oluşturma** iletişim kutusu görüntülenir.

    ![ASP.NET web projesi oluştur iletişim kutusu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    **Not:** Azure hesabınızda henüz oturum açmadıysanız oturum açmanız istenir.

3. Sanal makine için çeşitli ayarları seçin ve ardından **Tamam**. Bkz: [sanal makineler](http://go.microsoft.com/fwlink/?LinkId=623033) daha fazla bilgi için.

    DNS adı için girdiğiniz ad, sanal makinenin adı olacaktır.

    ![Sanal makine üzerinde iletişim kutusu oluşturma](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Azure sanal makine ve ardından hükümlerine oluşturur ve Uzak Masaüstü ve Web dağıtımı gibi uç noktaları yapılandırır

4. Sanal makine tam olarak yapılandırdıktan sonra sunucu Gezgini'nde sanal makinenin düğümünü seçin.

5. Bağlam menüsünü açın ve seçin **Etkinleştir'hata ayıklama**. Sanal makinede hata ayıklamayı etkinleştirmek istiyorsanız emin olup olmadığınız sorulduğunda **Evet**.

    Azure uzaktan hata ayıklama uzantısı hata ayıklamayı etkinleştirmek için sanal makineye yükler.

    ![Sanal makine hata ayıklamayı etkinleştir komutu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Azure etkinlik günlüğü](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. Açıklandığı şekilde projenizi yayımlamak [nasıl yapılır: bir Web projesi kullanarak tek tıklamayla yayımlama Visual Studio'da dağıtma](https://msdn.microsoft.com/library/dd465337.aspx). Sanal makinede üzerinde hata ayıklamak istediğiniz çünkü **ayarları** sayfasının **Web'i Yayımla** seçin **hata ayıklama** yapılandırma olarak. Bu hata ayıklama sırasında kod sembollerinin kullanılabilir olduğundan emin olur.

    ![Yayımlama ayarları](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. İçinde **dosya yayımlama seçeneği**seçin **hedefteki ek dosyaları Kaldır** proje daha erken bir zamanda zaten dağıtıldıysa.

8. Sunucu Gezgini'nde, sanal makinenin bağlam menüsünde projeye yayımlar sonra seçin **Debugger Ekle...**

    Azure sanal makinede işlemlerin bir listesini alır ve bunları işleme İliştir işlem iletişim kutusu gösterir.

    ![Hata ayıklayıcısı Ekle komutu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. İçinde **iliştirme** iletişim kutusunda **seçin** yalnızca istediğiniz hata ayıklanacak kod türlerini göstermek için sonuç listesinde sınırlamak için. 32 bit veya 64 bit yönetilen kod, yerel kod veya her ikisi de ayıklayabilirsiniz.

    ![Kod türünü seç iletişim kutusu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. Sanal makine üzerinde hata ayıklayın ve ardından istediğiniz işlemleri seçin **iliştirme**. Örneğin, w3wp.exe işlemi, sanal makinede bir web uygulamasında hata ayıklamak istiyorsanız seçebilirsiniz. Bkz: [hata ayıklama bir veya daha fazla işlem Visual Studio'da](https://msdn.microsoft.com/library/jj919165.aspx) daha fazla bilgi için.

## <a name="next-steps"></a>Sonraki adımlar

* Kullanım **IntelliTrace** yayın sunucusundan günlük çağrıları ve olayları toplamak için. Bkz: [IntelliTrace ve Visual Studio ile yayımlanan bulut hizmeti hata ayıklama](http://go.microsoft.com/fwlink/?LinkID=623016).

* Kullanım **Azure tanılama** rolleri geliştirme ortamında veya azure'da çalıştırıp çalıştırmadığınızı ayrıntılı bilgi roller içinde kod çalışmasını oturum. Bkz: [Azure tanılama kullanılarak günlük verilerinin toplanması](http://go.microsoft.com/fwlink/p/?LinkId=400450).
