---
title: VB Proje Özellikleri'nin uygulama sayfası
ms.date: 10/30/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ceb1612ee678a005cba0be0cfb44337c126cb71
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670968"
---
# <a name="application-page-project-designer-visual-basic"></a>Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)

Kullanım **uygulama** sayfası Proje Tasarımcısı projenin uygulama ayarları ve özellikleri belirtin.

Erişim için **uygulama** sayfasında, bir proje düğümü seçin (değil **çözüm** düğümü) içinde **Çözüm Gezgini**. Ardından **proje** > **özellikleri** menü çubuğundaki. Zaman **Proje Tasarımcısı** görüntülenirse, seçin **uygulama** sekmesi.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Genel Uygulama ayarları

Aşağıdaki seçenekler, bir uygulamanın genel ayarlarını yapılandırmak etkinleştirin.

### <a name="assembly-name"></a>Derleme adı

Derleme bildirimini içeren çıktı dosyasının adını belirtir. Bu özelliği değiştirirseniz **çıkış adı** özelliği de değişir.

Kullanarak bir komut isteminden çıkış dosyasının adını belirtebilirsiniz [/out (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/out) derleyici anahtarı.

Bu özelliği programlama yoluyla erişim hakkında daha fazla bilgi için bkz: <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

### <a name="root-namespace"></a>Kök ad alanı

Projedeki tüm dosyalar için temel ad alanını belirtir. Örneğin, ayarlarsanız **kök Namespace** için `Project1` ve sahip olduğunuz bir `Class1` kodunuzdaki herhangi bir ad dışında ad alanı olacaktır `Project1.Class1`. Varsa bir `Class2` ad alanında `Order` kodda, kendi ad alanı olacaktır `Project1.Order.Class2`.

Silerseniz **kök Namespace**, kodu projenizin ad alanı yapısını belirtebilirsiniz.

> [!NOTE]
> Kullanırsanız `Global` anahtar sözcüğü bir [Namespace deyimi](/dotnet/visual-basic/language-reference/statements/namespace-statement), projenizin kök ad alanı dışında bir ad alanı tanımlayabilirsiniz. Silerseniz **kök Namespace**, `Global` gereksinimini ortadan kaldırır üst düzey ad olur `Global` anahtar sözcüğü bir `Namespace` deyimi. Daha fazla bilgi için bkz: "Genel anahtar sözcüğü, arama Namespace deyimleri" [Visual Basic'de ad alanları](/dotnet/visual-basic/programming-guide/program-structure/namespaces).

Kodunuzda ad alanları oluşturma hakkında daha fazla bilgi için bkz: [Namespace deyimi](/dotnet/visual-basic/language-reference/statements/namespace-statement).

Kök ad alanı özelliği hakkında daha fazla bilgi için bkz. [/RootNamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace).

Bu özelliği programlama yoluyla erişim hakkında daha fazla bilgi için bkz: <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

### <a name="target-framework-all-configurations"></a>Hedef Framework'ü (tüm yapılandırmaları)

.NET Framework sürümünü belirtir, uygulama hedefler. Bu seçenek, bilgisayarınızda yüklü olan .NET Framework sürümleri bağlı olarak farklı değerlere sahip olabilir.

Varsayılan değer, belirtilen hedef Framework'ü eşleşen **yeni proje** iletişim kutusu.

> [!NOTE]
> Listelenen önkoşul paketleri [Önkoşullar iletişim kutusu](../../ide/reference/prerequisites-dialog-box.md) iletişim kutusu ilk kez açtığınızda, otomatik olarak ayarlanır. Projenin hedef çerçevesi daha sonra değiştirirseniz, yeni hedef Framework'ü el ile eşleştirmek için önkoşulları belirtmeniz gerekir.

Daha fazla bilgi için [nasıl yapılır: .NET Framework sürümü hedefleme](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) ve [Visual Studio çoklu sürüm desteğine genel bakış](../../ide/visual-studio-multi-targeting-overview.md).

### <a name="application-type"></a>Uygulama türü

Oluşturulacak uygulamanın türünü belirtir. Proje türüne bağlı olarak farklı değerler. Örneğin, bir **Windows Forms uygulaması** belirtebileceğiniz projesi **Windows Forms uygulaması**, **sınıf kitaplığı**, **konsol uygulaması**, **Windows hizmeti**, veya **Web Denetim Kitaplığı**.

Bir web uygulaması projesi belirtmelisiniz **sınıf kitaplığı**.

Hakkında daha fazla bilgi için **uygulama türü** özelliğine bakın [/target (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/target). Bu özelliğe program aracılığıyla erişme hakkında daha fazla bilgi için bkz: <xref:VSLangProj.ProjectProperties.OutputType%2A>.

### <a name="auto-generate-binding-redirects"></a>Bağlama yeniden yönlendirmelerini otomatik olarak oluştur

Uygulamanız veya bileşenleri aynı derlemenin birden fazla sürümüne başvuruyorsa, bağlama yeniden yönlendirmeleri projenize eklenir. Bağlama yeniden yönlendirmeleri proje dosyasında el ile tanımlamak istiyorsanız seçimini **otomatik oluştur bağlama yönlendirmeleri**. Bu onay kutusunu Visual Studio 2017 sürüm 15.7 sürümünde kullanıma sunulmuştur.

Yeniden yönlendirme hakkında daha fazla bilgi için bkz. [derleme sürümlerini yeniden yönlendirme](/dotnet/framework/configure-apps/redirect-assembly-versions).

### <a name="startup-form--startup-object--startup-uri"></a>Başlangıç formu / Başlangıç nesnesi / başlangıç URI'si

Uygulamanın başlangıç formu ya da giriş noktası belirtir.

Varsa **etkinleştir uygulama çerçevesi** seçilir (varsayılan), bu liste başlıklı **başlangıç formu** ve yalnızca bir form uygulama çerçevesi yalnızca başlangıç formları desteklediğinden değil nesneleri gösterir.

Projeyi WPF tarayıcı uygulaması ise, bu liste başlıklı **başlangıç URI**, ve varsayılan **Page1.xaml**. **Başlangıç URI** listesi uygulama başlatıldığında uygulama görüntüleyen kullanıcı arabirimi kaynağı (XAML öğesi) belirtmenize imkan tanır. Daha fazla bilgi için bkz. <xref:System.Windows.Application.StartupUri%2A>.

Varsa **etkinleştir uygulama çerçevesi** temizlendiğinde, bu liste olur **Başlangıç nesnesi** ve formlar ve sınıflar veya modülleriyle gösterir bir `Sub Main`.

**Başlangıç nesnesi** uygulama yüklenirken çağrılacak giriş noktasını tanımlar. Genellikle bu, uygulamanızda ya da çok ana formu ayarlandığından `Sub Main` yordamı, uygulama başlatıldığında çalıştırmanız gerekir. Sınıf kitaplıkları, bir giriş noktası olmadığı için tek seçenektir bu özellik için **(hiçbiri)**. Daha fazla bilgi için [/main](/dotnet/visual-basic/reference/command-line-compiler/main). Bu özelliğe program aracılığıyla erişmek için bkz: <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

### <a name="icon"></a>Simge

İstediğiniz, program simge olarak kullanılacak .ico dosyasını seçer. Seçin  **\<Gözat … >** için varolan grafiği gidin. Bkz: [/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) (veya [/win32icon (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option)) daha fazla bilgi için. Bu özelliğe program aracılığıyla erişmek için bkz: <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

### <a name="assembly-information"></a>Derleme bilgileri

Görüntülemek için bu düğmeye tıklayın [derleme bilgileri iletişim kutusu](../../ide/reference/assembly-information-dialog-box.md).

### <a name="enable-application-framework"></a>Uygulama Framework'ü etkinleştir

Bir proje uygulama çerçevesi kullanıp kullanmayacağını belirtir. Bu seçenek ayarı kullanılabilir seçenekleri etkiler **başlangıç formu**/**Başlangıç nesnesi**.

Bu onay kutusu seçili değilse, standart uygulamanızın kullandığı `Sub Main`. Bu onay kutusunu işaretleyerek özellikleri sağlayan **Windows Uygulama Çerçevesi Özellikleri** bölümünde ve ayrıca bir başlangıç formu seçmenizi gerektirir.

Bu onay kutusu işaretli değilse, uygulamanızın özel kullandığı `Sub Main` belirttiğiniz **başlangıç formu**. Bu durumda, bir başlangıç nesnesi belirtebilirsiniz (özel `Sub Main` bir yöntem veya bir sınıf) veya bir form. Ayrıca, seçeneklerinde **Windows Uygulama Çerçevesi Özellikleri** bölümü kullanılamıyor.

### <a name="view-windows-settings"></a>Windows ayarlarını görüntüle

Oluşturmak ve açmak için bu düğmeye tıklayın *app.manifest* dosya. Visual Studio, uygulama için bildirim verileri oluşturmak için bu dosyayı kullanır. Değiştirerek kümesi UAC yürütme düzeyi istenen sonra `<requestedExecutionLevel>` içindeki *app.manifest* gibi:

`<requestedExecutionLevel level="asInvoker" />`

ClickOnce çalışır bir düzeyde `asInvoker` veya sanallaştırılmış modunda (bildirim üretme yok). Sanallaştırılmış modunu belirtmek için tüm etiket app.manifest kaldırın.

Bildirim oluşturma hakkında daha fazla bilgi için bkz: [Windows Vista'da ClickOnce dağıtımı](../../deployment/clickonce-deployment-on-windows-vista.md).

## <a name="windows-application-framework-properties"></a>Windows uygulama Çerçeve Özellikleri

Aşağıdaki ayarlar kullanılabilir **Windows Uygulama Çerçevesi Özellikleri** bölümü. Bu seçenekler kullanılabilir yalnızca **etkinleştir uygulama çerçevesi** onay kutusu seçilidir.

> [!TIP]
> Bunu izleyen bir bölümde anlatılmaktadır **Windows Uygulama Çerçevesi Özellikleri** Windows Presentation Foundation (WPF) uygulamaları için özel ayarları.

### <a name="enable-xp-visual-styles"></a>XP görsel stilleri etkinleştirme

Etkinleştirir ya da olarak da bilinen Windows XP görsel stillerini devre dışı bırakır *Windows XP temalarını*. Windows XP görsel stilleri, örneğin, yuvarlatılmış köşeler ve dinamik renkleri denetimleriyle etkinleştirin. Varsayılan durumda etkindir.

### <a name="make-single-instance-application"></a>Tek örnek uygulama

Kullanıcıların uygulama birden çok örneğini çalıştırmasını engellemek için bu onay kutusunu seçin. Bu onay kutusu için varsayılan ayar *temizlenmiş*, uygulamanın çalıştırılması için birden fazla örneği sağlar. Daha fazla bilgi için <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> olay.

### <a name="save-mysettings-on-shutdown"></a>My.Settings kapanışında Kaydet

Uygulamanın belirtmek için bu onay kutusunu işaretleyin `My.Settings` ayarları, kullanıcıların bilgisayarlarını kapattığınızda kaydedilir. Varsayılan ayar etkindir. Bu seçenek devre dışı bırakılırsa, uygulama ayarlarını el ile çağırarak kaydedebilir `My.Settings.Save`.

### <a name="authentication-mode"></a>Kimlik doğrulama modu

Seçin **Windows** (şu anda oturum açmış kullanıcıyı tanımlamak için Windows kimlik doğrulaması kullanımını belirlemek için varsayılan). Çalışma zamanında bu bilgileri kullanarak alabilirsiniz `My.User` nesne. Seçin **uygulama tanımlı** varsayılan Windows kimlik doğrulama yöntemleri kullanmak yerine, kullanıcıların kimliklerini doğrulamak için kendi kodunuzu sağlayıp sağlamayacağınızı.

### <a name="shutdown-mode"></a>Kapatma

Seçin **başlangıç formu kapattığı zaman** (uygulama çıkış form başlangıç formu olarak ayarladığınızda, kapatır, diğer forms açık olsalar bile belirtmek için varsayılan). Seçin **zaman son formu kapanır** uygulamanın son formu kapatıldığında veya zaman çıkış belirtmek için `My.Application.Exit` veya `End` deyimi açıkça çağrılır.

Seçin **açık kapatma sırasında** açıkça çağırdığınızda uygulamadan çıkın belirtmek için `Shutdown`.

Seçin **son pencereyi** uygulama son pencere kapandığında veya açıkça çağırmanız exit belirtmek için `Shutdown`. Varsayılan ayar budur.

Seçin **ana pencereyi** uygulamanın ana pencere kapandığında veya açıkça çağırdığınızda çıkmak belirtmek için `Shutdown`.

### <a name="splash-screen"></a>Giriş ekranı

Giriş ekranı kullanmak istediğiniz form seçin. Daha önce bir giriş ekranı bir form veya şablon kullanarak oluşturmuş olmanız gerekir. Varsayılan değer **(hiçbiri)**.

### <a name="view-application-events"></a>Uygulama olaylarını görüntüle

Uygulama framework olayları için olay içine yazabileceğiniz bir olayları kod dosyasını görüntülemek için bu düğmeye tıklayın `Startup`, `Shutdown`, `UnhandledException`, `StartupNextInstance` ve `NetworkAvailabilityChanged`. Ayrıca, belirli uygulama framework yöntemlerini geçersiz kılabilirsiniz. Örneğin, Karşılama ekranında görünen davranışını geçersiz kılarak değiştirebileceğiniz `OnInitialize`.

## <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-apps"></a>Windows Presentation Foundation (WPF) uygulamaları için Windows uygulama Çerçeve Özellikleri

Aşağıdaki ayarlar kullanılabilir **Windows Uygulama Çerçevesi Özellikleri** bölümünde Proje bir Windows Presentation Foundation (WPF) uygulaması olduğunda. Bu seçenekler kullanılabilir yalnızca **etkinleştir uygulama çerçevesi** onay kutusu seçilidir. Bu tabloda listelenen seçeneklerden yalnızca WPF ya da WPF için kullanılabilen tarayıcı uygulamaları. WPF kullanıcı denetimi veya özel denetim kitaplığı için kullanılamaz.

### <a name="shutdown-mode"></a>Kapatma

Bu özellik yalnızca Windows Presentation Foundation (WPF) uygulamaları için geçerlidir.

Seçin **açık kapatma sırasında** açıkça çağırdığınızda uygulamadan çıkın belirtmek için <xref:System.Windows.Application.Shutdown%2A>.

Seçin **son pencereyi** uygulama son pencere kapandığında veya açıkça çağırmanız exit belirtmek için <xref:System.Windows.Application.Shutdown%2A>. Varsayılan ayar budur.

Seçin **ana pencereyi** uygulamanın ana pencere kapandığında veya açıkça çağırdığınızda çıkmak belirtmek için <xref:System.Windows.Application.Shutdown%2A>.

Bu ayar kullanma hakkında daha fazla bilgi için bkz. <xref:System.Windows.Application.Shutdown%2A>

### <a name="edit-xaml"></a>XAML Düzenle

Bu düğme, uygulama tanımı dosyası (Application.xaml) XAML Düzenleyicisi'nde açılır. Bu düğmeye tıkladığınızda *Application.xaml* uygulama tanımı düğümde açılır. Kaynakları tanımlama gibi belirli görevleri gerçekleştirmek için bu dosyayı düzenlemeniz gerekebilir. Uygulama tanımı dosyası mevcut değilse, Proje Tasarımcısı tane oluşturur.

### <a name="view-application-events"></a>Uygulama olaylarını görüntüle

Bu düğme açar `Application` sınıf dosyası (*Application.xaml.vb*) içinde bir kod Düzenleyicisi. Dosya mevcut değilse, Proje Tasarımcısı uygun sınıf ve ad alanına sahip bir tane oluşturur.

<xref:System.Windows.Application> Nesne (örneğin, uygulama başlatma veya kapatma) belirli uygulama durumu değişiklikleri meydana geldiğinde olayları başlatır. Bu sınıf sunan olayları tam bir listesi için bkz. <xref:System.Windows.Application>. Bu olaylar kullanıcı kod bölümünde işlenmektedir `Application` kısmi sınıf.