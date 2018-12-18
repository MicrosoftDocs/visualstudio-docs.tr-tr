---
title: Projeler ve çözümler oluşturma
ms.date: 02/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 06696ca975fb80eaa97cd265c9d45e6174d3b053
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348541"
---
# <a name="create-solutions-and-projects"></a>Projeler ve çözümler oluşturma

*Projeleri* kaynak kodu dosyaları, bit eşlemler, simgeler gibi Visual Studio'da, uygulamanızı oluşturmak için gereken öğeleri ve bileşen ve hizmet başvuruları tutun. Yeni bir proje oluşturduğunuzda, Visual Studio oluşturur bir *çözüm* proje içerecek. İsterseniz, diğer yeni veya mevcut projeleri çözüme sonra ekleyebilirsiniz. Çözümleri Ayrıca belirli hiçbir projeye bağlı olmayan dosyalar içerebilir.

![Çözüm/proje hiyerarşisi](./media/vside-proj-soln.png)

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz: [oluşturma projeleri Visual Studio'da Mac için](/visualstudio/mac/create-new-projects).

Projeler ve çözümler adlı bir araç penceresinde görüntüleyebilirsiniz **Çözüm Gezgini**. Bir örnek çözümde aşağıdaki ekran görüntüsünde gösterilmektedir **Çözüm Gezgini** (**BikeSharing.Xamarin UWP**), iki proje içerir: **BikeSharing.Clients.Core** ve **BikeSharing.Clients.Windows**. Her proje birden fazla dosyaları, klasörleri ve başvurular içerir. Proje adı kalın *başlangıç projesi*; diğer bir deyişle, uygulamayı çalıştırdığınızda başlatan proje. Projeyi başlangıç projesi olduğunu belirtebilirsiniz.

![Çözüm Gezgini projeleri](./media/vside-solution-explorer-projects.png)

Gerekli dosyaları ekleyerek kendiniz bir proje oluşturabilirsiniz, ancak Visual Studio size avantajlı bir başlangıç projesi şablonlar sunar. Bir şablondan yeni bir proje oluşturma, şu temel bir proje bu proje türü için sunar ve dosyaları yeniden adlandırmak veya yeni veya mevcut koda ve diğer kaynakları gerektiği gibi ekleyin.

Başka bir deyişle, çözümler ve projeler Visual Studio'da uygulamaları geliştirmek için gerekli değildir. Git'ten kopyaladığınız veya başka bir yerde indirilen kod yalnızca açabilirsiniz. Daha fazla bilgi için [kod Visual Studio'da projeler veya çözümler olmadan geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

> [!NOTE]
> Açıklamalar bu konuda, Visual Studio Community edition temel alır. İletişim kutuları ve menü komutları gördüğünüz ayarları ya da Visual Studio sürümü bağlı olarak burada açıklananlar farklılık gösterebilir. Ayarlarınızı, örneğin değiştirileceğini **genel** veya **Visual C++** ayarları seçebilirsiniz **Araçları** > **içeri ve dışarı aktarma ayarları**ve ardından **tüm ayarları Sıfırla**.

## <a name="to-create-a-project-from-a-project-template"></a>Bir proje şablonundan bir proje oluşturmak için

1. Visual Studio'da yeni bir proje oluşturmak için birden çok yolu vardır. Üzerinde **başlangıç sayfası**, bir proje şablonunun adını girin **arama proje şablonları** kutusuna veya tercih **yeni proje oluştur** açmak için bağlantıyı **yeni Proje** iletişim kutusu. Seçebilirsiniz **dosya** > **yeni** > **proje** menüsünde çubuk veya tercih **yeni proje** düğmesi araç.

   ![Başlangıç sayfası](./media/vside-newproject1.png)

   İçinde **yeni proje** iletişim kutusu, kullanılabilir proje şablonları görünür altında bir listede **şablonları** kategorisi. Şablonları Visual gibi dil ve proje türü programlama tarafından düzenlenir C#, JavaScript ve Azure Data Lake.

   ![Yeni Proje iletişim kutusu](./media/vside-newproject-templates-list.png)

   > [!NOTE]
   > Görüntülenen listeden kullanılabilir diller ve proje şablonları, kullanmakta olduğunuz Visual Studio ve yüklü iş yükleri sürümüne bağlıdır. Ek iş yüklerinin yükleme hakkında bilgi edinmek için [değiştirme Visual Studio iş yükleri ve bileşenleri ekleyerek veya kaldırarak tarafından 2017](../install/modify-visual-studio.md).

2. Bu üçgen dil adının yanındaki seçerek kullanmak istediğiniz programlama dili için şablonları listesini gösterme ve bir proje türü seçin.

   Kullanılabilir proje şablonları aşağıdaki örnekte görsel için C# .NET Core projeleri.

   ![Proje şablonları](./media/new-project-dialog-net-core.png)

3. Yeni proje için bir ad girin **adı** kutusu. Sisteminizde varsayılan konumda projeyi kaydetmek veya seçmek seçebileceğiniz **Gözat** başka bir konum bulmak için düğme.

   Çözüm adını değiştirin veya yeni proje seçerek bir Git deposuna eklemek de isteğe bağlı olarak seçebilirsiniz **kaynak denetimine Ekle**.

4. Seçin **Tamam** çözüm ve proje oluşturma düğmesi.

5. Ek bir proje çözüme eklemek istiyorsanız çözüm düğümü seçin **Çözüm Gezgini**ve ardından menü çubuğunda, **proje** > **Add New Item**.

## <a name="create-a-project-from-existing-code-files"></a>Varolan kod dosyalarından proje oluşturma

Bir kod kaynak dosyaları koleksiyonunu varsa, bunları projeye bir kolayca ekleyebilirsiniz.

1. Menüsünde **dosya** > **yeni** > **varolan koddan proje**.

1. İçinde **varolan kod dosyalarından proje oluşturma** Sihirbazı, istediğiniz proje türünü seçin **ne tür bir proje oluşturmak istersiniz?** aşağı açılan liste kutusunu ve ardından **İleri**  düğmesi.

1. Sihirbazı'nda, dosyaların konumuna göz atın ve ardından yeni proje için bir ad girin **adı** kutusu. İşiniz bittiğinde seçin **son** düğmesi.

> [!NOTE]
> Bu seçenek, dosyaları görece basit koleksiyonu en iyi şekilde çalışır. Şu anda yalnızca Visual C++, Apache Cordova, Visual Basic ve C# proje türleri desteklenir.

## <a name="add-files-to-a-solution"></a>Çözüme dosyaları ekleme

Çözüm için bir benioku dosyası gibi birden çok proje için geçerli bir dosya veya belirli bir proje altında daha sonra bunları çözüme ekleyebilirsiniz yerine mantıksal olarak çözüm düzeyinde ait diğer dosyaları varsa. Çözüm düğümünün (sağ tıklama) bağlam menüsünde bir çözüme bir öğe eklemek için **Çözüm Gezgini**, seçin **Ekle** > **yeni öğe**, veya **Ekleme** > **var olan öğe**.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Belirli bir .NET Framework sürümünü hedefleyen bir .NET projesi oluşturma

Bir proje oluşturduğunuzda, projeyi kullanacak şekilde istediğiniz .NET Framework'ün belirli bir sürümünü belirtebilirsiniz. Bir .NET framework sürümünü belirtmek için **Framework** açılan menüde **yeni proje** iletişim kutusu.

![Framework açılan yeni proje iletişim kutusunda](./media/vside-newproject-framework.png)

> [!NOTE]
> .NET Framework sürümlerini .NET Framework 4'den önceki erişmek için .NET Framework 3.5 yüklü olmalıdır.

## <a name="create-empty-solutions"></a>Boş Çözüm oluşturma

Projeleri olmayan boş çözümleri oluşturabilirsiniz. Bu durumda, çözümünüzü ve projelerinizi sıfırdan oluşturmak için istediğiniz tercih edilebilir.

### <a name="to-create-an-empty-solution"></a>Boş bir çözüm oluşturmak için

1. Menüsünde **dosya** > **yeni** > **proje**.

1. Sol (**şablonları**) bölmesinde seçin **diğer proje türleri** > **Visual Studio çözümleri** genişletilmiş listeden.

1. Orta bölmede seçin **boş çözüm**.

1. Girin **adı** ve **konumu** seçin, çözümünüz için değerler **Tamam**.

Boş bir çözüm oluşturduğunuzda, yeni veya var olan proje veya öğe için seçerek ekleyebileceğiniz **Yeni Öğe Ekle** veya **varolan öğeyi Ekle** üzerinde **proje** menüsü.

Daha önce bahsedildiği gibi bir proje veya çözüm gerek kalmadan kod dosyaları da açabilirsiniz. Bu şekilde kod geliştirme hakkında bilgi edinmek için [kod Visual Studio'da projeler veya çözümler olmadan geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-temporary-project-c-and-visual-basic"></a>Geçici bir proje (C# ve Visual Basic) oluşturma

Oluşturursanız, bir. AĞ tabanlı proje bir disk konumu belirtmeden geçici bir proje olan. Geçici projeler .NET projeleriyle denemeler olanak sağlar. Geçici bir projeyle çalışırken herhangi bir zamanda kaydetmek veya atmak seçebilirsiniz.

Geçici bir proje oluşturmak için ilk Git **Araçları** > **seçenekleri** > **projeler ve çözümler**  >   **Genel**, kaldırın **oluşturulduğunda yeni projeleri Kaydet** onay kutusu. Açılacağını **yeni proje** iletişim kutusunda her zaman olduğu gibi.

## <a name="delete-a-solution-project-or-item"></a>Çözüm, proje veya öğe silme

Çözümler ve bunların içeriğini kalıcı olarak silebilirsiniz ancak Visual Studio IDE kullanarak değil. Visual Studio içindeki öğeleri silme yalnızca bunları geçerli çözüm veya proje kaldırır. Bir çözüm ya da başka bir bileşen sisteminizden kalıcı olarak silmek için içeren klasörü silmek için dosya Gezgini'ni kullanın *.sln* ve *.suo* çözüm dosyaları. Ancak, bir çözüm kalıcı olarak silinmeden önce yeniden gerektiği durumlarda tüm projeleri veya dosyaları yedekleme önerilir.

> [!NOTE]
> *.Suo* varsayılan dosya Gezgini Ayarları altında görüntülenmez gizli bir dosya dosyasıdır. Gizli dosyaları göstermek için **görünümü** dosya Gezgini'nde, seçim menüsünde **gizli öğeleri** onay kutusu.

### <a name="to-permanently-delete-a-solution"></a>Bir çözümü kalıcı olarak silmek için

1. İçinde **Çözüm Gezgini**, silmek istediğiniz çözümünün bağlam menüsünde **klasörü dosya Gezgini'nde Aç**.

1. Dosya Gezgini'nde, bir düzey yukarı gidin.

1. Çözümü içeren klasörü seçin ve ardından **Sil** anahtarı.

## <a name="see-also"></a>Ayrıca bkz.

- [Projeler ve çözümler](../ide/solutions-and-projects-in-visual-studio.md)
- [Github'da Microsoft'un açık kaynak depolar](https://github.com/Microsoft)
- [Geliştirici kodu örnekleri](https://code.msdn.microsoft.com/)
- [Projeleri (Mac için Visual Studio) oluşturma](/visualstudio/mac/create-new-projects)