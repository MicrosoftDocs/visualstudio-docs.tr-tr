---
title: Windows Installer kullanarak Office çözümü dağıtma
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, setup project
- Office development in Visual Studio, MSI
- deploying applications [Office development in Visual Studio], setup project
- deploying applications [Office development in Visual Studio], MSI
- ClickOnce deployment [Office development in Visual Studio], MSI
- publishing Office solutions [Office development in Visual Studio], setup project
- Office applications [Office development in Visual Studio], MSI
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3e811fac767e8b89f0a6958511c54642f07190cf
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673061"
---
# <a name="deploy-an-office-solution-by-using-windows-installer"></a>Windows Installer kullanarak Office çözümü dağıtma
Office çözümünüz için bir Windows Installer kullanarak oluşturmayı öğrenin [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  

Bir Windows Installer dosyası oluşturmak için Visual Studio kullanarak, son kullanıcının bilgisayarında yönetici erişimi gerektiren bir Office çözümü dağıtabilirsiniz. Örneğin, böyle bir dosya, çözümü bir bilgisayarın tüm kullanıcıları için yalnızca bir kez yüklemek için kullanabilirsiniz. Çözüm bilgisayarın her kullanıcısı için ayrı olarak yüklenmesi gerekir ancak bu ayrıca ClickOnce kullanarak Office çözümü dağıtabilirsiniz.  


## <a name="in-this-topic"></a>Bu konuda  

- [VSTO eklenti örnekleri indirin](#Download)  

- [InstallShield Limited Edition'ı Al](#Obtain)  

- [Çözüme güven kazandırmak için nasıl karar verme](#ApplySecurity)  

- [Bir kurulum projesi oluşturmak](#Create)  

- [Proje çıktısı ekleme](#Add)  

- [Dağıtım ve uygulama bildirimleri Ekle](#AddD)  

- [Bağımlı bileşenleri önkoşul olarak yapılandır](#Configure)  

- [Kullanıcının bilgisayarında çözümü dağıtmak istediğiniz yeri belirtin](#Location)  

- [Bir VSTO eklentisinin yapılandırın](#ConfigureRegistry)  

- [Bir belge düzeyinde özelleştirmeyi Yapılandır](#ConfigureDocument)  

- [Kurulum projesi oluştur](#Build)  

ClickOnce kullanarak Office çözümünü dağıtma hakkında daha fazla bilgi için bkz. [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md).  

Kullanarak bir Windows Installer dosyası oluşturma hakkında daha fazla bilgi için [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], bkz: [Windows Installer kullanarak Office çözümü için Visual Studio 2010 araçlarını dağıtma](http://go.microsoft.com/fwlink/?LinkId=201807).  


## <a name="Download"></a>Örnekleri indir  
Bu konu aşağıdaki indirilebilir örneklere başvurur.  



|Örnek<br /><br />|Açıklama<br /><br />|  
|----------|---------------|  
|[Exceladdın](http://go.microsoft.com/fwlink/?LinkID=275492)<br /><br />|Bir Excel VSTO Office'in 32 bit veya 64-bit sürümü çalıştıran bir bilgisayara yükleyebilirsiniz eklenti.<br /><br />|  
|[ExcelWorkbook](http://go.microsoft.com/fwlink/?LinkID=275493)<br /><br />|Office'in 32 bit veya 64-bit sürümü çalıştıran bir bilgisayara yüklediğiniz bir Excel belge düzeyi özelleştirmesi.<br /><br />|  

## <a name="ApplySecurity"></a>Çözüme güven kazandırmak için nasıl karar verme  
Bir çözümün kullanıcı bilgisayarları üzerinde çalıştırmadan önce aşağıdaki yollardan biri vermelisiniz veya çözümü yükledikleri sırada kullanıcılar bir güvenlik istemine yanıt vermelidir.  


- Bilinen ve güvenilir bir yayımcıyı tanımlayan bir sertifika kullanarak bildirimleri imzalayın. Daha fazla bilgi için [uygulama ve dağıtım bildirimlerini imzalayarak çözüme güvenin](../vsto/granting-trust-to-office-solutions.md#Signing).  

- Çözümü kullanıcının bilgisayarındaki Program Files dizinine yükleyin.  

> [!NOTE]  
> Belge düzeyi özelleştirmeleri için belgenin konumunu da güvenilir olması gerekir. Daha fazla bilgi için [belgelere güven verme](../vsto/granting-trust-to-documents.md).  


## <a name="Obtain"></a>InstallShield Limited Edition'ı Al  
Visual Studio yüklediyseniz ücretsiz olan InstallShield Limited Edition (ISLE) kullanarak bir Windows Installer dosyası oluşturabilirsiniz. ISLE, Visual Studio'nun önceki sürümlerinde sunulan Kurulum ve dağıtım için proje şablonları işlevselliğinin yerine geçer.  


### <a name="to-get-installshield-limited-edition"></a>InstallShield Limited Edition'ı almak için  

1. Menü çubuğunda, **dosya** > **yeni** > **proje**.  

   **Yeni proje** iletişim kutusu açılır.  

2. Şablonlar bölmesinde, **diğer proje türleri**ve ardından **Kurulum ve dağıtım** şablonu.  

3. İçin proje türleri listesinde **Kurulum ve dağıtım**, seçin **InstallShield Limited Edition'ı Etkinleştir**ve ardından **Tamam** düğmesi.  

   InstallShield Limited Edition'ı alma hakkında bilgi sağlayan bir sayfa görüntülenir.  

4. Bu sayfada seçin **indirme web sitesine gidin** bağlantı.  

5. InstallShield Limited Edition indirme sayfasında ilgili alanlara gerekli bilgileri girin ve ardından **Şimdi Yükle** bağlantı.  

   İndirme, yükleme ve ürünü etkinleştirildikten sonra **InstallShield Limited Edition projesi** şablonu Visual Studio'da görünür.  


## <a name="Create"></a>Bir kurulum projesi oluşturmak  

1. İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], dağıtmak istediğiniz Office projesini açın.  

   Bu konu ile ilişkili VSTO eklenti örnekleri adlı bir proje içerir **Exceladdın**. Belge düzeyi özelleştirmesi örnekleri adlı bir proje içerir **ExcelWorkbook**. Bu konu, iki addan birini kullanarak, çözümünüzdeki Office projesine başvuracaktır.  

2. Menü çubuğunda, **dosya** > **Ekle** > **yeni proje**.  

   **Yeni Proje Ekle** iletişim kutusu açılır.  

3. Şablonlar bölmesinde, **diğer proje türleri**ve ardından **Kurulum ve dağıtım** şablonu.  

4. İçin proje türleri listesinde **Kurulum ve dağıtım**, seçin **InstallShield Limited Edition projesi**, projeyi adlandırın ve ardından **Tamam** düğmesi.  

   Oluşturduğunuz InstallShield Kurulum projesi çözümünüzde görünür.  

   Bu konu için örnek adlı bir kurulum projesi içeren **Officeaddınsetup**. Bu konu, aynı adı kullanarak, çözümünüzdeki Kurulum projesine başvuracaktır.  


## <a name="Add"></a>Proje çıktısı ekleme  
Yapılandırdığınız **Officeaddınsetup** Office projenizin çıktısını dahil etmek için proje. VSTO eklentisi projeleri için proje çıktısı yalnızca çözüm derlemesidir. Belge düzeyi özelleştirme projeleri için proje çıktısı yalnızca çözüm derlemesini yanı sıra belge dahildir.  


### <a name="to-add-the-project-output"></a>Proje çıktısı eklemek için  

1. İçinde **Çözüm Gezgini**, genişletme **Officeaddınsetup** proje düğümünü ve ardından **proje Yardımcısı** aşağıdaki çizimin gösterdiği dosya.  

   ![Proje Yardımcısı dosyası Çözüm Gezgini'nde](../vsto/media/installshield-projectassistant.png "Yardımcısı dosyası Çözüm Gezgini'ndeki proje")  

2. Menü çubuğunda, **görünümü** > **açık**.  

3. Sayfanın alt kısmında **proje Yardımcısı** sayfasında **uygulama dosyaları** aşağıdaki çizimin gösterdiği düğmesi.  

   ![Uygulama dosyaları düğmesi. ](../vsto/media/installshield-applicationfiles.png "Uygulama dosyaları düğmesini.")  

4. İçinde **uygulama dosyaları** sayfasında **proje çıktıları Ekle** düğmesi.  

5. İçinde **Visual Studio çıktı Seçici** iletişim kutusunda **birincil çıkışının** onay kutusunu işaretleyin ve ardından **Tamam** düğmesi.  


## <a name="AddD"></a>Dağıtım ve uygulama bildirimleri Ekle  

###  
1. İçinde **uygulama dosyaları** sayfasında **Add Files** düğmesi.  

2. İçinde **açık** iletişim kutusunda, çıktı dizinine gözatın **Exceladdın** proje.  

   Genellikle, çıktı dizini olan **bin\release** seçtiğiniz yapı yapılandırmasına bağlı olarak proje kök dizininin alt.  

3. Çıktı dizininde **Exceladdın.vsto** ve **Exceladdın.dll.manifest** dosyaları ve ardından **açık** düğmesi.  

   **Uygulama dosyaları** sayfası artık proje çıktı dosyasını, dağıtım bildirimini ve uygulama bildirimi aşağıdaki çizimde gösterildiği gibi içerir.  

   ![Kurulum projenizin çıkış dosyaları. ](../vsto/media/installshield-outputfiles.png "Kurulum projenizin çıktı dosyaları.")  


## <a name="Configure"></a>Bağımlı bileşenleri önkoşul olarak yapılandır  
Kurulum uygulamanız yalnızca aşağıdaki bileşenleri aynı çözümünüzün çalışması için gerekli olan tüm diğer bileşenleri içermelidir.  


- .NET Framework sürümü, Office çözümünüzün hedeflediği.  

- Office çalışma zamanı için Microsoft Visual Studio 2010 Araçları.  


### <a name="add-the-net-framework-4-or-the-net-framework-45-as-a-prerequisite"></a>Bir önkoşul olarak .NET Framework 4 veya .NET Framework 4.5 ekleme  

1. İçinde **Çözüm Gezgini**, genişletin **Officeaddınsetup** sırasıyla, proje düğümünü **uygulama verilerini belirtin** düğümünü seçip  **Yeniden dağıtılabilir dosyaları** aşağıdaki çizimin gösterdiği dosya.  

   ![Yeniden dağıtılabilir dosya Çözüm Gezgini'nde](../vsto/media/installshield-redistributablesfile.png "Çözüm Gezgini'nde dosyayı yeniden dağıtılabilir")  

2. Menü çubuğunda, **görünümü** > **açık**.  

   **Yeniden dağıtılabilir dosyaları** sayfası açılır.  

3. Yeniden dağıtılabilir bileşenler listesinde, .NET Framework sürümü için onay kutusunu seçin uygun, çözümünüzün hedeflediği.  

   Örneğin, çözümünüzün hedeflediği [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]seçin **Microsoft .NET Framework 4.5 Full** onay kutusu. Yeniden dağıtılabilir bileşeni yüklemek isteyip istemediğinizi soran bir iletişim kutusu görünebilir önce InstallShield gerektiren bileşeni önkoşul olarak ekleyebilirsiniz. Bu iletişim kutusu görüntülenmezse, bileşen bilgisayarınızda zaten mevcut.  

4. Bu iletişim kutusu görüntülenirse, seçin **Hayır** düğmesi.  


### <a name="AddToolsForOffice"></a>Visual Studio 2010 Tools for Office Runtime ekleme  
**Yeniden dağıtılabilir dosyaları** sayfa adında bir öğe içeriyor **Microsoft VSTO 2010 Runtime**, ancak çalışma zamanının daha eski bir sürümünü gösterir. Bu nedenle, en son sürüme başvuran bir yapılandırma dosyasını el ile oluşturabilirsiniz. Ardından bu dosyayı görünen tüm diğer öğeleri için yapılandırma dosyalarını ile aynı dizine koymanız gerekir **yeniden dağıtılabilir dosyaları** sayfası.  


#### <a name="to-add-the-visual-studio-2010-tools-for-office-runtime-as-a-prerequisite"></a>Office çalışma zamanı için Visual Studio 2010 Araçları bir önkoşul olarak eklemek için  

1. Not Defteri'ni açın ve aşağıdaki XML'i metin dosyasına yapıştırın.  


   ```xml  
   <?xml version="1.0" encoding="UTF-8"?>  
   <SetupPrereq>  
   <conditions>  
       <condition Type="32" Comparison="2" Path="HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4R" FileName="Version" ReturnValue="10.0.50903" Bits="2"></condition>  
   <condition Type="32" Comparison="2" Path="HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4R" FileName="Version" ReturnValue="10.0.50903" Bits="2"></condition>  
   </conditions>  
   <files>  
       <file LocalFile="<ISProductFolder>\SetupPrerequisites\VSTOR\vstor_redist.exe" URL="http://download.microsoft.com/download/C/0/0/C001737F-822B-48C2-8F6A-CDE13B4B9E9C/vstor_redist.exe" CheckSum="88b8aa9e8c90818f98c80ac4dd998b88" FileSize=" 0,40117912"></file>  
   </files>  
   <execute file="vstor_redist.exe" returncodetoreboot="1641,3010" requiresmsiengine="1">  
   </execute>  
   <properties Id="{15965040-56BB-49B8-A88F-3525C48D9BA8}" Description="This prerequisite installs the most recent version of the Microsoft Visual Studio 2010 Tools for Office Runtime." >  
   </properties>  

   </SetupPrereq>  
   ```  

2. Visual Studio'da bir GUID oluşturun. Üzerinde **Araçları** menüsünde seçin **GUID Oluştur**.  

3. İçinde **GUID Oluşturucu** programında **biçimi kayıt defteri** seçenek düğmesini **kopyalama** düğmesine ve ardından **çıkış** düğmesi.  

4. Not Defteri'nde, metnin yerine **uygulamanızın GUID Buraya** onun yerine GUID yapıştırma tarafından.  

   **&lt;Özellikleri&gt;** dosyanızın öğesi şuna benzer.  


   ```xml  
   <properties Id="{87989B73-21DC-4403-8FD1-0C68A41A6D8C}" Description="This prerequisite installs the most recent version of the Microsoft Visual Studio 2010 Tools for Office Runtime." >  
   </properties>  
   ```  

5. Notepad içinde menü çubuğunda seçin **dosya** > **Kaydet**.  

6. İçinde **Kaydet** iletişim kutusunda, Gözat, **Masaüstü** klasör.  

7. İçinde **farklı kaydetme türü** listesinde **tüm dosyalar (&#42;.&#42;)** .  

8. İçinde **dosya adı** kutusuna **Visual Studio 2010 Tools for Office Runtime.prq**ve ardından **Kaydet** düğmesi.  

   > [!NOTE]  
   >    Eklediğiniz emin **.prq** sonunda, bu dosyanın bir önkoşul dosyası olarak tanımlamak için dosya adı.  

9. Not Defteri'ni kapatın.  

10. Öğesinden, **Masaüstü** klasörü, kopyalama *Visual Studio 2010 Tools for Office Runtime.prq* aşağıdaki dizinlerin birine bilgisayarınızda dosyanın bulunduğu.  

   32 bit işletim sistemleri için: *%ProgramFiles%\InstallShield\2013LE\SetupPrerequisites\\*  

   64-bit işletim sistemleri için: *% ProgramFiles (x86) %\2013LE\SetupPrerequisites\\*  

11. İçinde **yeniden dağıtılabilir** sayfa InstallShield projesinin seçin **Yenile** aşağıdaki çizimde gösterildiği gibi yeniden dağıtılabilir bileşenler listesini yenilemek için düğme.  

   ![Yenile düğmesini. ](../vsto/media/installshield-refreshbutton.png "Yenile düğmesini.")  

12. Yeniden dağıtılabilir bileşenler listesinde seçin **Office çalışma zamanı için Visual Studio 2010 Araçları** onay kutusu.  

   Yeniden dağıtılabilir bileşeni yüklemek isteyip istemediğinizi soran bir iletişim kutusu de görünebilir. Bu iletişim kutusu görüntülenmezse, adımına atlayabilirsiniz [belirtin, kullanıcının bilgisayarında çözümü dağıtmak istediğiniz](#Location) bu konudaki.  

13. Bu iletişim kutusu görüntülenirse, seçin **Hayır** düğmesi.  


## <a name="Location"></a>Kullanıcının bilgisayarında çözümü yüklemek istediğiniz yeri belirtin  

1. İçinde **Çözüm Gezgini**, genişletin **Officeaddınsetup** düğümünü genişletin **kurulumunuzu düzenleyin** düğümünü seçip **genelbilgiler** dosya.  

2. Menü çubuğunda, **görünümü** > **açık**.  

3. Özellikler listesinde seçin **Gözat** düğmesinin yanındaki **INSTALLDIR** özelliği.  

4. İçinde **INSTALLDIR Ayarla** iletişim kutusunda, kullanıcının bilgisayarında çözümü yüklemek istediğiniz klasörü seçin.  

   > [!NOTE]  
   >    Dizinlerde de oluşturabilirsiniz **INSTALLDIR Ayarla** listede herhangi bir klasör için kısayol menüsünü açarak iletişim kutusu.  


## <a name="ConfigureRegistry"></a>Bir VSTO eklentisinin yapılandırın  
VSTO (bilgisayar başına) bilgisayarın tüm kullanıcıları için veya yalnızca (kullanıcı başına) yüklemeyi gerçekleştiren kullanıcı için yüklenecek eklenti isteyip istemediğinizi belirtebilirsiniz.  

Bilgisayar başına yüklemeleri desteklemek istiyorsanız, iki ayrı yükleyici oluşturun. Kullanıcının çalıştırdığı Office sürümüne (32-bit ve 64-bit) veya Windows sürümüne (32-bit ve 64-bit) tabanlı yükleyicileri bölebilirsiniz.  

Kullanıcı yüklemeleri Office ya da Windows sürümünden bağımsız olarak yalnızca bir yükleyici gerektirir.  

> [!NOTE]  
> Bu bölüm, yalnızca bir VSTO eklentisi dağıtıyorsanız geçerlidir. Belge düzeyinde bir özelleştirme dağıtımı yapıyorsanız hemen gidebilirsiniz [bir belge düzeyinde özelleştirmeyi Yapılandır](#ConfigureDocument) bölümü.  


### <a name="to-specify-whether-you-want-to-support-per-user-or-per-computer-installations"></a>Kullanıcı başına veya bilgisayar başına yüklemeleri desteklemek istediğinizi belirtmek için  

1. İçinde **Çözüm Gezgini**, genişletin **Officeaddınsetup** sırasıyla, proje düğümünü **kurulumunuzu** düğümünü seçip **genel bilgiler**  dosya.  

2. Menü çubuğunda, **görünümü** > **açık**.  

   Kurulum projesinin özellikleri görünür.  

3. Listesinde **AllUSERS** özelliği, bu çözüm, bilgisayarın tüm kullanıcıları için veya yalnızca çözümü yükleyen kullanıcı için yüklü olmasını isteyip istemediğinizi belirtin.  

   Geçerli kullanıcı için VSTO eklentisi yüklemek için seçin **ALLUSERS = "" (kullanıcı başına yükleme)**. Bilgisayarın tüm kullanıcıları için VSTO eklentisi yüklemek için seçin **ALLUSERS = 1 (makine başına yükleme)**  

   Sonraki yordamda, bulmak ve VSTO eklentisi yükleme Office uygulamasını etkinleştirmek için kayıt defteri anahtarları oluşturacaksınız. Bkz: [VSTO eklentileri için kayıt defteri girdileri](../vsto/registry-entries-for-vsto-add-ins.md).  


### <a name="to-create-registry-keys"></a>Kayıt defteri anahtarları oluşturma  

1. İçinde **Çözüm Gezgini**, seçin **proje Yardımcısı** düğümü.  

   Menü çubuğunda, **görünümü** > **açık**.  

2. Sayfanın alt kısmında **proje Yardımcısı** sayfasında **uygulama kayıt defteri** aşağıdaki çizimin gösterdiği düğmesi.  

   ![Uygulama kayıt defteri düğmesi. ](../vsto/media/installshield-applicationregistry.gif "Uygulama kayıt defteri düğmesi.")  

   **Uygulama kayıt defteri** sayfası görüntülenir.  

3. Altında **uygulamanızın yükleyeceği kayıt defteri verilerini yapılandırmak istiyor musunuz?**, seçin **Evet** seçenek düğmesini.  

4. İçinde **hedef bilgisayarın kayıt defteri görünümü** listesinde, oluşturmak istediğiniz yükleyicinin türünü etkinleştiren tuş hiyerarşisini ekleyin.  

   Bu bölümde yapılandırdığınız yol olup, kullanıcı başına yükleyici veya bir bilgisayar başına yükleyici oluşturduğunuza bağlıdır.  

   **Kullanıcı başına yükleyici**  

   **HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**  

   **Office sürümüne dayanan bilgisayar başına yükleyiciler**  



| Office sürümü<br /><br /> | InstallShield yapılandırma yolu<br /><br /> |
|----------------------------| - |
| 32 bit:<br /><br /> | **HKEY_LOCAL_MACHINE\Software(32-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |
| 64 bit<br /><br /> | **HKEY_LOCAL_MACHINE\Software(64-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |

   **Windows sürümüne dayanan bilgisayar başına yükleyiciler**  



| Windows sürümü<br /><br /> | InstallShield yapılandırma yolu<br /><br /> |
|-----------------------------| - |
| 32 bit:<br /><br /> | **HKEY_LOCAL_MACHINE\Software(32-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |
| 64 bit<br /><br /> | **HKEY_LOCAL_MACHINE\Software(32-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br />**HKEY_LOCAL_MACHINE\Software(64-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |

   > [!NOTE]  
   >    Office'in 32 bit ve 64-bit sürümleri, 64 bit Windows çalıştıran bir bilgisayarda çalıştırmak kullanıcılar için mümkün olduğu için 64 bit Windows için bir yükleyici iki kayıt defteri yolu gerektirir.  

   > [!NOTE]  
   >    En iyi uygulama, VSTO eklenti adını şirketinizin adı ile başlatın. Bu kural, anahtarın benzersiz olması ve VSTO eklentisi başka bir tedarikçi Çakışma olasılığını düşürür şansını artırır. Aynı ada sahip eklentiler, örneğin, diğer işlemelerin kayıt anahtarlarının üzerine yazabilir. Bu yaklaşım, anahtarın benzersiz olacak ancak potansiyel ad çakışmalarını azaltabilir garanti edemez.  

5. Anahtarların hiyerarşisini oluşturduktan sonra kısayol menüsünü açın **Samplecompany.exceladdın** anahtarı **yeni**ve ardından **dize değeri**.  

   Yeni bir dize değeri görünür **hedef bilgisayarın kayıt defteri verisi** listesi. Dize değerinin adı vurgulanır böylece yeniden adlandırabilirsiniz.  

6. Değerine Yeniden Adlandır **açıklama**.  

7. Aşağıdaki değerleri oluşturmak için bu işlemi yineleyin.  



|Değer türü<br /><br />|Ad<br /><br />|  
|--------------|--------|  
|Dize değeri<br /><br />|**FriendlyName**<br /><br />|  
|DWORD değeri<br /><br />|**LoadBehavior**<br /><br />|  
|Dize değeri<br /><br />|**Bildirimi**<br /><br />|  

8. Kısayol menüsünü açın **açıklama** değeri ve ardından **Değiştir**.  

   **Verilerini düzenleme** iletişim kutusu görüntülenir.  

9. İçinde **değer verisi** metin kutusuna **Excel Demo Add-ın**ve ardından **Tamam** düğmesi.  

   Bu açıklama kullanıcı Office uygulamasını açtığında görünür **seçenekleri** iletişim kutusunda, daha sonra **eklentileri** bölmesinde seçer VSTO eklentisi.  

10. Kısayol menüsünü açın **FriendlyName** değeri ve ardından **Değiştir**.  

   **Verilerini düzenleme** iletişim kutusu görüntülenir.  

11. İçinde **değer verisi** metin kutusuna **Excel Demo Add-ın**ve ardından **Tamam** düğmesi.  

   Bu dize görünür **COM eklentileri** Office uygulamasında iletişim kutusu. Varsayılan olarak, dize değeri VSTO eklenti kimliğidir  

12. Kısayol menüsünü açın **LoadBehavior** değeri ve ardından **Değiştir**.  

   **Verilerini düzenleme** iletişim kutusu görüntülenir.  

13. İçinde **değer verisi** metin kutusuna **3**ve ardından **Tamam** düğmesi.  

   Uygulama başlatıldığında 3 değeri VSTO eklentisi yükler. LoadBehavior değerleri hakkında daha fazla bilgi için bkz. [VSTO eklentileri için kayıt defteri girdileri](../vsto/registry-entries-for-vsto-add-ins.md).  

14. Kısayol menüsünü açın **bildirim** değeri ve ardından **Değiştir**.  

   **Verilerini düzenleme** iletişim kutusu görüntülenir.  

15. İçinde **değer verisi** metin kutusuna **File:///[INSTALLDIR]ExcelAddIn.vsto|vstolocal**ve ardından **Tamam** düğmesi.  

   Office çalışma zamanı için Visual Studio 2010 Araçları, dağıtım bildirimini bulmak için bu yolu kullanır. **[INSTALLDIR]** bu yolunun bir bölümü eşleyen bir makrodur **INSTALLDIR** özelliğinde **genel bilgiler** InstallShield Kurulum projenizin özellik sayfası. Bu özellik, VSTO eklenti yüklemek için hedef bilgisayarda konumu belirtir. **| Vstolocal** soneki çözümünüzün ClickOnce ön yükleme klasöründen yüklenmesini sağlar.  

> [!IMPORTANT]  
> VSTO eklentisi için Outlook içinde bir özel form bölgesi oluşturursanız, Outlook ile bölgeleri kaydetmek için daha fazla kayıt defteri girdileri oluşturmanız gerekir. Daha fazla bilgi için [kayıt defteri girdileri Outlook form bölgeleri](../vsto/registry-entries-for-vsto-add-ins.md#OutlookEntries).  


## <a name="ConfigureDocument"></a>Bir belge düzeyinde özelleştirmeyi Yapılandır  
Bu bölüm yalnızca belge düzeyinde özelleştirme yaptığınızda geçerlidir. Bir VSTO eklenti dağıtımı yapıyorsanız, hemen gidebilirsiniz [Kurulum projesi oluştur](#Build) bölümü.  

Belge düzeyi özelleştirmeleri, kayıt defteri anahtarlarını kullanmaz. Bunun yerine, özel belge özellikleri dağıtım bildiriminin konumunu içerir.  

Özel özellikleri değiştirmek için belge düzeyinde özelleştirmeyi belgeden kaldıran, ilgili özellikleri değiştiren ve ardından özelleştirmeyi belgeye etkilenebilecek bir program oluşturun. Ardından programı çalıştıran özel bir eylem oluşturun ve bu eylemi kurulum projenize ekleyin.  

### <a name="to-create-a-program-that-modifies-document-properties"></a>Belge özelliklerini değiştiren bir program oluşturmak için  

1. Menü çubuğunda, **dosya** > **Ekle** > **yeni proje**.  

   **Yeni Proje Ekle** iletişim kutusu görüntülenir.  

2. Şablonlar bölmesinde, kullanmak istediğiniz dil için düğümü seçin **Windows** klasör.  

3. İçin proje türleri listesinde **Windows**, seçin **konsol uygulaması** şablonu.  

4. Projeyi adlandırın **SetExcelDocumentProperties**ve ardından **Tamam** düğmesi.  

5. İçinde **Çözüm Gezgini**, seçin **tüm dosyaları göster** ilişkin kısayol menüsünü açın, düğme **SetExcelDocumentProperties** proje düğümünü ve ardından **Başvurusu Ekle**.  

6. İçinde **başvuru Yöneticisi** iletişim kutusunda **uzantıları** sekmesine ve ardından aşağıdaki derlemeler yanındaki onay kutusunu seçin ve ardından **Tamam** düğmesi.  


   - Microsoft.VisualStudio.Tools.Applications.Runtime  

   - Microsoft.VisualStudio.Tools.Applications.ServerDocument  

7. İçinde **Çözüm Gezgini**, seçin **Program.cs** dosyasını (C# uygulamalar için) veya **Module1.vb** dosyasını (Visual Basic uygulamaları).  

8. Menü çubuğunda, **görünümü** > **açık**.  

9. Tüm dosya içeriğini aşağıdaki kodla değiştirin.  

[!code-vb[Trin_CustomAction#1](../vsto/codesnippet/VisualBasic/setexceldocumentproperties/module1.vb#1)]
[!code-csharp[Trin_CustomAction#1](../vsto/codesnippet/CSharp/setexceldocumentproperties/program.cs#1)]  

10. Projeyi derle.  


### <a name="to-add-a-custom-action-that-runs-your-program"></a>Programınızı çalıştıran özel bir eylem eklemek için  

1. İçinde **Çözüm Gezgini**, genişletme **Officeaddınsetup** proje düğümünü ve ardından **proje Yardımcısı** aşağıdaki çizimin gösterdiği dosya.  

   ![Proje Yardımcısı dosyası Çözüm Gezgini'nde](../vsto/media/installshield-projectassistant.png "Yardımcısı dosyası Çözüm Gezgini'ndeki proje")  

2. Menü çubuğunda, **görünümü** > **açık**.  

3. Sayfanın alt kısmında **proje Yardımcısı** sayfasında **uygulama dosyaları** aşağıdaki çizimin gösterdiği düğmesi.  

   ![Uygulama dosyaları düğmesi. ](../vsto/media/installshield-applicationfiles.png "Uygulama dosyaları düğmesini.")  

4. İçinde **uygulama dosyaları** sayfasında **proje çıktıları Ekle** düğmesi.  

   **Visual Studio çıktı Seçici** iletişim kutusu görüntülenir.  

5. Altında **SetExcelDocumentProperties** düğümünü **birincil çıkışının** onay kutusunu işaretleyin ve ardından **Tamam** düğmesi.  

6. İçinde **Çözüm Gezgini**altında **Officeaddınsetup** düğümünü genişletin **Kurulum gereksinimlerini tanımlayın ve eylemleri** düğümünü seçip **özel Eylemler** klasör.  

7. Menü çubuğunda, **görünümü** > **açık**.  

   Olayların bir listesi için ekranın kenarındaki bölmede görünür.  

   > [!NOTE]  
   >    Bu listede yalnızca birkaç olayları InstallShield Limited Edition ile kullanılabilir. Bu yordamda, kullanarak programı çalıştıracaksınız **Kurulum başarıyla tamamlandıktan sonra iletişim** olay.  

8. Olaylar listesinde altında **yükleme sırasındaki özel eylemler**, kısayol menüsünü açın **Kurulum başarıyla tamamlandıktan sonra iletişim** olay seçip **yeni EXE**.  

   Adlı bir özel eylem **NewCustomAction1** altında görünür **Kurulum başarıyla tamamlandıktan sonra iletişim** olay. Özel bir eylem için özellik kümesi olayın yanındaki bölmede görünür.  

   > [!IMPORTANT]  
   >    İki **Kurulum başarıyla tamamlandıktan sonra iletişim** olayları, olaylar listesinde görünür. Örneğini seçtiğinizden emin olun **Kurulum başarıyla tamamlandıktan sonra iletişim** altında görüntülenen olay **yükleme sırasındaki özel eylemler** düğümü.  

9. Listesinde **kaynak konumu** özelliği seçin **ürünle birlikte yüklenen**.  

10. Seçin **Gözat** düğmesinin yanındaki **dosya adı** özelliği.  

11. İçinde **bir hedef dosya için Gözat** iletişim kutusunda, Gözat **SetExcelDocumentProperties.Primary.output** dosya ve ardından **açık** düğmesi.  

    Bu dosyanın konumu için belirttiğiniz klasöre bağlıdır **INSTALLDIR** Kurulum projesinin özellik. Örneğin, bu özellik adlı bir klasöre ayarlarsanız **[PersonalFolder] DemoWorkbookApp**, bulabilirsiniz **SetExcelDocumentProperties.Primary.output** atarak dosya **[ ProgramFilesFolder] \DemoWorkbookApp**.  

    Sonraki birkaç adımda belgenin çözüm Kimliğini alın ve sonra bu kimliği olacak konsol uygulamasına parametre olarak geçirin. Ayrıca, konumu belgenin, dağıtım bildirimini ve belge derlemesini de ileteceksiniz.  

12. Kısayol menüsünü açın **ExcelWorkbook** proje ve ardından **klasörü Windows Gezgini'nde Aç** veya **klasörü dosya Gezgini'nde Aç** işletim bağlı olarak sistemi.  

    Çözümünüzü içeren klasörü açar.  

13. Çözümünüzün proje dosyasını Not Defteri'nde açın. Visual Basic projeleri için dosya adıdır. *ExcelWorkbook.vbproj*. C# projeleri için dosya adıdır. *ExcelWorkbook.csproj*.  

14. Proje dosyasında arayın **&lt;SolutionID&gt;** öğesi, değerini panoya kopyalayın ve Not Defteri'ni kapatın.  

    Bu değeri konsol uygulamasına parametre olarak geçirin.  

15. Özellikler sayfasında **NewCustomAction1**ayarlayın **komut satırı** özelliğini aşağıdaki metin satırına.  


   ```cmd
   /assemblyLocation="[INSTALLDIR]ExcelWorkbook.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbook.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbook.xlsx" /solutionID="Your Solution ID"  
   ```  

16. Değiştirin **bilgisayarınızı çözüm kimliği** Pano'ya kopyaladığınız çözüm kimliği.  

   > [!IMPORTANT]  
   >    Bu özel eylemin çalıştırdığı konsol uygulaması [INSTALLDIR] dizinindeki belgelere erişebildiğini doğrulayın için yükleyicinizi sınayın. Kullanıcının bilgisayarındaki bazı dizinler (örneğin, Program Files dizini) yönetici erişimi gerektirebilir. Yönetici erişimi gerektiren bir dizine çözümünüzü dağıtıyorsanız, açılmalıdır **özellikleri** iletişim kutusunun *setup.exe* dosya öğesini **Uyumluluk** sekmesine tıklayın ve ardından **bu programı yönetici olarak çalıştır** yükleyiciyi dağıtmadan önce onay kutusu. Kullanıcıların Kurulum programını yönetici izinleriyle çalıştırmak istemiyorsanız, [INSTALLDIR] özelliğini kullanıcının büyük olasılıkla olan erişim dizine ayarlamak gibi **belgeleri** dizin. Daha fazla bilgi için [belirtin kullanıcının bilgisayarında çözümü yüklemek istediğiniz](#Location) bu konudaki.  


## <a name="Build"></a>Kurulum projesi oluştur  

1. İçinde **Çözüm Gezgini**, genişletin **hazırlamak için yayın** düğümünü seçip **yayınlar** dosya.  

2. Menü çubuğunda, **görünümü** > **açık**.  

   **Yapılar** Gezgini açılır yan bölmede, böylece oluşturmak istediğiniz sürümün türünü seçebilirsiniz.  

3. İçinde **yapılar** Gezgini seçin **Singleımage** klasör.  

4. Yanındaki bölmede **yapılar** Gezgini seçin **Setup.exe** sekmesi.  

5. İçinde **Setup.exe** özellik sayfası, gelen **InstallShield Önkoşullar konumu** listesinde **Web'den indir**.  

6. Menü çubuğunda, **derleme** > **Configuration Manager**.  

7. İçinde **etkin çözüm yapılandırması** listesinde **Singleımage**.  

8. İçinde **proje bağlamları** tablosu **yapılandırma** sütununun **Officeaddınsetup** projesinin **Singleımage**ve ardından seçin **Kapat** düğmesi.  

9. Menü çubuğunda, **derleme** > **Officeaddınsetup**.  

   Derleme tamamlandıktan sonra bulabilirsiniz *setup.exe* dosya **Officeaddınsetup** proje şu konumda: <em>OfficeAddInSetupProjectRoot</em> **\OfficeAddInSetup\Express\SingleImage\DiskImages\DISK1\\**  


## <a name="see-also"></a>Ayrıca bkz.  
[Office çözüm dağıtım önkoşulları](https://msdn.microsoft.com/library/9f672809-43a3-40a1-9057-397ce3b5126e)  
[Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)  
[VSTO eklentileri için kayıt defteri girişleri](../vsto/registry-entries-for-vsto-add-ins.md)  
[Özel belge özelliklerine genel bakış](../vsto/custom-document-properties-overview.md)  
[Office çözümlerine güven verme](../vsto/granting-trust-to-office-solutions.md)  
[Belgelere güven verme](../vsto/granting-trust-to-documents.md)  
[Windows Installer kullanarak Office çözümü için Visual Studio 2010 araçlarını dağıtma](http://go.microsoft.com/fwlink/?LinkId=201807)  
