---
title: 'Nasıl yapılır: oluşturma bir. Vsct dosya | Microsoft Docs'
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
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bbfdcf605a1c4346874ec222937a458225788151
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802642"
---
# <a name="how-to-create-a-vsct-file"></a>Nasıl yapılır: oluşturma bir. Vsct dosyası
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir XML tabanlı Visual Studio komut tablosu (.vsct) yapılandırma dosyası oluşturmanın birkaç yolu vardır.  
  
- İçinde yeni bir VSPackage oluşturabilirsiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] paketi şablonu.  
  
- XML-tabanlı komut tablosu yapılandırma derleyici Vsct.exe, varolan .ctc dosyasından bir dosya oluşturmak için kullanabilirsiniz.  
  
- Vsct.exe varolan .cto dosyasından .vsct dosyası oluşturmak için kullanabilirsiniz.  
  
- El ile yeni bir .vsct dosyası da oluşturabilirsiniz.  
  
  Bu konuda, el ile yeni .vsct dosyası oluşturma açıklanmaktadır.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>El ile yeni bir .vsct dosyası oluşturmak için  
  
1.  Başlangıç [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
2.  Üzerinde **dosya** menüsünde **yeni**ve ardından **dosya**.  
  
3.  İçinde **şablonları** bölmesinde tıklayın **XML dosyası** ve ardından **açık**.  
  
4.  Üzerinde **görünümü** menüsünde tıklatın **Özellikler penceresi** XML dosyasının özelliklerini görüntülemek için.  
  
5.  İçinde **özellikleri** penceresi, şemalar özelliği Gözat (...) düğmesine tıklayın.  
  
6.  XSD şemaları listesinde vsct.xsd şema seçin. Listede değilse, **Ekle** ve dosyayı yerel bir sürücüde bulun. Tıklayın **Tamam** işiniz bittiğinde.  
  
7.  XML dosyasında yazın `<CommandTable` ve sonra SEKME tuşuna basın. Kapatma etiketi yazarak `>`.  
  
     Bu temel .vsct dosyası oluşturur.  
  
8.  XML dosyasının eklemek istediğiniz öğeleri doldurmak, için uygun [VSCT şema](../../extensibility/vsct-xml-schema-reference.md). Daha fazla bilgi için [yazma. Vsct dosyaları](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yalnızca .vsct dosyası bir projeye ekleme derlemek için neden olmaz. Derleme işleminde içermelidir.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Projenin derlenmesi için .vsct dosyası eklemek için  
  
1.  Proje dosyanız, düzenleyicide açın. Proje yüklenirse, onu önce bellekten gerekir.  
  
2.  Ekleme bir [ItemGroup öğesi](../../msbuild/itemgroup-element-msbuild.md) aşağıdaki örnekte gösterildiği gibi bir VSCTCompile öğesi içeren.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     ResourceName öğe her zaman ayarlanmalıdır `Menus.ctmenu`.  
  
3.  Projeniz bir .resx dosyası içeriyorsa, aşağıdaki örnekte gösterildiği gibi bir MergeWithCTO öğesi içeren bir EmbeddedResource öğeyi ekleyin.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Bu işaretleme, katıştırılmış kaynaklar içeren ItemGroup öğesi içinde gitmeniz gerekir.  
  
4.  Genellikle, bir paket dosyası açmak *ProjectName*Package.cs veya *ProjectName*Düzenleyicisi'nde Package.vb.  
  
5.  ProvideMenuResource özniteliği aşağıdaki örnekte gösterildiği gibi paket sınıfına ekleyin.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     İlk parametre değeri, proje dosyasında tanımlanan ResourceName özniteliğinin değeri aynı olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yazma. Vsct dosyaları](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio komut tablosu (. Vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Nasıl yapılır: oluşturma bir. Vsct mevcut bir dosya. Ctc dosyası](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Nasıl yapılır: oluşturma bir. Vsct mevcut bir dosya. Cto dosyası](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md)

