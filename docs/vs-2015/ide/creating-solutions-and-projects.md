---
title: Çözümler ve projeler oluşturma | Microsoft Docs
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
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], deleting
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
ms.assetid: 836f8ca0-3fc9-4f4b-9090-45f2e4d2e9c8
caps.latest.revision: 49
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 336fb41ee6a4c90e7065187b2805aefe9e6e6df7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893708"
---
# <a name="creating-solutions-and-projects"></a>Çözümler ve Projeler Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projeleri, uygulamanızı oluşturmak için gerekli olan her şey için mantıksal kapsayıcılardır. Seçerek bir proje oluşturduğunuzda **dosya &#124; yeni &#124; proje** ana menüden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] içerdiği için bir çözüm oluşturur. Gerekirse daha fazla yeni veya mevcut projeleri çözüme daha sonra ekleyebilirsiniz. Geçici projeler (yalnızca .NET) oluşturabilir ve varolan kod dosyalarından projeler oluşturabilir, silinecek ile işiniz bittiğinde.  
  
> [!NOTE]
>  Açıklamalar bu konuda, Visual Studio Community edition temel alır. İletişim kutuları ve menü komutları gördüğünüz ayarları ya da Visual Studio sürümü bağlı olarak burada açıklananlar farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-project-from-an-installed-project-template"></a>Bir yüklü proje şablonundan bir proje oluşturun  
 **Dosya &#124; yeni &#124; proje** yeni proje iletişim kutusunu açmak için ana menüden. Sol bölmede altında **Intalled &#124; şablonları** programlama dil ve platform veya teknoloji seçtiğiniz, ardından Orta bölmede bir kullanılabilir şablonlardan seçin.  
  
 İçinde **yeni proje** iletişim kutusunda **çözüm** açılan yeni projeye yeni veya var olan bir çözümde veya Visual Studio'nun yeni bir örneğini oluşturmak için bu seçeneği sağlar.  
  
## <a name="create-a-project-from-existing-code-files"></a>Varolan kod dosyalarından proje oluşturma  
 Gevşek kaynak dosyaları koleksiyonunu varsa, bunları içeren bir proje kolayca oluşturabilirsiniz. Seçin **dosya &#124; yeni &#124;varolan koddan proje** başlatmak için **varolan kod dosyaları sihirbazından proje oluştur** ve yönergeleri izleyin.  
  
> [!TIP]
>  Bu seçenek, dosyaları görece basit koleksiyonları için en iyi çalışır.  
  
## <a name="create-a-temporary-project-c-and-visual-basic"></a>Geçici bir proje (C# ve Visual Basic) oluşturma  
 Geçici projeler ile birlikte çalışarak oluşturabilir ve bir disk konumu belirtmeden bir .NET projesi ile denemeler yapın. Bir proje oluşturduğunuzda, yalnızca bir proje türü ve şablon seçin ve bir ad belirtin **yeni proje** iletişim kutusu. Dilediğiniz zaman geçici projeyle çalışırken, kaydedebilirsiniz veya iptal edebilirsiniz.  
  
## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Belirli bir .NET Framework sürümünü hedefleyen bir .NET projesi oluşturma  
 Kullanarak .NET Framework'ün önceki sürümlerini hedeflemek için bir proje oluşturabilirsiniz **.NET Framework** sürüm en üstündeki aşağı açılan menüyü **yeni proje** iletişim kutusu. Yalnızca bu .NET Framework sürümü ile uyumlu olan şablonları listesinde görünecek bir proje şablonu seçmeden önce bu değeri ayarlayın.  
  
 Framework sürüm 4.0 öncesi erişmek için .NET Framework 3.5 yüklü olmalıdır.  
  
## <a name="downloading-sample-solutions"></a>Örnek çözümler yükleniyor  
 Örnek çözümlerinden indirip Visual Studio'yu kullanabilirsiniz [MSDN Kod Galerisi](http://go.microsoft.com/fwlink/?LinkId=254185).  
  
 Örnekleri tek tek indirebilir veya bir teknoloji veya konuya paylaşan alakalı örnekler içeren örnek paket, karşıdan yükleyebilirsiniz. Kaynak kodu değişiklikleri indirdiğiniz için herhangi bir örnek yayımlandığında bir bildirim alacaksınız.  
  
 Daha fazla bilgi için [Visual Studio örnekleri](../ide/visual-studio-samples.md).  
  
## <a name="adding-single-files-at-the-solution-level"></a>Çözüm düzeyinde tek dosya ekleme  
 Bazen birden çok projeye başvuran veya metin veya çözüm düzeyinde yerine belirli bir proje altında mantıksal olarak ait çeşitli veri içeren bir dosya olabilir.  Bir çözüme tek bir öğe eklemek için:  
  
1.  Ndeki çözüm düğümüne sağ **Çözüm Gezgini** ve **Ekle &#124; yeni öğe** veya **Ekle &#124; var olan öğe**.  
  
## <a name="creating-empty-solutions"></a>Boş Çözüm oluşturma  
 Bir çözümde bir proje bulunmalıdır olsa da, proje yok bir çözüm oluşturabilirsiniz.  
  
#### <a name="to-create-an-empty-solution"></a>Boş bir çözüm oluşturmak için  
  
1. Üzerinde **dosya** menüsünü tıklatın **yeni** ve ardından **yeni proje**.  
  
2. Sol bölmede seçin **yüklü**seçin **diğer proje türleri**ve ardından **Visual Studio çözümleri** genişletilmiş listeden.  
  
3. Orta bölmede seçin **boş çözüm**.  
  
4. Ayarlama **adı** ve **konumu** değerleri, çözümünüz ardından **Tamam**.  
  
   Boş bir çözüm oluşturduktan sonra yeni veya var olan proje veya öğe tıklayarak ekleyebilirsiniz **Yeni Öğe Ekle** veya **varolan öğeyi Ekle** üzerinde **proje** menüsü.  
  
### <a name="deleting-solutions"></a>Çözüm siliniyor  
 Bir çözüm kalıcı olarak silebilirsiniz ancak kullanarak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Bir çözüm silmeden önce başka bir çözüm içinde yeniden kullanmak isteyebileceğiniz herhangi bir projeyi taşıyın. Ardından .sln ve .suo çözüm dosyalarını içeren dizini silmek için dosya Gezgini'ni kullanın.  
  
> [!NOTE]
>  Varsayılan dosya Gezgini ayarlar altında görüntülenmez gizli bir dosya .suo dosyasıdır.  
  
##### <a name="to-delete-a-solution"></a>Bir çözümü silmek için  
  
1.  İçinde **Çözüm Gezgini**, silme ve çözüme sağ tıklayın **klasörü dosya Gezgini'nde Aç**.  
  
2.  Dosya Gezgini'nde, bir düzey yukarı gidin.  
  
3.  Çözümü içeren dizini seçin ve Sil'e basın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Projeler ve çözümler](../ide/solutions-and-projects-in-visual-studio.md)   
 [NIB nasıl yapılır: birden çok proje çözümü oluşturma](http://msdn.microsoft.com/en-us/02ecd6dd-0114-46fe-b335-ba9c5e3020d6)



