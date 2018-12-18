---
title: 'İzlenecek yol: bir gizlilik istemi göstermek için özel bir önyükleyici oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- dependencies [.NET Framework], custom bootstrapper package
- deploying applications [Visual Studio], custom prerequisites
- Windows Installer deployment, prerequisites
- prerequisites [.NET Framework], custom bootstrapper package
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: e8bd1101647973a7a8f206159f8910a4e633e5da
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893398"
---
# <a name="walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt"></a>İzlenecek yol: Bir Gizlilik İstemi Göstermek için Özel Bir Önyükleyici Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yeni dosya ve derleme sürümlerini sahip derlemeler kullanılabilir olduğunda otomatik olarak güncelleştirmek için ClickOnce uygulamaları yapılandırabilirsiniz. Müşterileriniz için bu davranış kabul ettiğinden emin olmak için bunları bir gizlilik istemi görüntüleyebilirsiniz. Ardından, bunlar otomatik olarak güncelleştirmek için uygulamaya izin verilip verilmeyeceğini seçebilirsiniz. Uygulamayı otomatik olarak güncelleştirmesine izin verilmiyorsa yüklemez.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   Visual Studio 2010.  
  
## <a name="creating-an-update-consent-dialog-box"></a>Bir güncelleştirme Onayı iletişim kutusu oluşturma  
 Bir gizlilik istemi görüntülenecek uygulama için Otomatik Güncelleştirmeler onay okuyucunun soran bir uygulama oluşturun.  
  
#### <a name="to-create-a-consent-dialog-box"></a>Onay iletişim kutusu oluşturmak için  
  
1. Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.  
  
2. İçinde **yeni proje** iletişim kutusu, tıklayın **Windows**ve ardından **WindowsFormsApplication**.  
  
3. İçin **adı**, türü **ConsentDialog**ve ardından **Tamam**.  
  
4. Form Tasarımcısı'nda tıklatın.  
  
5. İçinde **özellikleri** penceresinde değişiklik **metin** özelliğini **Güncelleştirme Onayı iletişim**.  
  
6. İçinde **araç kutusu**, genişletme **tüm Windows Formları**, sürükleyin bir **etiket** forma.  
  
7. Tasarımcıda etiket denetimi tıklayın.  
  
8. İçinde **özellikleri** penceresinde değişiklik **metin** özelliği altında **Görünüm** aşağıdaki:  
  
    Web üzerinde en son güncelleştirmeleri yüklemek üzere olduğunuz uygulama denetler. "Kabul ediyorum" tıklayarak denetlemek ve güncelleştirmeleri Internet'ten otomatik olarak yüklemek için uygulamayı yetkilendirme.  
  
9. İçinde **araç kutusu**, sürükleyin bir **onay kutusu** ortaya form denetimi.  
  
10. İçinde **özellikleri** penceresinde değişiklik **metin** özelliği altında **Düzen** için **ediyorum**.  
  
11. İçinde **araç kutusu**, sürükleyin bir **düğmesi** sol alt form denetimi.  
  
12. İçinde **özellikleri** penceresinde değişiklik **metin** özelliği altında **Düzen** için **İlerle**.  
  
13. İçinde **özellikleri** penceresinde değişiklik **(ad)** özelliği altında **tasarım** için **ProceedButton**.  
  
14. İçinde **araç kutusu**, sürükleyin bir **düğmesi** sağ alt köşesindeki form denetimi.  
  
15. İçinde **özellikleri** penceresinde değişiklik **metin** özelliği altında **Düzen** için **iptal**.  
  
16. İçinde **özellikleri** penceresinde değişiklik **(ad)** özelliği altında **tasarım** için **CancelButton**.  
  
17. Tasarımcıda çift **ediyorum** CheckedChanged olayı işleyicisi oluşturmak için onay kutusu.  
  
18. Form1 kod dosyasında, CheckedChanged olay işleyicisine aşağıdaki kodu ekleyin.  
  
     [!code-csharp[ConsentDialog#1](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#1)]
     [!code-vb[ConsentDialog#1](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#1)]  
  
19. Devre dışı bırakmak için sınıf oluşturucusu güncelleştirilemiyor **İlerle** varsayılan düğme.  
  
     [!code-csharp[ConsentDialog#6](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#6)]
     [!code-vb[ConsentDialog#6](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#6)]  
  
20. Form1 kod dosyasında, son kullanıcının çevrimiçi güncelleştirmeleri onaylamadığını izlemek bir Boolean değişkeni için aşağıdaki kodu ekleyin.  
  
     [!code-csharp[ConsentDialog#3](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#3)]
     [!code-vb[ConsentDialog#3](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#3)]  
  
21. Tasarımcıda çift **İlerle** düğme tıklama olayı işleyicisi oluşturmak için.  
  
22. Form1 kod dosyasında, tıklama olay işleyicisine aşağıdaki kodu ekleyin **İlerle** düğmesi.  
  
     [!code-csharp[ConsentDialog#2](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#2)]
     [!code-vb[ConsentDialog#2](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#2)]  
  
23. Tasarımcıda çift **iptal** düğme tıklama olayı işleyicisi oluşturmak için.  
  
24. Form1 kod dosyasında, tıklama olay işleyicisine aşağıdaki kodu ekleyin **iptal** düğmesi.  
  
     [!code-csharp[ConsentDialog#4](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#4)]
     [!code-vb[ConsentDialog#4](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#4)]  
  
25. Uygulama son kullanıcının çevrimiçi güncelleştirmeleri onay vermezse, bir hata döndürmek için güncelleştirin.  
  
     Yalnızca Visual Basic geliştiriciler için:  
  
    1. İçinde **Çözüm Gezgini**, tıklayın **ConsentDialog**.  
  
    2. Üzerinde **proje** menüsünü tıklatın **Modül Ekle**ve ardından **Ekle**.  
  
    3. Module1.vb kod dosyasında, aşağıdaki kodu ekleyin.  
  
        [!code-vb[ConsentDialog#7](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/module1.vb#7)]  
  
    4. Üzerinde **proje** menüsünde tıklatın **ConsentDialog özellikleri**ve ardından **uygulama** sekmesi.  
  
    5. Onay kutusunu temizleyin **etkinleştir uygulama çerçevesi**.  
  
    6. İçinde **Başlangıç nesnesi** açılan menüsünde, select **Module1**.  
  
       > [!NOTE]
       >  Uygulama Framework'ü devre dışı bırakma, Windows XP görsel stilleri, uygulama olayları, giriş ekranı, tek örnek uygulama ve diğer özellikleri devre dışı bırakır. Daha fazla bilgi için [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
       Visual C# yalnızca geliştiriciler için:  
  
       Program.cs kod dosyasını açın ve aşağıdaki kodu ekleyin.  
  
       [!code-csharp[ConsentDialog#5](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/program.cs#5)]  
  
26. Üzerinde **derleme** menüsünde tıklatın **BuildSolution**.  
  
## <a name="creating-the-custom-bootstrapper-package"></a>Özel önyükleyici paketi oluşturma  
 Son kullanıcılara bir gizlilik istemi göstermek için Güncelleştirme Onayı iletişim uygulama için bir özel önyükleyici paketi oluşturma ve bir önkoşul olarak ClickOnce uygulamalarınızın tümünü içerir.  
  
 Bu yordam, aşağıdaki belgeler oluşturarak özel önyükleyici paketi oluşturma işlemini göstermektedir:  
  
-   Bir Product.XML önyükleyici içeriğini açıklamak için dosyası.  
  
-   Dizeler ve Yazılım Lisans Koşulları'nı gibi paketinizi yerelleştirme özgü yönlerini listelemek için package.xml bildirim dosyası.  
  
-   Yazılım Lisans Koşulları'nı bir belge.  
  
#### <a name="step-1-to-create-the-bootstrapper-directory"></a>1. adım: önyükleyici dizini oluşturmak için  
  
1.  Adlı bir dizin oluşturmak **UpdateConsentDialog** SDKs\Windows\v7.0A\Bootstrapper\Packages %PROGRAMFILES%\Microsoft içinde.  
  
    > [!NOTE]
    >  Bu klasör oluşturmak için yönetici ayrıcalıkları gerekir.  
  
2.  UpdateConsentDialog dizininde, tr adlı bir dizin oluşturun.  
  
    > [!NOTE]
    >  Her yerel ayar için yeni bir dizin oluşturun. Örneğin, fr ve de yerel ayarlar için alt ekleyebilirsiniz. Bu dizinler, dil paketlerini ve Fransızca ve Almanca dizeleri gerekirse içerecektir.  
  
#### <a name="step-2-to-create-the-productxml-manifest-file"></a>2. adım: product.xml bildirim dosyası oluşturmak için  
  
1.  Adlı bir metin dosyası oluşturma `product.xml`.  
  
2.  Product.xml dosyasında aşağıdaki XML kodunu ekleyin. Var olan XML kodunun üzerine yazma emin olun.  
  
    ```  
    <Product  
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      ProductCode="Microsoft.Sample.EULA">  
      <!-- Defines the list of files to be copied on build. -->  
      <PackageFiles CopyAllPackageFiles="false">  
        <PackageFile Name="ConsentDialog.exe"/>  
      </PackageFiles>  
  
      <!-- Defines how to run the Setup package.-->  
      <Commands >  
        <Command PackageFile = "ConsentDialog.exe" Arguments=''>  
          <ExitCodes>  
            <ExitCode Value="0" Result="Success" />  
            <ExitCode Value="-1" Result="Fail" String="AU_Unaccepted" />  
            <DefaultExitCode Result="Fail"   
              FormatMessageFromSystem="true" String="GeneralFailure" />  
          </ExitCodes>  
        </Command>  
      </Commands>  
  
    </Product>  
    ```  
  
3.  Dosyayı UpdateConsentDialog önyükleyici dizine kaydedin.  
  
#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>3. adım: package.xml bildirimi oluşturmak için dosya ve yazılım lisans koşulları  
  
1.  Adlı bir metin dosyası oluşturma `package.xml`.  
  
2.  Package.xml dosyasında, yerel ayar tanımlayın ve Yazılım Lisans Koşulları'nı eklemek için aşağıdaki XML kodunu ekleyin. Var olan XML kodunun üzerine yazma emin olun.  
  
    ```  
    <Package   
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      Name="DisplayName"  
      Culture="Culture"  
      LicenseAgreement="eula.rtf">  
      <PackageFiles>  
        <PackageFile Name="eula.rtf"/>  
      </PackageFiles>  
  
      <!-- Defines a localizable string table for error messages. -->  
      <Strings>  
        <String Name="DisplayName">Update Consent Dialog</String>  
        <String Name="Culture">en</String>  
        <String Name="AU_Unaccepted">The automatic update agreement is not accepted.</String>  
        <String Name="GeneralFailure">A failure occurred attempting to launch the setup.</String>  
      </Strings>  
    </Package>  
    ```  
  
3.  UpdateConsentDialog önyükleyici dizinindeki en alt dosyayı kaydedin.  
  
4.  Yazılım Lisans koşulları EULA.rtf adlı bir belge oluşturun.  
  
    > [!NOTE]
    >  Yazılım Lisans Koşulları'nı lisanslama, garanti, yükümlülükler ve yerel yasalarınız hakkında bilgi içermelidir. Bu dosyalar yerel ayara özgü, bu nedenle dosyanın MBCS ya da UNICODE karakterleri destekler bir biçimde kaydedildiğinden emin olun. İçeriği hakkında hukuk departmanınıza Yazılım Lisans Koşulları'nın başvurun.  
  
5.  Belge UpdateConsentDialog önyükleyici dizinindeki en alt kaydedin.  
  
6.  Gerekirse, her yerel ayar için yazılım lisans koşulları için yeni package.xml bildirim dosyası ve yeni bir eula.rtf belgesi oluşturun. Örneğin, fr ve de yerel ayarlar için alt oluşturduysanız, ayrı package.xml bildirim dosyaları ve Yazılım Lisans Koşulları'nı oluşturun ve bunları fr ve de alt dizinler için kaydedin.  
  
## <a name="setting-the-update-consent-application-as-a-prerequisite"></a>Bir önkoşul olarak güncelleştirme onayı uygulamasını ayarlama  
 Visual Studio'da bir önkoşul olarak güncelleştirme onayı uygulamasını ayarlayabilirsiniz.  
  
#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Güncelleştirme Onayı uygulaması bir önkoşul olarak ayarlamak için  
  
1.  İçinde **Çözüm Gezgini**, dağıtmak istediğiniz, uygulamanızın adına tıklayın.  
  
2.  Üzerinde **proje** menüsünde tıklatın *ProjectName* **özellikleri**.  
  
3.  Tıklayın **Yayımla** sayfasında ve ardından **önkoşulları**.  
  
4.  Seçin **güncelleştirme onay iletişim kutusunu**.  
  
    > [!NOTE]
    >  Güncelleştirme Onayı iletişim önkoşulları iletişim kutusunda görmek için Visual Studio'yu kapatıp gerekebilir.  
  
5.  **Tamam**'ı tıklatın.  
  
## <a name="creating-and-testing-the-setup-program"></a>Oluşturma ve Kurulum programını sınama  
 Uygulamanız için bir önkoşul olarak güncelleştirme onayı uygulamasını ayarladıktan sonra önyükleyici ve yükleyici oluşturabilirsiniz.  
  
#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Oluşturma ve Kurulum programını tıklamadan test kabul ediyorum  
  
1.  İçinde **Çözüm Gezgini**, dağıtmak istediğiniz, uygulamanızın adına tıklayın.  
  
2.  Üzerinde **proje** menüsünde tıklatın *ProjectName* **özellikleri**.  
  
3.  Tıklayın **Yayımla** sayfasında ve ardından **Şimdi Yayımla**.  
  
4.  Yayınlama çıktısı otomatik olarak açılmazsa, yayınlama çıktısı için gidin.  
  
5.  Setup.exe programını çalıştırın.  
  
     Kurulum programı Güncelleştirme Onayı iletişim yazılım lisans sözleşmesini gösterir.  
  
6.  Yazılım lisans sözleşmesini okuyun ve ardından **kabul**.  
  
     Güncelleştirme Onayı iletişim uygulaması görünür ve aşağıdaki metni gösterir: Web üzerindeki en son güncelleştirmeleri yüklemek üzere olduğunuz uygulama denetler. Kabul ediyorum düğmesini tıklatarak Internet'teki otomatik olarak güncelleştirmeleri denetlemek için uygulamayı yetkilendirme.  
  
7.  Uygulamayı kapatın veya İptal'e tıklayın.  
  
     Uygulama bir hatayı gösterir: için sistem bileşenleri yüklenirken bir hata oluştu *ApplicationName*. Tüm sistem bileşenleri başarıyla yükleninceye kadar kurulum devam edemiyor.  
  
8.  Aşağıdaki hata iletisini göstermek için Ayrıntılar'ı tıklatın: Bileşen Güncelleştirme Onayı iletişim kutusu aşağıdaki hata iletisiyle başarısız oldu: "otomatik güncelleştirme anlaşmayı kabul edilmez." Aşağıdaki bileşenler yüklenemedi:-Güncelleştirme Onayı iletişim  
  
9. **Kapat**'ı tıklatın.  
  
#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Oluşturma ve Kurulum programını tıklayarak test kabul ediyorum  
  
1.  İçinde **Çözüm Gezgini**, dağıtmak istediğiniz, uygulamanızın adına tıklayın.  
  
2.  Üzerinde **proje** menüsünde tıklatın *ProjectName* **özellikleri**.  
  
3.  Tıklayın **Yayımla** sayfasında ve ardından **Şimdi Yayımla**.  
  
4.  Yayınlama çıktısı otomatik olarak açılmazsa, yayınlama çıktısı için gidin.  
  
5.  Setup.exe programını çalıştırın.  
  
     Kurulum programı Güncelleştirme Onayı iletişim yazılım lisans sözleşmesini gösterir.  
  
6.  Yazılım lisans sözleşmesini okuyun ve ardından **kabul**.  
  
     Güncelleştirme Onayı iletişim uygulaması görünür ve aşağıdaki metni gösterir: Web üzerindeki en son güncelleştirmeleri yüklemek üzere olduğunuz uygulama denetler. Kabul ediyorum düğmesini tıklatarak Internet'teki otomatik olarak güncelleştirmeleri denetlemek için uygulamayı yetkilendirme.  
  
7.  Tıklayın **ediyorum**ve ardından **İlerle**.  
  
     Uygulama yüklemeye başlar.  
  
8.  Uygulama Yükle iletişim kutusu görünürse, tıklatın **yükleme**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulama dağıtımının önkoşulları](../deployment/application-deployment-prerequisites.md)   
 [Önyükleyici paketleri oluşturma](../deployment/creating-bootstrapper-packages.md)   
 [Nasıl yapılır: Ürün bildirimi oluşturma](../deployment/how-to-create-a-product-manifest.md)   
 [Nasıl yapılır: Paket bildirimi oluşturma](../deployment/how-to-create-a-package-manifest.md)   
 [Ürün ve Paket Şema Başvurusu](../deployment/product-and-package-schema-reference.md)



