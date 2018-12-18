---
title: Kendi oluşturma başlangıç sayfasının | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Create start page
- custom start page
- customize start page
ms.assetid: a0df5b9c-0932-4e54-86f0-28530ad9d684
caps.latest.revision: 22
manager: douge
ms.openlocfilehash: 005f9597abd1ce688724af9fcb167a626e4cd885
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815045"
---
# <a name="creating-your-own-start-page"></a>Kendi başlangıç sayfası oluşturma
Başlangıç sayfası proje şablonunu kullanarak ya da boş bir başlangıç sayfası oluşturarak, özel bir başlangıç sayfası oluşturabilirsiniz.  
  
 XAML Tasarımcısı, Visual Studio uygulama modeli bağımlılıkları nedeniyle özel başlangıç sayfaları tamamen doğru görsel temsilini sağlamayabilir.  
  
## <a name="using-the-project-template"></a>Proje şablonunu kullanarak  
 Başlangıç sayfası proje şablonu, Visual Studio Başlangıç sayfası eksiksiz bir kopyasıdır bir başlangıç sayfası projesi oluşturur. Başlangıç sayfası, belirtime uygun daha sonra düzenleyebilirsiniz.  
  
#### <a name="to-create-a-custom-start-page-by-using-the-start-page-project-template"></a>Başlangıç sayfası proje şablonunu kullanarak özel bir başlangıç sayfası oluşturmak için  
  
1.  İndirme ve yükleme [başlangıç sayfası proje şablonu](http://go.microsoft.com/fwlink/?LinkId=186204) Visual Studio Galerisi.  
  
    > [!WARNING]
    >  Şu anda Visual Studio 2010 Başlangıç sayfası proje şablonu yükseltilmedi. Bu şablon yükseltme hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Visual Studio özel başlangıç sayfası yükseltme](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
2.  Şablonunu yükledikten sonra yeni bir başlangıç sayfası projesi oluşturur.  
  
3.  Yeni Proje iletişim kutusunun sol bölmede altında **yüklü şablonlar**, genişletme **diğer proje türleri** düğümünü ve ardından **genişletilebilirlik**.  
  
4.  Orta bölmede **özel başlangıç sayfası**, projenizi adlandırın ve tıklayın **Tamam**.  
  
     Visual Studio, Visual Studio Başlangıç sayfası eksiksiz bir kopyasıdır bir başlangıç sayfası projesi oluşturur.  
  
5.  Gelen **Çözüm Gezgini**açın **StartPage.xaml**.  
  
6.  StartPage.xaml düzenleyin.  
  
     Özel başlangıç yüklü sayfası ile Visual Studio deneysel örneği açmak için F5 tuşuna basarak iş görüntüleyebilirsiniz.  
  
## <a name="creating-a-blank-start-page"></a>Boş bir başlangıç sayfası oluşturma  
 Boş bir başlangıç sayfası oluşturmak için en kolay yolu, başlangıç sayfası proje şablonu kullanın ve ardından içeriği kaldırmak sağlamaktır.  
  
#### <a name="to-create-a-blank-start-page-by-using-the-start-page-project-template"></a>Başlangıç sayfası proje şablonu kullanarak boş bir başlangıç sayfası oluşturmak için  
  
1. Başlangıç sayfası proje başlangıç sayfası proje şablonunu kullanarak önceki yordamda açıklandığı gibi oluşturun.  
  
2. StartPage.xaml açın.  
  
3. Tüm sayfa içeriğinin yalnızca dış xml öğeleri ve içeren kılavuz bırakarak kaldırın <xref:System.Windows.Controls.Grid> öğesi, böylece, .xaml dosyasını aşağıdaki örneğe benzer.  
  
   ```xaml
      <Grid xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
                xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
                xmlns:sp="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.StartPage"
                xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.10.0"
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.10.0"
            mc:Ignorable="d" 
                d:DesignHeight="600" d:DesignWidth="800">
       <Grid>
           <!--Add content here.-->
       </Grid>
   </Grid>
   ```
      
4. Kullanmak istemediğiniz tüm destekleyici dosyaları kaldırın.  
  
    Dağıtım amaçları için .vsix ve .pkgdef dosyaları tutmanız gerekir.  
  
   Alternatif olarak, Visual Studio tarafından tanınması için doğru etiketi yapıya sahip bir XAML dosyası oluşturarak, boş bir başlangıç sayfası oluşturabilirsiniz. Ardından, biçimlendirme ve istenen Görünüm ve işlevselliği elde etmek için gerideki kod ekleyebilirsiniz. Daha fazla bilgi için [bir özel başlangıç sayfası oluşturma](../extensibility/creating-a-custom-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Test ve özel uygulama başlangıç sayfası  
 Özel başlangıç sayfası değil kilitlenme doğrulayana kadar çalıştırmak için birincil örneğine ayarlı değil. Özel başlangıç sayfası sınandığında birincil Visual Studio örneğinde bu yordamın son üç adımı yineleyerek sisteminize uygulayabilirsiniz.  
  
#### <a name="to-test-a-custom-start-page"></a>Özel başlangıç sayfası test etmek için  
  
1. F5 tuşuna basın.  
  
    Visual Studio'nun deneysel örneğinde yeni başlangıç yüklendi, ancak seçili sayfası ile açılır.  
  
2. Visual Studio'nun Deneysel örneğinin üzerinde **Araçları** menüsünde tıklatın **seçenekleri**.  
  
3. İçinde **seçenekleri** iletişim kutusunun **ortam**seçin **başlangıç**. Ardından **başlangıç sayfasını Özelleştir** listesinde, .xaml dosyanızı seçin ve tıklayın **Tamam**.  
  
4. Üzerinde **görünümü** menüsünü tıklatın **başlangıç sayfası**.  
  
    Çalışan başlangıç sayfası görüntülenir. Deneysel örneği kapatın, yeniden değişen tüm dosyaları kopyalayın ve ardından yeni değişiklikleri görmek için deneysel örneğinde yeniden açın gerekir.  
  
   Özel başlangıç sayfası için bin\debug dizininizden .vsix dosyasını karşıya yükleyerek paylaşabilirsiniz [Visual Studio Galerisi](http://go.microsoft.com/fwlink/?LinkID=123847) Web sitesini veya başka bir Web sitesi veya intranet paylaşın. Daha fazla bilgi için [özel başlangıç sayfaları dağıtma](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlangıç sayfasını özelleştirme](../ide/customizing-the-start-page-for-visual-studio.md)   
 [İzlenecek Yol: Başlangıç Sayfasına Özel XAML Ekleme](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)