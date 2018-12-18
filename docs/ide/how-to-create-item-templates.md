---
title: Öğe şablonları oluşturma
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- item templates [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: b871c5c502c026a8a374af232888c09f18798a0c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062463"
---
# <a name="how-to-create-item-templates"></a>Nasıl yapılır: öğe şablonları oluşturma

Bu makalede bir öğe şablonunu kullanarak oluşturma işlemi gösterilmektedir **şablonu Dışarı Aktarma Sihirbazı**. Şablonunuzu birden fazla dosyadan oluşur olup [nasıl yapılır: çok dosyalı şablonlar oluşturma](../ide/how-to-create-multi-file-item-templates.md).

## <a name="to-add-a-user-item-template-to-the-add-new-item-dialog-box"></a>Yeni Öğe Ekle iletişim kutusuna bir kullanıcı öğe şablonu eklemek için

1. Oluşturun veya bir projeyi Visual Studio'da açın.

1. Projeye bir öğe ekleyin ve istiyorsanız bunu değiştirin.

1. Burada parametre değişikliğini gerçekleşmesi belirtmek için kod dosyasını değiştirin. Daha fazla bilgi için [nasıl yapılır: şablonda parametreleri ikame etme](../ide/how-to-substitute-parameters-in-a-template.md).

1. Üzerinde **proje** menüsünde seçin **şablonu dışarı aktar**.

1. Üzerinde **seçtiğiniz şablon türüne** sayfasında **öğe şablonu**, öğeyi içeren projeyi seçin ve ardından **sonraki**.

1. Üzerinde **vermek öğesi seçin** için bir şablon oluşturmak ve ardından istediğiniz öğeyi seçin **sonraki**.

1. Üzerinde **Seç öğesi başvuruları** sayfasında, şablona dahil, ve ardından derleme başvurularını seçin **sonraki**.

1. Üzerinde **şablon seçenekleri** sayfasında, şablon adı ve isteğe bağlı bir açıklama, simge görüntüsü ve önizleme görüntüsü girin ve ardından **son**.

    Şablonun dosyaları eklenen bir *.zip* dosya ve sihirbazda belirtilen dizine kopyalanır. Varsayılan konum *%USERPROFILE%\Documents\Visual Studio \<sürüm\>\My dışarı aktarılan şablonları*.

1. Seçeneğini seçmediyseniz **otomatik olarak şablonu Visual Studio'ya içeri aktarma** içinde **şablonu Dışarı Aktarma Sihirbazı**, dışarı aktarılan şablonu bulun. Ardından, kullanıcı öğe şablonu dizinine kopyalayın. Varsayılan konum *%USERPROFILE%\Documents\Visual Studio \<sürüm\>\Templates\ItemTemplates*.

1. Visual Studio'yu kapatın ve yeniden açın.

1. Yeni bir proje oluşturun veya varolan bir projeyi açın ve ardından **proje** > **Yeni Öğe Ekle** veya basın **Ctrl** +  **Shift**+**A**.

   Öğe şablonu görünür **Yeni Öğe Ekle** iletişim kutusu. Bir açıklama eklediyseniz **şablonu Dışarı Aktarma Sihirbazı**, tanımı iletişim kutusunun sağ tarafında görünür.

## <a name="to-enable-the-item-template-to-be-used-in-a-universal-windows-app-project"></a>Bir evrensel Windows uygulaması projesinde kullanılacak öğe şablonunu etkinleştirme

Sihirbaz bir temel şablon oluşturmak için işin çoğunu yapar, ancak çoğu durumda el ile değiştirmeniz gerekir. *.vstemplate* şablon verdikten sonra dosya. Örneğin, öğe görünmesini istiyorsanız **Yeni Öğe Ekle** iletişim bir evrensel Windows uygulaması projesi için birkaç fazladan adım gerçekleştirmeniz gerekir.

1. Bir öğe şablonunu dışa aktarmak için önceki bölümdeki adımları izleyin.

1. Ayıklama *.zip* oluşturulan ve açık dosya *.vstemplate* dosyasını Visual Studio'da.

1. İçin bir C# Evrensel Windows projesi, aşağıdaki XML'i ekleyin içinde `<TemplateData>` öğesi:

   ```xml
   <TemplateID>Microsoft.CSharp.Class</TemplateID>
   ```

1. Visual Studio'da Kaydet *.vstemplate* dosya ve kapatın.

1. Kopyalama ve yapıştırma *.vstemplate* geri dosyasını *.zip* dosya.

     Varsa **dosya Kopyala** iletişim kutusu görüntülenirse, seçin **Kopyala ve Değiştir** seçeneği.

Artık bir evrensel Windows projesi için bu şablonu temel alan bir öğe ekleyebilirsiniz **Yeni Öğe Ekle** iletişim kutusu.

## <a name="to-enable-templates-for-specific-project-subtypes"></a>Belirli bir proje alt türleri için şablonlar etkinleştirmek için

Şablonunuz için yalnızca belirli proje alt türleri, Windows, Office, veritabanı veya Web gibi yalnızca görüntüleneceğini belirtebilirsiniz.

1. Bulun `ProjectType` öğesinde *.vstemplate* öğesi şablon dosyası.

1. Ekleme bir [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) öğesi hemen sonra `ProjectType` öğesi.

1. Öğesinin metin değeri şu değerlerden birine ayarlayın:

    - Windows
    - Office
    - Veritabanı
    - Web

Örneğin: `<ProjectSubType>Database</ProjectSubType>`

Aşağıdaki örnek, bir öğe şablonu için gösterir **Office** projeleri.

```xml
<VSTemplate Version="2.0.0" Type="Item" Version="2.0.0">
   <TemplateData>
      <Name>Class</Name>
      <Description>An empty class file</Description>
      <Icon>Class.ico</Icon>
      <ProjectType>CSharp</ProjectType>
      <ProjectSubType>Office</ProjectSubType>
      <DefaultName>Class.cs</DefaultName>
   </TemplateData>
   <TemplateContent>
      <ProjectItem>Class1.cs</ProjectItem>
   </TemplateContent>
</VSTemplate>
```

## <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>Şablonu Dışarı Aktar Sihirbazı'nı kullanarak olmadan bir öğe şablonunu el ile oluşturmak için

Bazı durumlarda bir öğe şablonunu el ile sıfırdan oluşturmak isteyebilirsiniz.

1. Bir proje ve proje öğesi oluşturun.

1. Proje öğesi şablon olarak kaydedilecek hazır olana kadar değiştirin.

1. Burada parametre değiştirme, varsa herhangi bir yere gerçekleşmesi gerektiğini belirtmek için kod dosyasını değiştirin. Parametre değiştirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: şablonda parametreleri ikame etme.](../ide/how-to-substitute-parameters-in-a-template.md)

1. Bir XML dosyası oluşturun ve ile kaydetmek bir *.vstemplate* proje öğesi dosyanız ile aynı dizinde dosya uzantısı.

1. Düzen *.vstemplate* öğesi şablon meta verilerini sağlamak için XML dosyası. Daha fazla bilgi için [Şablon Şeması Başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md) ve önceki bölümdeki örnek.

1. Kaydet *.vstemplate* dosya ve kapatın.

1. İçinde **Windows Explorer**, şablonunuzda dahil etmek istediğiniz dosyaları seçin. Seçime sağ tıklayın ve seçin **göndermek** > **sıkıştırılmış (daraltılmış) klasör**. Seçtiğiniz dosyalar sıkıştırılmadan bir *.zip* dosya.

1. Kopyalama *.zip* dosya ve kullanıcı öğe şablonu konuma yapıştırın. Visual Studio 2017'de varsayılan dizin, *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ItemTemplates*. Daha fazla bilgi için [nasıl yapılır: Proje ve öğe şablonları bulma ve düzenleme](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Nasıl yapılır: çok dosyalı öğe şablonları oluşturma](../ide/how-to-create-multi-file-item-templates.md)
- [Visual Studio Şablon Şeması Başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md)
