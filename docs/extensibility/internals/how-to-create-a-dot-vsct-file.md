---
title: 'Nasıl yapılır: oluşturma bir. Vsct dosya | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 612ad5668ebb1033ef07dcad1fc07030d78e1643
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921216"
---
# <a name="how-to-create-a-vsct-file"></a>Nasıl yapılır: .vsct dosyası oluşturma  
  
Bir XML tabanlı Visual Studio komut tablosu yapılandırması oluşturmanın birkaç yolu vardır (*.vsct*) dosyası.  
  
- İçinde yeni bir VSPackage oluşturabilirsiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] paketi şablonu.  
  
- XML-tabanlı komut tablosu yapılandırma derleyici kullanabileceğiniz *Vsct.exe*, varolan bir dosya oluşturmak için *.ctc* dosya.  
  
- Kullanabileceğiniz *Vsct.exe* oluşturmak için bir *.vsct* mevcut bir dosyadan *.cto* dosya.  
  
- El ile yeni bir oluşturabilirsiniz *.vsct* dosya.  
  
  Bu makalede el ile yeni bir oluşturma açıklanır *.vsct* dosya.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>El ile yeni bir .vsct dosyası oluşturmak için  
  
1. Başlangıç [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
2. Üzerinde **dosya** menüsünde **yeni**ve ardından **dosya**.  
  
3. İçinde **şablonları** bölmesinde tıklayın **XML dosyası** ve ardından **açık**.  
  
4. Üzerinde **görünümü** menüsünde tıklatın **özellikleri** XML dosyasının özelliklerini görüntülemek için.  
  
5. İçinde **özellikleri** penceresinde tıklayın **Gözat** düğmesini **şemaları** özelliği.  
  
6. XSD şemaları listeden seçin *vsct.xsd* şema. Listede değilse, **Ekle** ve dosyayı yerel bir sürücüde bulun. Tıklayın **Tamam** işiniz bittiğinde.  
  
7. XML dosyasında yazın *< CommandTable* ve tuşuna **sekmesini**. Kapatma etiketi yazarak *>*.  
  
    Bu eylem, bir temel oluşturur. *.vsct* dosya.  
  
8. XML dosyasının eklemek istediğiniz öğeleri doldurmak, için uygun [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md). Daha fazla bilgi için [.vsct dosyaları yazma](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Nasıl yapılır: Varolan .ctc dosyasından bir .vsct dosyası oluşturma  
  
XML tabanlı oluşturabilirsiniz *.vsct* var olan bir komut tablosu dosyasından *.ctc* kaynak dosyası. Bunu yaptığınızda yeni avantajlarından yararlanabilirsiniz XML tabanlı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komut tablosu (VSCT) derleyici biçimi.  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Bir .ctc dosyasından .vsct dosyası oluşturmak için  
  
1. Perl dil bir kopyasını edinin.  
  
2. Perl komut dosyasının bir kopyasını elde *ConvertCTCToVSCT.pl*, tipik olarak bulunan  *\<Visual Studio SDK'sını yükleme yolu > \VisualStudioIntegration\Tools\bin* klasör.  
  
3. Bir kopyasını elde *.ctc* dönüştürmek istediğiniz bir kaynak dosyası.  
  
4. Dosyaları aynı dizine koyun.  
  
5. İçinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komut istemi penceresinin, dizine gidin.  
  
6. Tür  
  
   ```  
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
   ```  
  
    Burada *PkgCmd.ctc* adıdır *.ctc* dosya ve *PkgCmd.vsct* adıdır *.vsct* oluşturmak istediğiniz dosya.  
  
    Bu eylem yeni bir oluşturur *.vsct* XML komut tablosu kaynak dosyası. Kullanarak dosyanın derleme *Vsct.exe*, siz VSCT derleyici olduğu diğer *.vsct* dosya.  
  
   > [!NOTE]
   >  Okunabilirliğini geliştirmek *.vsct* XML açıklamaları yeniden biçimlendirme tarafından dosya.  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Nasıl yapılır: Varolan .cto dosyasından .vsct dosyası oluşturma  
  
XML tabanlı oluşturabilirsiniz *.vsct* var olan bir ikili dosyadan *.cto* dosya. Bunun yapılması, yeni komut tablosu derleyici biçimi yararlanmak sağlar. Bu işlem works bile *.cto* dosya gelen derlenmiş bir *.ctc* dosya. Düzenle ve derleme *.vsct* .cto dosyasına başka bir dosya.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Bir .cto dosyasından .vsct dosyası oluşturmak için  
  
1.  Kopyalarını almak *.cto* dosya ve kendi ilişkili *.ctsym* dosya.  
  
2.  Dosyaları ile aynı dizine yerleştirin *vsct.exe* derleyici.  
  
3.  Visual Studio komut isteminde içeren dizine gidin *.cto* ve *.ctsym* dosyaları.  
  
4.  Tür  

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     Burada \<ctofilename\> adıdır *.cto* dosyası \<vsctfilename\> adıdır *.vsct* dosya oluşturmak ve \<symfilename\> adıdır *.ctsym* dosya.  
  
     Bu işlem yeni bir oluşturur *.vsct* XML komut tablosu derleyici dosyası. Düzenleyin ve dosyanın ile derleme *vsct.exe*, siz vsct derleyici olduğu diğer *.vsct* dosya.  
  
## <a name="compile-the-code"></a>Kod derleme  
 Yalnızca ekleme bir *.vsct* bir projeye neden olmaz, derlemek. Derleme işleminde içermelidir.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Projenin derlenmesi için .vsct dosyası eklemek için  
  
1.  Proje dosyanız, düzenleyicide açın. Proje yüklenirse, onu önce bellekten gerekir.  
  
2.  Ekleme bir [ItemGroup öğesi](../../msbuild/itemgroup-element-msbuild.md) içeren bir `VSCTCompile` öğesi, aşağıdaki örnekte gösterildiği gibi.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     `ResourceName` Öğe her zaman ayarlanmalıdır `Menus.ctmenu`.  
  
3.  Projeniz varsa bir *.resx* ekleyin bir `EmbeddedResource` öğesini içeren bir `MergeWithCTO` öğesi, aşağıdaki örnekte gösterildiği gibi:  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Bu işaretleme içinde gitmesi gereken `ItemGroup` katıştırılmış kaynaklar içeren öğe.  
  
4.  Genellikle, bir paket dosyası açmak  *\<ProjectName\>Package.cs* veya  *\<ProjectName\>Package.vb*, düzenleyicide.  
  
5.  Ekleme bir `ProvideMenuResource` aşağıdaki örnekte gösterildiği gibi paket sınıfına özniteliği.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     İlk parametre değeri değeriyle eşleşmelidir `ResourceName` proje dosyasında tanımlı öznitelik.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [.Vsct dosyaları yazma](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio komut tablosu (.vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md)