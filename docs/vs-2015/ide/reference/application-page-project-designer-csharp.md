---
title: Uygulama sayfası, Proje Tasarımcısı (C#) | Microsoft Docs
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
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
ms.assetid: f13701a8-4e2e-4474-9d60-bb43decbe0c1
caps.latest.revision: 61
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4a130a04be7a0645fef44ff6c8ae9dcc31b55dcf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867240"
---
# <a name="application-page-project-designer-c"></a>Uygulama Sayfası, Proje Tasarımcısı (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Kullanım **uygulama** sayfasının **Proje Tasarımcısı** projenin uygulama ayarları ve özellikleri belirtmek için.  
  
 Erişim için **uygulama** sayfasında, bir proje düğümü seçin (değil **çözüm** düğümü) içinde **Çözüm Gezgini**. Ardından **proje**, **özellikleri** menü çubuğundaki. Proje Tasarımcısı göründüğünde tıklayın **uygulama** sekmesi.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="general-application-settings"></a>Genel Uygulama ayarları  
 Aşağıdaki seçenekler uygulama genel ayarlarını yapılandırmak etkinleştirin.  
  
 **Derleme adı**  
 Derleme bildirimi tutacak çıkış dosyasının adını belirtir. Bu özelliği değiştirmek de değiştirecek **çıkış adı** özelliği. Kullanarak komut satırından bu değişikliği yapabilirsiniz [/out (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5). Bu özelliğe program aracılığıyla erişmek için bkz: <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.  
  
 **Varsayılan ad alanı**  
 Projeye eklenen dosyaları için temel ad alanını belirtir.  
  
 Bkz: [ad alanı](http://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f) kodunuzda ad alanları oluşturma hakkında daha fazla bilgi için.  
  
 Bu özelliğe program aracılığıyla erişmek için bkz: <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.  
  
 **Hedef Çerçeve**  
 .NET Framework sürümünü belirtir, uygulama hedefler. Bu seçenek, bilgisayarınızda yüklü olan .NET Framework sürümleri bağlı olarak farklı değerlere sahip olabilir.  
  
 Varsayılan olarak, seçtiğiniz hedef Framework'ü aynı değerdir **yeni proje** iletişim kutusu.  
  
> [!NOTE]
>  Listelenen önkoşul paketleri [Önkoşullar iletişim kutusu](../../ide/reference/prerequisites-dialog-box.md) iletişim kutusunu ilk açışınızda otomatik olarak ayarlanır. Projenin hedef çerçevesi daha sonra değiştirirseniz, yeni hedef Framework'ü el ile eşleştirmek için önkoşulları seçmeniz gerekecektir.  
  
 Daha fazla bilgi için [nasıl yapılır: .NET Framework sürümü hedefleme](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) ve [Visual Studio çoklu sürüm desteğine genel bakış](../../ide/visual-studio-multi-targeting-overview.md).  
  
 **Uygulama türü**  
 Oluşturulacak uygulamanın türünü belirtir. İçin [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] uygulamaları belirtebilirsiniz **Windows Store App**, **sınıf kitaplığı**, veya **WinMD dosyası**. Çoğu diğer uygulama türleri için belirttiğiniz **Windows uygulama**, **konsol uygulaması**, **sınıf kitaplığı**, **Windows hizmeti**, veya **Web Denetim Kitaplığı**.  
  
 Bir web uygulaması projesi belirtmelisiniz **sınıf kitaplığı**.  
  
 Belirtirseniz **WinMD dosyası** seçenek türleri tüm Windows programlama dilini çalışma zamanına öngörülen. Proje bir WinMD dosyası olarak çıkış paketleme tarafından uygulamanın birden çok dilde kod ve kodu yazdığınız gibi birlikte çalışmak tümü aynı dilde. Windows çalışma zamanı kitaplıkları dahil olmak üzere, hedef çözümleri için bu seçeneği belirtebilirsiniz [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] uygulamalar. Daha fazla bilgi için [C# ve Visual Basic'te Windows çalışma zamanı bileşenleri oluşturma](http://go.microsoft.com/fwlink/?LinkId=231895).  
  
> [!NOTE]
>  Windows çalışma zamanı türleri, böylece bunları hangi dil kullanır yerel nesneler olarak görünürler yansıtabilirsiniz. Örneğin, isteğe bağlı olarak, Windows çalışma zamanı ile etkileşim JavaScript uygulamaları JavaScript nesneleri bir dizi kullanın ve C# uygulamaları kitaplığı bir .NET nesneleri koleksiyon olarak kullanın. Projenin çıkış bir WinMD dosyası olarak paketleyerek Windows çalışma zamanı kullanan aynı teknolojiyi yararlanabilir.  
  
 Hakkında daha fazla bilgi için **uygulama türü** özelliğine bakın [/target (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f). Bu özelliği programlama yoluyla erişim hakkında daha fazla bilgi için bkz: <xref:VSLangProj.ProjectProperties.OutputType%2A>.  
  
 **Derleme bilgileri**  
 Bu düğmeye tıklandığında görüntüler [derleme bilgileri iletişim kutusu](../../ide/reference/assembly-information-dialog-box.md).  
  
 **Başlangıç nesnesi**  
 Uygulama yüklenirken çağrılacak giriş noktasını tanımlar. Bu uygulama ya da çok ana forma ya da genel olarak ayarlanmıştır `Main` yordamı, uygulama başlatıldığında çalıştırmanız gerekir. Sınıf kitaplıkları, bir giriş noktası olmadığı için tek seçenektir bu özellik için **(ayarlanmamış)**.  
  
 Bu seçenek bir WPF tarayıcı uygulaması projesinde varsayılan olarak **(ayarlanmamış)**. Diğer seçenek *Projectname*. uygulama. İçinde bu tür bir projeye ilişkin başlangıç URI uygulama başlatıldığında bir UI kaynak yüklemek için ayarlamanız gerekir. Bunu yapmak için projenizde Application.xaml dosyasını açın ve ayarlayın `StartupUri` gt;Window1.XAML gibi projenizi bir .xaml dosyasında özelliği. Kabul edilebilir kök öğeleri listesi için bkz. <xref:System.Windows.Application.StartupUri%2A>. Tanımlamak de bir `public static void Main()` projedeki bir sınıftaki yöntemi. Bu sınıf görünür **Başlangıç nesnesi** olarak listesinde *ProjectName.ClassName*. Ardından, sınıf Başlangıç nesnesi seçebilirsiniz.  
  
 Bkz: [/Main (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049) daha fazla bilgi için. Bu özelliğe program aracılığıyla erişmek için bkz: <xref:VSLangProj.ProjectProperties.StartupObject%2A>.  
  
## <a name="resources"></a>Kaynaklar  
 Aşağıdaki seçenekler uygulama genel ayarlarını yapılandırmak etkinleştirin.  
  
 **Simge ve bildirim**  
 Varsayılan olarak, bu radyo düğmesi seçilir ve **simgesi** ve **bildirim** seçenekleri etkinleşir. Bu, kendi simgesini seçin veya farklı bildirim oluşturma seçenekleri seçmenizi sağlar. Bu radyo düğmesi projesi için kaynak dosyasını sağlanmaktadır sürece seçili bırakın.  
  
 **Simgesi**  
 İstediğiniz, program simge olarak kullanılacak .ico dosyasını seçer. Var olan bir grafik göz atmak için üç nokta düğmesine tıklayın ya da istediğiniz dosyanın adını yazın. Bkz: [/win32icon (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138) daha fazla bilgi için. Bu özelliğe program aracılığıyla erişmek için bkz: <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.  
  
 **Bildirimi**  
 Windows Vista kullanıcı hesabı denetimi (UAC altında) uygulama çalışırken bir bildirim üretme seçeneğini belirler. Bu seçenek, aşağıdaki değerlere sahip olabilir:  
  
- **Varsayılan ayarlarla bildirimi katıştırmak**. Windows Güvenlik bilgisini uygulamanın yürütülebilir dosyasına katıştırma için olan belirten Windows Vista'da, Visual Studio çalıştığı zamanki destekler `requestedExecutionLevel` olması `AsInvoker`. Varsayılan seçenek budur.  
  
- **Bir bildirim olmadan uygulama oluşturma**. Bu yöntem olarak da bilinen *sanallaştırma*. Eski uygulamalarla uyumluluk için bu seçeneği kullanın.  
  
- **Properties\app.manifest**. Bu seçenek, ClickOnce veya Registration-Free COM tarafından dağıtılan uygulamalar için gereklidir Bir uygulamayı ClickOnce dağıtımını kullanarak yayımlarsanız **bildirim** için bu seçenek otomatik olarak ayarlanır.  
  
  **Kaynak dosyası**  
  Proje için kaynak dosyası sağlarken bu radyo düğmesini seçin. Bu seçeneği devre dışı bırakır **simgesi** ve **bildirim** seçenekleri.  
  
  Bir yol adı girin veya Gözat düğmesini kullanın (**...** ) bir Win32 kaynak dosyası projeye eklenecek.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
[Uygulama özelliklerini yönetme](../../ide/application-properties.md)  
 [Office Çözümlerinde Kod Yazma](http://msdn.microsoft.com/library/2d4d8fd0-e881-4829-976f-0d1a9221dec0)



