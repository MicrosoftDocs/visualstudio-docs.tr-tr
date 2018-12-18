---
title: Özel tanımlama Modelleme araç kutusu öğesi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, customizing the toolbox
ms.assetid: a2463606-1100-40ac-97f3-5ba22ca47b7c
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: dcb562eb76e13b5dcb16532ed808b2447de0d6c8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778416"
---
# <a name="define-a-custom-modeling-toolbox-item"></a>Özel bir modelleme araç kutusu öğesi tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir öğe veya sık kullandığınız bir desene göre öğeler grubu oluşturmayı kolaylaştırmak için yeni araçları modelleme diyagramları Visual Studio araç kutusu ekleyebilirsiniz. Bu araç kutusu öğelerini, diğer Visual Studio kullanıcılarına dağıtabilirsiniz.  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Özel araç bir diyagramda bir veya daha fazla yeni öğeleri oluşturur. Örneğin, şunlar gibi öğeleri oluşturmak için özel bir araç yapabilirsiniz:  
  
-   .NET profili ve .NET stereotip ile bir sınıf için bir paket bağlı.  
  
-   Gözlemci deseni temsil etmek için bir ilişkilendirme tarafından bağlantılı sınıfları çifti.  
  
> [!NOTE]
>  Öğe araçlarını oluşturmak için bu yöntemi kullanabilirsiniz. Diğer bir deyişle, bir diyagram üzerine araç kutusundan sürükleyin araçları oluşturabilirsiniz. Bağlayıcı araçları oluşturamazsınız.  
  
##  <a name="DefineTool"></a> Özel araç modelleme tanımlama  
  
#### <a name="to-define-a-custom-modeling-tool"></a>Bir özel Modelleme araç tanımlamak için  
  
1.  Bir öğe veya öğe grubunu içeren bir UML diyagram oluşturun.  
  
    -   Bu öğeler, bunlar arasındaki ilişkileri olabilir ve bağlantı noktaları, öznitelikleri, işlemleri veya PIN'leri gibi paketinizle öğeleri olabilir.  
  
2.  Yeni aracı vermek istediğiniz adı kullanarak diyagramı kaydedin. Üzerinde **dosya** menüsünde, kullanmak **Kaydet... Olarak**.  
  
3.  Windows Explorer'ı kullanarak iki diyagram dosyalarının şu klasörü veya herhangi bir alt klasöre kopyalayın:  
  
     *YourDocuments* **\Visual Studio\Architecture Tools\Custom araç kutusu öğeleri**  
  
    -   Bu klasör, zaten yoksa, oluşturun. Her ikisi de oluşturmanız gerekebilir **Mimari Araçları** ve **özel araç kutusu öğeleri**.  
  
    -   Diyagram dosyalarının ikisini de biten "... bir ada sahip bir kopyalama **diyagram**"ile biten bir ad ve"... **diagram.layout**"  
  
    -   İstediğiniz sayıda özel araçlar yapabilirsiniz. Her aracı için bir diyagram kullanın.  
  
4.  (İsteğe bağlı) Oluşturma bir **.tbxinfo** dosya açıklandığı [özel araç özellikleri tanımlama](#tbxinfo), aynı dizine ekleyin. Bu araç kutusu simgesi, araç ipucu ve benzeri tanımlamanıza olanak sağlar.  
  
    -   Tek bir **.tbxinfo** dosya, çeşitli araçları tanımlamak için kullanılabilir. Alt klasörlerinde diyagram dosyaları başvurabilir.  
  
5.  Visual Studio'yu yeniden başlatın. Ek aracı uygun diyagram türü için araç kutusunda görünür.  
  
### <a name="what-the-custom-tool-will-replicate"></a>Özel araç çoğaltma  
 Kaynak diyagram özelliklerinin çoğunu çoğaltma işlemi bir özel aracı:  
  
- Adları. Araç kutusundan bir öğe oluşturulduğunda, aynı ad alanında aynı ada önlemek gerekirse adının sonuna bir sayı eklenir.  
  
- Renkler, boyutları ve şekiller  
  
- Stereotipler ve paket profilleri  
  
- Soyut gibi özellik değerleri  
  
- Bağlantılı iş öğeleri  
  
- Çeşitlilikler ve ilişkilerinin diğer özellikleri  
  
- Şekiller göreli konumlarını.  
  
  Aşağıdaki özellikler, bir özel aracı korunmaz:  
  
- Basit şekiller. Bazı tür diyagramlar çizebilirsiniz model öğelerine, ilgili olmayan şekiller şunlardır.  
  
- Bağlayıcı yönlendirme. Bağlayıcılar el ile yönlendirmek, aracınızın kullanıldığında yönlendirme korunmaz. Bağlantı noktaları gibi bazı iç içe geçmiş şekillere konumlarını sahiplerinin göre korunmaz.  
  
##  <a name="tbxinfo"></a> Özel Araçlar özelliklerini tanımlama  
 Araç kutusu bilgileri (**.tbxinfo**) dosyası bir araç kutusu adı, simge, araç ipucu, sekme belirtin ve Yardım anahtar sözcüğü bir veya daha fazla özel araçlar için izin verir. Gibi herhangi bir ad verin **MyTools.tbxinfo**.  
  
 Dosya genel biçimi aşağıdaki gibidir:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<customToolboxItems xmlns="http://schemas.microsoft.com/visualstudio/[version]/ArchitectureTools/CustomToolboxItems">  
  <customToolboxItem fileName="MyObserverTool.classdiagram">  
    <displayName>  
       <value>Observer Pattern</value>  
    </displayName>  
    <tabName>  
       <value>UML Class Diagram</value>  
    </tabName>  
    <image><bmp fileName="ObserverPatternIcon.bmp"/></image>  
    <f1Keyword>  
      <value>ObserverPatternHelp</value>  
    </f1Keyword>  
    <tooltip>  
       <value>Create a pair of classes</value>  
    </tooltip>  
  </customToolboxItem>  
</customToolboxItems>  
```  
  
 Her öğenin değerini olabilir:  
  
- Örnekte gösterildiği gibi `<bmp fileName="…"/>` araç kutusu simgesinin ve `<value>string</value>` diğer öğeler için.  
  
  \- veya -  
  
- `<resource fileName="Resources.dll"`  
  
   `baseName="Observer.resources" id="Observer.tabname" />`  
  
   Bu durumda, dize değerlerini kaynaklar olarak derlenmiştir derlenmiş bir bütünleştirilmiş kod sağlayın.  
  
  Ekleme bir `<customToolboxItem>` tanımlamak istediğiniz her bir araç kutusu öğesi için düğüm.  
  
  Düğümlerin **.tbxinfo** dosyası aşağıdaki gibidir. Her düğüm için bir varsayılan değer yoktur.  
  
|Düğüm adı|tanımlar|  
|---------------|-------------|  
|displayName|Araç kutusu öğesi adı.|  
|tabName|Öğenin görüntülenmesi gereken araç kutusu sekmesi. Bu tür bir diyagram normal sekmede adını veya ayrı bir ad belirtebilirsiniz.|  
|görüntü|Bit eşlem konumunu (**.bmp**) dosyasını yükseklik ve genişlik 16 ve 24 bit renk derinliği olması gerekir.|  
|f1Keyword|Yardım konusunun bulur anahtar sözcüğü.|  
|Araç İpucu|Bu araç için bir araç ipucu.|  
  
 Visual Studio bit eşlem dosyasında düzenleyebilir ve yüksekliğini ve genişliğini 16 Özellikler penceresinde ayarlayın.  
  
> [!NOTE]
>  Diyagram dosyaları kendi kullanmayı denedikten sonra .tbxinfo dosyası kullanmaya başlamak, araç hem eski hem de bir araç kutusu öğesi yeni sürümleri içerdiğini fark edebilirsiniz. Diyagram dosyasının adını .tbxinfo dosyasında girildiyse bu da meydana gelebilir. Bu meydana gelirse, araç kısayol menüsünden seçin **sıfırlama araç kutusu**. Özel araç kutusu öğeleri kaybolur. Visual Studio'yu yeniden başlatın ve doğru özel öğeleri görünür.  
  
##  <a name="Extension"></a> Araç kutusu öğeleri Visual Studio Uzantısı'nda dağıtım yapma  
 Diğer araç kutusu öğeleri dağıtabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bunları Visual Studio Uzantısı (VSIX) paketleme tarafından kullanıcılar. Komutlar, profilleri ve diğer uzantılarla aynı VSIX dosyasına paketleyebilirsiniz. Daha fazla bilgi için [Visual Studio uzantılarını dağıtma](http://go.microsoft.com/fwlink/?LinkId=160780).  
  
 Visual Studio uzantısı oluşturmak için her zamanki şekilde VSIX proje şablonu kullanmaktır. Bunu yapmak için yüklü olmalıdır [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
#### <a name="to-add-a-toolbox-item-to-a-visual-studio-extension"></a>Visual Studio uzantısı için bir araç kutusu öğesi eklemek için  
  
1.  [Oluşturma ve test bir veya daha fazla özel araçları](#DefineTool).  
  
2.  [.Tbxinfo dosyası oluşturma](#tbxinfo) araçları başvuran.  
  
3.  Varolan bir Visual Studio uzantı projesi açın.  
  
     \- veya -  
  
     Yeni bir Visual Studio uzantı projesi tanımlayın.  
  
    1.  Üzerinde **dosya** menüsünde seçin **yeni**, **proje**.  
  
    2.  İçinde **yeni proje** iletişim kutusunun **yüklü şablonlar**, seçin **Visual C#**, **genişletilebilirlik**, **VSIX Proje**.  
  
4.  Araç kutusu tanımlarınıza projeye ekleyin. Dahil **.tbxinfo** dosyası, diyagram dosyaları, bit eşlem dosyaları ve herhangi bir kaynak dosyasını ve VSIX içine dahil edildiğinden emin olun.  
  
    -   Çözüm Gezgini'nde VSIX projesinin kısayol menüsünden seçin **Ekle**, **var olan öğe**. İletişim kutusunda ayarlanan **tür nesneleri: tüm dosyalar**. Dosyaları bulun, tüm bunları seçin ve ardından **Ekle**.  
  
        > [!NOTE]
        >  Bu projede model Düzenleyicisi, diyagram dosyaları açamaz.  
  
5.  Yeni eklediğiniz tüm dosyaların aşağıdaki özellikleri ayarlayın. Tüm Çözüm Gezgini'nde seçerek aynı anda özelliklerini ayarlayabilirsiniz. Diğer dosyalar projesinde özelliklerini değiştirilmemesi dikkat edin.  
  
     **Çıkış Dizinine Kopyala** = **her zaman Kopyala**  
  
     **Derleme eylemi** = **içerik**  
  
     **VSIX'e Ekle** = **true**  
  
6.  Açık **source.extension.vsixmanifest**. Uzantı bildirim düzenleyicisinde açar.  
  
7.  Altında **meta verileri**, özel araçlar için bir açıklama ekleyin.  
  
     Altında **varlıklar**, seçin **yeni** ve alanları iletişim kutusunda aşağıdaki gibi ayarlayın:  
  
    -   **Tür** = **özel uzantı türü**  
  
    -   Tür = `Microsoft.VisualStudio.ArchitectureTools.CustomToolboxItems`  
  
        > [!NOTE]
        >  Bu açılır listedeki seçeneklerden birini değildir. Klavyeyi kullanarak girmek zorunda.  
  
    -   **Kaynak** = **FileSystem'daki**.  
  
    -   **Yol** =, **.tbxinfo** , örneğin dosya **MyTools.tbxinfo**  
  
8.  Projeyi oluşturun.  
  
9. **Uzantı çalıştığını doğrulamak için**, F5 tuşuna basın. Visual Studio'nun bir Deneysel örneğini başlatır.  
  
     Deneysel örneği oluşturun veya ilgili türün bir UML diyagram açın. Doğru öğeleri oluşturur ve yeni aracınızın araç kutusunda görüntülendiğini doğrulayın.  
  
10. **Dağıtım için bir VSIX dosya elde edilir:** klasörü Windows Gezgini'nde açın **.\bin\Debug** veya **.\bin\Release** bulunacak **.vsix** dosya. Bu bir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] uzantı dosyası. Bilgisayarınızda yüklü ve olması da diğer Visual Studio kullanıcılarına gönderilebilir.  
  
#### <a name="to-install-custom-tools-from-a-visual-studio-extension"></a>Visual Studio Uzantısı'ndan özel araçlarını yüklemek için  
  
1.  Açık `.vsix` Windows Gezgini veya Visual Studio'da dosya.  
  
2.  Seçin **yükleme** iletişim kutusunda görüntülenir.  
  
3.  Kaldırmak veya geçici olarak uzantıyı devre dışı bırakmak için açık **Uzantılar ve güncelleştirmeler** gelen **Araçları** menüsü.  
  
## <a name="localization"></a>Yerelleştirme  
 Başka bir bilgisayara yüklendiğinde, aracı adları ve araç ipuçları hedef bilgisayarın dilinde görüntüler bir uzantı yapabilirsiniz.  
  
#### <a name="to-provide-versions-of-the-tool-in-more-than-one-language"></a>Birden fazla dilde Aracı sürümleri sağlamak için  
  
1. Bir veya daha fazla özel araçlarını içeren bir Visual Studio uzantı projesi oluşturun.  
  
    İçinde **.tbxinfo** dosya, Aracı'nın tanımlamak için kaynak dosya yöntemini kullanmak `displayName`, araç kutusu `tabName`ve araç ipucu. Bu dizeler tanımlandığı kaynak dosyası oluşturma, bir birleştirme dosyasına derlemek ve tbxinfo dosyasından başvurduğu.  
  
2. Diğer dillerdeki dizeler içeren kaynak dosyalarını içeren ek derlemeler oluşturun.  
  
3. Her ek derleme dilin kültür kodu adı olan bir klasöre yerleştirin. Örneğin, bir derleme Fransızca sürümü adlı bir klasör yerleştirin **fr**.  
  
4. Bağımsız kültür kodu, genellikle iki harf, belirli bir kültür gibi kullanmalısınız `fr-CA`. Kültür kodları hakkında daha fazla bilgi için bkz. [CultureInfo.GetCultures yöntemi](http://go.microsoft.com/fwlink/?LinkId=160782), kültür kodlarının tam listesini sağlar.  
  
5. Visual Studio uzantısı oluşturun ve dağıtın.  
  
6. Uzantıyı başka bir bilgisayarda yüklü olduğunda, kullanıcının yerel kültürü için kaynak dosyası sürümünü otomatik olarak yüklenir. Kullanıcının kültürü için bir sürüm sağlamadınız, varsayılan kaynakları kullanılır.  
  
   Prototip diyagramın farklı sürümlerini yüklemek için bu yöntemi kullanamazsınız. Öğeleri ve bağlayıcılar adları her yüklemede aynı olacaktır.  
  
## <a name="other-toolbox-operations"></a>Diğer araç kutusu işlemler  
 Normalde, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], araçlarını yeniden adlandırma, farklı araç kutusu sekmeleri taşımak ve onları silerek araç kutusunu kişiselleştirme. Ancak, bu değişiklikleri bu konu başlığında açıklanan yordamları ile oluşturulmuş özel modelleme araçları için devam etmez. Yeniden başlattığınızda [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], özel araçlar ile tanımlanmış adları ve konumları araç kutusu görünecektir.  
  
 Gerçekleştirdiğiniz, ayrıca, özel araçlarınızı görünmez **sıfırlama araç kutusu** komutu. Bununla birlikte, yeniden başlattığınızda görünecektir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML modellerini ve diyagramları genişletme](../modeling/extend-uml-models-and-diagrams.md)   
 [UML genişletmek için profil tanımlama](../modeling/define-a-profile-to-extend-uml.md)   
 [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [UML modelleri için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md)



