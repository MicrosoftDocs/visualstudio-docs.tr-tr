---
title: VSıX proje şablonu ile çalışmaya başlama | Microsoft Docs
description: Uzantı oluşturmak veya var olan bir uzantıyı dağıtım için paketlemek üzere VSıX proje şablonunu nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 56573ee1add273c76ab96657c74207c3e2b620c3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057643"
---
# <a name="get-started-with-the-vsix-project-template"></a>VSıX proje şablonu ile çalışmaya başlama

Bir uzantı oluşturmak veya var olan bir uzantıyı dağıtım için paketlemek üzere VSıX proje şablonunu kullanabilirsiniz. VSıX proje şablonunda hem Visual Basic hem de Visual C# sürümleri vardır ve Visual Studio SDK 'sının bir parçası olarak yüklenir.

 VSıX proje şablonu, uzantısı ve geldiği varlıklar hakkında bilgi içeren bir *Source. Extension. valtmanifest* dosyasından oluşur.

 VSıX proje şablonunu bulmak için Visual Studio SDK 'sını yüklemelisiniz. Daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>VSıX proje şablonunu kullanarak özel bir proje şablonu dağıtma

 Aşağıdaki adımlarda, diğer geliştiricilerle paylaşabileceğiniz veya Visual Studio Galerisine yükleyebileceğiniz bir proje şablonunu paketlemek için VSıX projesinin nasıl kullanılacağı gösterilmektedir.

1. Proje şablonu oluşturun.

    1. Şablonun oluşturulacağı projeyi açın. Bu proje herhangi bir proje türünde olabilir.

    2. **Proje** menüsünde **şablonu dışarı aktar**' a tıklayın. Sihirbazın adımlarını izleyin.

         *%UserProfile%\My verdim Studio {Version} \Aktarılmış şablonlarında \\* bir *. zip* dosyası oluşturulur.

2. Boş bir VSıX projesi oluşturun.

     **Dosya**  >  **Yeni**  >  **Proje**' yi seçin. Arama kutusuna "VSIX" yazın ve **VSIX projesinin** **C#** veya **Visual Basic** sürümünü seçin.

3. *. Zip* dosyasını projeye ekleyin. **Çıkış Dizinine Kopyala** özelliğini olarak ayarlayın `Copy Always` .

4. **Çözüm Gezgini**, *kaynak. Extension. valtmanifest* dosyasına çift tıklayarak **VSIX bildirim tasarımcısında** açın ve ardından aşağıdaki değişiklikleri yapın:

    - **Ürün adı** alanını **Proje Şablonum** olarak ayarlayın.

    - **Ürün kimliği** alanını **myprojecttemplate-1** olarak ayarlayın.

    - **Yazar** alanını **fabrikam** olarak ayarlayın.

    - **Açıklama** alanını **Proje Şablonum** olarak ayarlayın.

    - **Varlıklar** bölümünde, bir **Microsoft. VisualStudio. ProjectTemplate** türü ekleyin ve yolunu *. zip* dosyasının adı olarak ayarlayın.

5. *Source. Extension. valtmanifest* dosyasını kaydedin ve kapatın.

6. Projeyi derleyin.

7. Çıktı dizininde, *. vsix* dosyasına çift tıklayın.

8. **VSIX yükleyici** ileti kutusu görüntülenir. Uzantıyı yüklemek için yönergeleri izleyin.

9. Visual Studio 'Yu kapatın ve yeniden açın.

::: moniker range="vs-2017"

10. **Uzantılar ve güncelleştirmeler** ' i seçin ( **Araçlar** menüsünde) ve **Şablonlar** kategorisini seçin. Kullanılabilir uzantılardan biri **Proje Şablonum** olmalıdır.

::: moniker-end

::: moniker range=">=vs-2019"

10. **Uzantıları Yönet** ' i ( **Uzantılar** menüsünde) seçin ve **Şablonlar** kategorisini seçin. Kullanılabilir uzantılardan biri **Proje Şablonum** olmalıdır.

::: moniker-end

11. Yeni proje şablonu, **Yeni proje** iletişim kutusunda orijinal proje şablonuyla aynı yerde görüntülenir. Örneğin, bir Visual Basic konsol uygulamasından **vb konsolu** adlı bir şablon oluşturduysanız, **vb konsolu** Visual Basic **Konsolu uygulama** şablonuyla aynı bölmede görünür.

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Yeni proje Iletişim kutusunda şablonun konumunu belirtmek için

1. Şablon klasörleri *{Visual Studio yükleme yolu} \Common7\IDE\ProjectTemplates* ve *{Visual Studio yükleme yolu} \Common7\IDE\ItemTemplates* dizinlerinde bulunur. **Yeni proje** iletişim kutusundaki en üst düzey bölümlerin adları, şablon klasörlerinin adlarıyla tam olarak eşleşmez. Nerede farklıysa, şablon klasörünün adını kullanın.

    *. Vsix* dosya uzantısını *. zip* olarak değiştirin ve ardından dosyayı açın.

2. Şablonun içinde görünmesi gereken **Yeni proje** iletişim kutusunun bölümüyle aynı ada sahip yeni bir klasör oluşturun.

3. Şablon bir alt bölümde görünürse, aynı ada sahip bir alt klasör oluşturun.

4. Template *. zip* dosyasını yeni klasöre taşıyın.

5. *. Zip* uzantısını *. vsix* olarak değiştirin.

6. VSıX bildirimini açın.

7. VSıX bildiriminde, şablonun **varlık** yolunu, şablon dosyasını içeren dizin ağacının köküne işaret eden bir şekilde güncelleştirin. Örneğin, şablon *\Csharp\windows* ise, başvuru *\csharp*' a işaret etmelidir.
