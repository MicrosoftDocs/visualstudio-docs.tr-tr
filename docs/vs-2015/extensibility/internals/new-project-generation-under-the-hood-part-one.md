---
title: 'Yeni proje oluşturma: altyapı öğeleri, bir bölüm | Microsoft Docs'
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
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f1181cb3f84471727b181bb1ff91b69e8613b8a5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792936"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Yeni Proje Oluşturma: Altyapı Öğeleri, Bölüm Bir
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hiç kendi proje türünüzü oluşturmak hakkında düşündüğünüz? Yeni bir proje oluşturduğunuzda, gerçekte ne olacağını merak ediyorsunuz? Şimdi başlık altında bir göz atalım ve gerçekten neler olup bittiğini bakın.  
  
 Visual Studio sizin için koordine eden çeşitli görevler vardır:  
  
-   Tüm kullanılabilir proje türlerinin ağacını gösterir.  
  
-   Her proje türü için uygulama şablonları listesini görüntüler ve birini seçmenize olanak sağlar.  
  
-   Bu proje adı ve yolu gibi uygulama için proje bilgileri toplar.  
  
-   Bu, bu bilgileri açın proje fabrikası geçirir.  
  
-   Bu, geçerli çözümde proje öğeleri ve klasörleri oluşturur.  
  
## <a name="the-new-project-dialog-box"></a>Yeni Proje iletişim kutusu  
 Yeni bir proje için bir proje türü seçtiğinizde tüm başlar. Tıklayarak başlayalım **yeni proje** üzerinde **dosya** menüsü. **Yeni proje** iletişim kutusu görüntülenirse, şöyle bir şey görünümlü:  
  
 ![Yeni Proje iletişim kutusu](../../extensibility/internals/media/newproject.gif "NewProject")  
  
 Daha yakından göz atalım. **Proje türleri** ağacı oluşturmak için kullanabileceğiniz çeşitli proje türlerini listeler. Gibi bir proje türü seçtiğinizde **Visual C# Windows**, başlamanıza yardımcı olmak için uygulama şablonları listesini görürsünüz. **Visual Studio yüklenmiş şablonlar** Visual Studio tarafından yüklenir ve bilgisayarınızı herhangi bir kullanıcı için kullanılabilir. Yeni şablonu oluşturmak veya toplama eklenebilir **Şablonlarım** ve yalnızca sizin için kullanılabilir.  
  
 Bir şablon gibi seçtiğinizde **Windows uygulama**, iletişim kutusunda; Bu durumda, uygulama türünün açıklaması görünür **bir Windows Kullanıcı arabirimli bir uygulama oluşturmaya yönelik bir proje**.  
  
 Sayfanın alt kısmında **yeni proje** iletişim kutusunda, daha fazla bilgi toplamak çeşitli denetimler göreceksiniz. Gördüğünüz denetimlerin proje türüne bağlıdır, ancak bunlar genellikle bir proje içerir **adı** metin kutusuna bir **konumu** metin kutusu ve ilgili **Gözat** düğme ve bir **Çözüm adı** metin kutusu ve ilgili **çözüm için dizin oluştur** onay kutusu.  
  
## <a name="populating-the-new-project-dialog-box"></a>Yeni Proje iletişim kutusu doldurma  
 Burada mu **yeni proje** Al iletişim kutusu bilgilerini? İşte burada kullanım dışı bunlardan biri iki mekanizma vardır. **Yeni proje** iletişim kutusunda bir araya getirir ve her iki mekanizma alınan bilgileri görüntüler.  
  
 (Kullanım dışı) eski yöntem, sistem kayıt defteri girdilerini ve .vsdir dosyalarını kullanır. Bu mekanizma, Visual Studio açıldığı zaman çalışır. .Vstemplate dosyaları daha yeni bir yöntem kullanır. Visual Studio, örneğin, çalıştırarak başlatıldığında, bu mekanizma çalıştırır  
  
```  
devenv /setup  
```  
  
 veya  
  
```  
devenv /installvstemplates  
```  
  
### <a name="project-types"></a>Proje Türleri  
 Adını ve konumunu **proje türleri** düğümleri gibi kök **Visual C#** ve **diğer diller**, sistem kayıt defteri girdilerini tarafından belirlenir. Kuruluş alt düğümleri gibi **veritabanı** ve **akıllı cihaz**, karşılık gelen .vstemplate dosyaları içeren klasörleri hiyerarşisini yansıtır. İlk kök düğüm bakalım.  
  
#### <a name="project-type-root-nodes"></a>Proje türü kök düğümleri  
 Zaman [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] olan başlatıldı, sistem kayıt defteri anahtarı oluşturun ve kök düğümleri adlandırma HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs anahtarlarını erişir **proje türleri** ağaç. Bu bilgiler daha sonra kullanmak üzere önbelleğe alınır. Ara TemplateDirs\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1 anahtarı. Her girişin bir VSPackage GUID'dir. Alt anahtar adı (/ 1) göz ardı edilir, ancak bu varlığını gösteren bir **proje türleri** kök düğümü. Bir kök düğümü sırayla içinde görünümünü denetleyen birkaç alt olabilir **proje türleri** ağaç. Bunlardan bazıları bakalım.  
  
##### <a name="default"></a>(Varsayılan)  
 Kök düğümü adlarını yerelleştirilmiş bir dize kaynak kimliğidir. Dize kaynağını, uydu DLL'deki VSPackage GUID ile seçilen bulunur.  
  
 VSPackage GUID örnekte:  
  
 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}  
  
 ve kök düğümü (varsayılan değer) kaynak Kimliğini (/ 1) #2345 olduğu  
  
 Yakındaki paketleri anahtarında GUID arayın ve SatelliteDll alt inceleyin, dize kaynağı içeren derleme yolunu bulabilirsiniz:  
  
 \<Visual Studio yükleme yolu > \VC#\VCSPackages\1033\csprojui.dll  
  
 Bunu doğrulamak için dosya Gezgini'ni açın ve Visual Studio dizine csprojui.dll sürükleyin... Dize tablosu kaynak #2345 başlığı olduğunu gösteren **Visual C#**.  
  
##### <a name="sortpriority"></a>SortPriority  
 Bu kök düğümünde konumunu belirler **proje türleri** ağaç.  
  
 SortPriority REG_DWORD 0x00000014 (20)  
  
 Düşük öncelikli sayısını ağacında yüksek konumu.  
  
##### <a name="developeractivity"></a>DeveloperActivity  
 Bu alt anahtar yoksa kök düğümü konumunu Geliştirici Ayarları iletişim kutusu tarafından kontrol edilir. Örneğin,  
  
 VC # DeveloperActivity REG_SZ  
  
 Visual Studio için ayarlanmışsa Visual C# bir kök düğümü olacağını belirtir [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] geliştirme. Aksi takdirde, bir alt düğüm olacak **diğer diller**.  
  
##### <a name="folder"></a>Klasör  
 Bu alt anahtar yoksa kök düğümü belirtilen klasörün bir alt düğüm haline gelir. Olası klasörlerin listesini anahtarı altında görünür.  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders  
  
 Örneğin, veritabanı projeleri giriş PseudoFolders diğer proje türleri girişi ile eşleşen bir klasör anahtar vardır. Bu nedenle **proje türleri** ağacında **veritabanı projeleri** bir alt düğüm olacak **diğer proje türleri**.  
  
#### <a name="project-type-child-nodes-and-vstdir-files"></a>Proje türü alt düğümleri ve .vstdır dosyaları  
 Alt düğümler konumunu **proje türleri** ProjectTemplates klasörleri klasör hiyerarşisi ağacı izler. Makine şablonları için (**Visual Studio yüklenmiş şablonlar**), Visual Studio 14.0\Common7\IDE\ProjectTemplates\ \Program tipik konumdur ve kullanıcı şablonları (**Şablonlarım**), \My Documents\Visual Studio 14.0\Templates\ProjectTemplates tipik konumdur\\. Bu iki konum klasörü hiyerarşiden oluşturmak üzere birleştirilir **proje türleri** ağaç.  
  
 C# Geliştirici ayarları, Visual Studio için **proje türleri** ağacı aşağıdaki gibi görünür:  
  
 ![Proje türleri](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 İlgili ProjectTemplates klasörüne şöyle görünür:  
  
 ![Proje şablonları](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 Zaman **yeni proje** iletişim kutusu açılır ve [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ProjectTemplates klasörü erişir ve alt yapısında oluşturur **proje türleri** ağacıyla bazı değişiklikler:  
  
-   Kök düğümünde **proje türleri** ağaç uygulama şablonu tarafından belirlenir.  
  
-   Düğüm adı yerelleştirilmiş olmalıdır ve özel karakterler içerebilir.  
  
-   Sıralama düzenini değiştirilebilir.  
  
##### <a name="finding-the-root-node-for-a-project-type"></a>Bir proje türü için kök düğümü bulma  
 Visual Studio ProjectTemplates klasörleri erişir, tüm .zip dosyalarını açan ve herhangi bir .vstemplate dosyaları ayıklanır. .Vstemplate dosyası bir uygulama şablonunu açıklayan XML kullanır. Daha fazla bilgi için [yeni proje oluşturma: başlık altında ikinci Kısım](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 \<ProjectType > etiketi uygulama için proje türü belirler. Örneğin, bu etikete sahip bir EmptyProject.vstemplate dosyası \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip dosya içeriyor:  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 \<ProjectType > etiketi ve alt değil ProjectTemplates klasöründe, uygulama kök düğümünde belirler **proje türleri** ağaç. Örnekte, Windows CE uygulamalar altında görünür **Visual C#** kök düğümü ve Wındowsce VisualBasic klasörüne taşımak için olan olsa bile, Windows CE uygulamaları altında hala görüneceği  **Visual C#** kök düğümü.  
  
##### <a name="localizing-the-node-name"></a>Düğüm adı yerelleştirme  
 Visual Studio ProjectTemplates klasörleri erişir, bulduğu .vstdır dosyaları inceler. .Vstdır dosyası proje türünde görünümünü denetleyen bir XML dosyasıdır **yeni proje** iletişim kutusu. .Vstdır dosyasında kullanmak \<LocalizedName > Etiket adına **proje türleri** düğümü.  
  
 Örneğin, bu etiket \CSharp\Database\TemplateIndex.vstdir dosya içeriyor:  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 Bu, bu durumda, kök düğümü adlarını yerelleştirilmiş dize arar: uydu DLL ve kaynak Kimliğini belirler **veritabanı**. Yerelleştirilmiş adı gibi için klasör adları, mevcut olmayan özel karakterleri içerebilir **.NET**.  
  
 Hayır ise \<LocalizedName > etiketi, proje türü klasör kendisini adlı **SmartPhone2003**.  
  
##### <a name="finding-the-sort-order-for-a-project-type"></a>Bir proje türü için sıralama düzenini bulma  
 Proje türünü sıralama düzeninin belirlemek için .vstdır dosyalarını kullanın \<SortOrder > etiketi.  
  
 Örneğin, bu etiket \CSharp\Windows\Windows.vstdir dosya içeriyor:  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 \CSharp\Database\TemplateIndex.vstdir dosyanın daha büyük bir değer içeren bir etiket var:  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 Düşük sayısında \<SortOrder > etiketi, ağaç yüksek konumda böylece **Windows** düğümü görüntülenir, daha yüksek **veritabanı** düğümünde **proje türleri**  ağaç.  
  
 Hayır ise \<SortOrder > etiketi içeren tüm proje türleri aşağıdaki alfabetik sırada görünür bir proje türü için belirtilir \<SortOrder > belirtimleri.  
  
 Belgelerim'de .vstdır dosya olduğunu unutmayın (**Şablonlarım**) klasörleri. Kullanıcı uygulama proje türü adları yerelleştirilemez ve alfabetik sırada görünür.  
  
#### <a name="a-quick-review"></a>Hızlı bir inceleme  
 Şimdi değiştirmek **yeni proje** iletişim kutusu ve yeni bir kullanıcı proje şablonu oluşturun.  
  
1. MyProjectNode alt \Program Visual Studio 14.0\Common7\IDE\ProjectTemplates\CSharp klasöre ekleyin.  
  
2. Herhangi bir metin düzenleyicisi kullanarak MyProjectNode klasöründe bir MyProject.vstdir dosyası oluşturun.  
  
3. .Vstdır dosyanıza şu satırları ekleyin:  
  
   ```  
   <TemplateDir Version="1.0.0">  
       <SortOrder>6</SortOrder>  
   </TemplateDir>  
   ```  
  
4. .Vstdır dosyasını kaydedip kapatın.  
  
5. Herhangi bir metin düzenleyicisi kullanarak MyProjectNode klasöründe bir MyProject.vstemplate dosyası oluşturun.  
  
6. .Vstemplate dosyasını şu satırları ekleyin:  
  
   ```  
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
       <TemplateData>  
           <ProjectType>CSharp</ProjectType>  
       </TemplateData>  
   </VSTemplate>  
   ```  
  
7. The.vstemplate dosyasını kaydedin ve düzenleyiciyi kapatın.  
  
8. .Vstemplate dosyasını yeni bir sıkıştırılmış MyProjectNode\MyProject.zip klasörü gönderin.  
  
9. Visual Studio komut penceresinden şunu yazın:  
  
    ```  
    devenv /installvstemplates  
    ```  
  
   Visual Studio'yu açın.  
  
10. Açık **yeni proje** iletişim kutusu ve genişletin **Visual C#** proje düğümü.  
  
    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
    **MyProjectNode** Visual C# ' in Windows düğümü altında yalnızca bir alt düğüm olarak görünür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yeni Proje Oluşturma: Altyapı Öğeleri, Bölüm İki](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

