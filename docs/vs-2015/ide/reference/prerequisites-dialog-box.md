---
title: Önkoşullar iletişim kutusu | Microsoft Docs
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
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Prerequisites dialog box
ms.assetid: 53ac863c-77a0-409b-91e5-7a4bd8b8474e
caps.latest.revision: 79
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6aff33e7129123e2f910116a5d9352944e1c064a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183956"
---
# <a name="prerequisites-dialog-box"></a>Önkoşullar İletişim Kutusu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Bu iletişim kutusu, hangi önkoşul bileşenlerinin yüklendiğini, nasıl yüklendiğini ve sıra paketlerin yüklü olduğunu belirtir.  
  
 Bu iletişim kutusuna erişmek için bir proje düğümü seçin **Çözüm Gezgini**ve ardından **proje** menüsünde tıklatın **özellikleri**. Zaman **Proje Tasarımcısı** görünen tıklayın **Yayımla** sekmesi. Üzerinde **Yayımla** sayfasında **önkoşulları**. Projeler kurmak üzerinde **proje** menüsünde tıklatın **özellikleri**. Zaman **özellik sayfaları** iletişim kutusu görüntülendikten sonra **önkoşulları**.  
  
## <a name="uielement-list"></a>UIElement Listesi  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|**Önkoşul bileşenlerini yüklemek için Kurulum programı oluşturma**|Uygulamanızdan önce bağımlılık sırasına göre yüklenir, böylece uygulamanızın Kurulum programı (Setup.exe) Önkoşul bileşenlerini içerir. Varsayılan olarak, bu seçenek seçilidir. Seçilmezse, hiçbir Setup.exe oluşturulmaz.|  
|**Hangi önkoşulların yükleneceğini seçin**|Gibi bileşenlerin yüklenip yüklenmeyeceğini belirtir [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], Crystal Reports ve benzeri.<br /><br /> Örneğin, onay kutusunu seçerek yanındaki **SQL Server 2005 Express Edition SP2**, Kurulum programının bu bileşenin hedef bilgisayarda yüklü ve zaten yüklü değilse yükleyin doğrulamanız belirtin.<br /><br /> Her ön koşu paketi hakkında ayrıntılı bilgi için bu konunun ilerleyen bölümlerinde Önkoşullar bilgi tablosuna bakın.|  
|**Daha fazla yeniden dağıtılabilir bileşenler için Microsoft Update'i denetleyin**|Bu bağlantıyı tıklamak [bileşenleri yeniden dağıtmak için önyükleyici paketleri](http://go.microsoft.com/fwlink/?LinkId=208835) güncelleştirmeleri denetlemek için Web sitesi.|  
|**Bileşen satıcısının web sitesinden önkoşulları karşıdan yükleyin**|Önkoşul bileşenlerinin satıcının Web sitesinden yüklenmesi gerektiğini belirtir. Varsayılan seçenek budur.|  
|**Uygulamamla aynı konumdan önkoşulları karşıdan yükleyin**|Önkoşul bileşenlerin uygulama ile aynı konumdan yüklenmesi gerektiğini belirtir. Bu, tüm önkoşul paketleri yayımlama konumuna kopyalar. Bu seçeneğin çalışması için önkoşul paketleri geliştirme bilgisayarında olmalıdır.|  
|**Aşağıdaki konumdan önkoşulları karşıdan yükleyin**|Önkoşul bileşenlerinin seçtiğiniz konumdan yüklenmesi gerektiğini belirtir. Kullanabileceğiniz **Gözat** düğmesine bir konum seçin.|  
  
## <a name="prerequisites-information"></a>Önkoşullar bilgisi  
 Görünen önkoşul bileşenleri **önkoşulları** farklı aşağıdaki listede bu iletişim kutusu. Listelenen önkoşul paketleri **Önkoşullar iletişim kutusu** iletişim kutusunu ilk açışınızda otomatik olarak ayarlanır. Projenin hedef çerçevesi daha sonra değiştirirseniz, yeni hedef Framework'ü el ile eşleştirmek için önkoşulları seçmeniz gerekecektir.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|**.NET framework 3.5 SP1**|Bu paket aşağıdakileri yükler:<br /><br /> -.NET framework sürümleri 2.0, 3.0 ve 3.5.<br />-(X86) ve 64-bit (x64) 32-bit işletim sistemlerinde tüm .NET Framework sürümleri için destek.<br />-Paketle yüklenen her .NET Framework sürümü için dil paketleri.<br />-.NET Framework 2.0 ve 3.0 için hizmet paketleri.<br /><br /> .NET framework 3.0, Windows Vista ile ve .NET Framework 3.5 ile birlikte [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Hedef çerçeve kümesi ve 32-bit işletim sistemleri için derlenen tüm Visual Basic ve Visual C# projeleri için .NET framework 3.5 gereklidir **.NET Framework 3.5**ve Visual Basic ve Visual C# projeleri 64-bit işletim sistemleri için derlenmiş. (IA64 desteklenmiyor.) Visual Basic ve Visual C# projeleri varsayılan olarak herhangi bir CPU mimarisi için derlendiğine dikkat edin. Daha fazla bilgi için [Visual Studio çoklu sürüm desteğine genel bakış](../../ide/visual-studio-multi-targeting-overview.md), [.NET Framework yeniden dağıtma](http://msdn.microsoft.com/en-us/a18d0456-fd89-493e-97f4-756505bfe287), ve [64-bit uygulamalar için önkoşulları dağıtma](../../deployment/deploying-prerequisites-for-64-bit-applications.md).<br /><br /> Varsayılan olarak, bu öğe seçilidir.|  
|**.NET framework 3.5 SP1 istemci profili**|.NET Framework istemci profili, bir tam .NET Framework 3.5, istemci uygulamaları hedefleyen SP1 alt kümesidir. Bu, bir Windows Presentation Foundation (WPF), Windows Forms, Windows Communication Foundation (WCF) ve ClickOnce özellikleri altkümesini sağlar. Bu hızlı dağıtım senaryolarını WPF, Windows Forms, WCF ve konsol uygulamaları için .NET Framework istemci Profili'ni hedefleyen sağlar. Daha fazla bilgi için [.NET Framework istemci profili](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).|  
|**Microsoft .NET Framework 4 (x86 ve x64)**|Bu paket x86 ve x64 platformlar için .NET Framework 4 yükler.<br /><br /> Daha fazla bilgi için [Visual Studio çoklu sürüm desteğine genel bakış](../../ide/visual-studio-multi-targeting-overview.md), [.NET Framework yeniden dağıtma](http://msdn.microsoft.com/en-us/a18d0456-fd89-493e-97f4-756505bfe287), ve [64-bit uygulamalar için önkoşulları dağıtma](../../deployment/deploying-prerequisites-for-64-bit-applications.md).<br /><br /> Varsayılan olarak, bu öğe seçilidir.|  
|**Microsoft .NET Framework 4 istemci profili (x86 ve x64)**|.NET Framework 4 istemci profili, istemci uygulamaları hedefleyen tam .NET Framework 4'ün bir alt kümesidir. Bu, bir Windows Presentation Foundation (WPF), Windows Forms, Windows Communication Foundation (WCF) ve ClickOnce özellikleri altkümesini sağlar. Bu hızlı dağıtım senaryolarını WPF, Windows Forms ve konsol uygulamaları için .NET Framework 4 istemci Profili'ni hedefleyen sağlar. Daha fazla bilgi için [.NET Framework istemci profili](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).|  
|**Microsoft Office 2007 birincil birlikte çalışma derlemeleri**|Bu paket 2007 birincil birlikte çalışma bütünleştirilmiş kodları yükler Microsoft Office ürünleri. Birincil birlikte çalışma derlemesi, yönetilen kodun bir Microsoft Office uygulamasının COM tabanlı nesne modeliyle etkileşimini sağlar. Daha fazla bilgi için [Office birincil birlikte çalışma derlemeleri](http://msdn.microsoft.com/library/aa29d12c-185f-4558-a7cd-3d85f924203d).|  
|**Microsoft Visual Basic PowerPacks sürüm 10.0**|Güç paketleri, eklentiler, denetimler, bileşenler ve Visual Basic uygulamaları geliştirmenize yardımcı olacak araçlar. Bu sürümünü içeren <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bir Windows Form içeriğini yazdırmanızı sağlayan bir bileşen ve Visual Basic 6.0 yazıcı kodunun değiştirilmeden çalıştırılmasını sağlayan yazıcı uyumluluk kitaplığı.|  
|**.NET 2.0 için Microsoft Visual F # çalışma zamanı**|Bu paket x86 ve x64 işletim geleneksel nesne yönelimli ve buyurgan (yordamsal) programlamanın yanı sıra fonksiyonel programlama için destek sağlayan sistemler için Visual F # çalışma zamanı kitaplıklarını yükler. Bu paket, uygulama veya bileşenleri yazılmışsa Visual F # ve .NET Framework 2.0, .NET Framework 3.0 veya .NET Framework 3.5 yüklü olmalıdır.<br /><br /> Daha fazla bilgi için [F # dili başvurusu](http://msdn.microsoft.com/library/16b706f8-b5f2-4ff7-b2c1-64df33cd6adf).|  
|**.NET 4.0 için Microsoft Visual F # çalışma zamanı**|Bu paket x86 ve x64 işletim geleneksel nesne yönelimli ve buyurgan (yordamsal) programlamanın yanı sıra fonksiyonel programlama için destek sağlayan sistemler için Visual F # çalışma zamanı kitaplıklarını yükler. Bu paket, uygulama veya bileşenleri yazılmışsa Visual F # ve .NET Framework 4 yüklü olmalıdır.<br /><br /> Daha fazla bilgi için [F # dili başvurusu](http://msdn.microsoft.com/library/16b706f8-b5f2-4ff7-b2c1-64df33cd6adf).|  
|**Microsoft Visual Studio 2010 Rapor Görüntüleyicisi**|Bu paket, zengin Windows Forms ve ASP.NET uygulamaları için raporlama verileri eklemek için kullanabileceğiniz Rapor Görüntüleyicisi denetimlerini yükler.|  
|**Office çalışma zamanı (x86 ve x64) için Microsoft Visual Studio 2010**|Visual Studio Office geliştirici araçları, Microsoft Office ile özelleştirilmiş iş çözümleri oluşturmak için kullanımı kolay, tümleşik araçlar sunar. Office uygulamaları kullanıcı arabirimi olarak kullanan yönetilen, akıllı istemci çözümleri oluşturabilirsiniz. Araçlar geliştiricilerin dağıtma ve bakımını kolay güvenli çözümler oluşturmasını sağlar.<br /><br /> Daha fazla bilgi için [nasıl yapılır: bir Office çözümü ClickOnce kullanarak tarafından yayımlama](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).|  
|**SQL Server 2005 Express Edition SP2 (x 86)**|Bu paket, Microsoft SQL Server 2005 Express Edition SP2, temel alan bir veritabanı uygulama yükler [!INCLUDE[sqprsqext](../../includes/sqprsqext-md.md)]. SQL Server Express, Microsoft SQL Server Desktop Engine (MSDE) için yerini almıştır. SQL Server Express, ücretsiz olup (anlaşmaya tabi olarak) yeniden dağıtılabilir ve istemci veritabanı ve temel sunucu veritabanı çalışır. Bu SQL Server 2005, aşağıdaki farklar dışında aynıdır:<br /><br /> -Hiçbir Kurumsal özellik desteklenmez.<br />-Bir CPU ile sınırlıdır.<br />-arabellek havuzu için 1 gigabayt (GB) bellek sınırı.<br />-4 GB veritabanlarının maksimum boyutu.|  
|**SQL Server 2008 Express**|Bu paket, Microsoft SQL Server 2008 Express, ücretsiz bir Microsoft SQL Server 2008, küçük web, sunucu veya Masaüstü uygulamaları için ideal bir veritabanı sürümünü yükler. Ücretsiz geliştirme ve üretim için kullanılabilir. Ücretsiz [kayıt](http://go.microsoft.com/fwlink/?LinkId=130380) SQL Server 2008 Express'in uygulamalara dağıtımı için gereklidir.<br /><br /> Önyükleyicinin aşağıda verilmiştir:<br /><br /> -Bilgisayarda SQL Server 2008 Express veya üstü varsa, konumundaki SQL Server 2008 Express veya üstü bilgisayarda kalır.<br />-Bilgisayarın herhangi bir sürümü SQL Server 2008 Express veya üstü yoksa, paket SQL Server 2008 Express SP1'ın en son sürümünü yükler.<br /><br /> SQL Server 2008 Express hakkında daha fazla bilgi edinmek için [ http://go.microsoft.com/fwlink/?LinkId=183586 ](http://go.microsoft.com/fwlink/?LinkId=183586).|  
|**Visual C++ 2010 Çalışma zamanı kitaplıkları (IA64)**|Bu paket, Microsoft Windows işletim sistemi için programlama rutinlerini sağlayan Visual C++ çalışma zamanı kitaplıklarını Itanium mimarisi için yükler. Bu yordamlar C ve C++ dillerinin sağlanmayan birçok ortak programlama görevlerini otomatikleştirin.<br /><br /> Daha fazla bilgi için [C çalışma zamanı kitaplığı başvurusu](http://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8).|  
|**Visual C++ 2010 Çalışma zamanı kitaplıkları (x64)**|Bu paket, işletim sistemleri, Microsoft Windows işletim sistemi için programlama rutinlerini sağlayan x64 için Visual C++ çalışma zamanı kitaplıklarını yükler. Bu yordamlar C ve C++ dillerinin sağlanmayan birçok ortak programlama görevlerini otomatikleştirin.<br /><br /> Daha fazla bilgi için [C çalışma zamanı kitaplığı başvurusu](http://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8).|  
|**Visual C++ 2010 Çalışma zamanı kitaplıkları (x86)**|Bu paket, işletim sistemleri, Microsoft Windows işletim sistemi için programlama rutinlerini sağlayan x86 için Visual C++ çalışma zamanı kitaplıklarını yükler. Bu yordamlar C ve C++ dillerinin sağlanmayan birçok ortak programlama görevlerini otomatikleştirin.<br /><br /> Daha fazla bilgi için [C çalışma zamanı kitaplığı başvurusu](http://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8).|  
|**Windows Installer 3.1**|Bu paket, Windows Installer Kurulum projelerinin yüklenmesini sağlayan Microsoft Windows Installer yeniden dağıtılabilir 3.1 sürümünü yükler. Bu, Windows Server 2003 SP1 ve sonraki önceden yüklenir.<br /><br /> Varsayılan olarak, bu öğe seçilidir.|  
|**Windows Installer 4.5**|Bu paket, Windows Installer Kurulum projelerinin yüklenmesini sağlayan Microsoft Windows Installer yeniden dağıtılabilir, sürüm 4.5 yükler.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yayımlama Sayfası, Proje Tasarımcısı](../../ide/reference/publish-page-project-designer.md)   
 [Uygulama dağıtımının önkoşulları](../../deployment/application-deployment-prerequisites.md)   
 [.NET Framework yeniden dağıtma](http://msdn.microsoft.com/en-us/a18d0456-fd89-493e-97f4-756505bfe287)   
 [64-bit uygulamalar için önkoşulları dağıtma](../../deployment/deploying-prerequisites-for-64-bit-applications.md)   
 [Visual Studio Çoklu Sürüm Desteğine Genel Bakış](../../ide/visual-studio-multi-targeting-overview.md)



