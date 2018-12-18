---
title: VSIX proje şablonunu kullanmaya başlama | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 829ee38e5d22fbc38e47bdf9a2b9e7e9342957cd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817060"
---
# <a name="get-started-with-the-vsix-project-template"></a>VSIX proje şablonu ile çalışmaya başlama
VSIX proje şablonu, bir uzantı oluşturmak veya mevcut bir uzantı için dağıtım paketini için kullanabilirsiniz. VSIX proje şablonu Visual Basic ve Visual C# sürümü vardır ve Visual Studio SDK'ın bir parçası olarak yüklenir.  

 VSIX proje şablonu yalnızca oluşan bir *source.extension.vsixmanifest* uzantı ve varlıklar hakkında bilgi, birlikte gelen içeren dosya.  

 VSIX proje şablonunu bulmak için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>VSIX proje şablonunu kullanarak özel bir proje şablonu dağıtma  
 Aşağıdaki adımlar diğer geliştiriciler ile paylaşabilir veya Visual Studio Galeri'ye yükleyin, bir proje şablonu paketlemek için VSIX projesi kullanma işlemini gösterir.  

1.  Bir proje şablonu oluşturun.  

    1.  Bir şablon oluşturmak, projeyi açın. Bu proje bir proje türünde olabilir.  

    2.  Üzerinde **proje** menüsünü tıklatın **şablonu dışarı aktar**. Sihirbazın adımlarını tamamlayın.  

         A *.zip* dosyasının oluşturulduğunu *%USERPROFILE%\My Documents\Visual Studio \<sürüm > \My dışarı aktarılan şablonları\\*.  

2.  Boş bir VSIX projesi oluşturun.  

     Üzerinde **dosya** menüsünde tıklatın **yeni** ve ardından **proje**. Şunlardan birini seçin **Visual Basic** veya **Visual C#**. Seçili düğümü altında seçin **genişletilebilirlik**ve ardından **VSIX projesi**.  

3.  Ekleme *.zip* projeye dosya. Ayarlama, **çıkış dizinine Kopyala** özelliğini `Copy Always`.  

4.  İçinde **Çözüm Gezgini**, çift *source.extension.vsixmanifest* içinde açmak için dosyaya **VSIX bildirim Tasarımcısı**ve ardından aşağıdaki değişiklikleri yapın:  

    -   Ayarlama **ürün adı** alanı **My proje şablonu**.  

    -   Ayarlama **ürün kimliği** alanı **MyProjectTemplate - 1**.  

    -   Ayarlama **Yazar** alanı **Fabrikam**.  

    -   Ayarlama **açıklama** alanı **proje şablonumu**.  

    -   İçinde **varlıklar** bölümünde, eklemek bir **Microsoft.VisualStudio.ProjectTemplate** yazın ve kendi adına ayarlayın *.zip* dosya.  

5.  Kaydet ve Kapat *source.extension.vsixmanifest* dosya.  

6.  Projeyi oluşturun.  

7.  Çıktı dizininde çift *.vsix* dosya.  

8.  A **VSIX yükleyicisi** ileti kutusu görünür. Uzantıyı yüklemek için yönergeleri izleyin.  

9. Visual Studio'yu kapatın ve yeniden açın.  

10. Seçin **Uzantılar ve güncelleştirmeler** (üzerinde **Araçları** menüsü) seçip **şablonları** kategorisi. Kullanılabilir uzantılar biri olmalıdır **My proje şablonu**.  

11. Yeni Proje şablonu görünür **yeni proje** özgün proje şablonu olarak aynı yerde iletişim. Adlı bir şablon oluşturduysanız, örneğin, **VB konsol** bir Visual Basic konsol uygulamasından **VB konsol** Visual Basic ile aynı bölmede görünür **konsol uygulaması**şablonu.  

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Yeni Proje iletişim kutusunda şablon konumunu belirtmek için  

1. Şablon klasörlere yerleştirilir *{Visual Studio yükleme yolu} \Common7\IDE\ProjectTemplates* ve <em>{Visual Studio yükleme yolu} \Common7\IDE\ItemTemplates} dizinler. Adları üst düzey olarak bölümlerde **yeni proje</em>*  iletişim şablonu klasörlerin adlarını tam olarak eşleşmesi. Bunların değişiklik gösterdiği durumlarda, şablon klasörün adını kullanın.  

    Değişiklik *.vsix* dosya uzantısı için *.zip*ve ardından dosyasını açın.  

2. Bölümünü aynı ada sahip yeni bir klasör oluşturun **yeni proje** iletişim şablonu görüntülenmedir.  

3. Şablonun bir alt bölümünde görüntülenecek ise, aynı ada sahip bir alt klasör oluşturun.  

4. Şablon taşıma *.zip* yeni klasöre dosya.  

5. Değişiklik *.zip* uzantısı *.vsix*.  

6. VSIX bildirimi açın.  

7. VSIX bildiriminin güncelleştirme **varlık** olan şablon dosyasını içeren dizin ağacında kök dizinine işaret için şablonun yolu. Örneğin, şablon ise *\CSharp\Windows*, başvurunun işaret etmelidir *\CSharp*.
