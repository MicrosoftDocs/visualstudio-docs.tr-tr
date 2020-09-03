---
title: UML genişletmek için bir profil tanımlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- profiles, UML
- stereotypes, UML
- UML, profiles and stereotypes
- UML - extending, defining profiles
- UML, customizing
- UML, profiles
ms.assetid: 776589cb-f89d-48d5-aafa-04a4c074b0d6
caps.latest.revision: 44
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a495a566f78ceb2b89f8e2070837f038da352a4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918875"
---
# <a name="define-a-profile-to-extend-uml"></a>UML’yi genişletmek için profil tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Standart model öğelerini belirli amaçlarla özelleştirmek için bir *UML profili* tanımlayabilirsiniz. Bir profil, bir veya daha fazla *UML stereotiplerini*tanımlar. Bir stereotip, belirli bir nesne türünü temsil eden bir türü işaretlemek için kullanılabilir. Bir stereotip Ayrıca bir öğenin özellik listesini genişletebilir.

 Çeşitli profiller, Visual Studio 'nun desteklenen sürümleriyle yüklenir. Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport). Bu profiller ve stereotiplerin nasıl uygulanacağı hakkında daha fazla bilgi için bkz. [modelinize profiller ve Stereotipler Ile özelleştirme](../modeling/customize-your-model-with-profiles-and-stereotypes.md).

 UML 'i kendi iş alanı veya mimarinize uyarlamak ve genişletmek için kendi profillerinizi tanımlayabilirsiniz. Örneğin:

- Web sitelerini sık sık tanımlarsanız, sınıf diyagramlarındaki sınıflara uygulanabilen bir «Web sayfası» stereotipi sağlayan kendi profilinizi tanımlayabilirsiniz. Daha sonra bir Web sitesi planlamak için sınıf diyagramlarını kullanabilirsiniz. Her «Web sayfası» sınıfı, sayfa içeriği, stili, vb. için ek özelliklere sahip olur.

- Bankacılık yazılımı geliştiriyorsanız, «Account» stereotipi sağlayan bir profil tanımlayabilirsiniz. Daha sonra farklı hesap türlerini tanımlamak ve aralarındaki ilişkileri göstermek için sınıf diyagramlarını kullanabilirsiniz.

  Kendi profillerinizi ekibinize dağıtabilirsiniz. Her ekip üyesi, profilinizi yükleyebilir. Bu, kendi stereotiplerini kullanan modelleri düzenlemenizi ve oluşturmasını sağlar.

> [!NOTE]
> Bir profilin stereotiplerini düzenlemekte olduğunuz bir modele uygularsanız ve sonra modeli diğer kişilerle paylaşıyorsanız, aynı profili kendi bilgisayarlarına yüklemelidir. Aksi takdirde, kullandığınız stereotiplerin görmeyecektir.

 Profil genellikle daha büyük bir uzantının bir parçasıdır [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . Örneğin, bir modelin bazı parçalarını koda çeviren bir komut tanımlayabilirsiniz. Kullanıcıların çevirmek istedikleri paketlere uygulanması gereken bir profil tanımlayabilirsiniz. Yeni komutlarınızı profille birlikte tek bir uzantıya dağıtırsınız [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] .

 Ayrıca, bir profilin yerelleştirilmiş türevlerini de tanımlayabilirsiniz. Uzantınızı yükleyen kullanıcılar kendi kültürüne uygun olan değişkeni görebilir.

## <a name="how-to-define-a-profile"></a><a name="DefineProfile"></a> Profil tanımlama

#### <a name="to-define-a-uml-profile"></a>Bir UML profili tanımlamak için

1. Dosya adı uzantısına sahip yeni bir XML dosyası oluşturun `.profile` .

2. [Bir profilin yapısında](#Schema)açıklanan yönergelere göre stereotip tanımları ekleyin.

3. Profili bir Visual Studio uzantısına ( `.vsix` dosya) ekleyin. Profiliniz için yeni bir uzantı oluşturabilir ya da profili mevcut bir uzantıya ekleyebilirsiniz.

     [Bir Visual Studio uzantısına profil ekleme](#AddProfile)başlıklı sonraki bölüme bakın.

4. Uzantıyı bilgisayarınıza yükler.

    1. Dosya adı uzantısına sahip uzantı dosyasına çift tıklayın `.vsix` .

    2. Visual Studio’yu yeniden başlatın.

5. Profilin yüklü olduğunu doğrulayın.

    1. UML Explorer 'da modeli seçin.

    2. Özellikler penceresi **profiller** özelliğine tıklayın. Profiliniz menüde görünür. Profilin yanındaki onay işaretini ayarlayın.

    3. Profilinizin stereotipleri tanımladığı bir öğe seçin. Özellikler penceresi, **Stereotipler** özelliğine tıklayın. Stereotiplerinizin listede yer alacak. Onay işaretini stereotiplerin birine göre ayarlayın.

    4. Profiliniz bu stereotip için ek özellikler tanımlıyorsa, bunları görmek için stereotip özelliğini genişletin.

6. Uzantı dosyasını bilgisayarlarına yüklemek için diğer kullanıcılarına gönderin [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

## <a name="how-to-add-a-profile-to-a-visual-studio-extension"></a><a name="AddProfile"></a> Visual Studio uzantısına profil ekleme
 Bir profil yüklemek ve diğer kullanıcılara göndermenize izin vermek için, profili bir Visual Studio uzantısına eklemeniz gerekir. Daha fazla bilgi için bkz. [Visual Studio uzantılarını dağıtma](https://msdn.microsoft.com/library/dd393694(VS.100).aspx).

#### <a name="to-define-a-profile-in-a-new-visual-studio-extension"></a>Yeni bir Visual Studio uzantısında bir profil tanımlamak için

1. Visual Studio uzantı projesi oluşturun.

   > [!NOTE]
   > [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Bu yordamı kullanmak için yüklemiş olmanız gerekir.

   1. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

   2. **Yeni proje** iletişim kutusunda, **yüklü şablonlar**altında **Visual C#**' yi genişletin, **genişletilebilirlik**' e ve **VSIX projesi**' ne tıklayın. Proje adını ayarlayın ve **Tamam**' a tıklayın.

2. Profilinizi projeye ekleyin.

   - Çözüm Gezgini ' de projeye sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **var olan öğe**' ye tıklayın. İletişim kutusunda profil dosyanızı bulun.

3. Profil dosyasının, çıkış özelliğine **Kopyala** özelliğini ayarlayın.

   1. Çözüm Gezgini, profil dosyasına sağ tıklayın ve ardından **Özellikler**' e tıklayın.

   2. Özellikler penceresi, **Çıkış Dizinine Kopyala** özelliğini **her zaman Kopyala**olarak ayarlayın.

4. Çözüm Gezgini ' de, öğesini açın `source.extension.vsixmanifest` .

    Dosya uzantı bildirim düzenleyicisinde açılır.

5. **Varlıklar** sayfasında, profili açıklayan bir satır ekleyin:

   - **Yeni**' ye tıklayın. **Yeni varlık Ekle** iletişim kutusundaki alanları aşağıdaki gibi ayarlayın.

   - **Tür** olarak ayarla`Microsoft.VisualStudio.UmlProfile`

        Bu, açılan Seçimlerinizden biri değildir. Bu adı klavyeden girin.

   - **Dosya sisteminde dosya** ' ya tıklayın ve profil dosyanızın adını seçin, örneğin`MyProfile.profile`

6. Projeyi derleyin.

7. **Profilde hata ayıklamak Için**F5 'e basın.

    Visual Studio 'nun deneysel bir örneği açılır. Bu örnekte, bir modelleme projesi açın. UML Gezgini ' nde, modelin kök öğesini seçin ve Özellikler penceresi profilinizi seçin. Sonra modelin içindeki öğeleri seçin ve kendileri için tanımladığınız stereotipleri ayarlayın.

8. **Dağıtım için VSıX 'i ayıklamak için**

   1. Windows Gezgini 'nde, **. vsix** dosyasını bulmak için, **\ \Bin\debug** veya. **\bin\Release** klasörünü açın. Bu bir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] uzantı dosyasıdır. Bu, bilgisayarınıza yüklenebilir ve diğer Visual Studio kullanıcılarına gönderilebilir.

   2. Uzantıyı yüklemek için:

       1. Dosyaya çift tıklayın `.vsix` . Visual Studio Uzantı Yükleyicisi başlatılır.

       2. Çalıştıran tüm Visual Studio örneklerini yeniden başlatın.

   ' İ yüklemediyseniz, küçük uzantılar için aşağıdaki alternatif yordam kullanılabilir [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] .

#### <a name="to-define-a-profile-extension-without-using-visual-studio-sdk"></a>Visual Studio SDK kullanmadan bir profil uzantısı tanımlamak için

1. Aşağıdaki üç dosyayı içeren bir Windows dizini oluşturun:

    - *Yourprofile*`.profile`

    - `extension.vsixmanifest`

    - `[Content_Types].xml` -Bu adı köşeli ayraç ile burada gösterildiği gibi yazın

2. `[Content_Types].xml`Aşağıdaki metni içerecek şekilde düzenleyin. Her dosya adı uzantısı için bir giriş içerdiğine dikkat edin.

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
      <Default Extension="profile" ContentType="application/octet-stream" />
      <Default Extension="vsixmanifest" ContentType="text/xml" />
    </Types>
    ```

3. Var olan bir `extension.vsixmanifest` dosyayı kopyalayın ve BIR XML Düzenleyicisi ile düzenleyin. KIMLIĞI, adı ve Içerik düğümlerini değiştirin.

    - Bu dizinde bir örnek bulabilirsiniz `extension.vsixmanifest` :

         *sürücü* **: \Program Files\Microsoft Visual Studio [sürüm] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles**

    - Içerik düğümü şöyle olmalıdır:

        ```
        <Content>
          <CustomExtension Type="Microsoft.VisualStudio.UmlProfile"
          >YourProfile.Profile</CustomExtension>
        </Content>
        ```

4. Üç dosyayı daraltılmış bir dosyaya sıkıştırın.

     Windows Gezgini 'nde üç dosyayı seçin, sağ tıklayın, **Gönder**' in üzerine gelin ve ardından **Sıkıştırılmış (daraltılmış) klasör**' e tıklayın.

5. Daraltılmış dosyayı yeniden adlandırın ve dosya adı uzantısını `.zip` olarak değiştirin `.vsix` .

6. Profili, Visual Studio 'nun uygun sürümleriyle herhangi bir bilgisayara yüklemek için dosyasına çift tıklayın `.vsix` .

#### <a name="to-install-a-uml-profile-from-a-visual-studio-extension"></a>Bir Visual Studio uzantısı 'ndan bir UML profili yüklemek için

1. `.vsix`Windows Gezgini 'nde dosyaya çift tıklayın veya Visual Studio içinde açın.

2. Görüntülenen iletişim kutusunda, **yüklensin** ' e tıklayın.

3. Uzantıyı kaldırmak veya geçici olarak devre dışı bırakmak için, **Araçlar** menüsünden **Uzantılar ve güncelleştirmeler** ' i açın.

## <a name="how-to-define-localized-profiles"></a><a name="Localized"></a> Yerelleştirilmiş profilleri tanımlama
 Farklı kültürler ve diller için farklı profiller tanımlayabilir ve bunların tümünü aynı uzantıya paketleyebilirsiniz. Bir Kullanıcı uzantınızı yüklediğinde, kültürü için tanımladığınız profili görürler.

 Her zaman bir varsayılan profil sağlamanız gerekir. Kullanıcının kültürü için bir profil tanımlamadıysanız, varsayılan profili görürler.

#### <a name="to-define-a-localized-profile"></a>Yerelleştirilmiş bir profil tanımlamak için

1. Önceki bölümlerde[bir profil tanımlama](#DefineProfile) ve [Visual Studio uzantısına profil ekleme](#AddProfile)konularında açıklandığı şekilde bir profil oluşturun. Bu varsayılan profildir ve yerelleştirilmiş bir profil sağlamayan herhangi bir yüklemede kullanılacaktır.

2. Varsayılan profil dosyanız ile aynı dizine yeni bir dizin ekleyin.

    > [!NOTE]
    > Uzantıyı bir Visual Studio uzantısı projesi kullanarak oluşturuyorsanız, projeye yeni bir klasör eklemek için Çözüm Gezgini kullanın.

3. Yeni dizinin adını, Bulgarca veya Fransızca gibi yerelleştirilmiş kültürün ISO kısa kodu olarak değiştirin `bg` `fr` . Gibi belirli bir kültür değil, genellikle iki harf olmak üzere bağımsız bir kültür kodu kullanmanız gerekir `fr-CA` . Kültür kodları hakkında daha fazla bilgi için, kültür kodlarının tamamen bir listesini sağlayan [CultureInfo. Getkültürleri yöntemine](https://msdn.microsoft.com/library/system.globalization.cultureinfo.getcultures(VS.100).aspx)bakın.

4. Varsayılan profilinizin bir kopyasını yeni dizine ekleyin. Dosya adını değiştirmeyin.

     Örnek [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] bir uzantı klasörü, bir dosyaya oluşturulmadan veya sıkıştırılmadan önce, `.vsix` aşağıdaki klasörleri ve dosyaları içerir:

     `extension.vsixmanifest`

     `MyProfile.profile`

     `fr\MyProfile.profile`

     `de\MyProfile.profile`

    > [!NOTE]
    > `extension.vsixmanifest`Profillerin yerelleştirilmiş sürümlerine bir başvuruya eklememelisiniz. Kopyalanan profil dosyaları üst klasördeki profille aynı ada sahip olmalıdır.

5. Profilin yeni kopyasını düzenleyerek, Kullanıcı tarafından görünür olacak tüm parçalar hedef dile, örneğin `displayName` öznitelikler gibi.

6. İstediğiniz sayıda kültür için ek kültür klasörleri ve yerelleştirilmiş profiller oluşturabilirsiniz.

7. Uzantı projesini oluşturarak ya da önceki bölümlerde açıklandığı gibi tüm dosyaları sıkıştırarak Visual Studio uzantısı oluşturun.

## <a name="the-structure-of-a-profile"></a><a name="Schema"></a> Bir profilin yapısı

 Profil dosyalarını düzenlemenize yardımcı olması için `.xsd` dosyasını içine yükleyebilirsiniz:

 **%ProgramFiles%\Microsoft Visual Studio [sürüm] \Xml\Schemas**

 Bu bölüm örnek olarak C# profilini kullanır. Tüm profil tanımı şu şekilde görülebilir:

 *sürücü* **: \Program Files\Microsoft Visual Studio [Version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\umlprofiles\csharp.exe**

 Bu yolun ilk kısımları yüklemenizde farklılık gösterebilir.

 .NET profili hakkında daha fazla bilgi için bkz. [UML modelleri Için standart stereotipler](../modeling/standard-stereotypes-for-uml-models.md).

### <a name="main-sections-of-the-uml-profile-definition"></a>UML profil tanımının ana bölümleri
 Her profil aşağıdaki içeriği içerir:

```
<?xml version="1.0" encoding="utf-8"?>
<profile dslVersion="1.0.0.0"
       name="CSharpProfile" displayName="C# Profile"
       xmlns="http://schemas.microsoft.com/UML2.1.2/ProfileDefinition">
  <stereotypes>...</stereotypes>
  <metaclasses>...</metaclasses>
  <propertyTypes>...</propertyTypes>
</profile>
```

> [!NOTE]
> Çağrılan öznitelik `name` boşluk veya noktalama işareti içermemelidir. `displayName`Kullanıcı arabiriminde görünen özniteliği geçerli BIR XML dizesi olmalıdır.

 Her profil üç ana bölüm içerir. Ters sırada bunlar aşağıdaki gibidir:

- `<propertyTypes>` -Stereotipler bölümünde tanımlanan özellikler için kullanılan türlerin listesi.

- `<metaclasses>` -Bu profildeki stereotiplerin uygulandığı, IClass, IInterface, IOperation, IDependency gibi model öğe türlerinin listesi.

- `<stereotypes>` -stereotip tanımları. Her tanım, hedef model öğesine eklenen özelliklerin adlarını ve türlerini içerir.

#### <a name="property-types"></a>Özellik Türleri
 `<propertyTypes>`Bölümü bölümünde özellikler için kullanılan türlerin bir listesini bildirir `<stereotypes>` . İki tür özellik türü vardır: dış ve sabit listesi.

 Dış tür, standart bir .NET türünün tam nitelikli adını bildirir:

```
<externalType name="System.String" />
```

 Sabit listesi türü, sabit değerler kümesini tanımlar:

```
<enumerationType name="PackageVisibility">
  <enumerationLiterals>
    <enumerationLiteral name="internal" displayName="internal"  />
    <enumerationLiteral name="protectedinternal" displayName="protected internal" />
  </enumerationLiterals>
</enumerationType>
```

#### <a name="metaclasses"></a>Metaclasses
 `<metaclasses>`Bölüm, bu profildeki stereotiplerin tanımlanbileceği model öğesi türlerinin bir listesidir:

```
<metaclass
      name="Microsoft.VisualStudio.Uml.Classes.IClass" />
<metaclass
      name="Microsoft.VisualStudio.Uml.Classes.IInterface" />
<metaclass
      name="Microsoft.VisualStudio.Uml.Components.IComponent" />
```

 Meta sınıflar olarak kullanabileceğiniz model öğesi ve ilişki türlerinin tam listesi için bkz. [model öğe türleri](#Elements).

#### <a name="stereotype-definition"></a>Stereotip tanımı
 `<stereotypes>`Bölüm bir veya daha fazla stereotip tanımı içerir:

```
<stereotype name="CSharpClass" displayName="C# Class"> ...
```

 Her stereotip, uygulanabilecek bir veya daha fazla model öğesi ya da ilişki türlerini listeler. Tüm türetilmiş türlerini dahil etmek için temel türün adına izin verebilirsiniz. Örneğin, öğesini belirtirseniz, stereotip,, `Microsoft.VisualStudio.Uml.Classes.IType` `IClass` `IInterface` `IEnumeration` ve diğer birçok öğe türü için uygulanabilir.

```
<metaclasses>
  <metaclassMoniker name=
   "/CSharpProfile/Microsoft.VisualStudio.Uml.Classes.IClass" />
</metaclasses>
```

 `name`Özniteliği, `metaclassMoniker` bölümündeki bir öğenin bağlantıdır `<metaClasses>` .

> [!NOTE]
> Bilinen ad adı `/yourProfileName/` , `yourProfileName` `name` (Bu örnekte "CSharpProfile") profil özniteliğinde tanımlandığı, ile başlamalıdır. Bilinen ad, Metaclasses bölümündeki girdilerden birinin adıyla biter.

 Her stereotip, uygulandığı herhangi bir model öğesine eklediği sıfır veya daha fazla özelliği listeleyebilir. , `<propertyType>` Bölümünde tanımlanan türlerden birine bir bağlantı içerir `<propertyTypes>` . Bağlantı, bir veya öğesine başvurmak için bir `<externalTypeMoniker>` `<externalType>,` veya bir içermelidir `<enumerationTypeMoniker>` `<enumerationType>` . Yine, bağlantı profilinizin adıyla başlar.

```
  <properties>
    <property name="IsStatic"
            displayName="Is Static" defaultValue="false">
      <propertyType>
<externalTypeMoniker
               name="/CSharpProfile/System.Boolean" />
      </propertyType>
    </property>
    <property name="PackageVisibility"
              displayName="Package Visibility"
              defaultValue="internal">
      <propertyType>
        <enumerationTypeMoniker
              name="/CSharpProfile/PackageVisibility"/>
      </propertyType>
    </property>
  </properties>
</stereotype>
```

## <a name="model-element-types"></a><a name="Elements"></a> Model öğe türleri
 Stereotipleri tanımlayabilmeniz gereken türler kümesi [UML model öğe türlerinde](../modeling/uml-model-element-types.md)listelenmiştir.

## <a name="troubleshooting"></a>Sorun giderme
 Stereotiplerim UML modellerim görünmüyor.
Profilinizi bir paket veya modelde seçmeniz gerekir. Stereotipler daha sonra paket veya model içindeki öğelerde görüntülenir. Daha fazla bilgi için bkz. [UML model öğelerine stereotipler ekleme](../modeling/add-stereotypes-to-uml-model-elements.md).

 Bir UML modeli açtığımda şu hata görüntülenir: **VS1707: bir serileştirme hatası oluştuğundan aşağıdaki profiller yüklenemedi: MyProfile. Profile**
1. . Profile öğesinin temel XML sözdiziminin doğru olduğundan emin olun.

2. Her bir bilinen ad adının/profileName/nodeName. biçimde olduğundan emin olun ProfileName, kök profili düğümündeki ad özniteliğinin değeridir. Düğüme, bir Metaclass, externalType veya enumerationType ad özniteliğinin değeridir.

3. Sözdiziminin burada açıklandığı gibi ve _sürücüde_gösterildiği gibi olduğundan emin olun **: \Program Files\Microsoft Visual Studio [Version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles \\ **.

4. Hatalı uzantıyı kaldırın. **Araçlar** menüsünde **Uzantılar ve Güncelleştirmeler**’e tıklayın.

   - Uzantı görünmezse bir sonraki öğeye bakın.

5. VSıX dosyasını yeniden oluşturun ve yeniden yüklemek için Windows Gezgini 'nde açın. Yeniden başlatın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

   Uzantı, Uzantı Yöneticisi 'nde görünmez, ancak yeniden yüklemeye çalıştığınızda aşağıdaki ileti görüntülenir: **uzantı zaten tüm ilgili ürünlere yüklenmiş.**
   1. Uzantı dosyasını *LocalAppData*\microsoft\visualstudio \\ [Version] \ extensions\ alt klasöründen Kaldır

   - *LocalAppData*görmek Için, Windows Gezgini klasör seçeneklerinin Görünüm sekmesinde gizli dosyaları ve klasörleri göster ' i ayarlamanız gerekir.

   - *LocalAppData* genellikle C:\Users \\ *Kullanıcı adı*\appdata\local\ ' de

6. Yeniden başlatın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

## <a name="see-also"></a>Ayrıca Bkz.
 [UML model öğelerine stereotipler ekleme](../modeling/add-stereotypes-to-uml-model-elements.md) [modellerinizi PROFILLER ve](../modeling/customize-your-model-with-profiles-and-stereotypes.md) bir [UML modeli için standart stereotiplerle](../modeling/standard-stereotypes-for-uml-models.md) özelleştirme
 