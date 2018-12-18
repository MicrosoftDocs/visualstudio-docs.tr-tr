---
title: Bir projedeki başvuruları yönetme | Microsoft Docs
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
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- Visual C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
ms.assetid: 05d1c51b-44f3-4973-8a11-6c919b08ad62
caps.latest.revision: 55
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 10fed2fa77274469a7b82a1583e825c57ca4a581
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195604"
---
# <a name="managing-references-in-a-project"></a>Bir projedeki başvuruları yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir dış bileşene karşı kodu yazın veya bağlı hizmet önce projeniz ilk buna bir başvuru içermelidir. Visual Studio bileşen veya hizmet bulmak gereken bilgileri içeren bir proje dosyası girdisinde aslında bir başvurudur.  
  
 Bir başvuru eklemek için Çözüm Gezgini'ndeki başvurular düğümü sağ tıklatın ve seçin **Başvuru Ekle**. Daha fazla bilgi için [nasıl yapılır: başvurular ekleme veya kaldırma başvuru Yöneticisi'ni kullanarak](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).  
  
 ![Visual C dilinde bir başvuru ekleyin&#43;&#43;](../ide/media/vs2015-cpp-add-reference.png "vs2015_cpp_add_reference")  
  
 Aşağıdaki bileşenler/hizmet türlerini başvuru yapabilir:  
  
-   Windows Store app başvuruları  
  
-   .NET framework sınıf kitaplıkları veya derlemeleri  
  
-   COM bileşenleri  
  
-   Diğer derlemeleri veya aynı çözüm içindeki projelerin sınıf kitaplıkları  
  
-   XML Web hizmetleri  
  
## <a name="windows-store-app-references"></a>Windows Store App başvuruları  
  
### <a name="project-references"></a>Proje başvuruları  
 Windows 10'u hedefleyen Evrensel Windows Platformu (UWP) projeleri çözümdeki diğer UWP projeleri veya Windows Store projeleri veya ikilileri başvuruları hedefleyen oluşturabilirsiniz [!INCLUDE[win81](../includes/win81-md.md)]bu projeleri, kullanımdan kaldırılan API'leri kullanmıyorsa, sağlanan Windows 10'da. Daha fazla bilgi için [UWP için Windows çalışma zamanı 8'den taşıma](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx).  
  
 Yeniden hedeflemek seçerseniz [!INCLUDE[win81](../includes/win81-md.md)] projeleri Windows 10 için bkz. [yükseltme Visual Studio projelerini taşıma, geçirme ve](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)  
  
### <a name="extension-sdk-references"></a>Uzantı SDK başvuruları  
 Evrensel Windows Platformu (UWP) hedefleyen Visual Basic, C#, C++ ve JavaScript Windows Store projelerini hedefleyen olan uzantı Sdk'lerine başvurabilir [!INCLUDE[win81](../includes/win81-md.md)]uzantı Sdk'leri, Windows 10'da kullanımdan kaldırılan API'leri kullanmıyorsa sürece. Yoksa, Windows Store projeleri tarafından başvurulabilir hedefleyen UWP bulmak için uzantı SDK satıcısı sitesini gözden geçirin.  
  
 Belirlerseniz, uygulamanız tarafından başvurulan uzantı SDK'SİNİN desteklenmediğini ve ardından aşağıdaki adımları gerçekleştirmeniz gerekir:  
  
1.  Hataya neden olan projenin adını arayın. Projenizin hedeflediği platform, proje adı yanında, parantez içinde belirtilir. Örneğin, **MyProjectName (Windows 8.1)** projenizi anlamına **MyProjectName** platform sürümünü hedeflediği [!INCLUDE[win81](../includes/win81-md.md)].  
  
2.  Desteklenmeyen uzantı SDK'sine sahip satıcının sitesine gidin ve projenizin hedeflediği platformun sürümü ile uyumlu olan bağımlılıkları içeren uzantı SDK'SİNİN sürümünü yükleyin.  
  
    > [!NOTE]
    >  Bir uzantı SDK bağımlılıklar başka uzantı SDK'lar üzerinde olup bulmanın bir yolu olan Visual Studio'yu yeniden başlatın, yeni bir C# Windows Store projesi oluşturun, projeye sağ tıklayın ve seçin **Başvuru Ekle**Git  **Windows** sekmesine gidin **uzantıları** alt sekmesinde, uzantı SDK'yı seçip sağ bölmede bakmak **başvuru Yöneticisi**. Bağımlılıkları varsa, burada listelenir.  
  
    > [!IMPORTANT]
    >  Windows 10 projenizin hedeflediği ve önceki adımda yüklenen uzantı SDK'de Microsoft Visual C++ çalışma zamanı paketinde bağımlılık vardır, Microsoft Visual C++ çalışma zamanı sürümü Windows 10 ile uyumlu olan v14.0 olduğu ve yüklü Visual Studio 2015 ile.  
  
3.  Önceki adımda yüklenen uzantı SDK'de başka uzantı SDK'lar üzerinde bağımlılıkları varsa, sdk'lerinde bağımlılıklar siteleri için Git ve platformun sürümü ile uyumlu olan bu bağımlılıkların sürümlerini yükleyin, projenin hedeflediği.  
  
4.  Visual Studio'yu yeniden başlatın ve uygulamanızı açın.  
  
5.  Sağ **başvuruları** hataya ve proje düğümünde **Başvuru Ekle**  
  
6.  Tıklayın **Windows** sekmesini ve ardından **uzantıları** alt sekmesine, ardından eski uzantı Sdk'lerinin onay kutularının işaretini kaldırın ve yeni uzantı Sdk'lerinin onay kutularını işaretleyin. **Tamam**'ı tıklatın.  
  
## <a name="adding-a-reference-at-design-time"></a>Tasarım zamanında başvuru ekleme  
 Projenizde bir derlemeye bir başvuru yaptığınızda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] derleme aşağıdaki konumlarda arar:  
  
-   Geçerli proje dizini. (Kullanarak bu derlemeleri bulabilirsiniz **Gözat** sekmesini.)  
  
-   Aynı çözüm içindeki diğer proje dizinleri. (Bu derlemeleri bulabilirsiniz **projeleri** sekmesini.)  
  
> [!NOTE]
>  Tüm projeler, mscorlib öğesine dolaylı bir başvuru içerir. Visual Basic projeleri dolaylı bir başvuru içeren `Microsoft.VisualBasic`.  
>   
>  Tüm projeleri Visual Studio'da dolaylı bir başvuru içeren `System.Core`bile `System.Core` başvurular listesinden kaldırılır.  
  
## <a name="references-to-shared-components-at-run-time"></a>Çalışma zamanında başvuruları için paylaşılan bileşenleri  
 Çalışma zamanında bileşenler projenin veya çıkış yolunda olmalıdır [genel derleme önbelleği](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) (GAC). Bu konumlardan birinde olmayan bir nesneye başvuru içeriyorsa, projeyi oluşturduğunuzda projenin çıktı yoluna başvuruyu kopyalamanız gerekir. <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> Özelliği, bu kopyanın çıkarılmak zorunda olup olmadığını gösterir. Değer ise **True**, projeyi oluşturduğunuzda proje dizinine başvuru kopyalanır. Değer ise **False**, ise başvuru kopyalanmaz.  
  
 GAC'ye kayıtlı bir özel bileşene başvuru içeren bir uygulamayı dağıtırsanız, bileşen uygulama ile birlikte açmamasından dağıtılmaz <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> ayarı. Önceki sürümlerinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ayarladığınız <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> derlemenin dağıtıldığı emin olmak için bir başvuru özelliği. Şimdi, derlemeyi \Bin klasörüne el ile eklemelisiniz. Bu, özel kod ile size tanıdık olmayan yayımlama riskini azaltarak, scrutiny altında tüm özel kodları yerleştirir.  
  
 Varsayılan olarak, <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> özelliği **False** derleme veya bileşen, genel derleme önbelleğindeyse veya bir çerçeve bileşeniyse. Aksi takdirde, değeri şuna ayarlı **True**. Projeden projeye başvurular her zaman ayarlanmış **True**.  
  
## <a name="referencing-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Bir proje ya da farklı bir .NET Framework sürümünü hedefleyen derlemeye başvurma  
 Projelere veya farklı bir .NET Framework sürümünü hedef derlemelere başvuran uygulamalar oluşturabilirsiniz. Örneğin, hedefleyen bir uygulama oluşturabilirsiniz [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] hedefleyen bir derlemeye başvuran [!INCLUDE[dnprdnext](../includes/dnprdnext-md.md)]. Önceki bir sürümünü hedefleyen bir proje oluşturursanız [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], bir başvuru projede bir proje veya bütünleştirilmiş kod hedefleyen ayarlayamazsınız [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] veya .NET Framework sürüm 4.  
  
 Daha fazla bilgi için [belirli bir .NET Framework sürümünü hedefleme](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
## <a name="project-to-project-references"></a>Projeden projeye başvurular  
 Projeden projeye başvurular, derlemeler içeren projelere başvurulardır; bunları kullanarak oluşturduğunuz **proje** sekmesi. Visual Studio, projeye bir yolu verildiğinde bir derleme bulabilirsiniz.  
  
 Bir derleme üreten bir proje varsa, proje başvurusu ve bir dosya başvurusu (aşağıya bakın) kullanmamanız gerekir. Bir proje-proje başvurusunun avantajı yapı sistemindeki projeler arasında bağımlılık oluşturmasıdır. Bağımlı proje başvuran proje oluşturulan son daraltılmasından değişmiş ise oluşturulacaktır. Bu nedenle bağımlı proje oluşturmadan başvuran projeyi oluşturmak olasıdır ve başvuru geçersiz hale gelebilir bir dosya başvurusu bir yapı bağımlılığı oluşturmaz. (Diğer bir deyişle, proje proje daha önce oluşturulmuş bir sürümüne başvuruda bulunabilir.) Bu mümkün değildir bin dizininde gerekli tek bir DLL'nin çeşitli sürümleri neden olabilir. Bu çakışma oluştuğunda, bir ileti gibi görürsünüz [Uyarı: Bu 'dosya' başvurusunun üzerine yazacağından 'proje' projesindeki ' dosya' bağımlılığı çalıştırma dizinine kopyalanamıyor ](../misc/warning-the-dependency-file-in-project-project-cannot-be-copied-to-the-run-directory-because-it-would-overwrite-the-reference-file.md). Daha fazla bilgi için bkz [bozuk başvuruları sorun giderme](../ide/troubleshooting-broken-references.md) ve [nasıl yapılır: oluşturma ve proje bağımlılıkları kaldırma](../ide/how-to-create-and-remove-project-dependencies.md).  
  
> [!NOTE]
>  Bir projenin .NET Framework hedef sürümü, sürüm 4.5 ise ve diğer projenin hedef sürümü sürüm 2, 3, 3.5 veya 4.0 ise bir proje proje başvurusu yerine dosya başvurusu oluşturulur.  
  
## <a name="file-references"></a>Dosya başvuruları  
 Dosya başvuruları, derlemelere bir Visual Studio projesinin bağlamı dışından doğrudan başvurulardır; bunları kullanarak oluşturduğunuz **Gözat** sekmesinde **başvuru Yöneticisi**. Yalnızca bir derleme veya bileşen ve çıktı olarak oluşturan Proje yoksa bir dosya başvurusu kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bozuk başvurularda sorun giderme](../ide/troubleshooting-broken-references.md)   
 [Bütünleştirilmiş kodlarla programlama](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)   
 [Nasıl Yapılır: Başvuru Yöneticisi'ni Kullanarak Başvuru Ekleme veya Kaldırma](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)

