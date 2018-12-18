---
title: Uygulama sayfası, Proje Tasarımcısı (Visual Basic) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
ms.assetid: 8cec9fea-cd92-47ff-88dd-7c928f0b4a74
caps.latest.revision: 68
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9d2b23b5570a6372b727906a63ffb51513019df7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175493"
---
# <a name="application-page-project-designer-visual-basic"></a>Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Kullanım **uygulama** sayfası Proje Tasarımcısı projenin uygulama ayarları ve özellikleri belirtin.  
  
 Erişim için **uygulama** sayfasında, bir proje düğümü seçin (değil **çözüm** düğümü) içinde **Çözüm Gezgini**. Ardından **proje**, **özellikleri** menü çubuğundaki. Proje Tasarımcısı göründüğünde tıklayın **uygulama** sekmesi.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="general-application-settings"></a>Genel Uygulama ayarları  
 Aşağıdaki seçenekler, bir uygulamanın genel ayarlarını yapılandırmak etkinleştirin.  
  
 **Derleme adı**  
 Derleme bildirimini içeren çıktı dosyasının adını belirtir. Bu özelliği değiştirirseniz **çıkış adı** özelliği de değişir. Kullanarak bir komut isteminde bu değişikliği yapabilirsiniz [/out (Visual Basic)](http://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae). Bu özelliği programlama yoluyla erişim hakkında daha fazla bilgi için bkz: <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.  
  
 **Kök ad alanı**  
 Projedeki tüm dosyalar için temel ad alanını belirtir. Örneğin, ayarlarsanız **kök Namespace** için `Project1` ve sahip olduğunuz bir `Class1` kodunuzdaki herhangi bir ad dışında ad alanı olacaktır `Project1.Class1`. Varsa bir `Class2` ad alanında `Order` kodda, kendi ad alanı olacaktır `Project1.Order.Class2`.  
  
 Silerseniz **kök Namespace**, kodu projenizin ad alanı yapısını belirtebilirsiniz.  
  
> [!NOTE]
>  Global anahtar sözcüğü kullanıyorsanız bir [Namespace deyimi](http://msdn.microsoft.com/library/a31fbd95-9ace-4c3d-bbb1-51222a2272b2), projenizin kök ad alanı dışında bir ad alanı tanımlayabilirsiniz. Silerseniz **kök Namespace**, `Global` gereksinimini ortadan kaldırır üst düzey ad olur `Global` anahtar sözcüğü bir `Namespace` deyimi. Daha fazla bilgi için bkz: "Genel anahtar sözcüğü, arama Namespace deyimleri" [Visual Basic'de ad alanları](http://msdn.microsoft.com/library/cffac744-ab8c-4f1f-ba50-732c22ab4b88).  
  
 Kodunuzda ad alanları oluşturma hakkında daha fazla bilgi için bkz: [Namespace deyimi](http://msdn.microsoft.com/library/a31fbd95-9ace-4c3d-bbb1-51222a2272b2).  
  
 Kök ad alanı özelliği hakkında daha fazla bilgi için bkz. [/RootNamespace](http://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783).  
  
 Bu özelliği programlama yoluyla erişim hakkında daha fazla bilgi için bkz: <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.  
  
 **Hedef Framework'ü (tüm yapılandırmaları)**  
 .NET Framework sürümünü belirtir, uygulama hedefler. Bu seçenek, bilgisayarınızda yüklü olan .NET Framework sürümleri bağlı olarak farklı değerlere sahip olabilir.  
  
 Varsayılan değer, belirtilen hedef Framework'ü eşleşen **yeni proje** iletişim kutusu.  
  
> [!NOTE]
>  Listelenen önkoşul paketleri [Önkoşullar iletişim kutusu](../../ide/reference/prerequisites-dialog-box.md) iletişim kutusu ilk kez açtığınızda, otomatik olarak ayarlanır. Projenin hedef çerçevesi daha sonra değiştirirseniz, yeni hedef Framework'ü el ile eşleştirmek için önkoşulları belirtmeniz gerekir.  
  
 Daha fazla bilgi için [nasıl yapılır: .NET Framework sürümü hedefleme](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) ve [Visual Studio çoklu sürüm desteğine genel bakış](../../ide/visual-studio-multi-targeting-overview.md).  
  
 **Uygulama türü**  
 Oluşturulacak uygulamanın türünü belirtir. İçin [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] uygulamaları belirtebilirsiniz **Windows Store App**, **sınıf kitaplığı**, veya **WinMD dosyası**. Çoğu diğer uygulama türleri için belirttiğiniz **Windows uygulama**, **konsol uygulaması**, **sınıf kitaplığı**, **Windows hizmeti**, veya **Web Denetim Kitaplığı**.  
  
 Bir web uygulaması projesi belirtmelisiniz **sınıf kitaplığı**.  
  
 Belirtirseniz **WinMD dosyası** seçenek türleri tüm Windows programlama dilini çalışma zamanına öngörülen. Proje bir WinMD dosyası olarak çıkış paketleme tarafından uygulamanın birden çok dilde kod ve kodu yazdığınız gibi birlikte çalışmak tümü aynı dilde. Kullanabileceğiniz **WinMD dosyası** seçeneği de dahil olmak üzere Windows çalışma zamanı kitaplıkları hedefleyen çözümler için [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] uygulamalar. Daha fazla bilgi için [C# ve Visual Basic'te Windows çalışma zamanı bileşenleri oluşturma](http://go.microsoft.com/fwlink/?LinkId=231895).  
  
> [!NOTE]
>  Windows çalışma zamanı türleri, böylece bunları hangi dil kullanır yerel nesneler olarak görünürler yansıtabilirsiniz. Örneğin, isteğe bağlı olarak, Windows çalışma zamanı ile etkileşim JavaScript uygulamaları JavaScript nesneleri bir dizi kullanın ve C# uygulamaları kitaplığı bir .NET nesneleri koleksiyon olarak kullanın. Projenin çıkış bir WinMD dosyası olarak paketleyerek Windows çalışma zamanı kullanan aynı teknolojiyi yararlanabilir.  
  
 Hakkında daha fazla bilgi için **uygulama türü** özelliğine bakın [/target (Visual Basic)](http://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c). Bu özelliğe program aracılığıyla erişme hakkında daha fazla bilgi için bkz: <xref:VSLangProj.ProjectProperties.OutputType%2A>.  
  
 **Simgesi**  
 İstediğiniz, program simge olarak kullanılacak .ico dosyasını seçer. Seçin  **\<Gözat … >** için varolan grafiği gidin. Bkz: [/win32icon](http://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) (veya [/win32icon (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138)) daha fazla bilgi için. Bu özelliğe program aracılığıyla erişmek için bkz: <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.  
  
 **Başlangıç formu / Başlangıç nesnesi / başlangıç URI'si**  
 Uygulamanın başlangıç formu ya da giriş noktası belirtir.  
  
 Varsa **etkinleştir uygulama çerçevesi** seçilir (varsayılan), bu liste başlıklı **başlangıç formu** ve yalnızca bir form uygulama çerçevesi yalnızca başlangıç formları desteklediğinden değil nesneleri gösterir.  
  
 Projeyi WPF tarayıcı uygulaması ise, bu liste başlıklı **başlangıç URI**, ve varsayılan **Page1.xaml**. **Başlangıç URI** listesi uygulama başlatıldığında uygulama görüntüleyen kullanıcı arabirimi kaynağı (XAML öğesi) belirtmenize imkan tanır. Daha fazla bilgi için bkz. <xref:System.Windows.Application.StartupUri%2A>.  
  
 Varsa **etkinleştir uygulama çerçevesi** temizlendiğinde, bu liste olur **Başlangıç nesnesi** ve formlar ve sınıflar veya modülleriyle gösterir bir `Sub Main`.  
  
 **Başlangıç nesnesi** uygulama yüklenirken çağrılacak giriş noktasını tanımlar. Genellikle bu, uygulamanızda ya da çok ana formu ayarlandığından `Sub Main` yordamı, uygulama başlatıldığında çalıştırmanız gerekir. Sınıf kitaplıkları, bir giriş noktası olmadığı için tek seçenektir bu özellik için **(hiçbiri)**. Daha fazla bilgi için [/main](http://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0). Bu özelliğe program aracılığıyla erişmek için bkz: <xref:VSLangProj.ProjectProperties.StartupObject%2A>.  
  
 **Derleme bilgileri**  
 Görüntülemek için bu düğmeye tıklayın [derleme bilgileri iletişim kutusu](../../ide/reference/assembly-information-dialog-box.md).  
  
 **Uygulama Framework'ü etkinleştir**  
 Bir proje uygulama çerçevesi kullanıp kullanmayacağını belirtir. Bu seçenek ayarı kullanılabilir seçenekleri etkiler **başlangıç formu**/**Başlangıç nesnesi**.  
  
 Bu onay kutusu seçili değilse, standart uygulamanızın kullandığı `Sub Main`. Bu onay kutusunu işaretleyerek özellikleri sağlayan **Windows Uygulama Çerçevesi Özellikleri** bölümünde ve ayrıca bir başlangıç formu seçmenizi gerektirir.  
  
 Bu onay kutusu işaretli değilse, uygulamanızın özel kullandığı `Sub Main` belirttiğiniz **başlangıç formu**. Bu durumda, bir başlangıç nesnesi belirtebilirsiniz (özel `Sub Main` bir yöntem veya bir sınıf) veya bir form. Ayrıca, seçeneklerinde **Windows Uygulama Çerçevesi Özellikleri** bölümü kullanılamıyor.  
  
 **Windows ayarlarını görüntüle**  
 Oluştur ve app.manifest dosyası açmak için bu düğmeye tıklayın. Visual Studio, uygulama için bildirim verileri oluşturmak için bu dosyayı kullanır. Değiştirerek kümesi UAC yürütme düzeyi istenen sonra `<requestedExecutionLevel>` App.manifest'te yer aşağıda gösterildiği gibi etiketleyin:  
  
 `<requestedExecutionLevel level="asInvoker" />`  
  
 ClickOnce çalışır bir düzeyde `asInvoker` veya sanallaştırılmış modunda (bildirim üretme yok). Sanallaştırılmış modunu belirtmek için tüm etiket app.manifest kaldırın.  
  
 Bildirim oluşturma hakkında daha fazla bilgi için bkz: [Windows Vista'da ClickOnce dağıtımı](../../deployment/clickonce-deployment-on-windows-vista.md).  
  
## <a name="windows-application-framework-properties"></a>Windows uygulama Çerçeve Özellikleri  
 Aşağıdaki ayarlar kullanılabilir **Windows Uygulama Çerçevesi Özellikleri** bölümü. Bu seçenekler kullanılabilir yalnızca **etkinleştir uygulama çerçevesi** onay kutusu seçilidir. Bunu izleyen bir bölümde anlatılmaktadır **Windows Uygulama Çerçevesi Özellikleri** Windows Presentation Foundation (WPF) uygulamaları için ayarları.  
  
 **XP görsel stilleri etkinleştirme**  
 Etkinleştirir ya da olarak da bilinen Windows XP görsel stillerini devre dışı bırakır *Windows XP temalarını*. Windows XP görsel stilleri, örneğin, yuvarlatılmış köşeler ve dinamik renkleri denetimleriyle etkinleştirin. Varsayılan durumda etkindir. Windows XP görsel stilleri hakkında daha fazla bilgi için bkz: [Windows XP özellikleri ve Windows Forms denetimleri](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)).  
  
 **Tek örnek uygulama**  
 Kullanıcıların uygulama birden çok örneğini çalıştırmasını engellemek için bu onay kutusunu seçin. Varsayılan ayar için bu onay kutusu işaretli değildir. Bu ayar, uygulamanın çalıştırılması için birden fazla örneği sağlar.  
  
 **My.Settings kapanışında Kaydet**  
 Uygulamanın belirtmek için bu onay kutusunu işaretleyin `My.Settings` ayarları, kullanıcıların bilgisayarlarını kapattığınızda kaydedilir. Varsayılan ayar etkindir. Bu seçenek devre dışı bırakılırsa, uygulama ayarlarını el ile çağırarak kaydedebilir `My.Settings.Save`.  
  
 **Kimlik doğrulama modu**  
 Seçin **Windows** (şu anda oturum açmış kullanıcıyı tanımlamak için Windows kimlik doğrulaması kullanımını belirlemek için varsayılan). Çalışma zamanında bu bilgileri kullanarak alabilirsiniz `My.User` nesne. Seçin **uygulama tanımlı** varsayılan Windows kimlik doğrulama yöntemleri kullanmak yerine, kullanıcıların kimliklerini doğrulamak için kendi kodunuzu sağlayıp sağlamayacağınızı.  
  
 **Kapatma**  
 Seçin **başlangıç formu kapattığı zaman** (uygulama çıkış form başlangıç formu olarak ayarladığınızda, kapatır, diğer forms açık olsalar bile belirtmek için varsayılan). Seçin **zaman son formu kapanır** uygulamanın son formu kapatıldığında veya zaman çıkış belirtmek için `My.Application.Exit` veya `End` deyimi açıkça çağrılır.  
  
 Seçin **açık kapatma sırasında** açıkça çağırdığınızda uygulamadan çıkın belirtmek için `Shutdown`.  
  
 Seçin **son pencereyi** uygulama son pencere kapandığında veya açıkça çağırmanız exit belirtmek için `Shutdown`. Varsayılan ayar budur.  
  
 Seçin **ana pencereyi** uygulamanın ana pencere kapandığında veya açıkça çağırdığınızda çıkmak belirtmek için `Shutdown`.  
  
 **Giriş ekranı**  
 Giriş ekranı kullanmak istediğiniz form seçin. Daha önce bir giriş ekranı bir form veya şablon kullanarak oluşturmuş olmanız gerekir. Varsayılan değer **(hiçbiri)**.  
  
 **Uygulama olaylarını görüntüle**  
 Uygulama framework olayları için olay içine yazabileceğiniz bir olayları kod dosyasını görüntülemek için bu düğmeye tıklayın `Startup`, `Shutdown`, `UnhandledException`, `StartupNextInstance` ve `NetworkAvailabilityChanged`. Ayrıca, belirli uygulama framework yöntemlerini geçersiz kılabilirsiniz. Örneğin, Karşılama ekranında görünen davranışını geçersiz kılarak değiştirebileceğiniz `OnInitialize`.  
  
### <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-applications"></a>Windows Presentation Foundation (WPF) uygulamaları için Windows uygulama Çerçeve Özellikleri  
 Aşağıdaki ayarlar kullanılabilir **Windows Uygulama Çerçevesi Özellikleri** bölümünde Proje bir Windows Presentation Foundation uygulaması olduğunda. Bu seçenekler kullanılabilir yalnızca **etkinleştir uygulama çerçevesi** onay kutusu seçilidir. Bu tabloda listelenen seçeneklerden yalnızca WPF uygulamaları ya da WPF tarayıcı uygulamaları için kullanılabilir. WPF kullanıcı denetimi veya özel denetim kitaplığı için kullanılamaz.  
  
 **Kapatma**  
 Bu özellik yalnızca Windows Presentation Foundation uygulamaları için geçerlidir.  
  
 Seçin **açık kapatma sırasında** açıkça çağırdığınızda uygulamadan çıkın belirtmek için <xref:System.Windows.Application.Shutdown%2A>.  
  
 Seçin **son pencereyi** uygulama son pencere kapandığında veya açıkça çağırmanız exit belirtmek için <xref:System.Windows.Application.Shutdown%2A>. Varsayılan ayar budur.  
  
 Seçin **ana pencereyi** uygulamanın ana pencere kapandığında veya açıkça çağırdığınızda çıkmak belirtmek için <xref:System.Windows.Application.Shutdown%2A>.  
  
 Bu ayar kullanma hakkında daha fazla bilgi için bkz. <xref:System.Windows.Application.Shutdown%2A>  
  
 **XAML Düzenle**  
 Açın ve uygulama tanımı dosyası (Application.xaml) XAML Düzenleyicisi'nde değiştirmek için bu düğmeye tıklayın. Bu düğmeye tıkladığınızda, uygulama tanımı düğümde Application.xaml açılır. Kaynakları tanımlama gibi belirli görevleri gerçekleştirmek için bu dosyayı düzenlemeniz gerekebilir. Uygulama tanımı dosyası mevcut değilse, Proje Tasarımcısı tane oluşturur.  
  
 **Uygulama olaylarını görüntüle**  
 Görüntülemek için bu düğmeye tıklayın `Application` bir kod düzenleyicisi kısmi sınıf dosyasında (Application.xaml.vb). Dosya mevcut değilse, Proje Tasarımcısı uygun sınıf ve ad alanına sahip bir tane oluşturur.  
  
 <xref:System.Windows.Application> Nesne (örneğin, uygulama başlatma veya kapatma) belirli uygulama durumu değişiklikleri meydana geldiğinde olayları başlatır. Bu sınıf sunan olayları tam bir listesi için bkz. <xref:System.Windows.Application>. Bu olaylar kullanıcı kod bölümünde işlenmektedir `Application` kısmi sınıf.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
[Uygulama özelliklerini yönetme](../../ide/application-properties.md) [Office çözümlerinde kod yazma](http://msdn.microsoft.com/library/2d4d8fd0-e881-4829-976f-0d1a9221dec0)



