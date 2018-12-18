---
title: 'Nasıl yapılır: görüntüleme, kaydetme ve derleme günlüğü dosyalarını yapılandırma | Microsoft Docs'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b745a9e74fd4016db60883b06091a33c6d30d52
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860675"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Nasıl yapılır: görüntüleme, kaydetme ve derleme günlüğü dosyalarını yapılandırma

Visual Studio IDE içinde bir projeyi derledikten sonra bu yapı hakkındaki bilgileri görüntüleyebilirsiniz **çıkış** penceresi. Bu bilgileri kullanarak, örneğin, bir derleme hatası giderme olabilir. C++ projeleri için de aynı bilgileri görüntüleyebileceğiniz bir *.txt* dosyası oluşturulur ve otomatik olarak kaydedilir. Yönetilen kod projeleri için kopyalayın ve yapıştırın bilgilerinden **çıkış** penceresine bir *.txt* dosya ve dosyayı kaydedin. IDE, hangi tür bilgileri, her yapı hakkındaki görüntülemek istediğinizi belirtmek için de kullanabilirsiniz.

MSBuild kullanarak herhangi bir türden proje oluşturuyorsanız, oluşturabileceğiniz bir *.txt* yapı hakkındaki bilgileri kaydetmek için dosya. Daha fazla bilgi için [elde derleme günlükleri](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-view-the-build-log-file-for-a-c-project"></a>Bir C++ projesi için derleme günlük dosyasını görüntülemek için

1.  İçinde **Windows Explorer** veya **dosya Gezgini**, aşağıdaki dosyayı açın:  *\\...\Visual Studio \<sürüm\>\Projects\\ < ProjectName\>\\< ProjectName\>\Debug\\< ProjectName\>.txt*

## <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Yönetilen kod projesi için derleme günlük dosyası oluşturmak için

1.  Menü çubuğunda, **derleme** > **Çözümü Derle**.

2.  İçinde **çıkış** penceresinde derleme bilgileri vurgulayın ve ardından kopyalayın **Pano**.

3.  Gibi bir metin düzenleyicisinde açın **not defteri**bilgileri dosyasına yapıştırın ve kaydedin.

## <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Yapı günlüğünde dahil bilgi miktarını değiştirmek için

1.  Menü çubuğunda, **Araçları** > **seçenekleri**.

2.  Üzerinde **projeler ve çözümler** sayfasında **derleme ve çalıştırma** sayfası.

3.  İçinde **MSBuild proje oluşturması çıkış ayrıntısı** listesinde, aşağıdaki değerlerden birini seçin ve ardından **Tamam** düğmesi.

    |Ayrıntı düzeyi|Açıklama|
    | - |-----------------|
    |**Sessiz**|Yalnızca yapı özetini görüntüler.|
    |**En az**|Derleme ve hatalarını, uyarılarını ve ayrılır iletileri bir özeti, son derece önemli olarak görüntüler.|
    |**Normal**|Yapı özetini görüntüler. hataları, uyarıları ve son derece önemli olarak sınıflandırılmış iletileri; ve yapı ana adımlar. Bu ayrıntı düzeyini en sık kullanacaksınız.|
    |**Ayrıntılı**|Yapı özetini görüntüler. hataları, uyarıları ve son derece önemli olarak sınıflandırılmış iletileri; Tüm; derleme adımları ve itibaren normal önem kategorilere iletileri.|
    |**Tanılama**|Derleme için kullanılabilir olan tüm verileri görüntüler. Özel derleme betikleri ile ve diğer yapı sorunlarını hata ayıklama yardımcı olmak için bu düzeyde ayrıntı kullanabilirsiniz.|

     Daha fazla bilgi için [Seçenekler iletişim kutusu, projeler ve çözümler, derleme ve çalıştırma](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) ve <xref:Microsoft.Build.Framework.LoggerVerbosity>.

    > [!IMPORTANT]
    > Proje etkili olması yaptığınız değişiklikleri için yeniden oluşturmanız gerekir **çıkış** penceresi (tüm projeler) ve  *<ProjectName>.txt* dosyası (yalnızca C++ projeleri için).

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme günlükleri alın](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Derleme ve temizleme projeleri ve Visual Studio çözümleri](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)