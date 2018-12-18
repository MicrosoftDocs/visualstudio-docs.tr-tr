---
title: Bir projedeki başvuruları yönetme
ms.date: 04/11/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e772f4d861e4b16499ad9be9d7c814320e1a14f9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31950952"
---
# <a name="manage-references-in-a-project"></a>Bir projedeki başvuruları yönetme

Dış bileşen karşı kod yazın veya hizmeti bağlı önce projenize önce bir başvuru içermelidir. Aslında Visual Studio bileşen veya hizmet bulmak gerekli bilgileri içeren bir proje dosyasındaki bir giriş başvurudur.

Bir başvuru eklemek için sağ tıklayın **başvuruları** veya **bağımlılıkları** düğümünde **Çözüm Gezgini** ve **Başvuru Ekle**. Ayrıca proje düğümüne sağ tıklayın ve seçin **Ekle** > **başvuru**. Daha fazla bilgi için bkz: [nasıl yapılır: başvuru ekleyip](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

![Visual C bir başvuru ekleyin&#43;&#43;](../ide/media/vs2015_cpp_add_reference.png)

Aşağıdaki bileşenler ve hizmetlerle türlerini başvuru ekleyebilirsiniz:

- .NET framework sınıf kitaplıkları veya derlemeler

- UWP uygulamaları

- COM bileşenleri

- Diğer derlemeler veya aynı çözümdeki projelerin sınıf kitaplıkları

- XML Web hizmetleri

## <a name="uwp-app-references"></a>UWP uygulama başvuruları

### <a name="project-references"></a>Proje başvuruları

Evrensel Windows Platformu (UWP) projeleri bu projeleri Windows 10'da kullanım dışı API'ları kullanmayın sağlanan başvuruları diğer UWP projeleri veya Windows 8.1 projeleri veya ikili dosyaları, oluşturabilirsiniz. Daha fazla bilgi için bkz: [UWP'ye Windows çalışma zamanı 8'den Taşı](/windows/uwp/porting/w8x-to-uwp-root).

Windows 10 için Windows 8.1 projeleri yeniden hedefleyin isterseniz bkz [bağlantı noktası, geçirme ve yükseltme Visual Studio projeleri](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

### <a name="extension-sdk-references"></a>Uzantı SDK başvurular

Visual Basic, C#, C++ ve JavaScript Evrensel Windows Platformu (UWP) uygulamaları, bu uzantı SDK'ları Windows 10'da kullanım dışı API'ları kullanmayın sürece uzantısı SDK'ları hedefleyen Windows 8.1 başvuruda bulunabilir. Lütfen olup, UWP uygulamaları tarafından başvurulabilir çıkışı bulmak için uzantı SDK satıcı sitesini denetleyin.

Karar verirseniz, uygulamanız tarafından başvurulan uzantısı SDK desteklenmiyor sonra aşağıdaki adımları gerçekleştirmeniz gerekir:

1. Hataya neden olan projesinin adı arayın. Projenizi hedefleme platform proje adının yanında parantez içinde belirtilir. Örneğin, **MyProjectName (Windows 8.1)** projenizi anlamına **MyProjectName** platform sürüm Windows 8.1 desteği.

1. Desteklenmeyen uzantı SDK'sı sahibi satıcı sitesine gidin ve projenizin hedefleme platform sürümü ile uyumlu olan bağımlılıkları olan uzantı SDK sürümünü yükleyin.

    > [!NOTE]
    > Bir uzantı SDK bağımlılıkları diğer uzantısı SDK olup bulmak için bir yoldur bakarak **başvuru Yöneticisi**. Visual Studio'yu yeniden başlatın, yeni bir C# UWP uygulaması projesi oluşturun ve ardından projeye sağ tıklayın ve seçin **Başvuru Ekle**. Git **Windows** sekmesi, sonra **uzantıları** alt sekmesine ve uzantı SDK'yı seçin. Sağ bölmede bakabilir **başvuru Yöneticisi**. Bağımlılıkları varsa, bunlar var. listelenir.

    > [!IMPORTANT]
    > Projenizi Windows 10 hedefleme ve uzantısı önceki adımda yüklenen SDK'sı, Microsoft Visual C++ çalışma zamanı paketi üzerinde bir bağımlılığa sahiptir, Microsoft Visual C++ çalışma zamanı Windows 10 ile uyumlu olan paket sürümü v14.0 olur ve yüklü Visual Studio ile.

1. Önceki adımda yüklenen uzantı SDK diğer uzantısı SDK bağımlılıklarına sahipse, bağımlılıkları kendi ve projeniz platform sürümü ile uyumlu Bu bağımlılıklar sürümlerini yükleyen satıcılarının siteleri gidin hedefleme.

1. Visual Studio'yu yeniden başlatın ve uygulamanızı açın.

1. Sağ tıklayın **başvuruları** veya **bağımlılıkları** hata neden oldu ve proje düğümüne **Başvuru Ekle**.

1. Tıklatın **Windows** sekmesini ve ardından **uzantıları** alt sekmesinde, eski uzantısı SDK'ları için onay kutusunun işaretini kaldırın ve yeni uzantı SDK'ları için onay kutularını denetleyin. **Tamam**'ı tıklatın.

## <a name="add-a-reference-at-design-time"></a>Tasarım zamanında bir başvuru ekleyin

Projenizi derleme için bir başvuru yaptığınızda, Visual Studio derleme aşağıdaki konumlarda arar:

- Geçerli proje dizini. (Bu derlemeler kullanarak bulabilirsiniz **Gözat** sekmesi.)

- Diğer aynı çözüme proje dizinlerde. (Bu derlemeler bulabilirsiniz **projeleri** sekmesi.)

> [!NOTE]
> - Tüm projeleri için dolaylı bir başvuru içeren **mscorlib**.
> - Tüm projeleri için dolaylı bir başvuru içeren `System.Core`olsa bile `System.Core` başvuruları listesinden kaldırılır.
> - Visual Basic projeleri için dolaylı bir başvuru içeren <xref:Microsoft.VisualBasic>.

## <a name="references-to-shared-components-at-run-time"></a>Paylaşılan bileşenler çalışma zamanında başvurular

Çalışma zamanında bileşenleri projenin çıkış yolu veya genel derleme önbelleği (GAC) içinde olmalıdır. Proje şu konumlardan birinde olmayan bir nesneye başvuru içeriyorsa, projeyi derlerken çıkış yolu projenin referansı kopyalamanız gerekir. <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> Özelliği, bu kopya yapılması sahip olup olmadığını belirtir. Değer ise **doğru**, projeyi derlerken başvuru proje dizinine kopyalanır. Değer ise **yanlış**, başvuru kopyalanmaz.

GAC içinde kayıtlı bir özel bileşenine bir başvuru içeren bir uygulamayı dağıtırsanız, bileşen uygulama ile bakılmaksızın dağıtılmaz <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> ayarı. Visual Studio'nun önceki sürümleri, ayarlayabilirsiniz <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> derleme dağıtıldı emin olmak için bir başvuru özelliği. Şimdi, \Bin klasörüne el ile derleme eklemeniz gerekir. Bu, size tanıdık olmayan özel kod yayımlama riskini azaltma scrutiny altındaki tüm özel kod koyar.

Varsayılan olarak, <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> özelliği ayarlanmış **False** derleme veya bileşeni Genel Derleme Önbelleği'ya bir çerçeve bileşeni ise. Değer kümesine Aksi halde, **doğru**. Proje Proje başvuruları her zaman ayarlanır **doğru**.

## <a name="reference-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Bir proje veya farklı bir .NET Framework sürümünü hedefler derleme başvurusu

Projeleri veya farklı bir .NET Framework sürümünü hedef derlemeleri başvuruda bulunan uygulamaları oluşturabilirsiniz. Örneğin, .NET Framework 4. 5'i hedefleyen bir derlemeyi başvuran hedef .NET Framework 4.6, bir uygulama oluşturabilirsiniz. .NET Framework'ün önceki bir sürümünü hedefleyen bir projede oluşturursanız, bu proje bir proje veya daha yeni bir sürümü hedefler derleme için bir başvuru ayarlanamıyor.

Daha fazla bilgi için bkz: [çoklu sürüm desteğine genel bakış](../ide/visual-studio-multi-targeting-overview.md).

## <a name="project-to-project-references"></a>Proje için proje başvuruları

Proje Proje başvuruları derlemeleri içeren projelere başvurular; yine de uygun istiyor musunuz? bunları kullanarak oluşturduğunuz **proje** sekmesi. Visual Studio derleme yolu projeye verildiğinde bulabilirsiniz.

Bir derlemeyi üreten bir proje sahip olduğunuzda, proje başvurusu ve dosya başvurusu (aşağıya bakın) kullanmamanız gerekir. Proje proje başvurusu avantajlarından yapı sistem projeler arasında bir bağımlılık oluşturmasıdır. Başvuru proje oluşturulan en son ne zaman beri değişmişse bağımlı proje oluşturulacak. Dosya başvurusu, başvuru proje bağımlı proje oluşturmadan oluşturmak mümkün müdür ve başvuru geçersiz hale gelebilir derleme bağımlılığına oluşturmaz. (Diğer bir deyişle, proje önceden oluşturulmuş bir projenin sürümü başvurabilir.) Bu gerekli tek bir DLL birkaç sürümlerinde sonuçlanabilir *bin* mümkün olmayan dizin. Bu çakışma oluştuğunda bir ileti gibi görürsünüz "Uyarı: 'dosya' başvuru üzerine yazacağından 'proje' projesindeki ' dosya' bağımlılığı çalıştırma dizinine kopyalanamıyor". Daha fazla bilgi için bkz: [başvuruları bozuk sorun giderme](../ide/troubleshooting-broken-references.md) ve [nasıl yapılır: oluşturun ve proje bağımlılıkları kaldırın](../ide/how-to-create-and-remove-project-dependencies.md).

> [!NOTE]
> Bir dosya başvurusu proje proje başvurusu yerine hedef bir proje .NET Framework sürüm 4.5 sürümüdür ve diğer projenin hedef sürüm 2, 3, 3.5 veya 4.0 sürümünü ise oluşturulur.

## <a name="file-references"></a>Dosya başvuruları

Dosya başvuruları Visual Studio projesi bağlamı dışında derlemeleri doğrudan başvurusudur. Bunları kullanarak oluşturduğunuz **Gözat** sekmesinde **başvuru Yöneticisi**. Bir derlemeyi veya bileşeni ve çıkış olarak oluşturan Proje değil yalnızca varsa dosya başvurusu kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Bozuk başvurularda sorun giderme](../ide/troubleshooting-broken-references.md)
- [Nasıl yapılır: Başvuru Ekle Kaldır](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
