---
title: Tam Zamanında Hata Ayıklama
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
- CSharp
- VB
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 51
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0b89dd1e0a395e034fa2321269e4174da359b336
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052338"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>Visual Studio'da Tam Zamanında Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio dışında çalışan bir uygulamada bir özel durum veya kilitlenme oluştuğunda just-In-Time hata ayıklama Visual Studio otomatik olarak başlatır. Bu, Visual Studio çalışmadığı zamanlarda uygulamanızı test edin ve bir sorun ortaya çıktığında, Visual Studio ile hata ayıklamayı başlatmak sağlar.

Just-In-Time hata ayıklama, Windows Masaüstü uygulamaları için çalışır. Windows Evrensel uygulamaları için çalışmaz ve Görselleştiriciler gibi yerel bir uygulama içinde barındırılan yönetilen kod için çalışmaz.

## <a name="BKMK_Scenario"></a> Just-ın-Time vermedi. hata ayıklayıcı iletişim Kutsu, bir uygulamayı çalıştırmayı denerken?

Visual Studio Just-ın-Time gördüğünüzde sürecektir eylemleri hata ayıklayıcısı iletişim kutusu bağımlı ne yapılacağını çalışıyorsunuz:

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>İletişim kutusunun kurtulun ve yalnızca istiyorsanız uygulama normal şekilde çalıştırın

1. (Gelişmiş kullanıcılar için) Visual Studio yüklü (veya daha önce yüklü olan ve yinelemeyi kaldırmış varsa) [devre dışı bırakma, Just-ın-Time hata ayıklama](#BKMK_Enabling) ve uygulamayı yeniden çalıştırmayı deneyin.

2. Internet Explorer'da bir web uygulaması çalıştırıyorsanız, betik hata ayıklamasını devre dışı bırakın.

    Internet Seçenekleri iletişim kutusunda betik hata ayıklamasını devre dışı bırakın. Buradan erişebilirsiniz **Denetim Masası** / **ağ ve Internet** / **Internet Seçenekleri** (tam adımlar sürümünüze bağlıdır Windows ve Internet Explorer).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

3. Hatanın bulunduğu web sayfasını yeniden açın. Bu sorunu çözmezse, sorunu düzeltmek için web uygulama sahibine başvurun.

4. Başka türde bir Windows uygulama çalıştırıyorsanız, hatayı düzeltin ve sabit sürümünü yeniden yüklemeyi uygulama sahibine başvurun gerekecektir.

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>(Gelişmiş kullanıcılar) hata ayıklama veya düzeltmek istiyorsanız

- Olmalıdır [Visual Studio'nun yüklü](https://www.microsoft.com/download/details.aspx?id=48146) hata hakkında ayrıntılı bilgi görüntülemek ve hata ayıklamak deneyin. Bkz: [kullanarak JIT](#BKMK_Using_JIT) ayrıntılı yönergeler için. Hatayı çözün ve uygulama düzeltme, hatayı gidermek için uygulama sahibine başvurun.

##  <a name="BKMK_Enabling"></a> Etkinleştirme veya devre dışı bırakma, Just-ın-Time hata ayıklama
 Etkinleştirebilir veya tam zamanında Visual Studio'dan hata ayıklama devre dışı **Araçlar / Seçenekler** iletişim kutusu.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Etkinleştirme veya devre dışı bırakma, Just-ın-Time hata ayıklama

1. Visual Studio'yu açın. Üzerinde **Araçları** menüsünü tıklatın **seçenekleri**.

2. İçinde **seçenekleri** iletişim kutusunda **hata ayıklama** klasör.

3. İçinde **hata ayıklama** klasörüne **Just-ın-Time** sayfası.

4. İçinde **temizleyintypes bu tür kod hata ayıklama** kutusunda seçin veya ilgili program türünü: **yönetilen**, **yerel**, veya **betik**.

    Tam zamanında etkinleştirildikten sonra hata ayıklama devre dışı bırakmak için yönetici ayrıcalıklarıyla çalıştırıyor olmalısınız. Etkinleştirme Just-ın-Time hata ayıklama, bir kayıt defteri anahtarı ayarlar ve bu anahtarı değiştirmek için yönetici ayrıcalıkları gerekir.

5. **Tamam**'ı tıklatın.

   Visual Studio artık bilgisayarınızda yüklü olsa bile just-In-Time hata ayıklamayı hala etkin. Visual Studio yüklü değil, tam zamanında Visual Studio'dan hata ayıklama devre dışı bırakamazsınız **seçenekleri** iletişim kutusu. Bu durumda, tam zamanında hata ayıklama Windows kayıt defterini düzenleyerek devre dışı bırakabilirsiniz.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Kayıt defterini düzenleyerek devre dışı bırakma, Just-ın-Time hata ayıklama

1.  Üzerinde **Başlat** menü, arayın ve çalıştırın `regedit.exe`

2.  İçinde **Kayıt Defteri Düzenleyicisi'ni** penceresinde bulun ve izleme kayıt defteri girişleri silin:

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\\. NETFramework\DbgManagedDebugger

3.  Bilgisayarınızı bir 64-bit işletim sistemi çalıştırıyorsa aşağıdaki kayıt defteri girdilerini de silin:

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\DbgManagedDebugger

4.  Yanlışlıkla silmemek veya herhangi bir kayıt defteri anahtarı değiştirmek için dikkatli olun.

5.  Kapat **Kayıt Defteri Düzenleyicisi'ni** penceresi.

> [!NOTE]
>  Tam zamanında hata ayıklama için bir sunucu tarafı uygulama devre dışı bırakmaya çalıştığınız ve bu adımlar sorunu yok, IIS uygulama ayarlarında, sunucu tarafı hata ayıklamayı kapatmanız ve yeniden deneyin.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Etkinleştirme Just-ın-Time hata ayıklama için bir Windows formu

1.  Varsayılan olarak, Windows Forms uygulamaları program, kurtarabilirsiniz durumunda çalışmaya devam etmesini sağlar bir üst düzey özel durum işleyicisine sahiptir. Örneğin, Windows Forms uygulaması işlenmeyen bir özel durum oluşturursa, aşağıdakine benzer bir iletişim kutusu görürsünüz:

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     Bir Windows Forms uygulamasına etkinleştirme Just-ın-Time hata ayıklama için aşağıdaki ek adımları gerçekleştirmeniz gerekir:

2.  Ayarlama `jitDebugging` değerini `true` içinde `system.windows.form` machine.config bölümünde veya  *\<uygulama adı >*. exe.config dosyası:

    ```
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3.  Bir C++ Windows Form uygulamasında de ayarlamalısınız `DebuggableAttribute` .config dosyasında ya da kodunuzda. Derleme yaparsanız [/zi](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) ve olmadan [/Og](http://msdn.microsoft.com/library/d10630cc-b9cf-4e97-bde3-8d7ee79e9435), derleyici bu özniteliği sizin için ayarlar. Ancak, bir yayın olmayan yapılandırmada yapı hata ayıklamak istiyorsanız, bu kendiniz ayarlamanız gerekir. Bunu, aşağıdaki satırı uygulamanızın AssemblyInfo.cpp dosyasına olduğunuz ekleyerek yapabilirsiniz:

    ```
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     Daha fazla bilgi için bkz. <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Just-ın-Time hata ayıklamasını kullanın
 Bu bölüm, yürütülebilir bir özel durum oluşturduğunda ne olacağını gösterir.

 Visual Studio bu adımları izlemek için yüklü olması gerekir. Visual Studio yoksa, ücretsiz indirebileceğiniz [Visual Studio 2015 Community Edition](https://www.microsoft.com/download/details.aspx?id=48146).

 Yüklediğinizde Visual Studio, Just-ın-Time hata ayıklama varsayılan olarak etkindir.

 Bu bölümün amacı doğrultusunda, C# konsol uygulaması Visual Studio'da oluşturur oluşturacağız bir <xref:System.NullReferenceException>.

 Visual Studio'da C# konsol uygulaması oluşturma (**dosya / yeni / Project / Visual C# / konsol uygulaması**) adlı **ThrowsNullException**. Visual Studio'da proje oluşturma hakkında daha fazla bilgi için bkz. [izlenecek yol: basit bir uygulama oluşturma](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).

 Projeyi Visual Studio'da açıldığında, Program.cs dosyasını açın. Ana() yöntemi, bir çizgi konsola yazdırır ve ardından bir NullReferenceException oluşturur aşağıdaki kodla değiştirin:

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
>  Çalışmak için bu yordamı sırayla bir [yayın Yapılandırması](../debugger/how-to-set-debug-and-release-configurations.md), devre dışı bırakmak gereksinim [yalnızca kendi kodum](../debugger/just-my-code.md). Visual Studio'da **Araçlar / Seçenekler**. İçinde **seçenekleri** iletişim kutusunda **hata ayıklama**. Denetimden Kaldır **yalnızca benim kodumu etkinleştir**.

 Çözümü derleyin (Visual Studio'da **derleme / zümü**). Hata ayıklama veya sürüm yapılandırmasını seçebilirsiniz. Derleme yapılandırmaları hakkında daha fazla bilgi için bkz. [derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md).

 Derleme işlemi, bir yürütülebilir ThrowsNullException.exe oluşturur. C# projesini oluşturduğunuz klasörü altında bulabilirsiniz: **...\ThrowsNullException\ThrowsNullException\bin\Debug** veya **...\ThrowsNullException\ThrowsNullException\bin\Release**.

 ThrowsNullException.exe çift tıklayın. Böyle bir komut penceresi görmeniz gerekir:

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 Birkaç saniye sonra bir hata penceresinde görüntülenir:

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 Tıklamayın **iptal**! Birkaç saniye sonra iki düğme görmelisiniz **hata ayıklama** ve **Programı Kapat**. Tıklayın **hata ayıklama**.

> [!CAUTION]
>  Uygulamanızda güvenilmeyen kod varsa, bir güvenlik uyarısı iletişim kutusu görünür. Bu iletişim kutusu, hata ayıklamaya devam edip etmemeyi karar vermenize olanak sağlar. Hata ayıklamaya devam etmeden önce kodun güvenilir olup olmadığına karar verin. Size kodu kendiniz mi yazdınız? Kodlayıcıya güveniyor musunuz? Uygulama uzak makinede çalışıyorsa, işlemin adını hatırlar mısınız? Uygulamayı yerel olarak çalışıyor olsa bile, mutlaka güvenilir olabildiği anlamına gelmez. Bilgisayarınızda kötü amaçlı kod olasılığını göz önünde bulundurun. Kod üzeresiniz, karar verirseniz, güvenilir hata ayıklama, tıklayın **hata ayıklama**. ' A tıklayıp **hata ayıklama**.

 **Visual Studio anlık hata ayıklayıcısı** penceresi görüntülenir:

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 Altında **olası hata ayıklayıcıları**, durumunda olduklarını görmüş olmalısınız **Microsoft Visual Studio 2015 yeni bir örneğini** satır seçili. Zaten seçili değilse, şimdi seçin.

 Pencerenin en altında **seçili hata ayıklayıcısını kullanarak hata ayıklamak istiyor musunuz?**, tıklayın **Evet**.

 ThrowsNullException projeyi Visual Studio'nun yeni bir örneğinde yürütme özel durum oluşturan satırında durduruldu ile açar:

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 Bu noktada hata ayıklama başlayabilirsiniz. Bu gerçek bir uygulama varsa, kodu özel neden durum bulmak gerekir.

## <a name="just-in-time-debugging-errors"></a>Just-In-Time hata ayıklama hataları
 program çöktüğünde iletişim görmüyorsanız Bu bilgisayarınızdaki Windows hata bildirimi ayarları nedeniyle olabilir. Daha fazla bilgi için [. WER ayarları](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx).

 Just-ın-Time ile ilişkili aşağıdaki hata iletilerinden görebileceğiniz hata ayıklama.

-   **Kilitlenen işleme iliştirilemiyor. Belirtilen program Windows veya bir MS-DOS programı değil.**

     Başka bir kullanıcı olarak çalışan bir işleme eklemeyi denediğinizde, bu hata oluşur.

     Bu soruna geçici bir çözüm, Visual Studio, başlangıç açmak **iliştirme** iletişim kutusundan **hata ayıklama** menü ve hata ayıklamak istediğiniz bulma işlemi **kullanılabilir işlemler**listesi. İşlemin adını bilmiyorsanız, bakmak **Visual Studio anlık hata ayıklayıcısı** iletişim ve Not işlem kimliği İşlemi seçin **kullanılabilir işlemler** listelemek ve tıklayın **iliştirme**. İçinde **Visual Studio anlık hata ayıklayıcısı** iletişim kutusunda, tıklayın **Hayır** iletişim kutusunu kapatın.

-   **Hiçbir kullanıcı giriş yapmadığından hata ayıklayıcı başlatılamadı.**

     Just-ın-Time olduğunda bu hata oluşur çalışır bir makinede Visual Studio'yu başlatmak hata ayıklama konsolda oturum açmış hiçbir kullanıcı olduğu. Hiçbir kullanıcı oturum açmadığından, Just-ın-Time görüntülemek için bir kullanıcı oturumu var. hata ayıklama iletişim kutusu.

     Bu sorunu gidermek için makinede oturum açın.

-   **Sınıf kayıtlı değil.**

     Bu hata, hata ayıklayıcının, büyük olasılıkla bir yükleme sorunu nedeniyle kayıtlı olmayan bir COM sınıfı oluşturmayı denediğini gösterir.

     Bu sorunu gidermek için Visual Studio yüklemenizi onarın veya yeniden yüklemek için kurulum diskini kullanın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Hata ayıklayıcı, güvenlik](../debugger/debugger-security.md) [hata ayıklayıcı temel bilgileri](../debugger/debugger-basics.md) [Just-ın-hata ayıklama, Time, Seçenekler iletişim kutusu](../debugger/just-in-time-debugging-options-dialog-box.md) [güvenlik uyarısı: güvenilmeyen bir kullanıcının sahip olduğu işleme ekleme olabilir tehlikeli. Aşağıdaki bilgiler kuşkulu görünüyorsa ya da emin değilseniz, bu işleme eklemeyin.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)
