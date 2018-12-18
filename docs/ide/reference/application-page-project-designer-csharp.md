---
title: Uygulama sayfasındaki C# proje özellikleri
ms.date: 10/30/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6ac755bfab72a2e87b652bfb92d3343b46ff45dc
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672827"
---
# <a name="application-page-project-designer-c"></a>Uygulama Sayfası, Proje Tasarımcısı (C#)

Kullanım **uygulama** sayfasının **Proje Tasarımcısı** projenin uygulama ayarları ve özellikleri belirtmek için.

Erişim için **uygulama** sayfasında, bir proje düğümü seçin (değil **çözüm** düğümü) içinde **Çözüm Gezgini**. Ardından **proje** > **özellikleri** menü çubuğundaki. Zaman **Proje Tasarımcısı** görünen tıklayın **uygulama** sekmesi.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Genel Uygulama ayarları

Aşağıdaki seçenekler uygulama genel ayarlarını yapılandırmak etkinleştirin.

**Derleme adı**

Derleme bildirimi tutacak çıkış dosyasının adını belirtir. Bu özellik ayrıca değiştirilir **çıkış adı** özelliği.

Kullanarak komut satırından bu değişikliği yapabilirsiniz [/out (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).

Bu özelliğe program aracılığıyla erişmek için bkz: <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**Varsayılan ad alanı**

Projeye eklenen dosyaları için temel ad alanını belirtir.

Bkz: [ad alanı](/dotnet/csharp/language-reference/keywords/namespace) kodunuzda ad alanları oluşturma hakkında daha fazla bilgi için.

Bu özelliğe program aracılığıyla erişmek için bkz: <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Hedef Çerçeve**

.NET Framework sürümünü belirtir, uygulama hedefler. Bu seçenek, bilgisayarınızda yüklü olan .NET Framework sürümleri bağlı olarak farklı değerlere sahip olabilir.

Varsayılan olarak, seçtiğiniz hedef Framework'ü aynı değerdir **yeni proje** iletişim kutusu.

> [!NOTE]
> Listelenen önkoşul paketleri [Önkoşullar iletişim kutusu](../../ide/reference/prerequisites-dialog-box.md) iletişim kutusunu ilk açışınızda otomatik olarak ayarlanır. Projenin hedef çerçevesi daha sonra değiştirirseniz, yeni hedef Framework'ü el ile eşleştirmek için önkoşulları seçmeniz gerekir.

Daha fazla bilgi için [nasıl yapılır: .NET Framework sürümü hedefleme](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) ve [Visual Studio çoklu sürüm desteğine genel bakış](../../ide/visual-studio-multi-targeting-overview.md).

**Çıkış türü**

Oluşturulacak uygulamanın türünü belirtir. Proje türüne bağlı olarak farklı değerler. Örneğin, bir **konsol uygulaması** belirtebileceğiniz projesi **Windows uygulama**, **konsol uygulaması**, veya **sınıf kitaplığı** olarak Çıkış türü.

Bir web uygulaması projesi belirtmelisiniz **sınıf kitaplığı**.

Hakkında daha fazla bilgi için **çıkış türü** özelliğine bakın [/target (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).

Bu özelliği programlama yoluyla erişim hakkında daha fazla bilgi için bkz: <xref:VSLangProj.ProjectProperties.OutputType%2A>.

**Bağlama yeniden yönlendirmelerini otomatik olarak oluştur**

Uygulamanız veya bileşenleri aynı derlemenin birden fazla sürümüne başvuruyorsa, bağlama yeniden yönlendirmeleri projenize eklenir. Bağlama yeniden yönlendirmeleri proje dosyasında el ile tanımlamak istiyorsanız seçimini **otomatik oluştur bağlama yönlendirmeleri**. Bu onay kutusunu Visual Studio 2017 sürüm 15.7 sürümünde kullanıma sunulmuştur.

Yeniden yönlendirme hakkında daha fazla bilgi için bkz. [derleme sürümlerini yeniden yönlendirme](/dotnet/framework/configure-apps/redirect-assembly-versions).

**Başlangıç nesnesi**

Uygulama yüklenirken çağrılacak giriş noktasını tanımlar. Bu uygulama ya da çok ana forma ya da genel olarak ayarlanmıştır `Main` yordamı, uygulama başlatıldığında çalıştırmanız gerekir. Sınıf kitaplıkları, bir giriş noktası olmadığı için tek seçenektir bu özellik için **(ayarlanmamış)**.

Varsayılan olarak, bir WPF uygulaması projesinde bu seçeneği ayarlanır **(ayarlanmamış)**. Diğer seçenek \[ProjeAdı] .app. Bir WPF projesinde, başlangıç URI'ın bir kullanıcı Arabirimi kaynak uygulaması başladığında yüklenmesini ayarlamanız gerekir. Bunu yapmak için açık *Application.xaml* ayarlayın ve dosya projenizde `StartupUri` özelliğini bir *.xaml* projenizde, aşağıdaki gibi dosya *gt;Window1.XAML*. Kabul edilebilir kök öğeleri listesi için bkz. <xref:System.Windows.Application.StartupUri%2A>. Ayrıca tanımlamalıdır bir `public static void Main()` projedeki bir sınıftaki yöntemi. Bu sınıf görünür **Başlangıç nesnesi** olarak listesinde *ProjectName.ClassName*. Ardından, sınıf Başlangıç nesnesi seçebilirsiniz.

Bkz: [/Main (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) daha fazla bilgi için. Bu özelliğe program aracılığıyla erişmek için bkz: <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

**Derleme bilgileri**

Bu düğme açar [derleme bilgilerini](../../ide/reference/assembly-information-dialog-box.md) iletişim kutusu.

## <a name="resources"></a>Kaynaklar

**Kaynakları** seçenekleri, uygulamanızın kaynak ayarları yapılandırmanıza yardımcı olur.

**Simge ve bildirim**

Varsayılan olarak, bu radyo düğmesi seçilir ve **simgesi** ve **bildirim** seçenekleri etkinleşir. Bu, kendi simgesini seçin veya farklı bildirim oluşturma seçenekleri seçmenizi sağlar. Bu radyo düğmesi projesi için kaynak dosyasını sunuyorsunuz sürece seçili bırakın.

**Simgesi**

Kümeleri *.ico* , program simgesi kullanmak istediğiniz dosya. Tıklayın **Gözat** varolan grafiği için göz atın veya istediğiniz dosyanın adını yazın. Bkz: [/win32icon (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option) daha fazla bilgi için.

Bu özelliğe program aracılığıyla erişmek için bkz: <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

**Bildirimi**

Windows Vista kullanıcı hesabı denetimi (UAC altında) uygulama çalışırken bir bildirim üretme seçeneğini belirler. Bu seçenek, aşağıdaki değerlere sahip olabilir:

- **Varsayılan ayarlarla bildirimi katıştırmak**. Windows Güvenlik bilgisini uygulamanın yürütülebilir dosyasına katıştırma için olan belirten Windows Vista'da, Visual Studio çalıştığı zamanki destekler `requestedExecutionLevel` olması `AsInvoker`. Varsayılan seçenek budur.

- **Bir bildirim olmadan uygulama oluşturma**. Bu yöntem olarak da bilinen *sanallaştırma*. Eski uygulamalarla uyumluluk için bu seçeneği kullanın.

- **Properties\app.manifest**. Bu seçenek, ClickOnce veya Registration-Free COM tarafından dağıtılan uygulamalar için gereklidir Bir uygulamayı ClickOnce dağıtımını kullanarak yayımlarsanız **bildirim** için bu seçenek otomatik olarak ayarlanır.

**Kaynak dosyası**

Proje için kaynak dosyası sağlarken bu radyo düğmesini seçin. Bu seçeneği devre dışı bırakır **simgesi** ve **bildirim** seçenekleri.

Bir yol adı girin veya Gözat düğmesini kullanın (**...** ) bir Win32 kaynak dosyası projeye eklenecek.