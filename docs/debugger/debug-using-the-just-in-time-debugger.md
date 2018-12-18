---
title: Tam zamanında hata ayıklayıcı ile hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 09/24/18
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: ee4d79a5-a1d2-4418-a93f-dd57a53e1836
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f66d3fdcd400be9356776647b0ead118e83d7108
ms.sourcegitcommit: c5e72875206b8c5737c29d5b1ec7b86eec747303
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49382759"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Tam zamanında hata ayıklayıcı, Visual Studio kullanarak hata ayıklama

Just-In-Time hata ayıklama Visual Studio otomatik olarak ne zaman dışında Visual Studio hataları veya kilitlenmeleri çalışan bir uygulamanın başlatabilirsiniz. Just-ın-hata ayıklama Time ile Visual Studio dışında uygulamaları test edin ve bir sorun oluştuğunda, hata ayıklamayı başlatmak için Visual Studio'yu açın.

Just-In-Time hata ayıklama, Windows Masaüstü uygulamaları için çalışır. Evrensel Windows uygulamaları için ya da Görselleştiriciler gibi yerel bir uygulama içinde barındırılan yönetilen kod için çalışmaz.

> [!TIP]
> Yalnızca istiyorsanız Durdur görüntülenmesini, tam zamanında hata ayıklayıcı iletişim kutusu, ancak Visual Studio yüklü, bakın [tam zamanında hata ayıklayıcı devre dışı](../debugger/just-in-time-debugging-in-visual-studio.md). Visual Studio'nun bir kez olsaydı gerekebilir [Windows kayıt defterinden devre dışı bırakma, Just-ın-Time hata ayıklama](#disable-just-in-time-debugging-from-the-windows-registry). 

##  <a name="BKMK_Enabling"></a> Etkinleştirme veya devre dışı bırakma, Just-ın-Time debugging in Visual Studio

>[!NOTE]
>Etkinleştirmek ya da tam zamanında hata ayıklama devre dışı bırakmak için Visual Studio'yu bir yönetici olarak çalıştırıyor olmanız gerekir. Etkinleştirme veya devre dışı Just-ın-Time hata ayıklama, bir kayıt defteri anahtarı ayarlar ve yönetici ayrıcalıkları, bu anahtarı değiştirmek için gerekebilir. Visual Studio'yu yönetici olarak açmak için Visual Studio uygulamayı sağ tıklatıp seçin **yönetici olarak çalıştır**. 

Tam zamanında hata ayıklama Visual Studio'dan yapılandırabileceğiniz **Araçları** > **seçenekleri** (veya **hata ayıklama** > **seçenekleri**) iletişim kutusu. 

**Etkinleştirme veya devre dışı bırakma, Just-ın-Time hata ayıklama için:**

1. Üzerinde **Araçları** veya **hata ayıklama** menüsünde **seçenekleri** > **hata ayıklama**  >   **Just-ın-Time**.

   ![JIT hata ayıklama devre dışı bırakmak veya etkinleştirmek](../debugger/media/dbg-jit-enable-or-disable.png "etkinleştirmek veya devre dışı JIT hata ayıklama")

1. İçinde **temizleyintypes aşağıdaki kod türleri için hata ayıklama** kutusunda, kullanmak istediğiniz tam zamanında hata ayıklamak için hata ayıklama kod türlerini seçin: **yönetilen**, **yerel**, ve/veya  **Betik**.
   
1. Seçin **Tamam**.

Just-ın-Time etkinleştirirseniz, hata ayıklayıcı, ancak bir uygulama kilitlendiğinde veya hataları, bkz: zaman açılmazsa [sorun giderme tam zamanında hata ayıklama](#jit_errors).

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Tam zamanında hata ayıklama Windows kayıt defterinden devre dışı bırak

Visual Studio artık bilgisayarınızda yüklü olsa bile just-In-Time hata ayıklamayı hala etkin. Visual Studio artık yüklü değilse, tam zamanında hata ayıklama Windows kayıt defterini düzenleyerek devre dışı bırakabilirsiniz.

**Tam zamanında hata ayıklama kayıt defterini düzenleyerek devre dışı bırakmak için:**

1.  Windows gelen **Başlat** menüsü çalıştırma **Kayıt Defteri Düzenleyicisi'ni** (*regedit.exe*).

2.  İçinde **Kayıt Defteri Düzenleyicisi'ni** penceresinde bulun ve aşağıdaki kayıt defteri girişleri silin:

    -   **HKEY_LOCAL_MACHINE\Software\Microsoft\\. NETFramework\DbgManagedDebugger**

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![JIT kayıt defteri anahtarı](../debugger/media/dbg-jit-registry.png "JIT kayıt defteri anahtarı")

3.  Ayrıca bilgisayarınızın bir 64-bit işletim sistemi çalıştırıyorsa aşağıdaki kayıt defteri girdilerini silin:

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\DbgManagedDebugger**

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Silinmemesi veya başka bir kayıt defteri anahtarlarını değiştirme emin olun.

5.  Kapat **Kayıt Defteri Düzenleyicisi'ni** penceresi.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Just-ın-Time etkinleştirmek bir Windows formunda hata ayıklama

Varsayılan olarak, Windows Form uygulamalar, kurtarabilirsiniz durumunda çalışmaya devam uygulamayla bir üst düzey özel durum işleyicisine sahiptir. Bir Windows Forms uygulaması işlenmeyen bir özel durum oluşturursa aşağıdaki iletişim kutusunu gösterir:

![Windows Form işlenmeyen özel durum](../debugger/media/windowsformsunhandledexception.png "Windows Form işlenmeyen özel durum")

Tam zamanında yerine standart Windows formu hata işleme hata ayıklamayı etkinleştirmek için bu ayarları ekleyin:

-  İçinde `system.windows.forms` bölümünü *machine.config* veya  *\<uygulama adı >. exe.config* dosya, ayarlama `jitDebugging` değerini `true`:
    
    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```
    
-  Bir C++ Windows Form uygulamasında, ayrıca ayarlayın `DebuggableAttribute` için `true` içinde bir *.config* dosya ya da kodunuzda. Derleme yaparsanız [/zi](/cpp/build/reference/z7-zi-zi-debug-information-format) ve olmadan [/Og](/cpp/build/reference/og-global-optimizations), derleyici bu özniteliği sizin için ayarlar. Bir yayın olmayan yapılandırmada yapı hata ayıklamak istiyorsanız, ancak ayarlamalısınız `DebuggableAttribute` uygulamanızın içinde aşağıdaki satırı ekleyerek *AssemblyInfo.cpp* dosyası:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```
   
   Daha fazla bilgi için bkz. <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="BKMK_Using_JIT"></a>Kullanma Just-ın-Time hata ayıklama
 Bu örnekte, Just-ın-uygulama bir hata oluşturduğunda hata ayıklama Time açıklanmaktadır.

 - Visual Studio bu adımları izlemek için yüklü olması gerekir. Visual Studio yoksa, ücretsiz indirebileceğiniz [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).
   
 - Olun emin Just-ın-Time hata ayıklama [etkin](#BKMK_Enabling) içinde **Araçları** > **seçenekleri** > **hata ayıklama**  >  **Just-ın-Time**.

Bu örnekte, Visual Studio'da atan bir C# konsol uygulaması yapacaksınız bir [NullReferenceException](/dotnet/api/system.nullreferenceexception).

1. Visual Studio'da C# konsol uygulaması oluşturma (**dosya** > **yeni** > **proje** > **Visual C#**  >  **Konsol uygulaması**) adlı *ThrowsNullException*. Visual Studio'da proje oluşturma hakkında daha fazla bilgi için bkz. [izlenecek yol: basit bir uygulama oluşturma](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).
   
1. Projeyi Visual Studio'da açıldığında açın *Program.cs* dosya. Ana() yöntemi, bir çizgi konsola yazdırır ve ardından bir NullReferenceException oluşturur aşağıdaki kodla değiştirin:
   
   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```
   
1. Çözümü derlemek için ya da seçin **hata ayıklama** (varsayılan) veya **yayın** yapılandırma tıklayın ve ardından **derleme** > **çözümü yeniden derle** . 
   
   >[!NOTE]
   >- Seçin **hata ayıklama** tam hata ayıklama deneyimi için yapılandırma. 
   >- Seçerseniz [yayın](../debugger/how-to-set-debug-and-release-configurations.md) yapılandırması gerekir devre dışı [yalnızca kendi kodum](../debugger/just-my-code.md) çalışmak için bu yordamı için. Altında **Araçları** > **seçenekleri** > **hata ayıklama**, seçimini **yalnızca benim kodumu etkinleştir**.
   Derleme yapılandırmaları hakkında daha fazla bilgi için bkz. [anlama derleme yapılandırmaları](../ide/understanding-build-configurations.md).
   
1. Oluşturulan uygulamayı açma *ThrowsNullException.exe* C# proje klasöründe (*...\ThrowsNullException\ThrowsNullException\bin\Debug* veya *...\ThrowsNullException\ ThrowsNullException\bin\Release*). 
   
   Aşağıdaki komut penceresini görmeniz gerekir:
   
   ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")
   
1. **Tam zamanında hata ayıklayıcı seçin** iletişim kutusu açılır.
   
   ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")
   
   Altında **kullanılabilir hata ayıklayıcılar**seçin **yeni bir örneğini \<, tercih edilen Visual Studio sürümü >**, henüz seçili değilse. 
   
1. Seçin **Tamam**.
   
   ThrowsNullException projeyi Visual Studio'nun yeni bir örneğinde yürütme özel durumu oluşturan satırında durduruldu ile açar:
   
   ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

Bu noktada hata ayıklama başlayabilirsiniz. Gerçek bir uygulamada hata ayıkladığınız kod özel neden durum bulmak gerekir.

> [!CAUTION]
> Uygulamanızı, güvenilmeyen kod içeriyorsa, hata ayıklama ile devam edilip edilmeyeceğine karar olanak sağlayan bir güvenlik uyarısı iletişim kutusu görünür. Hata ayıklama devam etmeden önce kodun güvenilir olup olmadığına karar verin. Size kodu kendiniz mi yazdınız? Uygulama uzak makinede çalışıyorsa, işlemin adını hatırlar mısınız? Uygulamayı yerel olarak çalışıyorsa, bilgisayarınızda çalışan bir kötü amaçlı kod olasılığını göz önünde bulundurun. Kodun güvenilir olduğuna karar verirseniz, seçin **Tamam**. Aksi takdirde seçin **iptal**.

## <a name="jit_errors"></a> Sorun giderme Just-ın-Time hata ayıklama 

Just-ın-Time, hata ayıklama başlamıyor bir uygulama kilitlendiğinde Visual Studio'da etkinleştirilmiş olsa da:

- Windows hata bildirimi üzerinden hata bilgisayarınızda işleme sürüyor. 
  
  Bu sorunu gidermek için eklemek için Kayıt Defteri Düzenleyicisi'ni kullanmak bir **DWORD değerini** , **devre dışı**, ile **değer verisi** , **1**, aşağıdaki kayıt defteri anahtarları için:
  
  

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows hata raporlama**
    
  - (64-bit makineler için): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows hata raporlama**
  
  Daha fazla bilgi için [. WER ayarları](https://docs.microsoft.com/windows/desktop/wer/wer-settings).
  
- Just-ın-Time bir bilinen Windows soruna neden olabilecek hata ayıklayıcının başarısız. 
  
  Düzeltme eklemektir bir **DWORD değerini** , **otomatik**, ile **değer verisi** , **1**, aşağıdaki kayıt defteri anahtarları için:
  
  
  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**
    
  - (64-bit makineler için): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Just-ın-Time sırasında aşağıdaki hata iletilerinden görebileceğiniz hata ayıklama:

- **Kilitlenen işleme iliştirilemiyor. Belirtilen program Windows veya bir MS-DOS programı değil.**

    Hata ayıklayıcı, başka bir kullanıcı altında çalışan bir işleme ekleme denedi.

    Visual Studio'da bu sorunu geçici olarak çözmek için açık **hata ayıklama** > **iliştirme**ve hata ayıklamak istediğiniz işlemi bulun **kullanılabilir işlemler** Liste. İşlemin adını bilmiyorsanız işlem Kimliğini bulma **Visual Studio anlık hata ayıklayıcısı** iletişim. İşlemi seçin **kullanılabilir işlemler** listesinde ve seçin **iliştirme**. Seçin **Hayır** Just-ın-Time kapatmak için hata ayıklayıcı iletişim.

- **Hiçbir kullanıcı giriş yapmadığından hata ayıklayıcı başlatılamadı.**

    Just-ın-Time görüntülemek için bir kullanıcı oturumu olduğundan, konsolda oturum açmış kullanıcı bulunmayan yok iletişim hata ayıklama.

    Bu sorunu gidermek için makinede oturum açın.

- **Sınıf kayıtlı değil.**

    Hata ayıklayıcının, büyük olasılıkla bir yükleme sorunu nedeniyle kayıtlı olmayan bir COM sınıfı oluşturmayı denedi.

    Bu sorunu gidermek için Visual Studio yüklemenizi onarın veya yeniden yüklemek için Visual Studio Yükleyicisi'ni kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)
- [Hata ayıklayıcısı temel bilgileri](../debugger/getting-started-with-the-debugger.md)
- [Just-ın-Time hata ayıklama, Seçenekler iletişim kutusu](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Güvenlik Uyarısı: Güvenilmeyen bir kullanıcının sahip olduğu işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler kuşkulu görünüyorsa ya da emin değilseniz, bu işleme eklemeyin.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
