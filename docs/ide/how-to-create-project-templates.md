---
title: Proje şablonları oluşturma
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- project templates [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5cb90ea6f1e404d65ac3c375f49e77dd02c6711c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066921"
---
# <a name="how-to-create-project-templates"></a>Nasıl yapılır: Proje şablonları oluşturma

Bu konuda bir şablon kullanarak nasıl oluşturabileceğiniz gösterilmektedir **şablonu Dışarı Aktarma Sihirbazı**, şablonunuzda paketleri bir *.zip* dosya.

## <a name="to-create-a-user-project-template-by-using-the-export-template-wizard"></a>Şablonu Dışarı Aktarma Sihirbazı'nı kullanarak bir kullanıcı proje şablonu oluşturmak için

1. Bir proje oluşturun.

    > [!NOTE]
    > Bir proje adlandırma şablon kaynağını ne zaman yalnızca geçerli tanımlayıcı karakterler kullanın. Aksi takdirde, şablondan oluşturulan projelerde derleme hataları oluşabilir. Geçerli tanımlayıcı karakterler hakkında daha fazla bilgi için bkz. [bildirilen öğe adları (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) veya [tanımlayıcıları (C++)](/cpp/cpp/identifiers-cpp). Alternatif olarak, [şablon parametreleri](../ide/template-parameters.md) "güvenli" adları sınıflar ve ad alanları için kullanılacak.

2. Bir şablon olarak dışarı hazır olana kadar proje düzenleyin. Örneğin, burada parametre değişikliğini gerçekleşmesi belirtmek için kod dosyalarını düzenlemek isteyebilirsiniz. Bkz: [nasıl yapılır: şablonda parametreleri ikame etme](../ide/how-to-substitute-parameters-in-a-template.md).

3. Üzerinde **proje** menüsünde seçin **şablonu dışarı aktar**.

   **Şablonu Dışarı Aktarma Sihirbazı** açılır.

4. Üzerinde **seçtiğiniz şablon türüne** sayfasında **proje şablonu**. İçin bir şablonu dışarı aktarma ve ardından istediğiniz projeyi seçin **sonraki**.

5. Üzerinde **şablon seçenekleri** önizleme görüntüsü şablonunuz için sayfa ve bir ad ve isteğe bağlı bir açıklama girin. Bu öğe görünmez **yeni proje** iletişim kutusu. Seçin **son**.

   Proje içine aktarılır bir *.zip* dosya belirtilen çıkış konumda ve, seçili olduğunda, Visual Studio'ya içeri aktarıldı.

>[!NOTE]
> Şablonunuzda bulmak için **yeni proje** iletişim kutusunda **yüklü** ve ardından karşılık gelen kategoriyi genişletmek `ProjectType` öğesinde *.vstemplate*dosya. Örneğin, bir *.vstemplate* içeren dosya `<ProjectType>CSharp</ProjectType>` altında görünür **yüklü** > **Visual C#** , varsayılan olarak. Şablonunuzu yalnızca bu dizinde bir klasör oluşturduktan ve yerleştirme, şablonun bir alt proje türü düzenleyebilirsiniz *.zip* içindeki dosya. Daha fazla bilgi için [nasıl yapılır: şablonları bulma ve düzenleme](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="other-ways-to-create-project-templates"></a>Proje şablonları oluşturmak için diğer yolları

Proje şablonları el ile bir klasöre projesi oluşturan dosyaları toplama ve ardından oluşturma oluşturabileceğiniz bir *.vstemplate* uygun meta verileri olan XML dosyası. Daha fazla bilgi için [nasıl yapılır: web şablonlarını elle oluşturma](../ide/how-to-manually-create-web-templates.md).

Visual Studio SDK yüklenmiş ise, tamamlanan şablon dağıtımı için bir VSIX dosyası kullanarak kayabilir **VSIX projesi** şablonu. Daha fazla bilgi için [VSIX proje şablonunu kullanmaya başlama](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Nasıl yapılır: öğe şablonları oluşturma](../ide/how-to-create-item-templates.md)
- [VSIX proje şablonunu kullanmaya başlama](../extensibility/getting-started-with-the-vsix-project-template.md)