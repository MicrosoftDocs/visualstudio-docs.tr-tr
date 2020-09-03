---
title: Çözümler ve projeler oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 10375e00eb850691e88d01c56a87bb967c40e9ea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850562"
---
# <a name="creating-solutions-and-projects"></a>Çözümler ve Projeler Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projeler, uygulamanızı derlemek için gereken her şeye yönelik mantıksal kapsayıcılardır. Ana menüden **dosya &#124; yeni &#124; proje** ' yi seçerek bir proje oluşturduğunuzda, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bunu içeren bir çözüm oluşturur. Daha sonra, gerekirse çözüme daha fazla yeni veya mevcut proje ekleyebilirsiniz. Mevcut kod dosyalarından projeler oluşturabilirsiniz ve bunlar ile işiniz bittiğinde silinecek geçici projeler (yalnızca .NET) oluşturabilirsiniz.

> [!NOTE]
> Bu konudaki açıklamalar, Visual Studio Community sürümünü temel alır. Gördüğünüz iletişim kutuları ve menü komutları, ayarlarınıza veya Visual Studio sürümüne bağlı olarak burada açıklananlardan farklı bir şekilde farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-project-from-an-installed-project-template"></a>Yüklü bir proje şablonundan proje oluşturma
 Yeni proje iletişim kutusunu açmak için **dosya yeni &#124; projesi** ana menüden &#124;. Sol bölmedeki **&#124; şablonlar** ' ın altında, programlama dilini ve platformunu veya teknolojisini seçip ortadaki bölmedeki kullanılabilir şablonlar ' ı seçin.

 **Yeni proje** iletişim kutusunda, **çözüm** açılır listesi yeni veya var olan bir çözümde ya da Visual Studio 'nun yeni bir örneğinde yeni proje oluşturma seçeneği sunar.

## <a name="create-a-project-from-existing-code-files"></a>Varolan kod dosyalarından bir proje oluşturma
 Gevşek kaynak dosyaları koleksiyonunuz varsa, bunları içeren bir projeyi kolayca oluşturabilirsiniz. Varolan koddan **Proje oluşturma Sihirbazı 'nı** başlatmak Için mevcut **Koddan dosya &#124; yeni &#124;projesi** öğesini seçin ve yönergeleri izleyin.

> [!TIP]
> Bu seçenek görece basit dosya koleksiyonları için en iyi şekilde kullanılır.

## <a name="create-a-temporary-project-c-and-visual-basic"></a>Geçici bir proje oluşturma (C# ve Visual Basic)
 Geçici projelerle çalışarak bir disk konumu belirtmeden bir .NET projesi oluşturabilir ve bunlarla denemeler yapabilirsiniz. Bir proje oluşturduğunuzda, **Yeni** proje iletişim kutusunda bir proje türü ve şablon seçip bir ad belirtmeniz yeterlidir. Herhangi bir zamanda, geçici projeyle çalışırken kaydedebilirsiniz, ya da iptal edebilirsiniz.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>.NET Framework belirli bir sürümünü hedefleyen bir .NET projesi oluşturma
 **Yeni proje** iletişim kutusunun üst kısmındaki **.NET Framework** sürümü açılır menüsünü kullanarak .NET Framework önceki sürümlerini hedeflemek için bir proje oluşturabilirsiniz. Bu değeri bir proje şablonu seçmeden önce, yalnızca bu .NET Framework sürümüyle uyumlu olan şablonlar listede görünecek şekilde ayarlayın.

 4,0 ' den önceki Framework sürümlerine erişmek için sisteminizde .NET Framework 3,5 yüklü olmalıdır.

## <a name="downloading-sample-solutions"></a>Örnek çözümler indiriliyor
 Visual Studio 'Yu kullanarak [MSDN kod galerisindeki](https://code.msdn.microsoft.com/)örnek çözümleri indirebilir ve yükleyebilirsiniz.

 Örnekleri tek tek indirebilir veya bir teknolojiyi veya konuyu paylaşan ilgili örnekleri içeren bir örnek paket indirebilirsiniz. Karşıdan yüklediğiniz herhangi bir örnek için kaynak kodu değişiklikleri yayımlandığında bir bildirim alırsınız.

 Daha fazla bilgi için bkz. [Visual Studio örnekleri](../ide/visual-studio-samples.md).

## <a name="adding-single-files-at-the-solution-level"></a>Çözüm düzeyinde tek dosya ekleme
 Bazen birden çok projenin başvurduğu bir dosyanız olabilir veya belirli bir proje altında, mantıksal olarak çözüm düzeyinde bulunan metin veya çeşitli veriler içerir.  Bir çözüme tek bir öğe eklemek için:

1. **Çözüm Gezgini** çözüm düğümüne sağ tıklayın ve **&#124; yeni öğe Ekle** ' yi seçin veya **mevcut &#124; öğeyi ekleyin**.

## <a name="creating-empty-solutions"></a>Boş çözümler oluşturma
 Projenin bir çözümde bulunması gerekse de proje olmayan bir çözüm oluşturabilirsiniz.

#### <a name="to-create-an-empty-solution"></a>Boş bir çözüm oluşturmak için

1. **Dosya** menüsünde **Yeni** ' ye ve ardından **Yeni proje**' ye tıklayın.

2. Sol bölmede, **yüklü**' ı seçin, **diğer proje türleri**' ni seçin ve ardından genişletilmiş listeden **Visual Studio çözümleri** ' ni seçin.

3. Orta bölmede **boş çözüm**' ü seçin.

4. Çözümünüz için **ad** ve **konum** değerlerini ayarlayın ve ardından **Tamam**' a tıklayın.

   Boş bir çözüm oluşturduktan sonra, **Yeni öğe Ekle** ' ye tıklayarak veya **Proje** menüsünde **var olan öğeyi Ekle** ' ye tıklayarak yeni veya var olan projeleri veya öğeleri ekleyebilirsiniz.

### <a name="deleting-solutions"></a>Çözümleri silme
 Bir çözümü kalıcı olarak silebilirsiniz, ancak öğesini kullanarak kaldırabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Bir çözümü silmeden önce, başka bir çözümde kullanmak isteyebileceğiniz tüm projeleri taşıyın. Ardından,. sln ve. suo çözüm dosyalarını içeren dizini silmek için dosya Gezgini 'ni kullanın.

> [!NOTE]
> . Suo dosyası, varsayılan dosya Gezgini ayarları altında görüntülenmeyen gizli bir dosyadır.

##### <a name="to-delete-a-solution"></a>Bir çözümü silmek için

1. **Çözüm Gezgini**' de, silinecek çözüme sağ tıklayın ve **Dosya Gezgini 'nde klasörü aç**' ı seçin.

2. Dosya Gezgini 'nde, bir düzey yukarı gidin.

3. Çözümü içeren dizini seçin ve Sil 'e basın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md) [nib nasıl yapılır: çoklu proje çözümleri oluşturma](https://msdn.microsoft.com/02ecd6dd-0114-46fe-b335-ba9c5e3020d6)
