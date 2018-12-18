---
title: 'Nasıl yapılır: öğe şablonları oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project item templates, XML reference
- project item templates, custom template locations
- project item templates, creating
- project item templates, metadata files
ms.assetid: 77bc53d4-d607-4820-a032-7e3b365891b5
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8559fb8b32b83d352bd9ec82cf426903aff13a19
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863639"
---
# <a name="how-to-create-item-templates"></a>Nasıl Yapılır: Öğe Şablonları Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Adımları [ilk yordam](../ide/how-to-create-item-templates.md#export_template) Bu konuyu kullanarak bir öğe şablonu oluşturma işlemi gösterilmektedir **şablonu dışarı aktar** Sihirbazı. Şablonunuzu birden fazla dosyadan oluşur olup [nasıl yapılır: çok dosyalı öğe şablonları oluşturma](../ide/how-to-create-multi-file-item-templates.md).  
  
 Birçok iş temel şablon oluşturmak için sihirbaz yapar, ancak çoğu durumda şablon verdikten sonra .vstemplate dosyasını el ile değiştirmeniz gerekir. Örneğin, öğe görünmesini istiyorsanız **Yeni Öğe Ekle** iletişim kutusu için bir [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulaması projesinde sahip olacaksınız birkaç fazladan adım gerçekleştirmeniz. [İkinci yordam](../ide/how-to-create-item-templates.md#modify_template) bu konuda, o görevi gerçekleştirmenize yardımcı olur.  
 
 Bazı durumlarda istediğiniz veya bir öğe şablonunu sıfırdan el ile oluşturmanız gerekir. [Üçüncü yordamı](../ide/how-to-create-item-templates.md#create_template) bunun nasıl yapılacağını gösterir.  
  
 Bkz: [Visual Studio şablon şeması başvurusu](../extensibility/visual-studio-template-schema-reference.md) .vstemplate dosyasında kullanılan öğeleri hakkında bilgi için.  
  
### <a name="to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box"></a>Yeni Öğe Ekle iletişim kutusuna özel proje öğesi şablon eklemek için  
  
1.  Bir proje oluşturduğunuzda veya [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
2.  Projeye bir öğe ekleyin ve isterseniz bunu değiştirebilirsiniz.  
  
3.  Burada parametre değişikliğini gerçekleşmesi belirtmek için kod dosyasını değiştirin. Daha fazla bilgi için [nasıl yapılır: şablonda parametreleri ikame](../ide/how-to-substitute-parameters-in-a-template.md).  
  
4.  Üzerinde **dosya** menüsünü tıklatın **şablonu dışarı aktar**.  
  
5.  Tıklayın **öğe şablonu**, öğeyi içeren projeyi seçin ve tıklayın **sonraki**.  
  
6.  Bir şablon oluşturmak ve istediğiniz öğeyi seçin **sonraki**.  
  
7.  Şablona dahil ve derleme başvurularını seçin **sonraki**.  
  
8.  Simge dosyası adı, önizleme görüntüsünü, şablon adı ve şablon açıklamasını yazın ve tıklayın **son**.  
  
     Şablonun dosyaları .zip dosyası olarak eklenir ve iletişim kutusunda belirttiğiniz her dizin kopyalanır. Varsayılan konum **... \Users\\< kullanıcı adı\>\Documents\Visual Studio \<sürüm > \My dışarı aktarılan şablonları\\**  klasör.  
  
    > [!WARNING]
    >  Visual Studio'nun önceki sürümlerinde varsayılan konumdur **... \Users\\< kullanıcı adı\>\Documents\Visual Studio \<sürüm > \Templates\ItemTemplates**.  
  
### <a name="to-enable-the-item-template-to-be-used-in-a-store-project"></a>Bir depolama projesinde kullanılacak öğe şablonunu etkinleştirme  
  
1. Bir öğe şablonunu dışa aktarmak için yukarıdaki yordamdaki adımları izleyin.  
  
2. .Vstemplate dosyası kopyalanan .zip dosyasından ayıkla... \Users\\*kullanıcıadı*\Documents\Visual Studio *sürüm*\Templates\ItemTemplates\ (veya **Şablonlarım dışarı**) klasörü.  
  
3. .Vstemplate dosyasını Visual Studio'da açın.  
  
4. Bir Windows 8.1 için C# projesinde, .vstemplate dosyasında mağazası aşağıdaki XML'i açılış ve kapanış içinde ekleme `<TemplateData>` etiketi: `<TemplateGroupID>WinRT-Managed</TemplateGroupID>`.  
  
    Değerini bir C++ Windows 8.1 mağazası projesi kullanan `WinRT-Native-6.3`. Windows 10 ve diğer proje türleri için bkz: [Templategroupıd öğesi (Visual Studio şablonları)](../extensibility/templategroupid-element-visual-studio-templates.md).  
  
    Aşağıdaki örnek, XML satırından sonra bir .vstemplate dosyasının tüm içeriğini gösterir `<TemplateGroupID>WinRT-Managed</TemplateGroupID>` için eklendi. Bu örnek, C# projelerine özgüdür. Değiştirebileceğiniz <ProjectTpe> ve \< [Templategroupıd](../extensibility/templategroupid-element-visual-studio-templates.md)> diğer dil ve proje türlerini belirtmek için öğeleri.  
  
   ```xml  
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
     <TemplateData>  
       <DefaultName>MyItemStoreTemplate.xaml</DefaultName>  
       <Name>MyItemStoreTemplate</Name>  
       <Description>This is an example itemtemplate</Description>  
       <ProjectType>CSharp</ProjectType>  
       <SortOrder>10</SortOrder>  
       <Icon>__TemplateIcon.ico</Icon>  
       <TemplateGroupID>WinRT-Managed</TemplateGroupID>  
     </TemplateData>  
     <TemplateContent>  
       <References />  
       <ProjectItem SubType="Designer" TargetFileName="$fileinputname$.xaml" ReplaceParameters="true">MyItemTemplate.xaml</ProjectItem>  
       <ProjectItem SubType="Code" TargetFileName="$fileinputname$.xaml.cs" ReplaceParameters="true">MyItemTemplate.xaml.cs</ProjectItem>  
     </TemplateContent>  
   </VSTemplate>  
   ```  
  
    Diğer olası Templategroupıd değerler için bkz. [Templategroupıd öğesi (Visual Studio şablonları)](../extensibility/templategroupid-element-visual-studio-templates.md)). Tam .vstemplate işinize yarayacak [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)  
  
5. Visual Studio'da .vstemplate dosyasını kaydedin ve kapatın.  
  
6. Yer alan .zip dosyasına .vstemplate dosyasını kopyalayıp.. \Users\\*kullanıcıadı*\Documents\Visual Studio *sürüm*\Templates\ItemTemplates\ klasör.  
  
    Varsa **dosya Kopyala** iletişim kutusu görüntülenirse, seçin **Kopyala ve Değiştir** seçeneği.  
  
   Artık bu şablona dayanan bir öğeyi ekleyebileceğiniz bir [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] kullanarak proje **Yeni Öğe Ekle** iletişim kutusu.  
  
   Parametre adları hakkında daha fazla bilgi için bkz: [şablon parametreleri](../ide/template-parameters.md).  
  
### <a name="to-enable-templates-for-specific-project-sub-types"></a>Belirli bir proje alt türleri için şablonlar etkinleştirmek için  
  
1. Geliştirme ortamı, proje öğeleri Öğe Ekle iletişim kutusundan belirli projeleri için kullanılabilir hale sağlar. Windows, Web, Office veya veritabanı projeleri için özel öğeler kullanılabilmesi için bu yordamı kullanın.  
  
    ProjectType öğesi öğe şablonu için .vstemplate dosyasını bulun.  
  
    Ekleme bir [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) öğeden hemen sonra ProjectType öğesi.  
  
2. Öğesinin metin değeri şu değerlerden birine ayarlayın:  
  
   1. Windows  
  
   2. Office  
  
   3. Veritabanı  
  
   4. Web  
  
      Örneğin: `<ProjectSubType>Database</ProjectSubType>`  
  
      Aşağıdaki örnek, Office projeleri için kullanılabilir öğe şablonu gösterir.  
  
   ```  
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
  
### <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>Şablonu Dışarı Aktar Sihirbazı'nı kullanarak olmadan bir öğe şablonunu el ile oluşturmak için  
  
1.  Bir proje ve proje öğesi oluşturun.  
  
2.  Proje öğesi şablon olarak kaydedilecek hazır olana kadar değiştirin.  
  
3.  Burada parametre değişikliği gerçekleşmesi gerektiğini belirtmek için kod dosyasını uygun bir şekilde değiştirin. Parametre değiştirme hakkında daha fazla bilgi için bkz: nasıl yapılır: şablonda parametreleri ikame.  
  
4.  Bir XML dosyası oluşturun ve bir .vstemplate dosya adı uzantısı, yeni bir öğe şablonu ile aynı dizinde kullanarak kaydedin.  
  
5.  Öğe şablonu meta verilerini sağlamak için .vstemplate XML dosyasına yazar. Daha fazla bilgi için [Visual Studio şablon şeması başvurusu](../extensibility/visual-studio-template-schema-reference.md) ve önceki bölümdeki örnek.  
  
6.  .Vstemplate dosyasını kaydedin ve kapatın.  
  
7.  Windows Gezgini'nde, şablona dahil, seçime sağ tıklayın, göndermek için tıklayın ve ardından sıkıştırılmış klasöre tıklayın istediğiniz dosyaları seçin. Seçtiğiniz dosyaların bir .zip dosyasına sıkıştırılır.  
  
8.  .Zip dosyasını kopyalayın ve kullanıcı öğe şablonu konuma yapıştırın. Visual Studio 2015'te varsayılan dizin... \Users\\< kullanıcı adı\>\Documents\Visual Studio 2015\Templates\ItemTemplates\\. Daha fazla bilgi için bkz: nasıl yapılır: bulun ve düzenleme proje ve öğe şablonları.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)   
 [Nasıl yapılır: çok dosyalı öğe şablonları oluşturma](../ide/how-to-create-multi-file-item-templates.md)   
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)