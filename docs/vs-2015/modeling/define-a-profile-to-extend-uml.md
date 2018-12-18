---
title: UML genişletmek için profil tanımlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiles, UML
- stereotypes, UML
- UML, profiles and stereotypes
- UML - extending, defining profiles
- UML, customizing
- UML, profiles
ms.assetid: 776589cb-f89d-48d5-aafa-04a4c074b0d6
caps.latest.revision: 44
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 37c4560b767828be0ec43419ff92ec5b6f9863ea
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730337"
---
# <a name="define-a-profile-to-extend-uml"></a>UML’yi genişletmek için profil tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tanımlayabileceğiniz bir *UML profili* belirli amaçlar için standart model öğelerini özelleştirmek için. Bir profili bir veya daha fazla tanımlar *UML stereotipini*. Stereotip belirli bir tür nesneyi temsil eden bir türü işaretlemek için kullanılabilir. Stereotip ayrıca öğenin özellikler listesini genişletebilirsiniz.  
  
 Birkaç profil Visual Studio'nun desteklenen sürümleri yüklenir. Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport). Bu profiller ve stereotiplerin nasıl uygulandığı hakkında daha fazla bilgi için bkz: [modelinizi profiller ve stereotipler aracılığıyla özelleştirme](../modeling/customize-your-model-with-profiles-and-stereotypes.md).  
  
 Uyum ve kendi iş alanınız veya Mimariniz için UML genişletmek amacıyla kendi profilinizi tanımlayabilirsiniz. Örneğin:  
  
- Sık sık Web siteleri tanımlıyorsanız, sınıf diyagramlardaki sınıflara uygulanabilecek «WebSayfası» stereotipi sağlayan kendi profilinizi tanımlayabilirsiniz. Ardından, bir Web sitesi planlamak için sınıf diyagramlarını kullanabilirsiniz. Her «Websayfası» sınıfının sayfa içeriği, stili ve benzerleri için ek özelliklere sahip olması gerekir.  
  
- Bankacılık yazılımı geliştiriyorsanız, «Hesap» stereotipi sağlayan bir profil tanımlayabilirsiniz. Ardından, hesabın farklı türlerini tanımlamak ve onlar arasındaki ilişkileri göstermek için sınıf diyagramlarını kullanabilirsiniz.  
  
  Kendi profillerinizi ekibinize dağıtabilirsiniz. Her ekip üyesi profilinizi yükleyebilir. Bu, bunları düzenlemek ve stereotiplerini kullanan modelleri oluşturmak sağlar.  
  
> [!NOTE]
>  Bir profil düzenleme ve model diğer kişilerle paylaşın, bir modelde stereotipleri uygularsanız, bunlar aynı profili kendi bilgisayarlarına yüklemeniz gerekir. Aksi halde, kullandığınız stereotipleri görme olanakları olmayacaktır.  
  
 Bir profil genellikle daha büyük bir parçası olan [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] uzantısı. Örneğin, bazı bölümlerini koda bir model çeviren komut tanımlayabilirsiniz. Kullanıcıların çevirmek istedikleri paketlere uygulamaları gereken bir profil tanımlayabilirsiniz. Yeni komutunuz ile birlikte profilinizi tek bir dağıtmanız gerekir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] uzantısı.  
  
 Bir profilin yerelleştirilmiş türevlerini de tanımlayabilirsiniz. Uzantınızı yükleyen kullanıcılar kendi kültürlerine uygun değişkeni görebilirler.  
  
##  <a name="DefineProfile"></a> Bir profil nasıl tanımlanır  
  
#### <a name="to-define-a-uml-profile"></a>Bir UML profili tanımlamak için  
  
1.  Dosya adı uzantısı ile yeni bir XML dosyası oluşturma `.profile`.  
  
2.  Nda açıklanan yönergelere göre stereotip tanımlarını ekleyin [profilin yapısı](#Schema).  
  
3.  Visual Studio Uzantısına Profil ekleyin (`.vsix` dosyası). Profiliniz için yeni bir uzantı oluşturabilir veya profili varolan uzantıya ekleyin.  
  
     Sonraki bölüme bakın [Visual Studio Uzantısına Profil ekleme](#AddProfile).  
  
4.  Uzantıyı bilgisayarınıza yükleyin.  
  
    1.  Bir dosya adı uzantısına sahip uzantı dosyasına çift `.vsix`.  
  
    2.  Visual Studio'yu yeniden başlatın.  
  
5.  Profilin yüklendiğini doğrulayın.  
  
    1.  UML Explorer'da modeli seçin.  
  
    2.  Özellikler penceresinde tıklayın **profilleri** özelliği. Profiliniz menüde görünecektir. Profilin yanındaki onay işaretini ayarlayın.  
  
    3.  Kendisi için profilinizi stereotipleri tanımladığı bir öğe seçin. Özellikler penceresinde tıklayın **stereotipler** özelliği. Stereotipleriniz listede görüntülenir. Stereotiplerden bir tanesi karşı onay işaretini ayarlayın.  
  
    4.  Profiliniz bu stereotip için ek özellikler tanımlarsa onları görmek için stereotip özelliğini genişletin.  
  
6.  Uzantı dosyası diğer kullanıcılara göndermenize [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kendi bilgisayarlarına yüklemek için.  
  
##  <a name="AddProfile"></a> Bir Visual Studio Uzantısına Profil ekleme  
 Bir profili yüklemek ve diğer kullanıcılara göndermenize olanak tanımak için bir Visual Studio Uzantısına Profil eklemeniz gerekir. Daha fazla bilgi için [Visual Studio uzantılarını dağıtma](http://go.microsoft.com/fwlink/?LinkId=160780).  
  
#### <a name="to-define-a-profile-in-a-new-visual-studio-extension"></a>Yeni bir Visual Studio Uzantısında bir profil tanımlamak için  
  
1. Visual Studio uzantı projesi oluşturun.  
  
   > [!NOTE]
   >  Yüklemiş olmanız gerekir [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] için bu yordamı kullanın.  
  
   1.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.  
  
   2.  İçinde **yeni proje** iletişim kutusunda, **yüklü şablonlar**, genişletin **Visual C#**, tıklayın **genişletilebilirlik**ve ardından tıklayın **VSIX projesi**. Proje adını ayarlayın ve tıklayın **Tamam**.  
  
2. Profilinizi projeye ekleyin.  
  
   -   Çözüm Gezgini'nde projeye sağ tıklayın, fareyle **Ekle**ve ardından **var olan öğe**. İletişim kutusunda profil dosyanızı bulun.  
  
3. Profil dosyanızın ayarlamak **çıktıya Kopyala** özelliği.  
  
   1.  Çözüm Gezgini profil dosyasına sağ tıklayın ve ardından **özellikleri**.  
  
   2.  Özellikler penceresinde ayarlayın **çıkış dizinine Kopyala** özelliğini **her zaman Kopyala**.  
  
4. Çözüm Gezgini'nde açın `source.extension.vsixmanifest`.  
  
    Dosya, uzantı bildirim düzenleyicisinde açılır.  
  
5. Üzerinde **varlıklar** sayfasında, profili açıklayan bir satır ekleyin:  
  
   -   **Yeni**'yi tıklatın. Alanlar kümesinde **yeni varlık Ekle** aşağıdaki gibi iletişim.  
  
   -   Ayarlama **türü** için `Microsoft.VisualStudio.UmlProfile`  
  
        Bu açılan seçeneklerden biri değil. Klavyeden bu adı girin.  
  
   -   Tıklayın **FileSystem'daki** ve örneğin profil dosyanızın adını seçin `MyProfile.profile`  
  
6. Projeyi oluşturun.  
  
7. **Hata ayıklama, profil için**, F5 tuşuna basın.  
  
    Visual Studio deneysel örneği açılır. Bu örnekte, bir modelleme projesi açın. UML Gezgini'nde, modelin ve Özellikler penceresinde kök öğe seçin, profilinizi seçin. Ardından model içinde öğeleri seçin ve onlar için tanımladığınız stereotipleri ayarlayın.  
  
8. **VSIX'i dağıtım için ayıklamak için**  
  
   1.  Windows Gezgini'nde klasörü açın **.\bin\Debug** veya **.\bin\Release** bulunacak **.vsix** dosya. Bu bir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] uzantı dosyası. Bilgisayarınızda yüklü ve diğer Visual Studio kullanıcılarına gönderilebilir.  
  
   2.  Uzantıyı yüklemek için:  
  
       1.  Çift `.vsix` dosya. Visual Studio Uzantı Yükleyicisi başlayacaktır.  
  
       2.  Visual Studio'nun çalışan örneklerini yeniden başlatın.  
  
   Yüklememişseniz aşağıdaki alternatif yordam küçük uzantılar için kullanılabilir [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
#### <a name="to-define-a-profile-extension-without-using-visual-studio-sdk"></a>Visual Studio SDK kullanmadan bir profil uzantısı tanımlamak için  
  
1.  Aşağıdaki üç dosyayı içeren Windows dizini oluşturun:  
  
    -   *YourProfile* `.profile`  
  
    -   `extension.vsixmanifest`  
  
    -   `[Content_Types].xml` -Bu adı köşeli ayraç ile burada gösterildiği gibi yazın  
  
2.  Düzen `[Content_Types].xml` aşağıdaki metini kapsamak için. Her dosya adı uzantısı için bir girdi içerdiğine dikkat edin.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
      <Default Extension="profile" ContentType="application/octet-stream" />  
      <Default Extension="vsixmanifest" ContentType="text/xml" />  
    </Types>  
    ```  
  
3.  Mevcut bir kopyalama `extension.vsixmanifest` ve bir XML Düzenleyicisi ile düzenleyin. Kimliği, adı ve içerik düğümlerini değiştirin.  
  
    -   Bir örnek bulabilirsiniz `extension.vsixmanifest` bu dizinde:  
  
         *Sürücü* **: Visual Studio [sürüm] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles \Program**  
  
    -   İçerik düğümü şunun gibi olmalıdır:  
  
        ```  
        <Content>  
          <CustomExtension Type="Microsoft.VisualStudio.UmlProfile"  
          >YourProfile.Profile</CustomExtension>  
        </Content>  
        ```  
  
4.  Üç dosyayı sıkıştırılmış dosya içine sıkıştırın.  
  
     Windows Gezgini'nde üç dosyayı seçin, sağ tıklayın, fareyle **göndermek için**ve ardından **sıkıştırılmış (daraltılmış) klasör**.  
  
5.  Daraltılmış dosyayı yeniden adlandırın ve kendi dosya adı uzantısını değiştirmek `.zip` için `.vsix`.  
  
6.  Visual Studio'nun uygun sürümleri ile herhangi bir bilgisayarda, profili yüklemek için çift tıklayın `.vsix` dosya.  
  
#### <a name="to-install-a-uml-profile-from-a-visual-studio-extension"></a>Visual Studio Uzantısı'ndan bir UML profili yüklemek için  
  
1.  Çift `.vsix` Windows Gezgini'nde dosya ya da Visual Studio'da açın.  
  
2.  Tıklayın **yükleme** iletişim kutusunda görüntülenir.  
  
3.  Kaldırmak veya geçici olarak uzantıyı devre dışı bırakmak için açık **Uzantılar ve güncelleştirmeler** gelen **Araçları** menüsü.  
  
##  <a name="Localized"></a> Yerelleştirilmiş profiller nasıl tanımlanır  
 Farklı kültürler ve diller için farklı profiller tanımlayabilir ve tümünü aynı uzantı içinde bunları paket. Bir kullanıcı sizin uzantınızı yüklediği zaman onların kültürü için tanımladığınız profili görürler.  
  
 Her zaman varsayılan bir profil sağlamalısınız. Kullanıcının kültürü için bir profil tanımlamadıysanız, onlar varsayılan profili göreceklerdir.  
  
#### <a name="to-define-a-localized-profile"></a>Yerelleştirilmiş bir profili tanımlamak için  
  
1.  Önceki bölümlerde açıklandığı gibi bir profil oluşturun[bir profil nasıl tanımlanır](#DefineProfile) ve [Visual Studio Uzantısına Profil ekleme](#AddProfile). Bu durum, varsayılan profildir ve yerelleştirilmiş profil sağlamaz herhangi bir yüklemede kullanılan.  
  
2.  Varsayılan profil dosyası ile aynı dizinde yeni bir dizin ekleyin.  
  
    > [!NOTE]
    >  Visual Studio uzantı projesi kullanarak uzantı oluşturuyorsanız, projeye yeni bir klasör eklemek için Çözüm Gezgini'ni kullanın.  
  
3.  Yeni dizinin adını ISO kısa koduna yerelleştirilmiş kültür için gibi değiştirmek `bg` Bulgarca için veya `fr` Fransızca için. Bağımsız kültür kodu, genellikle iki harf, belirli bir kültür gibi kullanmalısınız `fr-CA`. Kültür kodları hakkında daha fazla bilgi için bkz. [CultureInfo.GetCultures yöntemi](http://go.microsoft.com/fwlink/?LinkId=160782), kültür kodlarının tam listesini sağlar.  
  
4.  Varsayılan profilinizin kopyasını yeni dizine ekleyin. Dosya adını değiştirmeyin.  
  
     Bir örnek [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] oluşturulmadan veya sıkıştırılmadan önce uzantı klasörü, bir `.vsix` dosyasında, aşağıdaki klasörleri ve dosyaları içerir:  
  
     `extension.vsixmanifest`  
  
     `MyProfile.profile`  
  
     `fr\MyProfile.profile`  
  
     `de\MyProfile.profile`  
  
    > [!NOTE]
    >  İçine eklememelisiniz `extension.vsixmanifest` Profillerin yerelleştirilmiş sürümlerine başvuru. Kopyalanmış profil dosyaları ana klasördeki profil adıyla aynı olmalıdır.  
  
5.  Gibi kullanıcıya görünür olacak tüm parçaları hedef dile çevirerek profilin yeni kopyasını düzenleyin `displayName` öznitelikleri.  
  
6.  Ek kültür klasörleri ve istediğiniz kadar çok kültür için yerelleştirilmiş profiller oluşturabilirsiniz.  
  
7.  Uzantı Projesini oluşturarak veya önceki bölümlerde açıklandığı gibi tüm dosyaları sıkıştırarak Visual Studio uzantısı oluşturun.  
  
##  <a name="Schema"></a> Bir profilin yapısı  
 UML profilleri için XSD dosyası aşağıdaki örnekte bulunabilir: [ayar stereotipleri ve profilleri XSD](http://go.microsoft.com/fwlink/?LinkID=213811). Profil dosyalarını düzenlemenize yardımcı olmak için yükleme `.xsd` dosyası:  
  
 **%ProgramFiles%\Microsoft visual Studio [sürüm] \Xml\Schemas**  
  
 Bu bölümde, C# profili örnek olarak kullanılmıştır. Tam profil tanımı şurada görülebilir:  
  
 *Sürücü* **: Visual Studio [sürüm] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\CSharp.profile \Program**  
  
 Bu yolun ilk bölümleri yüklemenizde farklılık gösterebilir.  
  
 .NET profili hakkında daha fazla bilgi için bkz. [UML modelleri için standart stereotipler](../modeling/standard-stereotypes-for-uml-models.md).  
  
### <a name="main-sections-of-the-uml-profile-definition"></a>UML Profil tanımının ana bölümleri  
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
>  Adlandırılan öznitelik `name` boşluklar veya noktalama işareti içermemelidir. Öznitelik `displayName`, kullanıcı arabiriminde görünen geçerli XML dizesi olmalıdır.  
  
 Her profil üç ana bölüm içerir. Ters sırada aşağıdakileri kullanabilirsiniz:  
  
-   `<propertyTypes>` -Stereotipler bölümünde tanımlanmış özellikler için kullanılan türlerin listesi.  
  
-   `<metaclasses>` -Bu profildeki stereotiplerin uygulandığı, örneğin, IClass, IInterface, IOperation, IDependency model öğe türlerinin listesi.  
  
-   `<stereotypes>` -stereotip tanımları. Her tanım hedef model öğesine eklenen özelliklerin türleri ve adlarını içerir.  
  
#### <a name="property-types"></a>Özellik Türleri  
 `<propertyTypes>` Bölümünde özellikler için kullanılan türlerin listesini bildirir `<stereotypes>` bölümü. İki çeşit özellik türü vardır: dış ve numaralandırma.  
  
 Dış tür standart .NET türünün tam nitelikli adını bildirir:  
  
```  
<externalType name="System.String" />  
```  
  
 Bir numaralandırma türü değişmez değerler kümesini tanımlar:  
  
```  
<enumerationType name="PackageVisibility">  
  <enumerationLiterals>  
    <enumerationLiteral name="internal" displayName="internal"  />  
    <enumerationLiteral name="protectedinternal" displayName="protected internal" />  
  </enumerationLiterals>  
</enumerationType>  
```  
  
#### <a name="metaclasses"></a>Metaclasses  
 `<metaclasses>` Bölümü, bu profildeki stereotiplerin tanımlanabildiği model öğe türleri listesidir:  
  
```  
<metaclass   
      name="Microsoft.VisualStudio.Uml.Classes.IClass" />  
<metaclass  
      name="Microsoft.VisualStudio.Uml.Classes.IInterface" />  
<metaclass  
      name="Microsoft.VisualStudio.Uml.Components.IComponent" />  
```  
  
 Metaclasses olarak kullanılabilen model öğe ve ilişki türlerinin tam listesi için bkz. [Model öğe türleri](#Elements).  
  
#### <a name="stereotype-definition"></a>Stereotip tanımı  
 `<stereotypes>` Bölümü bir veya daha çok stereotip tanımları içerir:  
  
```  
<stereotype name="CSharpClass" displayName="C# Class"> ...  
```  
  
 Her stereotip için uygulanabilir bir veya daha fazla model öğe veya ilişki türlerini listeler. Tüm türetilmiş türlerini dahil etmek için bir temel türün adını verebilirsiniz. Örneğin, belirtirseniz `Microsoft.VisualStudio.Uml.Classes.IType`, stereotip uygulanabilecek `IClass`, `IInterface`, `IEnumeration`ve öğenin birçok diğer türüne.  
  
```  
<metaclasses>  
  <metaclassMoniker name=  
   "/CSharpProfile/Microsoft.VisualStudio.Uml.Classes.IClass" />  
</metaclasses>  
```  
  
 `name` Özniteliği `metaclassMoniker` içindeki bir öğeye bir bağlantıdır `<metaClasses>` bölümü.  
  
> [!NOTE]
>  Takma ad ile başlamalıdır `/yourProfileName/`burada `yourProfileName` tanımlanan `name` özniteliği ' % s'profil (Bu örnekte "CSharpProfile"). Bilinen ad, metaclasses bölümündeki girdilerin birinin adı ile sona erer.  
  
 Her stereotip için uygulandığı herhangi bir model öğeye eklediği sıfır veya daha çok özelliği listeleyebilir. `<propertyType>` Tanımlanan türlerden biri için bir bağlantı içeren `<propertyTypes>` bölümü. Bağlantı aşağıdakilerden biri olması gereken bir `<externalTypeMoniker>` başvurmak için bir `<externalType>,` veya `<enumerationTypeMoniker>` başvurmak için bir `<enumerationType>`. Tekrar, bağlantı profilinizin adı ile başlar.  
  
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
  
##  <a name="Elements"></a> Model öğe türleri  
 Stereotipler için tanımlayabileceğiniz türler kümesi listelenir [UML model öğe türleri](../modeling/uml-model-element-types.md).  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Stereotiplerim my UML modellerimde görünmüyor.  
 Profilinizi bir paket veya model seçmek zorunda. Stereotipler sonra model veya paketin içinde öğelerin üzerinde görünür. Daha fazla bilgi için [Ekle stereotipler için UML model öğelerini](../modeling/add-stereotypes-to-uml-model-elements.md).  
  
 UML modelini açtığımda aşağıdaki hata görünür: **VS1707: seri hale getirme hata oluştuğu için aşağıdaki profilleri yüklenemiyor: MyProfile.profile**  
 1.  Profili, temel XML sözdiziminin doğru olduğundan emin olun.  
  
2. Her Takma adın form/ProfileName/nodename içinde olduğundan emin olun. ProfileName kök profil düğümündeki ad özniteliğinin değeridir. NodeName metaclass, externalType veya enumerationType ad özniteliğinin değeridir.  
  
3. Burada açıklandığı ve gösterildiği şekilde bir söz dizimi olduğundan emin olun _sürücü_**: \Program Visual Studio [sürüm] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\\** .  
  
4. Hatalı uzantıyı kaldırın. Üzerinde **Araçları** menüsünü tıklatın **Uzantılar ve güncelleştirmeler**.  
  
   -   Uzantı görünmüyorsa sonraki öğeye bakın.  
  
5. VSIX dosyasını yeniden oluşturun ve tekrar yüklemek için Windows Gezgini'nde açın. Yeniden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
   Uzantı, Uzantı Yöneticisi'nde görünmez, ancak yeniden yüklemeye çalıştığınızda, aşağıdaki ileti görünür: **uzantı zaten uygun tüm ürünler için yüklü.**  
   1.  Uzantı dosyasını kaldırın, bir alt *LocalAppData*\Microsoft\VisualStudio\\[sürüm] \Extensions\  
  
   -   Görmek için *LocalAppData*, Windows Gezgini Klasör Seçenekleri'nin Görünüm sekmesinde gizli dosyaları göster ayarlamanız gerekir.  
  
   -   *LocalAppData* genellikle C:\Users içinde olduğu\\*kullanıcıadı*\AppData\Local\  
  
6. Yeniden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Model öğelerine stereotipler ekleme](../modeling/add-stereotypes-to-uml-model-elements.md)   
 [Modelinizi profiller ve stereotipler aracılığıyla özelleştirme](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [UML modelleri için standart stereotipler](../modeling/standard-stereotypes-for-uml-models.md)   
 [Örnek: Renkli UML öğeleri Sterotipe göre](http://go.microsoft.com/fwlink/?LinkID=213841)   
 [Örnek: Ayar Sterotipleri, XSD profili](http://go.microsoft.com/fwlink/?LinkID=213811)



