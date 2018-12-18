---
title: Önkoşullar İletişim Kutusu
ms.date: 06/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5faf8e34a9aca77cd6762b5409919fac0978caf7
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176934"
---
# <a name="prerequisites-dialog-box"></a>Önkoşullar iletişim kutusu

**Önkoşulları** iletişim kutusu, hangi önkoşul bileşenlerinin yüklendiğini, nasıl yüklendiğini ve yüklü paketleri sıra belirtir.

![Visual Studio'da, Önkoşullar iletişim kutusu](media/prerequisites-dialog-box.png)

İletişim kutusuna erişmek için bir proje düğümü seçin **Çözüm Gezgini**ve ardından **proje** > **özellikleri**. Zaman **Proje Tasarımcısı** görüntülenirse, seçin **Yayımla** sekmesine tıklayın ve ardından **önkoşulları**. Projeler kurmak üzerinde **proje** menüsünde tıklatın **özellikleri**. Zaman **özellik sayfaları** iletişim kutusu görüntülendikten sonra **önkoşulları**.

## <a name="uielement-list"></a>UIElement listesi

|Öğe|Açıklama|
|-------------|-----------------|
|**Önkoşul bileşenlerini yüklemek için Kurulum programı oluşturma**|Uygulamanızın Kurulum programına Önkoşul bileşenlerini içerir (*Setup.exe*) ve böylece bunlar uygulamanızdan önce bağımlılık sırasına göre yüklenmesi. Varsayılan olarak, bu seçenek seçilidir. Seçilmezse, hiçbir *Setup.exe* oluşturulur.|
|**Hangi önkoşulların yükleneceğini seçin**|.NET Framework ve C++ çalışma zamanı kitaplıkları gibi bileşenlerin yüklenip yüklenmeyeceğini belirtir.<br /><br />Örneğin, onay kutusunu seçerek yanındaki **SQL Server 2012 Express**, belirttiğiniz Kurulum programının bu bileşenin hedef bilgisayarda yüklü ve yüklü değilse yükleyin olup olmadığını doğrulamanız gerekir.<br /><br />Her ön koşu paketi hakkında ayrıntılı bilgi için bkz: [Önkoşullar bilgi](#prerequisites-information).|
|**Bileşen satıcısının web sitesinden önkoşulları karşıdan yükleyin**|Önkoşul bileşenlerinin satıcının Web sitesinden yüklenmesi gerektiğini belirtir. Varsayılan seçenek budur.|
|**Uygulamamla aynı konumdan önkoşulları karşıdan yükleyin**|Önkoşul bileşenlerin uygulama ile aynı konumdan yüklenmesi gerektiğini belirtir. Bu, tüm önkoşul paketleri yayımlama konumuna kopyalar. Bu seçeneğin çalışması için önkoşul paketleri geliştirme bilgisayarında olmalıdır.|
|**Aşağıdaki konumdan önkoşulları karşıdan yükleyin**|Önkoşul bileşenlerinin girdiğiniz konumdan yüklenmesi gerektiğini belirtir. Kullanabileceğiniz **Gözat** düğmesine bir konum seçin.|

## <a name="prerequisites-information"></a>Önkoşullar bilgisi

Görünen önkoşul bileşenleri **önkoşulları** farklı aşağıdaki listede bu iletişim kutusu. Listelenen önkoşul paketleri **Önkoşullar iletişim kutusu** iletişim kutusunu ilk açışınızda otomatik olarak ayarlanır. Projenin hedef çerçevesi daha sonra değiştirirseniz, yeni hedef Framework'ü el ile eşleştirmek için önkoşulları seçmeniz gerekir.

|Öğe|Açıklama|
|-------------|-----------------|
|**.NET framework 3.5 SP1**|Bu paket aşağıdakileri yükler:<br /><br /> -.NET framework sürümleri 2.0, 3.0 ve 3.5.<br />-(X86) ve 64-bit (x64) 32-bit işletim sistemlerinde tüm .NET Framework sürümleri için destek.<br />-Paketle yüklenen her .NET Framework sürümü için dil paketleri.<br />-.NET Framework 2.0 ve 3.0 için hizmet paketleri.<br /><br /> .NET framework 3.0, Windows Vista ile bulunur ve .NET Framework 3.5 Visual Studio'ya dahildir. Hedef çerçeve kümesi ve 32-bit işletim sistemleri için derlenen tüm Visual Basic ve C# projeleri için .NET framework 3.5 gereklidir **.NET Framework 3.5**ve 64 bit için derlenen Visual Basic ve C# projeleri işletim sistemleri. (IA64 desteklenmiyor.) Visual Basic ve C# projeleri varsayılan olarak herhangi bir CPU mimarisi için derlendiğine dikkat edin. Daha fazla bilgi için [Visual Studio çoklu sürüm desteğine genel bakış](../../ide/visual-studio-multi-targeting-overview.md) ve [64-bit uygulamalar için önkoşulları dağıtma](../../deployment/deploying-prerequisites-for-64-bit-applications.md).|
|**Microsoft .NET Framework 4.x**|Bu paket, .NET Framework'ü yükler 4.x x86 ve x64 platformlar için.|
|**SQL Server 2014 (x64 ve x86) için Microsoft System CLR Types**|Bu paket, x64 ya da x86 için SQL Server 2014 için Microsoft System CLR Types yükler.|
|**SQL Server 2008 R2 Express**|Bu paket, Microsoft SQL Server 2008 R2 Express, ücretsiz bir Microsoft SQL Server 2008 R2, küçük web, sunucu veya Masaüstü uygulamaları için ideal bir veritabanı sürümünü yükler. Ücretsiz geliştirme ve üretim için kullanılabilir.|
|**SQL Server 2012 Express**|Bu paket, Microsoft SQL Server 2012 Express'i yükler.|
|**SQL Server 2012 Express LocalDB**|Bu paket, Microsoft SQL Server 2012 Express LocalDB yükler.|
|**Visual C++ "14" çalışma zamanı kitaplıkları (ARM)**|Bu paket, Microsoft Windows işletim sistemi için programlama rutinlerini sağlayan Visual C++ çalışma zamanı kitaplıklarını Itanium mimarisi için yükler. Bu yordamlar C ve C++ dillerinin sağlanmayan birçok ortak programlama görevlerini otomatikleştirin.<br /><br /> Daha fazla bilgi için [C çalışma zamanı kitaplığı başvurusu](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Visual C++ "14" çalışma zamanı kitaplıklarının (x64)**|Bu paket, işletim sistemleri, Microsoft Windows işletim sistemi için programlama rutinlerini sağlayan x64 için Visual C++ çalışma zamanı kitaplıklarını yükler. Bu yordamlar C ve C++ dillerinin sağlanmayan birçok ortak programlama görevlerini otomatikleştirin.<br /><br /> Daha fazla bilgi için [C çalışma zamanı kitaplığı başvurusu](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Visual C++ "14" çalışma zamanı kitaplıklarının (x86)**|Bu paket, işletim sistemleri, Microsoft Windows işletim sistemi için programlama rutinlerini sağlayan x86 için Visual C++ çalışma zamanı kitaplıklarını yükler. Bu yordamlar C ve C++ dillerinin sağlanmayan birçok ortak programlama görevlerini otomatikleştirin.<br /><br /> Daha fazla bilgi için [C çalışma zamanı kitaplığı başvurusu](/cpp/c-runtime-library/c-run-time-library-reference).|

## <a name="see-also"></a>Ayrıca bkz.

- [Yayın Sayfası, Proje Tasarımcısı](../../ide/reference/publish-page-project-designer.md)
- [Uygulama Dağıtımının Önkoşulları](../../deployment/application-deployment-prerequisites.md)
- [64 bit Uygulamalar için Dağıtım Önkoşulları](../../deployment/deploying-prerequisites-for-64-bit-applications.md)
- [Visual Studio Çoklu Sürüm Desteğine Genel Bakış](../../ide/visual-studio-multi-targeting-overview.md)