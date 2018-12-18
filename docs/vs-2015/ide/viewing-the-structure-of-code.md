---
title: Kod yapısını görüntüleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.documentoutline.window
- vs.objectbrowser
- vs.classview
- VS.CodeDefinitionView
- VS.CodeDefinitionWindow
- vs.componentpicker
- vs.callbrowser
helpviewer_keywords:
- document outline window.
- Visual Studio, object browser
- Visual Studio, code definition window
- call hierarchy
- Visual Studio, document outline window
- code definition window
- Visual Studio, class view
- Visual Studio, call hierarchy window
- class view
- object browser
ms.assetid: e6064f58-5ad9-4f05-8c3f-12e994b6583f
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d110056488b7555bc7bbccc5cbad3205d9de7405
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49901651"
---
# <a name="viewing-the-structure-of-code"></a>Kod Yapısını Görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nesneleri ve üyeleri Visual Studio projelerinde ve nesneleri ve üyeleri .NET Framework bileşenlerini, COM bileşenlerini dinamik bağlantı kitaplıklarını (DLL) inceleyebilir ve kitaplıkları (TLB) yazın.  
  
 Aşağıdaki bölümlerde bu belgenin farklı kod yapısı windows açıklanmaktadır.  
  
 [Sınıf Görünümü (Visual Basic, C#, C++)](#BKMK_ClassView)  
  
 [Çağrı hiyerarşisi (Visual Basic, C#, C++)](#BKMK_CallHierarchy)  
  
 [Nesne Tarayıcısı](#BKMK_ObjectBrowser)  
  
 [Kod tanımı penceresi (C#, C++)](#BKMK_CodeDefinition)  
  
 Ayrıca **Çözüm Gezgini** türleri ve üyeleri, projelerinizde göz atmak için simgeleri aramak, bir yöntemin çağrı hiyerarşisini görüntülemek, sembol başvurularını ve birden çok araç pencereleri arasında geçiş yapmak zorunda kalmadan daha fazlasını bulun daha önce listelenen.  
  
 Visual Studio Enterprise yüklüyse tüm çözümdeki yapısını kodunuzu ve bağımlılıklarını görselleştirin ve sizi ilgilendiren kod bölümlerini aşağı ayrıntıya kod haritaları'nı kullanabilirsiniz. Daha fazla bilgi için [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md).  
  
> [!NOTE]
>  Visual Studio sürümü ve kullandığınız ayarlar IDE içindeki özellikleri etkileyebilir. Bunlar, bu konuda açıklanan olanlardan farklı olabilir.  
  
##  <a name="BKMK_ClassView"></a> Sınıf Görünümü (Visual Basic, C#, C++)  
 **Sınıf Görünümü** parçası olarak gösterilen **Çözüm Gezgini** gibi ayrı bir pencerede iyi. **Sınıf görünümü** penceresi uygulamanın öğelerini görüntüler. Üst bölme ad alanlarını, türleri, arabirimleri, numaralandırmalar ve sınıflar ve alt bölmesinde üst bölmede seçilen türe ait üyelerini görüntüler. Bu pencere öğesini kullanarak, kaynak kodu üye tanımlarında taşıyabilirsiniz (veya **Nesne Tarayıcısı** öğe çözümünüzü dışında tanımlı ise).  
  
 Alt öğeleri görüntülemek için bir proje derlemek zorunda değilsiniz **sınıf görünümü**. Kod projenizde değiştirirken penceresi yenilenir.  
  
 Kod proje düğümünü ve seçerek projenize ekleyebilirsiniz **Ekle** açmak için düğmeyi **Yeni Öğe Ekle** iletişim kutusu. Kodu ayrı bir dosyada eklenir.  
  
 Projeniz için kaynak kodu denetimi, iade edildiğinde, her **sınıf görünümü** öğesi dosyanın kaynak kodu durumunu belirten bir simge görüntüler. Ortak kaynak kodu denetimi komutları gibi **kullanıma**, **iade**, ve **en son sürümü Al** öğesi için kısayol menüsünde de mevcuttur.  
  
### <a name="class-view-toolbar"></a>Sınıf Görünümü araç çubuğu  
 Sınıf Görünümü araç çubuğu, aşağıdaki komutları içerir.  
  
|||  
|-|-|  
|**Yeni klasör**|Sanal klasör veya sık kullanılan öğeleri düzenlemek alt klasör oluşturur. Etkin çözüm (.suo) dosyası kaydedilirler. Yeniden adlandırma ya da kodunuzda bir öğeyi sil sonra sanal bir klasörde bir hata düğümü olarak görünebilir. Bu sorunu düzeltmek için hata düğümü silin. Bir öğeyi yeniden adlandırdıysanız, bu proje hiyerarşisindeki klasörüne yeniden taşıyabilirsiniz.|  
|**Geri**|Daha önce seçilen öğe için gider.|  
|**İleriye doğru**|Seçili öğeye ileri gider.|  
|**Sınıf diyagramı görüntüle** (kod projeleri yalnızca yönetilen)|Bir ad alanı seçin veya yazın, kullanılabilir **sınıf görünümü**. Bir ad alanı seçili olduğunda, sınıf diyagramı içinde tüm türleri gösterir. Bir tür seçili olduğunda, sınıf diyagramına yalnızca bu türünü gösterir.|  
  
### <a name="class-view-settings"></a>Sınıf Görünümü ayarlar  
 **Sınıf görünümü ayarlar** araç çubuğunda, aşağıdaki ayarlara sahiptir.  
  
|||  
|-|-|  
|**Temel türleri Göster**|Temel türleri görüntülenir.|  
|**Türetilmiş türleri Göster**|Türetilmiş türler görüntülenir.|  
|**Gizli türleri ve üyeleri Göster**|Gizli türleri ve üyeleri (istemcileri tarafından kullanılmak üzere tasarlanmamıştır) açık gri metin görüntülenir.|  
|**Ortak üyeleri Göster**|Genel üye görüntüleniyor.|  
|**Korunan üyeleri Göster**|Korumalı üye görüntüleniyor.|  
|**Özel üyeleri Göster**|Özel üyeler görüntülenir.|  
|**Diğer üyeleri Göster**|Diğer türde üye görüntülenir, iç dahil olmak üzere (veya Visual Basic'te Friend) üyeler.|  
|**Devralınan üyeleri Göster**|Devralınan üye görüntüleniyor.|  
|**Uzantı yöntemleri Göster**|Genişletme yöntemleri görüntülenir.|  
  
### <a name="class-view-shortcut-menu"></a>Sınıf Görünümü kısayol menüsü  
 Kısayol menüsünde **sınıf görünümü** seçilen proje türünü bağlı olarak aşağıdaki komutları içerebilir.  
  
|||  
|-|-|  
|**Tanıma Git**|Kaynak kodu ya da öğenin açıklamasını bulur **Nesne Tarayıcısı**, öğeyi projede tanımlı değil.|  
|**Tanım göz atın**|Seçili öğeyi görüntüler **Nesne Tarayıcısı**.|  
|**Tüm başvuruları Bul**|Şu anda seçili nesne öğesi bulur ve sonuçları görüntüler bir **sonuçları Bul** penceresi.|  
|**Filtre türü** (kod yalnızca yönetilen)|Yalnızca seçilen tür veya ad alanı görüntüler. Seçerek filtreyi kaldırabilirsiniz **Temizle Bul** (X) düğmesini yanındaki **Bul** kutusu.|  
|**Kopyala**|Öğenin tam adını kopyalar.|  
|**Alfabetik olarak Sırala**|Türleri ve üyeleri alfabetik olarak ada göre listeler.|  
|**Üye türe göre sırala**|Türleri ve üyeleri türe göre sırayla unutmayın (sınıflar arabirimleri koyun, arabirimler, temsilciler koyun ve yöntemler, Özellikler önünde gibi) listeler.|  
|**Üye erişimine göre sırala**|Liste türleri ve üyeleri erişimlerine göre sırayla, genel veya özel gibi yazın.|  
|**Üye türüne göre grupla**|Türler ve üyeler gruplara nesne türüne göre sıralar.|  
|**Git için bildirimi** (yalnızca C++ kodu)|Türe veya üyeye bildirimi varsa kaynak kodunu görüntüler.|  
|**Tanıma Git**|Türün veya üyenin tanımı varsa kaynak kodunu görüntüler.|  
|**Başvuruya Git**|Türe veya üyeye başvuru varsa kaynak kodunu görüntüler.|  
|**Çağrı hiyerarşisini görüntüle**|Seçili yöntemi görüntüler **çağrı hiyerarşisi** penceresi.|  
  
##  <a name="BKMK_CallHierarchy"></a> Çağrı hiyerarşisi (Visual Basic, C#, C++)  
 **Çağrı hiyerarşisi** penceresi gösterir, burada belirtilen yöntem (veya özellik veya Oluşturucu) olarak adlandırılır ve söz konusu yönteminden çağrılan yöntemler listelenmiştir. Belirtilen kapsamda olan yöntemleri çağıran/çağrılan ilişkileri gösteren çağrı grafı birden fazla düzeyde görüntüleyebilirsiniz.  
  
 Görüntüleyebileceğiniz **çağrı hiyerarşisi** yöntem (veya özellik veya Oluşturucu) seçip ardından penceresi **sınıf hiyerarşisini görüntüle** kısayol menüsünde. Aşağıdaki resimde görünen benzemelidir.  
  
 ![Çağrı hiyerarşisi birden çok düğüm açık](../ide/media/multiplenodes.png "MultipleNodes")  
Çağrı hiyerarşisi penceresi  
  
 Araç çubuğunda yanıdaki açılan listeyi kullanarak, hiyerarşinin bir kapsam belirtebilirsiniz: çözüm, geçerli proje veya geçerli belge.  
  
 Ana bölmede yöntemi gelen ve giden çağrıları görüntüler ve **çağrı siteleri** bölmesi, seçilen çağrı konumunu görüntüler. Sanal veya soyut üyeler için bir **geçersiz kılmaları yöntem adı** düğümü görüntülenir. Arabirim üyeleri için bir **uygulayan yöntem adı** düğümü görüntülenir.  
  
 **Çağrı hiyerarşisi** penceresi yöntemi burada bir yöntem bir olay işleyicisi eklenir veya bir temsilciye atanmış basamak içeren grubu başvuruları bulamazsa. Bu başvurular bulmak için kullanın **tüm başvuruları Bul** komutu.  
  
 Kısayol menüsünde **çağrı hiyerarşisi** penceresi, aşağıdaki komutlar içerir.  
  
|||  
|-|-|  
|**Yeni kök olarak Ekle**|Seçili düğümü yeni bir kök düğümü ekler.|  
|**Kökü Kaldır**|Ağaç görünümü bölmesinde seçilen kök düğümü kaldırır.|  
|**Tanıma Git**|Bir yöntemin orijinal tanımına gider.|  
|**Tüm başvuruları Bul**|Projede seçilen yöntemi tüm başvurularını bulur.|  
|**Kopyala**|Seçili düğümü (ancak onun alt düğümleri) kopyalar.|  
|**Yenileme**|Bilgileri yeniler.|  
  
##  <a name="BKMK_ObjectBrowser"></a> Nesne Tarayıcısı  
 **Nesne Tarayıcısı** projelerinizde kod açıklamaları görüntüler.  
  
 Görüntülemek istediğiniz filtreleyebilirsiniz **Nesne Tarayıcısı**. Pencerenin en üstündeki açılan listeyi kullanarak, aşağıdaki seçenekleri arasından seçim yapabilirsiniz:  
  
- Herhangi bir .NET Framework  
  
- Silverlight  
  
- Etkin çözüm  
  
- Özel bir bileşenler kümesi  
  
  Özel bileşenler, yönetilen kod yürütülebilir dosyaları, Kütüphane derlemelerini, tür kitaplıkları ve .ocx dosya dahil edebilirsiniz. C++ özel bileşenler eklemek mümkün değildir. Özel ayarlar, Visual Studio kullanıcı uygulama dizininde, % APPDATA%\Roaming\Microsoft\VisualStudio\11.0\ObjBrowEX.dat kaydedilir.  
  
  Sol bölmesinde **Nesne Tarayıcısı** .NET Framework ve COM bileşenleri gibi fiziksel kapsayıcılar gösterir. İçerdikleri ad alanlarını görüntülemek için kapsayıcı düğümlerini genişletin ve ardından içerdikleri türleri görüntülenecek ad alanları genişletin. Üyeleri (örneğin, özellikleri ve yöntemleri), bir türünü seçtiğinizde, sağ bölmede listelenir. Alt sağ bölmesinde seçtiğiniz öğe hakkındaki ayrıntılı bilgileri görüntüler.  
  
  Kullanarak belirli bir öğe için arama yapabilirsiniz **arama** pencerenin üst kısmındaki kutusu. Aramalar büyük/küçük harfe duyarsızdır. Arama sonuçları, sol bölmede görüntülenir. Aramayı temizlemek için seçin **Aramayı Temizle** (X) düğmesini yanındaki **arama** kutusu.  
  
  **Nesne Tarayıcısı** yaptığınız seçimleri izini ve gidebilirsiniz seçimlerinizi arasında kullanarak **İleri** ve **geri** araç çubuğundaki düğmeler.  
  
  Kullanabileceğiniz **Nesne Tarayıcısı** (derleme, ad alanı, tür veya üye) bir öğe ve seçerek bir açık çözüme bir bütünleştirilmiş kod başvurusu eklemek için **Başvuru Ekle** araç çubuğunda.  
  
### <a name="object-browser-settings"></a>Nesne Tarayıcısı ayarları  
 Kullanarak **nesne tarayıcısı ayarları** düğme araç çubuğunda, aşağıdaki görünümlerden birini belirtebilirsiniz.  
  
|||  
|-|-|  
|**Görünüm ad alanları**|Sol bölmede, fiziksel kapsayıcılar yerine ad alanları görüntüler. Ad alanlarında birden çok fiziksel kapsayıcılarda depolanan birleştirilir.|  
|**Görünüm kapsayıcıları**|Fiziksel kapsayıcılar yerine ad alanları, sol bölmede görüntülenir. **Ad alanlarını görüntülemek** ve **görünümü kapsayıcıları** birbirini dışlayan ayarlarıdır.|  
|**Temel türleri Göster**|Temel türleri görüntüler.|  
|**Türetilmiş türleri Göster**|Türetilmiş türleri görüntüler.|  
|**Gizli türleri ve üyeleri Göster**|Görüntüler gizli türleri ve üyeleri (istemcileri tarafından kullanılmak üzere tasarlanmamıştır)'açık gri metin.|  
|**Ortak üyeleri Göster**|Genel üyeler görüntüler.|  
|**Korunan üyeleri Göster**|Korumalı üyeler görüntüler.|  
|**Özel üyeleri Göster**|Özel üyeler görüntüler.|  
|**Diğer üyeleri Göster**|Diğer iç üyelerini (veya Visual Basic'te Friend) türler üyelerini görüntüler.|  
|**Devralınan üyeleri Göster**|Devralınan üyeleri görüntüler.|  
|**Uzantı yöntemleri Göster**|Genişletme yöntemleri görüntüler.|  
  
### <a name="object-browser-shortcut-menu-commands"></a>Nesne tarayıcı kısayol menü komutları  
 Kısayol menüsünde **Nesne Tarayıcısı** öğe türüne bağlı olarak aşağıdaki komutları içerebilir seçili.  
  
|||  
|-|-|  
|**Tanım göz atın**|Seçili öğe için birincil düğüm gösterir.|  
|**Tüm başvuruları Bul**|Şu anda seçili nesne öğesi bulur ve sonuçları görüntüler bir **sonuçları Bul** penceresi.|  
|**Türe göre filtrele**|Yalnızca seçilen tür veya ad alanı görüntüler. Seçerek filtreyi kaldırabilirsiniz **Aramayı Temizle** düğmesi.|  
|**Kopyala**|Öğenin tam adını kopyalar.|  
|**Kaldır**|Özel bileşen kümesi kapsamı ise seçilen bileşen kapsamından kaldırır.|  
|**Alfabetik olarak Sırala**|Türleri ve üyeleri alfabetik olarak ada göre listeler.|  
|**Nesne türüne göre sırala**|Türleri ve üyeleri türe göre sırayla unutmayın (sınıflar arabirimleri koyun, arabirimler, temsilciler koyun ve yöntemler, Özellikler önünde gibi) listeler.|  
|**Nesne erişime göre sırala**|Liste türleri ve üyeleri erişimlerine göre sırayla, genel veya özel gibi yazın.|  
|**Nesne türüne göre grupla**|Türler ve üyeler gruplara nesne türüne göre sıralar.|  
|**Git için bildirimi** (yalnızca C++ projeleri)|Türe veya üyeye bildirimi varsa kaynak kodunu görüntüler.|  
|**Tanıma Git**|Türün veya üyenin tanımı varsa kaynak kodunu görüntüler.|  
|**Başvuruya Git**|Türe veya üyeye başvuru varsa kaynak kodunu görüntüler.|  
|**Çağrı hiyerarşisini görüntüle**|Seçili yöntemi görüntüler **çağrı hiyerarşisi** penceresi.|  
  
##  <a name="BKMK_CodeDefinition"></a> Kod tanımı penceresi (C#, C++)  
 **Kod tanımı** penceresinde etkin projedeki seçili tür veya üyenin tanımı gösterilir. Türe veya üyeye bir kod Görünümü penceresi veya Kod düzenleyicisinde seçilebilir.  
  
 Bu pencereyi salt okunur olsa da, yer imlerinde veya kesme noktaları ayarlayabilirsiniz. Görüntülenen tanımı değiştirmek için seçin **tanımını Düzenle** kısayol menüsünde. Bu kaynak dosyasını Kod düzenleyicisinde açar ve tanımı başladığı noktasını satıra taşır.  
  
### <a name="code-definition-shortcut-menu"></a>Kod tanımı kısayol menüsü  
 Kısayol menüsünde **kod tanımı** penceresi programlama diline bağlı olarak aşağıdaki komutları içerebilir.  
  
|||  
|-|-|  
|**Birim testleri oluşturma**|Seçilen öğe için birim testleri oluşturur.|  
|**Sıralı Diyagram Oluştur**|Bir yöntem seçildiğinde, sıralı diyagram oluşturur.|  
|**Özel erişimci oluştur**|Çözümde bir birim test varsa, test kodu erişmek için kullandığı bir yöntem oluşturur.|  
|**Tanıma Git**|Tanımı (veya tanımları, parçalı sınıflar) bulur ve bunları görüntüler bir **sonuçları Bul** penceresi.|  
|**Tüm başvuruları Bul**|Türe veya üyeye yapılan başvurular çözümde bulur.|  
|**Çağrı hiyerarşisini görüntüle**|Yönteminde görüntüler **çağrı hiyerarşisi** penceresi.|  
|**Arama testleri Göster**|Projede birim testleri varsa, seçili kodu çağıran testler gösterir.|  
|**Arama Testleri Çalıştır**|Projede birim testleri varsa, seçilen kod için testleri çalıştırır.|  
|**Kesme noktası**|Bir kesme noktası (veya izleme noktası) ekler.|  
|**İmlece kadar Çalıştır**|Programın hata ayıklama modunda İmleç konumuna çalıştırır.|  
|**Kopyala**|Seçili satır kopyalar.|  
|**Anahat Oluşturma**|Standart komutlar anahat oluşturma.|  
|**Tanımı Düzenle**|Ekleme noktasını kod penceresinde tanım taşır.|  
|**Kodlama Seç**|Açılır **kodlama** penceresi bir dosya için kodlama ayarlayabilirsiniz.|  
  
### <a name="document-outline-window"></a>Belge Anahattı penceresi  
 Kullanabileceğiniz **belge anahattı** veya HTML sayfaları için XAML sayfa tasarımcıyı veya bir Windows Form Tasarımcısı gibi tasarımcı görünümleri ile birlikte penceresi. Böylece form veya sayfadaki mantıksal yapısını görüntülemek ve derin katıştırılmış veya gizli denetimler Bu pencere öğeleri bir ağaç görünümünde görüntüler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sınıf Görünümü ve Nesne Tarayıcısı Simgeleri](../ide/class-view-and-object-browser-icons.md)



