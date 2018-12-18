---
title: ClickOnce kullanarak Office çözümü dağıtma
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, deploying solutions
- ClickOnce deployment [Office development in Visual Studio], deploying solutions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e46a0bdc23ee16c4821d3da751d5a90aa62a14c3
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673074"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>ClickOnce kullanarak Office çözümü dağıtma
  ClickOnce kullanırsanız Office çözümünüzü daha az sayıda adımla dağıtabilirsiniz. Güncelleştirmeleri yayımlarsanız, çözümünüz bunları otomatik olarak algılar ve yükler. Bununla birlikte, ClickOnce, çözümünüzü bir bilgisayarın her kullanıcısı için ayrı ayrı yüklemenizi gerektirir. Bu nedenle, Windows Installer kullanmayı düşünmeniz gerekir (*.msi*) aynı bilgisayarda çözümünüzü birden fazla kullanıcı çalıştıracaksa.  

## <a name="in-this-topic"></a>Bu konuda  

- [Çözümü yayımlama](#Publish)  

- [Nasıl çözüme güven kazandırmak istediğinize karar verme](#Trust)  

- [Kullanıcıların çözümü yüklemesine yardımcı olma](#Helping)  

- [Bir çözümün belgesini son kullanıcının bilgisayarına koyma (yalnızca belge düzeyinde özelleştirmeler) yerleştirin.](#Put)  

- [Bir çözümün belgesini SharePoint (yalnızca belge düzeyinde özelleştirmeler) çalıştıran bir sunucuya koyma yerleştirin](#SharePoint)  

- [Özel bir yükleyici oluşturma](#Custom)  

- [Güncelleştirme yayımlama](#Update)  

- [Bir çözümün yükleme konumunu değiştirme](#Location)  

- [Bir çözümü önceki bir sürüme geri alma](#Roll)  

  Bir Windows Installer dosyası oluşturarak bir Office çözümünü dağıtma hakkında daha fazla bilgi için bkz. [Windows Installer kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  

##  <a name="Publish"></a> Çözümü yayımlama  
 Çözümünüzü kullanarak yayımlayabilirsiniz **Yayımlama Sihirbazı** veya **Proje Tasarımcısı**. Bu yordamda kullanacağınız **Proje Tasarımcısı** çünkü tam bir set Yayımlama seçenekleri sağlar. Bkz: [yayımlama sihirbazını &#40;Visual Studio'da Office geliştirme&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).  

#### <a name="to-publish-the-solution"></a>Çözümü yayımlamak için  

1. İçinde **Çözüm Gezgini**, projeniz için düğümü seçin.  

2. Menü çubuğunda, **proje**, *ProjectName* **özellikleri**.  

3. İçinde **Proje Tasarımcısı**, seçin **Yayımla** sekmesinde, aşağıdaki resimde gösterilmektedir.  

    ![Yayımlama sekmesindeki Proje Tasarımcısı'nın](../vsto/media/vsto-publishtab.png "yayımlama sekmesindeki Proje Tasarımcısı")  

4. İçinde **yayımlama klasörü konumu (ftp sunucusu veya dosya yolu)** kutusunda, istediğiniz klasörün yolunu girin **Proje Tasarımcısı** çözüm dosyalarını kopyalamak için.  

    Aşağıdaki yol türlerinden herhangi birini girebilirsiniz.  

   -   Bir yerel yol (örneğin, *C:\FolderName\FolderName*).  

   -   Bir ağınızdaki bir klasörün Tekdüzen Adlandırma Kuralı (UNC) yolu (örneğin,  *\\\ServerName\FolderName*).  

   -   Göreli bir yol (örneğin, *yayınklasörü\\*, hangi proje varsayılan olarak yayımlanır klasör).  

5. İçinde **yükleme klasörü URL'si** kutusunda, son kullanıcıların nerede çözümünüzü konumun tam yolunu girin.  

    Konumu henüz bilmiyorsanız, herhangi bir şey bu alana girmeyin. Varsayılan olarak, ClickOnce, kullanıcılarınızın çözümü yüklediği klasörde güncelleştirmeleri arar.  

6. Seçin **önkoşulları** düğmesi.  

7. İçinde **önkoşulları** iletişim kutusunda **Önkoşul bileşenlerini yüklemek için Kurulum programını Oluştur** onay kutusu seçilidir.  

8. İçinde **yüklenecek önkoşulları seçin** listesinde, onay kutularını seçin **Windows Installer 4.5** ve uygun .NET Framework paketi.  

    Örneğin, çözümünüzün hedeflediği [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], onay kutularını işaretleyin **Windows Installer 4.5** ve **Microsoft .NET Framework 4.5 Full**.  

9. Çözümünüz .NET Framework 4.5 hedefliyse, ayrıca seçin **Office çalışma zamanı için Visual Studio 2010 Araçları** onay kutusu.  

    > [!NOTE]  
    >  Varsayılan olarak, bu onay kutusu görünmez. Bu onay kutusunu göstermek için bir Önyükleyici paketi oluşturmanız gerekir. Bkz: [Visual Studio 2012 ile bir önyükleyici paketi için bir Office 2013 VSTO eklentisi oluşturma](create-vsto-add-ins-for-office-by-using-visual-studio.md).  

10. Altında **Önkoşullar için yükleme konumunu belirtin**, görüntülenen ve ardından seçeneklerden birini **Tamam** düğmesi.  

     Aşağıdaki tabloda her bir seçenek açıklanmaktadır.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |**Bileşen satıcısının web sitesinden önkoşulları karşıdan yükleyin**|Kullanıcıdan, bu önkoşulları satıcının sitesinden indirmesi ve yüklemesi istenir.|  
    |**Uygulamamla aynı konumdan önkoşulları karşıdan yükleyin**|Önkoşul yazılımı çözümle birlikte yüklenir. Bu seçeneği tercih ederseniz, Visual Studio sizin için önkoşul paketlerinin tümünü yayımlama konumuna kopyalar. Bu seçeneğin çalışması için önkoşul paketleri geliştirme bilgisayarında olmalıdır.|  
    |**Aşağıdaki konumdan önkoşulları karşıdan yükleyin**|Visual Studio tüm önkoşul paketlerini belirttiğiniz konuma kopyalar ve bunları çözümle birlikte yükler.|  

     Bkz: [Önkoşullar iletişim kutusu](/visualstudio/ide/reference/prerequisites-dialog-box).  

11. Seçin **güncelleştirmeleri** düğmesi, her bir son kullanıcı VSTO eklenti veya özelleştirme güncelleştirmeleri denetlemek ve ardından istediğiniz sıklığı belirtin **Tamam** düğmesi.  

    > [!NOTE]  
    >  Bir CD veya çıkarılabilir sürücü kullanarak dağıtım yapıyorsanız seçin **asla güncelleştirmeleri denetleme** seçenek düğmesini.  

     Bir güncelleştirmenin nasıl yayımlanacağı hakkında daha fazla bilgi için bkz. [güncelleştirme yayımlama](#Update).  

12. Seçin **seçenekleri** düğmesi, seçenekleri gözden **seçenekleri** iletişim kutusuna ve ardından **Tamam** düğmesi.  

13. Seçin **Şimdi Yayımla** düğmesi.  

     Visual Studio, bu yordamda daha önce belirttiğiniz yayımlama klasörüne aşağıdaki klasörleri ve dosyaları ekler.  

    - **Uygulama dosyaları** klasör.  

    - Kurulum programı.  

    - En son sürümün dağıtım bildirimine işaret eden bir dağıtım bildirimi.  

      **Uygulama dosyaları** yayımladığınız her sürüm için bir alt klasör içerir. Her bir sürüme özgü alt klasörde aşağıdaki dosyalar bulunur.  

    - Uygulama bildirimi.  

    - Dağıtım bildirimi.  

    - Özelleştirme derlemeleri.  

      Aşağıdaki çizimde, Outlook VSTO eklenti için yayımlama klasörünün yapısı gösterilmektedir.  

      ![Klasör yapısını yayımlama](../vsto/media/publishfolderstructure.png "klasör yapısını yayımlama")  

    > [!NOTE]  
    >  ClickOnce ekler *.deploy* derlemelere uzantısı böylece güvenli bir Internet Information Services (IIS) yüklemesi, güvenli olmayan bir uzantı nedeniyle dosyaları engellemez. Kullanıcı çözümü yüklediğinde ClickOnce kaldırır *.deploy* uzantısı.  

14. Çözüm dosyalarını, bu yordamda daha önce belirttiğiniz yükleme konumuna kopyalayın.  

##  <a name="Trust"></a> Nasıl çözüme güven kazandırmak istediğinize karar verme  
 Bir çözümün kullanıcı bilgisayarları üzerinde çalışması için önce, sizin güven kazandırmanız ya da kullanıcıların çözümü yükledikleri sırada bir güvenlik istemine yanıt vermeleri gerekir. Çözüme güven kazandırmak için, bilinen ve güvenilir bir yayımcıyı tanımlayan bir sertifika kullanarak bildirimleri imzalayın. Bkz: [uygulama ve dağıtım bildirimlerini imzalayarak çözüme güvenin](../vsto/granting-trust-to-office-solutions.md#Signing).  

 Bir belge düzeyi özelleştirmeyi dağıtıyorsanız ve belgeyi kullanıcının bilgisayarında bir klasöre yerleştirin veya belgeyi bir SharePoint sitesinde kullanılabilir hale getirmek istiyorsanız, Office belgesinin konumunu güvendiğinden emin olun. Bkz: [belgelere güven verme](../vsto/granting-trust-to-documents.md).  

##  <a name="Helping"></a> Kullanıcıların çözümü yüklemesine yardımcı olma  
 Kullanıcılar kurulum programını çalıştırarak, dağıtım bildirimini açarak veya belge düzeyinde bir özelleştirme olması durumunda belgeyi doğrudan açarak çözümü yükleyebilirler. En iyi uygulama olarak, kullanıcılar çözümünüzü kurulum programını kullanarak yüklemelidir. Diğer iki yaklaşım önkoşul yazılımlarının yüklendiğinden emin garanti etmez. Kullanıcılar belgeyi yükleme konumundan açmak isterse, Office uygulamasının Güven Merkezi'nde bu konumu güvenilir konumlar listesine eklemeleri gerekir.  

### <a name="opening-the-document-of-a-document-level-customization"></a>Belge düzeyinde bir özelleştirmenin belgesini açma  
 Kullanıcılar, belge düzeyinde bir özelleştirmenin belgesini doğrudan yükleme konumundan açabilirler veya belgeyi kendi yerel bilgisayarlarına kopyalayıp sonra bu kopyayı açabilirler.  

 En iyi uygulama olarak, kullanıcılar belgenin bir kopyasını kendi bilgisayarlarında açmalıdır; böylece birden fazla kullanıcı aynı anda aynı kopyayı açmaya çalışmaz. Bu uygulamayı zorunlu tutmak için, kurulum programınızı, belgeyi kullanıcı bilgisayarlarına kopyalayacak şekilde yapılandırabilirsiniz. Bkz: [bir çözümün belgesini son kullanıcının bilgisayarına koyma (yalnızca belge düzeyinde özelleştirmeler) & lt;](#Put).  

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Bir IIS Web sitesinden dağıtım bildirimini açarak çözümü yükleme  
 Kullanıcılar, web'ten dağıtım bildirimini açmak suretiyle bir Office çözümünü yükleyebilirler. Ancak, güvenli bir Internet Information Services (IIS) yüklemesi olan dosyalar engeller *.vsto* uzantısı. Bir Office çözümünü IIS kullanarak dağıtabilmeniz için önce MIME türü IIS'de tanımlanmalıdır.  

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>IIS 6.0'a .vsto MIME türünü eklemek için  

1.  IIS 6.0 çalıştıran sunucuda seçin **Başlat** > **tüm programlar** > **Yönetimsel Araçlar**  >   **Internet Information Services (IIS) Yöneticisi**. 

2.  Bilgisayar adı seçin **Web siteleri** klasörünü veya yapılandırdığınız web sitesi.  

3.  Menü çubuğunda, **eylem** > **özellikleri**.  

4.  Üzerinde **HTTP üstbilgileri** sekmesini, **MIME türleri** düğmesi.  

5.  İçinde **MIME türleri** penceresinde seçin **yeni** düğmesi.  

6.  İçinde **MIME türü** penceresinde girin **.vsto** uzantısını girin **application/x-ms-vsto** MIME olarak yazın ve ardından yeni ayarları uygulayın.  

    > [!NOTE]  
    >  Değişikliklerin etkili olması için, World Wide Web Yayımlama Hizmeti'ni yeniden başlatmalı veya çalışan işleminin tekrar geri dönmesini beklemelisiniz. Sonra tarayıcının disk önbelleğini temizlemeli ve açmayı denerseniz *.vsto* yeniden dosya.  

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>IIS 7.0 .vsto MIME türünü eklemek için  

1.  IIS 7.0 çalıştıran sunucuda seçin **Başlat** > **tüm programlar** > **Donatılar**.  

2.  Kısayol menüsünü açın **komut istemi**ve ardından **yönetici olarak çalıştır.**  

3.  İçinde **açık** kutusuna aşağıdaki yolu girin ve ardından **Tamam** düğmesi.  

    ```cmd
    %windir%\system32\inetsrv   
    ```  

4.  Aşağıdaki komutu girin ve ardından yeni ayarları uygulayın.  

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']  
    ```  

    > [!NOTE]  
    >  Değişikliklerin etkili olması için, World Wide Web Yayımlama Hizmeti'ni yeniden başlatmalı veya çalışan işleminin tekrar geri dönmesini beklemelisiniz. Sonra tarayıcının disk önbelleğini temizlemeli ve açmayı denerseniz *.vsto* yeniden dosya.  

##  <a name="Put"></a> Bir çözümün belgesini son kullanıcının bilgisayarına koyma (yalnızca belge düzeyinde özelleştirmeler) yerleştirin.  
 Çözümünüzün belgesini, son kullanıcının bilgisayarına bunları için dağıtım sonrası eylemi oluşturarak kopyalayabilirsiniz. Böylece, çözümünüzü yükledikten sonra belgeyi kendi bilgisayarlarına yükleme konumundan el ile kopyalamak kullanıcı yok. Dağıtım sonrası eylemi tanımlayan bir sınıf oluşturun, derleme ve çözüm yayımlama, uygulama bildirimini değiştirin ve uygulama ve dağıtım bildirimini yeniden imzalamanız gerekecektir.  

 Aşağıdaki yordamlarda projenizin adına olduğunu varsayın **ExcelWorkbook** ve çözümü yayımlama **C:\publish** bilgisayarınızda dizin.  

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Dağıtım sonrası eylemi tanımlayan bir sınıf oluşturma  

1. Menü çubuğunda, **dosya** > **Ekle** > **yeni proje**.  

2. İçinde **Yeni Proje Ekle** iletişim kutusundaki **yüklü şablonlar** bölmesinde seçin **Windows** klasör.  

3. İçinde **şablonları** bölmesinde seçin **sınıf kitaplığı** şablonu.  

4. İçinde **adı** alanına **FileCopyPDA**ve ardından **Tamam** düğmesi.  

5. İçinde **Çözüm Gezgini**, seçin **FileCopyPDA** proje.  

6. Menü çubuğunda, **proje** > **Başvuru Ekle**.  

7. Üzerinde **.NET** sekmesinde, başvuruları eklemek `Microsoft.VisualStudio.Tools.Applications.Runtime` ve `Microsoft.VisualStudio.Tools.Applications.ServerDocument`.  

8. Sınıfı Yeniden Adlandır `FileCopyPDA`ve sonra dosyanın içeriğini kod ile değiştirin. Bu kod aşağıdaki görevleri gerçekleştirir:  

   - Belgeyi kullanıcının masaüstüne kopyalar.  

   - Dağıtım bildirimi için tam olarak nitelenmiş bir yola göreli bir yol _AssemblyLocation özelliğini değiştirir.  

   - Kullanıcı çözümü kaldırırsa, dosyayı siler.  

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]  

### <a name="build-and-publish-the-solution"></a>Çözümü derleme ve yayımlama  

1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **FileCopyPDA** proje ve ardından **yapı**.  

2.  Kısayol menüsünü açın **ExcelWorkbook** proje ve ardından **yapı**.  

3.  Kısayol menüsünü açın **ExcelWorkbook** proje ve ardından **Başvuru Ekle**.  

4.  İçinde **Başvuru Ekle** iletişim kutusunda **projeleri** sekmesini, **FileCopyPDA**ve ardından **Tamam** düğmesi.  

5.  İçinde **Çözüm Gezgini**, seçin **ExcelWorkbook** proje.  

6.  Menü çubuğunda **proje** > **yeni klasör**.  

7.  ENTER **veri**ve ardından **Enter** anahtarı.  

8.  İçinde **Çözüm Gezgini**, seçin **veri** klasör.  

9. Menü çubuğunda, **proje** > **varolan öğeyi Ekle**.  

10. İçinde **varolan öğeyi Ekle** iletişim kutusunda, çıktı dizinine gözatın **ExcelWorkbook** projesinin **gt;ExcelWorkbook.xlsx** dosya ve seçin **Ekleme** düğmesi.  

11. İçinde **Çözüm Gezgini** seçin **gt;ExcelWorkbook.xlsx** dosya.  

12. İçinde **özellikleri** penceresinde değişiklik **derleme eylemi** özelliğini **içerik** ve **çıkış dizinine Kopyala** özelliği **Yeniyse Kopyala**.  

     Bu adımları tamamladığınızda projeniz aşağıdaki gösterimi andıracaktır.  

     ![Dağıtım sonrası eylemini Proje yapısı. ](../vsto/media/vsto-postdeployment.png "Proje yapısını sonrası dağıtım eylemi.")  

13. Yayımlama **ExcelWorkbook** proje.  

### <a name="modify-the-application-manifest"></a>Uygulama bildiriminde değişiklik yapma  

1.  Açık **c:\publish** kullanarak dizin **dosya Gezgini**.  

2.  Açık **uygulama dosyaları** çözümünüzü sürümü yayımlanan klasörü ve en son karşılık gelen klasörü açın.  

3.  Açık **ExcelWorkbook.dll.manifest** dosyasını Not Defteri gibi bir metin düzenleyicisinde.  

4.  Sonra `</vstav3:update>` öğesi, aşağıdaki kodu ekleyin. Sınıf özniteliği için `<vstav3:entryPoint>` öğesi, aşağıdaki sözdizimini kullanın: *gt;NamespaceName.ClassName &*. Sonuçta elde edilen giriş noktası adı aşağıdaki örnekte, ad alanını ve sınıf adları aynı olduğundan `FileCopyPDA.FileCopyPDA`.  

    ```xml
    <vstav3:postActions>  
      <vstav3:postAction>  
        <vstav3:entryPoint  
          class="FileCopyPDA.FileCopyPDA">  
          <assemblyIdentity  
            name="FileCopyPDA"  
            version="1.0.0.0"  
            language="neutral"  
            processorArchitecture="msil" />  
        </vstav3:entryPoint>  
        <vstav3:postActionData>  
        </vstav3:postActionData>  
      </vstav3:postAction>  
    </vstav3:postActions>  
    ```  

### <a name="re-sign-the-application-and-deployment-manifests"></a>Uygulama ve dağıtım bildirimlerini yeniden imzalama  

1.  İçinde **%USERPROFILE%\Documents\Visual Studio 2013\projects\excelworkbook\excelworkbook & lt** klasörü, kopyalama **gt;ExcelWorkbook_TemporaryKey.pfx &** sertifika dosyası ve yapıştırın *Yayınklasörü* **\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion_ klasör.

2.  Visual Studio komut istemi açın ve sonra dizinleri **c:\publish\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion_ klasöre (örneğin, **c:\publish\Application Files\ExcelWorkbook_1_0_0_4**).  

3.  Aşağıdaki komutu çalıştırarak değiştirilmiş uygulama bildirimini imzalayın:  

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx  
    ```  

     "ExcelWorkbook.dll.manifest başarıyla imzalandı" iletisi görüntülenir.  

4.  Değiştirin **c:\publish** klasörünü ve ardından güncelleştirme ve oturum dağıtım bildirimi için aşağıdaki komutu çalıştırın:  

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex  
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"  
    ```  

    > [!NOTE]  
    >  Önceki örnekte, MostRecentVersionNumber çözümünüzün en son yayımlanan sürümünün sürüm numarasıyla değiştirin (örneğin, **1_0_0_4**).  

     "ExcelWorkbook.vsto başarıyla imzalandı" iletisi görüntülenir.  

5.  Kopyalama *ExcelWorkbook.vsto* dosyasını **c:\publish\Application Files\ExcelWorkbook**\__MostRecentVersionNumber_ dizin.  

##  <a name="SharePoint"></a> Bir çözümün belgesini SharePoint (yalnızca belge düzeyinde özelleştirmeler) çalıştıran bir sunucuya koyma yerleştirin  
 Belge düzeyinde özelleştirmenizi SharePoint kullanarak son kullanıcılara yayımlayabilirsiniz. Kullanıcılar SharePoint sitesine gidip belgeyi açtığında, çalışma zamanı çözümü paylaşılan ağ klasöründen kullanıcının yerel bilgisayarına otomatik olarak yükler. Çözüm yerel olarak yüklendikten sonra, belge başka bir yere (örneğin, masaüstüne) kopyalansa bile özelleştirme işlevini yerine getirmeye devam eder.  

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Belgeyi SharePoint çalıştıran bir sunucuya koymak için  

1.  Çözüm belgesini SharePoint sitesindeki bir belge kitaplığına ekleyin.  

2.  Aşağıdaki yaklaşımlardan biri için adımları uygulayın:  

    -   SharePoint çalıştıran sunucuyu, tüm bilgisayarlarda Word veya Excel'deki Güven Merkezi'ne eklemek için Office Yapılandırma Aracı'nı kullanın.  

         Bkz: [güvenlik ilkeleri ve ayarları Office 2010'daki](http://go.microsoft.com/fwlink/?LinkId=99227).  

    -   Her kullanıcının aşağıdaki adımları uygulamasını sağlayın.  

        1.  Yerel bilgisayarda Word veya Excel'i açın seçin **dosya** sekmesine ve ardından **seçenekleri** düğmesi.  

        2.  İçinde **Güven Merkezi** iletişim kutusunda **Güvenilen Konumlar** düğmesi.  

        3.  Seçin **(önerilmez) Ağımdaki Güvenilen Konumlara izin ver** onay kutusunu işaretleyin ve ardından **yeni konum Ekle** düğmesi.  

        4.  İçinde **yolu** kutusunda, karşıya yüklediğiniz belgeyi içeren SharePoint belge kitaplığının URL'sini girin (örneğin, *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName*).  

             Varsayılan Web sayfasını, adını gibi ekleme *default.aspx* veya *AllItems.aspx*.  

        5.  Seçin **bu konumdaki alt klasörler güvenilen ayrıca** onay kutusunu işaretleyin ve ardından **Tamam** düğmesi.  

             Kullanıcılar belgeyi SharePoint sitesinden açtığında, belge açılır ve özelleştirme yüklenir. Kullanıcılar belgeyi kendi masaüstlerine kopyalayabilir. Belgedeki özellikler belgenin ağ konumuna işaret ettiğinden, özelleştirme çalışmaya devam edecektir.  

##  <a name="Custom"></a> Özel bir yükleyici oluşturma  
 Çözümü yayımladığınızda sizin için oluşturulan Kurulum programını kullanmak yerine, Office çözümünüz için özel bir yükleyici oluşturabilirsiniz. Örneğin, yüklemeyi başlatmak için bir oturum açma komut dosyası kullanabilir veya çözümü, kullanıcı etkileşimi olmadan yüklemek için bir toplu iş dosyası kullanabilirsiniz. Bu senaryolar en çok, önkoşullar son kullanıcı bilgisayarlarında zaten yüklü olduğunda işe yarar.  

 Özel yükleme işleminizin bir parçası, Office çözümleri için yükleyici aracını çağırın (*VSTOInstaller.exe*), varsayılan olarak şu konumda yüklü:  

 *%CommonProgramFiles%\Microsoft shared\VSTO\10.0\VSTOInstaller.exe*  

 Araç bu konumda değilse, kullanabileceğiniz **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\vsto Runtime setup\v4\ınstallerpath** veya **hkey_local_machıne\software\wow6432node\microsoft\vsto Runtime Setup\v4 \InstallerPath** bu aracın yolunu bulmak için kayıt defteri anahtarı.  

 Aşağıdaki parametreleri kullanabilirsiniz *VSTOinstaller.exe*.  


| Parametre | Tanım |
|------------------| - |
| /Install veya /I | Çözümü yükler. Bu seçeneğin ardından bir dağıtım bildiriminin konumunu vermelisiniz. Yerel bilgisayarda, Evrensel Adlandırma Kuralı (UNC) dosya paylaşımına bir yol belirtebilirsiniz. Yerel bir yol belirtebilirsiniz (*C:\FolderName\PublishFolder*), göreli bir yol (*Yayımla\\*), veya tam bir konum (*\\\ServerName\ KlasörAdı* veya http://<em>ServerName/FolderName</em>). |
| /Uninstall veya /U | Çözümü kaldırır. Bu seçeneğin ardından bir dağıtım bildiriminin konumunu vermelisiniz. Bir yolu bir UNC dosyası paylaşımı yerel bilgisayarda bulunabilir belirtebilirsiniz. Yerel bir yol belirtebilirsiniz (*c:\FolderName\PublishFolder*), göreli bir yol (*Yayımla\\*), veya tam bir konum (*\\\ServerName\ KlasörAdı* veya http://<em>ServerName/FolderName</em>). |
| /Silent veya /S | Kullanıcıdan bir şey girmesini istemeden veya ileti görüntülemeden yükler veya kaldırır. Güven istemi gerekiyorsa, özelleştirme yüklendiğinde veya değil. |
| /Help or /? | Yardım bilgilerini görüntüler. |

 Çalıştırdığınızda *VSTOinstaller.exe*, aşağıdaki hata kodları görünebilir.  

|Hata Kodu|Tanım|  
|----------------|----------------|  
|0|Çözüm başarıyla yüklendi ya da kaldırıldı veya VSTOInstaller Yardımı görüntülendi.|  
|-100|Bir veya daha fazla komut satırı seçeneği geçerli değil veya bir kereden fazla ayarlandı. Daha fazla bilgi için girin "vstoinstaller /?" veya [ClickOnce Office çözümü için özel bir yükleyici oluşturma](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e).|  
|-101|Bir veya daha fazla komut satırı seçeneği geçerli değil. Daha fazla bilgi için "vstoinstaller /?" girin.|  
|-200|Dağıtım bildirimi URI'si geçerli değil. Daha fazla bilgi için "vstoinstaller /?" girin.|  
|-201|Dağıtım bildirimi geçerli olmadığından çözüm yüklenemedi. Bkz: [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md).|  
|-202|Visual Studio Araçları uygulama bildiriminin Office bölümü için geçerli olmadığından çözüm yüklenemedi. Bkz: [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md).|  
|-203|İndirme hatası oluştuğundan çözüm yüklenemedi. Dağıtım bildiriminin URI'sini veya ağ dosya konumunu denetleyin ve sonra yeniden deneyin.|  
|-300|Bir güvenlik özel durumu oluştuğundan çözüm yüklenemedi. Bkz: [güvenli Office çözümleri](../vsto/securing-office-solutions.md).|  
|-400|Çözüm yüklenemedi.|  
|-401|Çözüm kaldırılamadı.|  
|-500|Çözüm yüklenemediğinden ya da kaldırılamadığından veya dağıtım bildirimi indirilemediğinden işlem iptal edildi.|  

##  <a name="Update"></a> Güncelleştirme yayımlama  
 Bir çözümü güncelleştirmek için onu yeniden kullanarak yayımladığınız **Proje Tasarımcısı** veya **Yayımlama Sihirbazı**, ve sonra da güncelleştirilen çözümü yükleme konumuna kopyalayın. Dosyaları yükleme konumuna kopyalarken, önceki dosyaların üzerine yazdığınızdan emin olun.  

 Çözüm denetleyen bir sonraki seferde bir güncelleştirme, bulun ve yeni sürümü otomatik olarak yükleyin.  

##  <a name="Location"></a> Bir çözümün yükleme konumunu değiştirme  
 Bir çözüm yayımlandıktan sonra yükleme yolunu ekleyebilir veya değiştirebilirsiniz. Yükleme yolunu değiştirmek istemenizin nedeni şunlardan biri veya daha fazlası olabilir:  

- Kurulum programı, henüz yükleme yolu bilinmezken derlenmiştir.  

- Çözüm dosyaları farklı bir konuma kopyalanmıştır.  

- Yükleme dosyalarını barındıran sunucu yeni bir ada veya konuma sahiptir.  

  Bir çözümün yükleme yolunu değiştirmek için kurulum programını güncelleştirmelisiniz; daha sonra da kullanıcıların bunu çalıştırması gerekir. Belge düzeyinde özelleştirmeler için, kullanıcıların ayrıca belgelerindeki bir özelliği de yeni konuma işaret edecek şekilde güncelleştirmeleri gerekir.  

> [!NOTE]  
>  Kullanıcılardan belge özelliklerini güncelleştirmelerini talep etmek istemiyorsanız, güncelleştirilen belgeyi yükleme konumundan almak için kullanıcıları sorabilir.  

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Kurulum programındaki yükleme konumunu değiştirmek için  

1. Açık bir **komut istemi** penceresi ve yükleme klasörüne dizin değiştirin.  

2. Kurulum programı çalıştırın ve `/url` parametresini yeni yükleme yolunu dize olarak alır.  

    Aşağıdaki örnekte, Fabrikam web sitesindeki bir konumun yükleme yolunun nasıl değiştirileceği gösterilmektedir; ancak siz bu URL'yi istediğiniz yol ile değiştirebilirsiniz:  

   ```cmd  
   setup.exe /url="http://www.fabrikam.com/newlocation"  
   ```  

   > [!NOTE]  
   >  Bir ileti ekrana gelir ve yürütülebilir öğenin imzasının geçersiz kılınacağını belirtirse, çözümü imzalamak için kullanılan sertifika artık geçerli değil ve yayımcısı bilinmiyor demektir. Sonuç olarak, kullanıcıların, çözümü yüklemeden önce çözümün kaynağına güvendiklerini onaylamaları gerekecektir.  

   > [!NOTE]  
   >  URL geçerli değerini görüntülemek için Çalıştır `setup.exe /url`.  

   Belge düzeyinde özelleştirmeler için kullanıcıların belgeyi açın ve ardından kendi _AssemblyLocation özelliğini güncelleştirmek gerekir. Aşağıdaki adımlarda kullanıcıların bu görevi nasıl yerine getirecekleri açıklanmaktadır.  

#### <a name="to-update-the-assemblylocation-property-in-a-document"></a>Bir belgede _AssemblyLocation özelliğini güncelleştirmek için  

1.  Üzerinde **dosya** sekmesini, **bilgisi**, aşağıdaki resimde gösterilmektedir.  

     ![Excel'de bilgileri sekmesi](../vsto/media/vsto-infotab.png "Excel'de bilgileri sekmesi")  

2.  İçinde **özellikleri** listesinde **Gelişmiş Özellikler**, aşağıdaki resimde gösterilmektedir.  

     ![Excel'de Gelişmiş özellikleri. ](../vsto/media/vsto-advanceddocumentproperties.png "Gelişmiş Excel'de özellikleri.")  

3.  Üzerinde **özel** sekmesinde **özellikleri** listesinde, aşağıdaki çizimde gösterildiği gibi _AssemblyLocation seçin.  

     ![AssemblyLocation özellik. ](../vsto/media/vsto-assemblylocationproperty.png "AssemblyLocation özelliği.")  

     **Değer** kutusu dağıtım bildirimi tanımlayıcısını içerir.  

4.  Tanımlayıcıdan önce belgenin biçiminde bir çubuk ardından tam yolunu girin *yolu*|*tanımlayıcı* (örneğin, *File://ServerName/ KlasörAdı/FileName | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9 & lt*.  

     Bu tanımlayıcıyı biçimlendirme hakkında daha fazla bilgi için bkz. [özel belge özelliklerine genel bakış](../vsto/custom-document-properties-overview.md).  

5.  Seçin **Tamam** button, kaydedin ve kapatın.  

6.  Çözümü belirtilen konuma yüklemek için, kurulum programını /url parametresi olmadan çalıştırın.  

##  <a name="Roll"></a> Bir çözümü önceki bir sürüme geri alma  
 Bir çözümü geri aldığınızda, kullanıcıları bu çözümün önceki bir sürümüne geri döndürmüş olursunuz.  

#### <a name="to-roll-back-a-solution"></a>Bir çözümü geri almak için  

1.  Çözümün yükleme konumunu açın.  

2.  Üst düzey klasör yayımlama, dağıtım bildirimini Sil ( *.vsto* dosyası).  

3.  Geri almak istediğiniz sürüme ait alt klasörü bulun.  

4.  O alt klasördeki dağıtım bildirimini üst düzey publish klasörüne kopyalayın.  

     Örneğin, çağrılan bir çözümü geri almak için **Outlookaddın1** sürümünden 1.0.0.1 sürümünden 1.0.0.0 sürümüne, dosyayı kopyalama **OutlookAddIn1.vsto** gelen **Outlookaddın1_1_0_0_0** klasör. Yapıştırma dosyanın en üst düzey publish klasörüne sürüme özgü dağıtım bildiriminin üzerine yazmak, **Outlookaddın1_1_0_0_1** olan zaten vardır.  

     Aşağıdaki resimde, bu örnekteki publish (yayımlama) klasörü yapısı gösterilmektedir.  

     ![Klasör yapısını yayımlama](../vsto/media/publishfolderstructure.png "klasör yapısını yayımlama")  

     Kullanıcının uygulamayı ya da özelleştirilmiş belgeyi bir sonraki açışında, dağıtım bildirimindeki değişiklik algılanır. Office çözümünün önceki sürümü ClickOnce önbelleğinden çalışır.  

> [!NOTE]  
>  Yerel veriler çözümün sadece bir önceki sürümü için kaydedilir. İki sürüm geri alırsanız, yerel veriler korunmaz. Yerel veriler hakkında daha fazla bilgi için bkz. [ClickOnce uygulamalarında yerel ve uzak veri erişim](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).  

## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)   
 [Office çözümleri yayımlama](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Nasıl yapılır: ClickOnce kullanarak Office çözümü yayımlama](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [Nasıl yapılır: ClickOnce Office çözümünü yükle](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)   
 [Nasıl yapılır: bir belge düzeyinde Office çözümü ClickOnce kullanarak bir SharePoint sunucusuna yayımlama](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)   
 [Bir ClickOnce office çözümü için özel bir yükleyici oluşturma](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)  


