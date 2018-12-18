---
title: VSIX proje şablonunu kullanmaya başlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1f7230bce49342ad8e31baeb3f46c72f1c45d776
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787737"
---
# <a name="getting-started-with-the-vsix-project-template"></a>VSIX Proje Şablonunu Kullanmaya Başlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSIX proje şablonu, bir uzantı oluşturmak veya mevcut bir uzantı için dağıtım paketini için kullanabilirsiniz. VSIX proje şablonu Visual Basic ve Visual C# sürümü vardır ve Visual Studio SDK'ın bir parçası olarak yüklenir.  
  
 VSIX proje şablonu yalnızca uzantısı hakkında bilgi içeren bir source.extension.vsixmanifest dosyası ve onu birlikte gelen varlıkları oluşur.  
  
 VSIX proje şablonunu bulmak için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="deploying-a-custom-project-template-using-the-vsix-project-template"></a>VSIX proje şablonunu kullanarak özel bir proje şablonu dağıtma  
 Aşağıdaki adımlar diğer geliştiriciler ile paylaşabilir veya Visual Studio Galeri'ye yükleyin, bir proje şablonu paketlemek için VSIX projesi kullanma işlemini gösterir.  
  
1.  Bir proje şablonu oluşturun.  
  
    1.  Bir şablon oluşturmak, projeyi açın. Bu proje bir proje türünde olabilir.  
  
    2.  Üzerinde **dosya** menüsünü tıklatın **şablonu dışarı aktar**. Sihirbazın adımlarını tamamlayın.  
  
         Bir .zip dosyası, %USERPROFILE%\My Documents\Visual Studio içinde oluşturulan  *\<sürüm >* \My dışarı aktarılan şablonları\\.  
  
2.  Boş bir VSIX projesi oluşturun.  
  
     Üzerinde **dosya** menüsünde tıklatın **yeni** ve ardından **proje**. Şunlardan birini seçin **Visual Basic** veya **Visual C#**. Seçili düğümü altında seçin **genişletilebilirlik**ve ardından **VSIX projesi**.  
  
3.  .Zip dosyasını projeye ekleyin. Ayarlama, **çıkış dizinine Kopyala** özelliğini `Copy Always`.  
  
4.  İçinde **Çözüm Gezgini**, çift `source.extension.vsixmanifest` içinde açmak için dosyaya **VSIX bildirim Tasarımcısı**ve ardından aşağıdaki değişiklikleri yapın:  
  
    -   Ayarlama **ürün adı** alanı **My proje şablonu**.  
  
    -   Ayarlama **ürün kimliği** alanı **MyProjectTemplate - 1**.  
  
    -   Ayarlama **Yazar** alanı **Fabrikam**.  
  
    -   Ayarlama **açıklama** alanı **proje şablonumu**.  
  
    -   İçinde **varlıklar** bölümünde, eklemek bir **Microsoft.VisualStudio.ProjectTemplate** yazın ve yolu .zip dosyasının adına ayarlayın.  
  
5.  Source.extension.vsixmanifest dosyasını kaydedip kapatın.  
  
6.  Projeyi oluşturun.  
  
7.  Çıktı dizininde .vsix dosyasını çift tıklayın.  
  
8.  A **VSIX yükleyicisi** ileti kutusu görünür. Uzantıyı yüklemek için yönergeleri izleyin.  
  
9. Visual Studio'yu kapatın ve yeniden açın.  
  
10. Seçin **Uzantılar ve güncelleştirmeler** (üzerinde **Araçları** menüsü) seçip **şablonları** kategorisi. Kullanılabilir uzantılar biri olmalıdır **My proje şablonu**.  
  
11. Yeni Proje şablonu görünür **yeni proje** özgün proje şablonu olarak aynı yerde iletişim. Adlı bir şablon oluşturduysanız, örneğin, **VB konsol** bir Visual Basic konsol uygulamasından **VB konsol** Visual Basic ile aynı bölmede görünür **konsol uygulaması**şablonu.  
  
#### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Yeni Proje iletişim kutusunda şablon konumunu belirtmek için  
  
1.  Şablon klasörlere yerleştirilir *Visual Studio yükleme yolu*\Common7\IDE\ProjectTemplates ve *Visual Studio yükleme yolu*\Common7\IDE\ItemTemplates dizinleri. Yeni Proje iletişim kutusunun üst düzey bölümlerin adlarını şablon klasörlerin adlarını tam olarak aynı. Bunların değişiklik gösterdiği durumlarda, şablon klasörün adını kullanın.  
  
     .Vsix dosyasını uzantısını .zip olarak değiştirin ve dosyayı açın.  
  
2.  Yeni Proje iletişim bölümünü şablonu görüntülenmelidir aynı ada sahip yeni bir klasör oluşturun.  
  
3.  Şablonun bir alt bölümünde görüntülenecek ise, aynı ada sahip bir alt klasör oluşturun.  
  
4.  Şablon .zip dosyası, yeni bir klasöre taşıyın.  
  
5.  .Zip uzantısı .vsix değiştirin.  
  
6.  VSIX bildirimi açın.  
  
7.  VSIX bildiriminin güncelleştirme **varlık** olan şablon dosyasını içeren dizin ağacında kök dizinine işaret için şablonun yolu. Örneğin, şablonu içinde \CSharp\Windows ise, başvuru için \CSharp işaret etmelidir.

