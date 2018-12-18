---
title: VSIX Uzantı Şeması 2.0 başvurusu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e295bc8c09f41c4c1c77b216a9d91d0644d2d24e
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388549"
---
# <a name="vsix-extension-schema-20-reference"></a>VSIX Uzantı Şeması 2.0 başvurusu
VSIX dağıtım bildirimi dosyası, bir VSIX paketinin içeriğini açıklar. Dosya biçimi, bir şema tarafından yönetilir. Özel türler ve öznitelikler eklemek bu şema 2.0 sürümünü destekler.  Bildirim şeması genişletilebilir. Yükleyici bildirimi XML öğeleri ve onu anlamıyor öznitelikleri yok sayar.  
  
> [!IMPORTANT]
>  Visual Studio 2015, Visual Studio 2010, Visual Studio 2012 veya Visual Studio 2013 biçimlerde VSIX dosyalarını yükleyebilir.  
  
## <a name="package-manifest-schema"></a>Paket bildirim şeması  
 Bildirim XML dosyasının kök öğe `<PackageManifest>`. Tek bir öznitelikle `Version`, bildirim biçimi sürümünü olduğu. Biçimine büyük değişiklikler yaptıysanız, sürüm biçimi değiştirilir. Bu makalede bildirim biçimi sürüm 2.0, ayarlayarak bildiriminde belirtilen `Version` öznitelik değeri olarak sürüm = "2.0".  
  
### <a name="packagemanifest-element"></a>PackageManifest öğesi  
 İçinde `<PackageManifest>` kök öğesi, aşağıdaki öğeleri kullanabilirsiniz:  
  
-   `<Metadata>` -Meta verileri ve reklam bilgileri paket hakkında. Yalnızca bir `Metadata` öğesi bildiriminde izin verilir.  
  
-   `<Installation>` -Bu bölümde CD'lerden yükleyebilirsiniz uygulama SKU'ları da dahil olmak üzere bu uzantı paketi yüklenebilir biçimini tanımlar. Yalnızca tek bir `Installation` öğesi bildiriminde izin verilir. Bir bildirim olmalıdır bir `Installation` öğesi ya da bu paketin herhangi bir SKU'yu yüklemek gerekmez.  
  
-   `<Dependencies>` -Bu paket bağımlılıklarını isteğe bağlı bir listesi aşağıda tanımlanmıştır.  
  
-   `<Assets>` -Bu bölümde, tüm bu paketi içinde yer alan varlıkları içerir. Olmadan, bu bölümde, bu paket, herhangi bir içerik yüzey olmaz.  
  
-   `<AnyElement>*` -Bildirim şeması öğeleri izin vermek için yeterince esnektir. Bildirim yükleyicisi tarafından tanınmıyor herhangi bir alt öğe Uzantı Yöneticisi API'SİNDE ek XmlElement nesneler olarak sunulur. Bu alt öğeleri kullanılarak, VSIX uzantıları, Visual Studio'da çalışan kod, çalışma zamanında erişebileceği bildirimi dosyasındaki ek verileri tanımlayabilirsiniz. Bkz: <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements%2A> ve <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.LocalizedAdditionalElements%2A>.  
  
### <a name="metadata-element"></a>Meta veri öğesi  
 Bu bölüm, paket kimliğini ve reklam bilgileri hakkındaki meta veriler değildir. `<Metadata>` Aşağıdaki öğeleri içerir:  
  
-   `<Identity>` -Bu paket için kimlik bilgilerini tanımlar ve aşağıdaki öznitelikler içerir:  
  
    -   `Id` -Bu öznitelik, yazarı tarafından seçmiş paketi için benzersiz bir kimliği olması gerekir. CLR Türleri namespaced aynı şekilde adı nitelendirilmesi gerekir: Company.Product.Feature.Name. `Id` Özniteliği 100 karakter ile sınırlıdır.  
  
    -   `Version` -Bu paketi ve içeriğini sürümünü tanımlar. Bu öznitelik CLR derleme sürümü oluşturma biçimdedir: Major.Minor.Build.Revision (1.2.40308.00). Daha yüksek bir sürüm numarasına sahip bir paketi paket güncelleştirmelerini kabul edilir ve mevcut yüklü sürümü yüklenebilir.  
  
    -   `Language` -Bu öznitelik varsayılan dil paketini ve bu bildirimi metinsel verilere karşılık gelir. Örneğin kaynak derlemeleri için bu öznitelik CLR yerel ayar kodu kuralını izleyen: en-us, en, fr-fr. Belirtebileceğiniz `neutral` Visual Studio herhangi bir sürümünü çalıştıran bir dilden uzantısı bildirmek için. Varsayılan değer `neutral` şeklindedir.  
  
    -   `Publisher` -Bu öznitelik, bir şirket veya tek ad bu paketin yayımcısı tanımlar. `Publisher` Özniteliği 100 karakter ile sınırlıdır.  
  
-   `<DisplayName>` -Bu öğe Uzantı Yöneticisi kullanıcı Arabiriminde görüntülenen kullanıcı dostu paket adını belirtir. `DisplayName` İçerik 50 karakterle sınırlıdır.  
  
-   `<Description>` -Bu isteğe bağlı Uzantı Yöneticisi kullanıcı Arabiriminde görüntülenen kısa bir açıklamasını paketi ve içeriğini bir öğedir. `Description` İstediğiniz, ancak bunun herhangi bir metin içeriğini içerebilir 1000 karakterle sınırlıdır.  
  
-   `<MoreInfo>` -Bu isteğe bağlı öğe, bu paketin tam açıklamasını içeren bir sayfaya çevrimiçi bir URL'dir. Protokolü http belirtilmesi gerekir.  
  
-   `<License>` -Bu isteğe bağlı göreli bir yol pakette yer alan bir lisans dosyası (.txt, .rtf) bir öğedir.  
  
-   `<ReleaseNotes>` -Bu isteğe bağlı paketi (.txt, .rtf); Aksi takdirde Sürüm Notları'nı görüntüleyen bir Web sitesi URL'sine bulunan bir yayın notları dosyaya göreli yol bir öğedir.  
  
-   `<Icon>` -Bu isteğe bağlı göreli bir yol pakette yer alan bir görüntü dosyasının (png, bmp, jpeg, ICO) bir öğedir. Simge görüntüsü 32 x 32 piksel olmalıdır (ya da bu boyuta küçültülebilir) ve kullanıcı Arabirimi listview içinde görünür. Hayır ise `Icon` öğesi belirtilmişse, bir varsayılan kullanıcı arabirimini kullanır.  
  
-   `<PreviewImage>` -Bu isteğe bağlı göreli bir yol pakette yer alan bir görüntü dosyasının (png, bmp, jpeg) bir öğedir. Önizleme görüntüsü 200 x 200 piksel olmalıdır ve kullanıcı Arabirimi ayrıntılarında görüntülenir. Hayır ise `PreviewImage` öğesi belirtilmişse, bir varsayılan kullanıcı arabirimini kullanır.  
  
-   `<Tags>` -Bu isteğe bağlı öğe arama ipuçları için kullanılan ek noktalı virgülle ayrılmış metin etiketleri listeler. `Tags` Öğesi 100 karakter ile sınırlıdır.  
  
-   `<GettingStartedGuide>` -Bu isteğe bağlı bir HTML dosyası için göreli bir yol veya uzantısı veya bu paket içindeki içeriği nasıl kullanılacağı hakkında bilgi içeren bir Web sitesinin URL'sini bir öğedir. Bu kılavuz, yüklemenin bir parçası olarak başlatılır.  
  
-   `<AnyElement>*` -Bildirim şeması öğeleri izin vermek için yeterince esnektir. Bildirim yükleyicisi tarafından tanınmayan herhangi bir alt öğe XmlElement nesnelerin bir listesi sunulur. Bu alt öğeleri kullanılarak, VSIX uzantılarını ek veri bildirim dosyasında tanımlayabilir ve bunları çalışma zamanında numaralandırır.  
  
### <a name="installation-element"></a>Yükleme öğesi  
 Bu bölümde, bu paketin yüklenmesi biçimini ve CD'lerden yükleyebilirsiniz uygulama SKU'ları tanımlar. Bu bölüm, aşağıdaki öznitelikler içerir:  
  
-   `Experimental` -Bu öznitelik tüm kullanıcılar için şu anda yüklü olan bir uzantısı varsa, ancak aynı bilgisayarda güncelleştirilmiş bir sürümünü geliştiriyorsanız true olarak ayarlayın. Örneğin, tüm kullanıcılar için MyExtension 1.0 yüklediğiniz, ancak istiyorsanız MyExtension 2.0 aynı bilgisayarda hata ayıklamak için Deneysel ayarlamak "true" =. Bu öznitelik, Visual Studio 2015 güncelleştirme 1'de kullanılabilir ve üzerinde desteklenir.  
  
-   `Scope` -Bu özniteliği, "Genel" veya "ProductExtension" değerini alabilir:  
  
    -   "Genel", belirli bir SKU'ya yükleme kapsamında değil belirtir. Örneğin, bir uzantı SDK'sı yüklü olduğunda bu değeri kullanılır.  
  
    -   "ProductExtension", tek Visual Studio SKU'lar için kapsamlı bir geleneksel VSIX uzantısı (sürüm 1.0) yüklendiğini belirtir. Varsayılan değer budur.  
  
-   `AllUsers` -İsteğe bağlı bu özniteliği, bu paket tüm kullanıcılar için yükleneceğini belirtir. Varsayılan olarak, paketi, kullanıcı başına olduğunu belirten, bu öznitelik false değeridir. (Bu değeri true olarak ayarlayın, yüklemeyi gerçekleştiren kullanıcının sonuç VSIX'i yüklemek için yönetimsel ayrıcalık düzeyine Yükselt gerekir.  
  
-   `InstalledByMsi` -İsteğe bağlı bu öznitelik, bir MSI tarafından bu paketin yüklü olup olmadığını belirtir. Bir MSI tarafından yüklenen paketler yüklenir ve MSI (Programlar ve Özellikler) ve değil Visual Studio uzantısı Yöneticisi tarafından yönetilir.  Varsayılan olarak, bir MSI tarafından paketin yüklü olmadığını belirtir, bu öznitelik false değeridir.  
  
-   `SystemComponent` -İsteğe bağlı bu özniteliği, bu paket sistem bileşeni değerlendirilip değerlendirilmeyeceğini belirtir. Sistem bileşenleri Uzantı Yöneticisi Arabiriminde gösterme ve güncelleştirilemiyor. Varsayılan olarak, paket sistem bileşeni olmadığını belirtir, bu öznitelik false değeridir.  
  
-   `AnyAttribute*` - `Installation` Öğesi, çalışma zamanında bir ad-değer çiftinin sözlüğü olarak kullanıma sunulacak öznitelikleri açık uçlu bir kümesini kabul eder.  
  
-   `<InstallationTarget>` -VSIX Yükleyici paketi burada yükler konumu bu öğe denetler. Varsa değerini `Scope` özniteliktir "ProductExtension" paket bildirim dosyası içeriğini kullanılabilirliğini uzantılarını bildirmek üzere bir parçası olarak yüklü olan bir SKU hedef gerekir. `<InstallationTarget>` Öğesinin aşağıdaki ne zaman öznitelikleri `Scope` özniteliğine sahip açıkça veya varsayılan değer "ProductExtension":  
  
    -   `Id` -Bu öznitelik, paket tanımlar.  Öznitelik ad alanı kuralını izler: Company.Product.Feature.Name. `Id` Özniteliği 100 karakter ile sınırlıdır ve yalnızca alfasayısal karakterler içerebilir. Beklenen değer:  
  
        -   Microsoft.VisualStudio.IntegratedShell  
  
        -   Microsoft.VisualStudio.Pro  
  
        -   Microsoft.VisualStudio.Premium  
  
        -   Microsoft.VisualStudio.Ultimate  
  
        -   Microsoft.VisualStudio.VWDExpress  
  
        -   Microsoft.VisualStudio.VPDExpress  
  
        -   Microsoft.VisualStudio.VSWinExpress  
  
        -   Microsoft.VisualStudio.VSLS  
  
        -   My.Shell.App  
  
    -   `Version` -Bu öznitelik, minimum ve maksimum desteklenen sürümleri bu SKU ile bir sürüm aralığı belirtir. Bir paket sürümlerini destekliyorsa SKU'ları ayrıntı. Sürüm aralığı gösterimi [10.0-11.0] olduğu  
  
        -   [-en düşük sürüm kapsamlı.  
  
        -   ]-en yüksek sürüm kapsamlı.  
  
        -   (-özel en düşük sürüm.  
  
        -   )-en yüksek sürümü özel.  
  
        -   Tek sürüm # - yalnızca belirtilen sürümü.  
  
        > [!IMPORTANT]
        >  VSIX şemasının 2.0 sürümünde, Visual Studio 2012'de sunulmuştur. Bu şema kullanmak için Visual Studio 2012 olmalıdır veya daha sonra bu makinede yüklü ve ürünün bir parçası olan VSIXInstaller.exe kullanın. Visual Studio 2012 veya üzeri Vsıxınstaller, ancak sonraki sürümlerinde bir yükleyici kullanarak yalnızca Visual Studio'nun önceki sürümlerini hedefleyebilir. 
        
        Visual Studio 2017 sürüm numaraları bulunabilir [Visual Studio derleme numaraları ve yayın tarihleri](../install/visual-studio-build-numbers-and-release-dates.md).
        
        Visual Studio 2017 sürümleri için sürüm belirtme, alt sürümü her zaman olmalıdır **0**. Visual Studio 2017 sürüm 15.3.26730.0 [15.0.26730.0,16.0). Örneğin, ifade edilmelidir Bu yalnızca, Visual Studio 2017 sürüm numaraları gereklidir.
  
    -   `AnyAttribute*` - `<InstallationTarget>` Öğesi, çalışma zamanında bir ad-değer çiftinin sözlüğü olarak sunulan açık uçlu bir kümesini öznitelikleri sağlar.  
  
### <a name="dependencies-element"></a>Bağımlılıklar öğesi  
 Bu öğe bu paket bildirir bağımlılıkların bir listesini içerir. Herhangi bir bağımlılığın belirtilirse, bu paketleri (tarafından tanımlanan kendi `Id`) önce yüklenmiş olmalıdır.  
  
-   `<Dependency>` Öğe - bu alt öğenin öznitelikleri şunlardır:  
  
    -   `Id` -Bu öznitelik için bağımlı paketi benzersiz bir kimliği olması gerekir. Bu kimlik değeri eşleşmelidir `<Metadata><Identity>Id` bu pakete bağımlı olan bir paketin özniteliği. `Id` Öznitelik ad alanı kuralını izler: Company.Product.Feature.Name. Öznitelik 100 karakter ile sınırlıdır ve yalnızca alfasayısal karakterler içerebilir.  
  
    -   `Version` -Bu öznitelik, minimum ve maksimum desteklenen sürümleri bu SKU ile bir sürüm aralığı belirtir. Bir paket sürümlerini destekliyorsa SKU'ları ayrıntı. Sürüm aralığı gösterimi [12.0, 13.0], burada:  
  
        -   [-en düşük sürüm kapsamlı.  
  
        -   ]-en yüksek sürüm kapsamlı.  
  
        -   (-özel en düşük sürüm.  
  
        -   )-en yüksek sürümü özel.  
  
        -   Tek sürüm # - yalnızca belirtilen sürümü.  
  
    -   `DisplayName` -Bu öznitelik iletişim kutuları ve hata iletileri gibi kullanıcı Arabirimi öğelerinde kullanılan bağımlı paketi görünen adıdır. Bağımlı paketi MSI tarafından yüklenmediği sürece özniteliği isteğe bağlıdır.  
  
    -   `Location` -İsteğe bağlı bu özniteliği, iç içe geçmiş bir VSIX paketi bu VSIX'e göreli yol veya bir URL'ye bağımlılık için indirme konumunu belirtir. Bu öznitelik, önkoşul istediğiniz paketi bulmak kullanıcının yardımcı olmak için kullanılır.  
  
    -   `AnyAttribute*` - `Dependency` Öğesi, çalışma zamanında bir ad-değer çiftinin sözlüğü olarak kullanıma sunulacak öznitelikleri açık uçlu bir kümesini kabul eder.  
  
### <a name="assets-element"></a>Varlıklar öğesi  
 Bu öğe bir listesini içeren `<Asset>` uzantısı ya da içerik her öğe için etiketleri, bu paket tarafından ortaya.  
  
- `<Asset>` -Bu öğe aşağıdaki öznitelikler ve öğeler içeriyor:  
  
  - `Type` -Uzantı veya bu öğe tarafından temsil edilen içerik türü. Her `<Asset>` tek bir öğe olmalıdır `Type`, ancak birden çok `<Asset>` öğeleri aynı olabilir `Type`. Bu öznitelik ad alanı kurallarına göre tam bir ad temsil edilebilir. Bilinen türleri şunlardır:  
  
    1. Microsoft.VisualStudio.VsPackage  
  
    2. Microsoft.VisualStudio.MefComponent  
  
    3. Microsoft.VisualStudio.ToolboxControl  
  
    4. Microsoft.VisualStudio.Samples  
  
    5. Microsoft.VisualStudio.ProjectTemplate  
  
    6. Microsoft.VisualStudio.ItemTemplate  
  
    7. Microsoft.VisualStudio.Assembly  
  
       Kendi türlerinizi oluşturmak ve bunları benzersiz adlar verin. Visual Studio içindeki çalışma zamanında kodunuzu listeleme ve Uzantı Yöneticisi API aracılığıyla bu özel tür erişim.  
  
  - `Path` -Dosya veya klasörün varlığı içeren paket içindeki göreli yolu.  
    
  - `TargetVersion` -belirli bir varlık uygulandığı sürüm aralığı. Varlıklar farklı sürümlerine, Visual Studio'nun birden çok sürümünü sevk edilmesi için kullanılır. Geçerli olması Visual Studio 2017.3 veya daha yenisini gerektirir.
  
  - `AnyAttribute*` -Çalışma zamanında bir ad-değer çiftinin sözlüğü olarak sunulan açık uçlu bir kümesini öznitelikleri.  
  
     `<AnyElement>*` -Herhangi bir yapılandırılmış içerik arasında izin verilen bir `<Asset>` başlar ve bitiş etiketi. Tüm öğeleri XmlElement nesnelerin bir listesini sunulur. VSIX uzantılarını yapısal türe özgü meta veriler bildirim dosyasında tanımlayabilir ve bunları çalışma zamanında numaralandırır.  
  
### <a name="sample-manifest"></a>Örnek bildirimi  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">  
  <Metadata>  
    <Identity Id="0000000-0000-0000-0000-000000000000" Version="1.0" Language="en-US" Publisher="Company" />  
    <DisplayName>Test Package</DisplayName>  
    <Description>Information about my package</Description>  
    <MoreInfo>http://www.fabrikam.com/Extension1/</MoreInfo>  
    <License>eula.rtf</License>  
    <ReleaseNotes>notes.txt</ReleaseNotes>  
    <Icon>Images\icon.png</Icon>  
    <PreviewImage>Images\preview.png</PreviewImage>  
  </Metadata>  
  <Installation InstalledByMsi="false" AllUsers="false" SystemComponent="false" Scope="ProductExtension">  
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="[11.0, 12.0]" />  
  </Installation>  
  <Dependencies>  
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="[4.5,)" />  
    <Dependency Id="Microsoft.VisualStudio.MPF.12.0" DisplayName="Visual Studio MPF 12.0" d:Source="Installed" Version="[12.0]" />  
  </Dependencies>  
  <Assets>  
    <Asset Type="Microsoft.VisualStudio.VsPackage" d:Source="Project" d:ProjectName="%CurrentProject%" Path="|%CurrentProject%;PkgdefProjectOutputGroup|" />  
  </Assets>  
</PackageManifest>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio uzantıları gönderme](../extensibility/shipping-visual-studio-extensions.md)
