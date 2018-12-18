---
title: 'Nasıl yapılır: oluşturma ve katılımsız yükleme çalıştırma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing Visual Studio, unattended
- unattended installation, Visual Studio
ms.assetid: 3867b5dc-ed34-4ee2-be32-a42e7e320517
caps.latest.revision: 44
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: bc1a6ba1a36dd7514257fcbb8ba4c26ca1ee6116
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065525"
---
# <a name="how-to-create-and-run-an-unattended-installation-of-visual-studio"></a>Nasıl Yapılır: Katılımsız Visual Studio Yüklemesi Oluşturma ve Çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçin yükleme uygulamasını çalıştırarak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir katılımsız (yani sessiz özelleştirilmiş olan) olarak DVD gibi medya yerine bir intranet üzerinden yükleme. Bu konu nasıl hazırlayacağınızı açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bu tür bir ağ paylaşımından yükleme.

## <a name="creating-a-network-image"></a>Bir ağ görüntüsü oluşturma
 İlk olarak, bir ağ görüntüsü oluşturmak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] medya.

#### <a name="to-create-a-network-image"></a>Bir ağ görüntüsü oluşturmak için

1.  Sunucuda bir klasör oluşturun (örneğin, *sürücü*: \IDEinstall\\).

2.  Yükleyici'den indirin [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015)ve ardından çalıştırın *ürün*.exe/layout *sürücü*: \IDEinstall\

3.  Ideinstall klasörünü ağda paylaşın ve uygun güvenlik ayarlarını ayarlayın.

     İçin yükleme uygulamasının ağ yolu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] benzer \\ \\ *ServerName*\IDEinstall\\*ürün*.exe.

    > [!NOTE]
    >  Herhangi bir yol ve dosya adı birleşimi 260 karakterden uzunsa kurulum başarısız olabilir. Bir yolda uzunluğu en fazla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 221 karakterdir.  Yerel yol adı 70 karakteri aşmamalıdır ve ağ yolu adı 39 karakteri aşmamalıdır.

     Yükleme de çalışmayabilir yol içinde klasör adlarında gömülü boşluklar varsa (örneğin, "\\\\*ServerName*\IDE yükleme" veya \\ \\ *ServerName*\Visual studio\\).

## <a name="deploying-visual-studio-in-unattended-mode"></a>Katılımsız modda Visual Studio dağıtma
 Dağıtılacak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] katılımsız modda AdminDeployment.xml dosyasını değiştirmeniz gerekir. Bunu yapmak için önce AdminDeployment.xml dosyasını kullanarak oluşturmalısınız `/CreateAdminFile`  *\<dosya konumu >* komut satırı parametresi. Ağınıza bir Visual Studio dağıtımı gönderin veya bu dosyayı koyarsanız bir kurulum içine çeker. Bu dosya daha sonra kullanabileceğiniz *sürücü*: \IDEinstall\packages dizin. AdminDeployment.xml dosyası bir işletim sistemi, mimari, Visual Studio ya da işletim sistemi dil sürümü için benzersiz değil.

> [!CAUTION]
>  Bazı durumlarda, seçili AdminDeployment.xml dosyasında listelenen öğelerin yüklenmemiş. Bu sorunu çözmek için işaretlenen öğeleri Yerleştir "Seçili ="yes"", **son** AdminDeployment.xml dosyası.
>
>  Ardından bir öğesi isteğe bağlı bağımlılıklar yüklemek istemiyorsanız, üst ilk öğesini seçin ve ardından isteğe bağlı bağımlılıklar aşağıdaki ekran görüntüsünde gösterildiği gibi ana sonra seçimini gerekir:
>
>  ![Yükleme öğeleri AdminDeployment.xml dosyasını sonunda](../install/media/vs2015-install-endoffileadmindeploy.PNG "vs2015_Install_EndOfFileAdminDeploy")
>
>  Yalnızca bir üst isteğe bağlı alt öğeleri atlamak için bunu yapmak için başka bir yolu olan — herhangi diğer bir deyişle, olarak eklemeyin "Seçili"Hayır"=" öğeleri — ancak yine de tüm yerleştirmeniz gerekir "Seçili ="yes"" AdminDeployment.xml dosyasını sonunda öğeleri.

> [!IMPORTANT]
>  Yükleme sırasında bilgisayar otomatik olarak bir veya daha fazla kez yeniden başlatılabilir. Yeniden başlatıldıktan sonra bilgisayar yeniden başlatılmadan önce yüklemeyi gerçekleştirmek için oturum açıldıysa yeniden aynı kullanıcı hesabıyla oturum açmalısınız. Katılımsız yükleme çalıştırmadan önce Önkoşul bileşenlerini yükleyerek otomatik yeniden başlatmaları engelleyebilirsiniz. İçinde "Önlemek yeniden Kurulum sırasında" başlıklı bölüme daha fazla bilgi için bkz [Visual Studio Yönetici Kılavuzu](../install/visual-studio-administrator-guide.md).

 AdminDeployment dosyası şeması aşağıdaki öğeleri içerir:

|Öğe|Öznitelik|Değerler|Açıklama|
|-------------|---------------|------------|-----------------|
|BundleCustomizations|TargetDir|*Yolu*|Yükleme uygulamasının kullanıcı arabirimindeki yolu geçersiz kılma olarak aynı şekilde davranır. Visual Studio zaten yüklüyse bu öğe yoksayılır.|
|BundleCustomizations|NoWeb|Evet&#124;varsayılan|Bu öğenin değeri Evet ise, hiçbir zaman yükleme uygulaması kurma eylemi sırasında web sitesine gidin dener.|
|Selectableıtemcustomization|Hidden|Evet&#124;yok|Bu öğenin değeri Evet ise, özelleştirme ağacında seçilebilir bir öğeyi gizler.|
|Selectableıtemcustomization|Seçili|Evet&#124;yok|Seçer veya özelleştirme ağacında seçilebilir bir öğeyi siler.|
|BundleCustomizations|Akış|Yol|Kullanıcı kullanmak istediği akış konumu.  Bu akış için kullanılan sonraki işlemleri (varsayılan olarak "varsayılan") makinedeki değiştirin.|
|BundleCustomizations|SuppressRefreshPrompt|Evet&#124;varsayılan|Kullanıcı, kullanılabilir daha yeni bir tane yoksa, Kurulum yenilemek için istemde engeller.|
|BundleCustomizations|NoRefresh|Evet&#124;varsayılan|Kullanılabilir daha yeni bir tane yoksa, Kurulum yenileyin olmaz.|
|BundleCustomizations|NoCacheOnlyMode|Evet&#124;varsayılan|Paket önbelleğinin önceden doldurulmasını engeller.|

> [!WARNING]
>  Yükleme uygulaması, gizli olsa bile Selectableıtem öğesinin seçili durumuna uyar. Her zaman seçilebilir bir öğeyi yüklemek istiyorsanız, örneğin, onu gizli ve seçili olarak işaretleyebilirsiniz.

#### <a name="to-create-an-unattended-installation-of-visual-studio"></a>Visual Studio katılımsız yükleme oluşturmak için

1.  İçinde *sürücü*: \IDEinstall\AdminDeployment.XML dosya, "" aşağıdaki örnekte gösterildiği gibi Evet olarak "varsayılan" BundleCustomizations öğesinin NoWeb özniteliğinin değeri değiştirin:

     Değişiklik `<BundleCustomizations TargetDir="default" NoWeb="default"/>` için `<BundleCustomizations TargetDir="default" NoWeb="yes"/>`

2.  Selectableıtemcustomization özniteliğini isteğe bağlı bileşenler için gerektiği şekilde değiştirin ve dosyayı kaydedin.

## <a name="running-unattended-setup"></a>Katılımsız Kurulum çalıştırma
 Katılımsız Kurulum çalıştırabilirsiniz ya da istemci bilgisayarlarda Visual Studio için yükleme uygulamasını otomatik olarak çalıştırarak veya uygulamayı çalıştırmak kullanıcıların kendilerini tanımladığınız ayarlarla.

#### <a name="to-run-an-unattended-installation-on-a-client-computer"></a>Katılımsız bir yüklemeyi istemci bilgisayarda çalıştırmak için

- Açık **Başlat** menüsünde seçin **çalıştırma**yazıp enter \\ \\ *ServerName*\IDEinstall\vs_*ürün*.exe/adminfile *PathOfTheAdmindeployment.xmlFile*<em>AdditionalParametersAsNeeded</em>

   Örneğin, aşağıdaki komut satırını belirtebilirsiniz: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\ IDEinstall\AdminDeployment.xml /quiet /norestart`

#### <a name="to-enable-clients-to-manually-install-visual-studio-with-pre-defined-settings"></a>Visual Studio'yu önceden tanımlanmış ayarlar ile el ile yüklemek istemcileri etkinleştirmek için

1.  Özelleştirilmiş AdminDeployment.xml dosyasını salt okunur bir ağ paylaşımına kopyalayın (örneğin, \\ \\ *ServerName*\IDEinstall\packages\AdminDeployment.xml).

2.  Bu paylaşımdan yüklemek kullanıcıları etkinleştirin.

## <a name="maintaining-an-installation"></a>Yükleme koruması
 Açarsanız **Denetim Masası** ve yükleme uygulamasını yeniden çalıştırırsanız Visual Studio'nun özelliklerini değiştirebilir, programlama dillerini kaldırabilir ve onarmak veya Visual Studio'yu kaldırın.

> [!NOTE]
>  Bakım modunu kullanmak için yerel bilgisayarda yönetici kimlik bilgileriniz olmalıdır.

#### <a name="to-maintain-an-installation-on-a-client-computer"></a>Bir istemci bilgisayar yüklemesi korumak için

-   Açık **Denetim Masası**ve ardından **programlar ve Özellikler**.

-   Seçin [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ve ardından **değişiklik**.

#### <a name="to-change-admindeployment-settings-on-a-client-computer-after-visual-studio-has-been-installed"></a>Visual Studio yüklendikten sonra istemci bilgisayarda AdminDeployment ayarlarını değiştirmek için

1. Gerektiği gibi AdminDeployment.xml güncelleştirin.

2. Açık **Başlat** menüsünü ve ardından **çalıştırmak**.

3. Aşağıdaki metni girin: \\ \\ *ServerName*\IDEinstall\vs_*ürün*.exe/adminfile PathToAdmindeployment.xml dosyası

    AdditionalParametersAsNeeded

    Örneğin, aşağıdaki komut satırını belirtebilirsiniz: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\IDEinstall\AdminDeployment.xml /quiet /norestart`

   Visual Studio yüklendikten sonra onarım varsayılan parametredir. Güncelleştirilmiş bir/adminfile ile Visual Studio'yu onarırsanız, güncelleştirilmiş AdminDeployment.xml dosyasını çağıran değerlerle geçerli yönetici dağıtma ayarları geçersiz kılar.

## <a name="updating-an-installation"></a>Bir yüklemeyi güncelleştirme
 Microsoft Visual Studio 2015 için birkaç güncelleştirme yayımladı. Bu bölümde, güncelleştirmeleri içerir, böylece Visual Studio 2015'in, katılımsız yükleme görüntüsünü güncelleştirmek açıklanmaktadır.

#### <a name="to-update-an-unattended-installation-of-visual-studio"></a>Visual Studio katılımsız yüklemesini güncelleştirmek için

1. Mevcut ağ görüntüde Product.exe dosyasını bulun, sağ tıklayın ve ardından **özellikleri**.

2. Tıklayın **ayrıntıları** sekmesini ve sonra Not **ürün sürümü** özelliği.

    ![Visual Studio katılımsız yüklemesi Özellikleri iletişim kutusunda örneği](../install/media/unattended-install-properties-dialog-box.PNG "katılımsız yükleme - özellikleri iletişim kutusu")

3. ###### <a name="if-the-product-version-is-140247200-or-140247201-follow-these-steps"></a>Ürün sürümü 14.0.24720.0 veya 14.0.24720.1 ise, şu adımları izleyin:
4. 1.  Çalıştırma *Product.exe* /layout *sürücü:* \IDEinstall Internet erişimi olan bir makinede. (Örneğin, çalıştırın: `vs_enterprise.exe /Layout d:\IDEinstall`.)

   2.  / Layout işlemi tamamlandıktan sonra yeni görüntüyü yeni bir konuma kopyalayın.

   3.  Oluşturun ve AdminDeployment.xml dosyasını değiştirin. Bunu yapmak için `/CreateAdminFile`  *\<dosya konumu >* komut satırı parametresi. (Daha fazla bilgi için bu makalenin "Katılımsız modda Visual Studio dağıtma" bölümüne bakın.)

   4.  İstemci makinesinde daha önce yüklediğiniz Visual Studio kopyası güncelleştirmek için aşağıdaki komutu çalıştırın: "\\\\*Sunucu1*\IDEinstall_Updated_1\\*Product.exe*  /adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml/quiet/norestart ".

        Örneğin, şunu çalıştırın: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`
5. ###### <a name="for-other-product-version-values-follow-these-steps"></a>Diğer ürün sürümü değerler için şu adımları izleyin:
6. 1.  Çalıştırma *Product.exe* /layout *sürücü:* \IDEinstall Internet erişimi olan bir makinede. (Örneğin, `vs-enterprise.exe /Layout d:\IDEinstall`.)

   2.  / Layout işlemi tamamlandıktan sonra yeni görüntüyü yeni bir konuma kopyalayın. (Veya bunun yerine mevcut ağ görüntü geçersiz kılabilir.)

   3.  Oluşturun ve sonra AdminDeployment.xml dosyasını değiştirmektir. Bunu yapmak için `/CreateAdminFile`  *\<dosya konumu >* komut satırı parametresi. (Daha fazla bilgi için bu makalenin "Katılımsız modda Visual Studio dağıtma" bölümüne bakın.)

   4.  Görüntüyü yeni bir konuma kopyalayın, daha önce yüklediğiniz Visual Studio kopyası güncelleştirmek için istemci makinesinde aşağıdaki komutu çalıştırmanız gerekir: "\\\\*Sunucu1*\IDEinstall_Updated_1\\ *Product.exe* /adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml/quiet/norestart ".

        Örneğin, şunu çalıştırın: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`

   5.  Mevcut ağ görüntü geçersiz kılarsanız, önceki adımda listelenen komutunu çalıştırabilirsiniz ya da aşağıdakileri yapabilirsiniz:

   6.  1.  Açık **Denetim Masası**ve ardından **programlar ve Özellikler**.

       2.  Seçin **Visual Studio**ve ardından **değişiklik**.

       3.  Visual Studio bakım modunda başlattıktan sonra tıklayın **Değiştir**.

       4.  En son güncelleştirmeyi Özellikler sayfasında görünmesi gerekir. Yüklemek için istediğiniz özellikleri seçin **sonraki**ve ardından **güncelleştirme** güncelleştirme hem yeni özellikler yüklemek için.

## <a name="registering-the-product"></a>Ürün kaydediliyor
 Yükleme tamamlandıktan sonra kopyanızı kaydetmenizi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] içinden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

#### <a name="to-register"></a>Kaydetmek için

1.  Açık **yardımcı** menüsünü seçip **ürünü kayıt ettir**.

2.  Ürün anahtarını girin.

     (Daha fazla bilgi için [nasıl yapılır: Visual Studio ürün anahtarını bulmak](../install/how-to-locate-the-visual-studio-product-key.md) ve [nasıl yapılır: Visual Studio'yu dağıtırken ürün anahtarlarını otomatik olarak uygulama](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md) Konular.)

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'yu yükleyin](../install/install-visual-studio-2015.md)