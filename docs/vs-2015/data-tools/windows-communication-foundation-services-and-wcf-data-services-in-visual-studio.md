---
title: Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, WCF Data
- WCF services, binding to
- WCF services, asynchronous service methods
- service references [Visual Studio]
- WCF Data Services
- asynchronous calls
- service references [Visual Studio], type sharing
- endpoints [WCF]
- asynchronous service methods
- service references [Visual Studio] endpoints
- WCF services, type sharing
- Windows Communication Foundation, in Visual Studio
- services, WCF
- WCF service, Visual Studio
- data services, WCF
- services, in Visual Studio
- data binding [Visual Studio], WCF
- service endpoints [Visual Studio]
- service references [Visual Studio], asynchronous calls
- services, Windows Communication Foundation
- type sharing in WCF services
- WCF services, endpoints
- service method, called asynchronously[Visual Studio]
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3cabee0dce9120dcfcc6d31e6f1541eaca72b5ea
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051438"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Visual Studio, Windows Communication Foundation (WCF) ile çalışmaya yönelik araçlar sağlar ve [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], dağıtılmış uygulamalar oluşturmak için Microsoft teknolojileri. Bu konuda hizmetlerinden tanıtır bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] perspektif. Tüm belgeler için bkz. [WCF Veri Hizmetleri 4.5](http://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a).

## <a name="what-is-wcf"></a>WCF nedir?
 [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] güvenli, güvenilir, işlenen ve birlikte çalışabilen bir dağıtılmış uygulamalar oluşturmak için birleştirilmiş bir çerçevedir. ASMX Web Hizmetleri, .NET uzaktan iletişim, Enterprise Hizmetleri (DCOM) ve MSMQ gibi eski işlemler arası iletişimi teknolojilerini değiştirir. WCF bu teknolojilerden birleşik bir programlama modeli altında işlevselliğini bir araya getirir. Bu, dağıtılmış uygulamalar geliştirme deneyimi basitleştirir.

#### <a name="what-are-wcf-data-services"></a>WCF Veri Hizmetleri nelerdir
 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] Açık veri (OData) protokolü standart uygulamasıdır.  Tablolu verileri gibi standart HTTP fiillerini kullanarak veri alma, sonrası, YERLEŞTİRME veya silme gelmesini REST API'ler, bir dizi açığa WCF veri hizmetleri sağlar. Sunucu tarafında, WCF Veri Hizmetleri tarafından değiştirilen [ASP.NET Web API](http://www.asp.net/web-api) yeni OData hizmetlerini oluşturma. WCF Veri Hizmetleri İstemci Kitaplığı Visual Studio'dan bir .NET uygulamasında OData hizmetlerini kullanma için iyi bir seçim olmaya devam eder (**proje &#124; hizmet Başvurusu Ekle**). Daha fazla bilgi için [WCF Veri Hizmetleri 4.5](http://go.microsoft.com/fwlink/?LinkID=119952).

### <a name="wcf-programming-model"></a>WCF programlama modeli
 İki varlık arasındaki iletişimi WCF programlama modeline dayanır: bir WCF hizmeti ve bir WCF istemcisi. Programlama modeli içinde kapsüllenir <xref:System.ServiceModel> ad alanında [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

#### <a name="wcf-service"></a>WCF Hizmeti
 Bir WCF hizmeti, hizmet ve istemci arasındaki bir sözleşme tanımlayan bir arabirim dayanır. İle işaretlenmiş bir <xref:System.ServiceModel.ServiceContractAttribute> aşağıdaki kodda gösterildiği gibi öznitelik:

 [!code-csharp[WCFWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#6)]
 [!code-vb[WCFWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#6)]

 [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
 [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]

 İşlevleri veya yöntemleri ile işaretleyerek bir WCF hizmeti tarafından sunulan tanımladığınız bir <xref:System.ServiceModel.OperationContractAttribute> özniteliği. Ayrıca, bileşik bir türü ile işaretleyerek serileştirilmiş verilerini açığa çıkarabilir bir <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği. Bu, istemcisinde veri bağlama sağlar.

 Bir arabirim ve metotlarını tanımlandıktan sonra bunlar arabirimi uygulayan bir sınıf içinde kapsüllenir. Tek bir WCF hizmet sınıfı, birden çok hizmet sözleşmelerini uygulayabilirsiniz.

 Bir WCF hizmeti olarak tüketim üzerinden ne bilinen için sunulan bir *uç nokta*. Uç nokta hizmetiyle iletişim kurmak için tek yolu sağlar. diğer sınıflarla gibi bir doğrudan başvuru hizmetine erişilemiyor.

 Bir uç nokta, adres, bağlama ve bir sözleşme oluşur. Hizmet bulunduğu adresi tanımlar; Bu URL, bir FTP adresi veya ağ ya da yerel yolu olabilir. Bir bağlama hizmeti ile iletişim bir şekilde tanımlar. WCF bağlamaları, HTTP veya FTP, Windows kimlik doğrulaması veya kullanıcı adları ve parolalar gibi bir güvenlik mekanizması gibi bir protokol belirtmek için verimli bir model sağlar ve daha fazlasını. Bir sözleşme WCF hizmet sınıfı tarafından sunulan işlemlerini içerir.

 Birden fazla uç nokta için tek bir WCF hizmet sunulabilir. Bu, farklı şekilde aynı hizmetle iletişim kurmak farklı istemcilerin sağlar. Örneğin, bir bankacılık hizmeti bir uç nokta çalışanlar ve başka bir dış müşteriler için her bağlama, farklı bir adres kullanarak sağlar ve/veya sözleşme.

#### <a name="wcf-client"></a>WCF istemcisi
 Bir WCF istemcisi oluşan bir *proxy* bir WCF Hizmeti ile iletişim kurmak bir uygulama sağlar ve bir uç nokta eşleşen bir uç nokta için hizmet tanımlı. Proxy app.config dosyasında istemci tarafında oluşturulur ve hizmet tarafından kullanıma sunulan yöntemleri ve türleri hakkında bilgi içerir. Birden çok uç noktalarını kullanıma Hizmetleri için istemci kendi gereksinimlerini, örneğin, HTTP üzerinden iletişim kurmak ve Windows kimlik doğrulaması kullanmak için en uygun olanı seçebilirsiniz.

 Bir WCF istemcisi oluşturulduktan sonra diğer nesnelerde olduğu gibi kodunuzda hizmete başvuramaz. Örneğin, çağrılacak `GetData` yazma aşağıdakine benzer kod daha önce gösterilen yöntemi:

 [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
 [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]

## <a name="wcf-tools-in-visual-studio"></a>WCF Visual Studio Araçları
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] WCF hizmetleri ve WCF istemcileri hem oluşturmanıza yardımcı olacak araçlar sağlar. Araçlar gösteren bir kılavuz için bkz. [izlenecek yol: Windows Forms'ta basit bir WCF hizmeti oluşturma](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="creating-and-testing-wcf-services"></a>Oluşturma ve WCF hizmetleri test etme
 WCF kullanabileceğiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kendi hizmetinizi hızla oluşturmak için bir temel olarak şablonlar. Ardından, hata ayıklamak ve hizmeti test etmek için WCF hizmet otomatik konağı ve WCF Test İstemcisi kullanabilirsiniz. Bu araçlar birlikte hızlı ve kolay bir hata ayıklama ve test döngüsünü sağlamak ve erken bir aşamada bir barındırma modeli için işleme gereksinimini ortadan kaldırır.

#### <a name="wcf-templates"></a>WCF şablonları
 WCF [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] şablonları, hizmet geliştirme için bir temel sınıf yapısı sağlar. WCF çeşitli şablonlar kullanılabilir **Yeni Proje Ekle** iletişim kutusu. Bunlar, WCF hizmet kitaplığı projeleri, WCF Hizmeti Web siteleri ve WCF Hizmeti öğe şablonları içerir.

 Bir şablon seçin, bir hizmet sözleşmesi, hizmet uygulaması ve hizmet yapılandırması için dosyalar eklenir. Hizmet, basit bir "Merhaba Dünya" türünü oluşturma, tüm gerekli özniteliklere zaten eklenir ve kod yazmadan yoktu. Elbette, işlevleri ve gerçek dünya hizmetiniz için yöntemler sağlamak üzere kod eklemek istediğiniz ancak şablonların temel sağlamasıdır.

 WCF şablonları hakkında daha fazla bilgi için bkz: [WCF Visual Studio şablonları](http://msdn.microsoft.com/library/6a608575-3535-4190-89da-911e24c8374f).

#### <a name="wcf-service-host"></a>WCF hizmet konağı
 Başladığınızda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hata ayıklayıcı (F5 tuşuna basarak) WCF hizmeti için bir proje, WCF hizmet konağı Aracı hizmeti yerel olarak barındırmak için otomatik olarak başlatılır. WCF hizmet konağı bir WCF Hizmeti projesini Hizmetleri'nde numaralandırır, projenin yapılandırması yükler ve bulduğu her hizmet için bir ana bilgisayar örneği oluşturur.

 WCF hizmet konağı kullanarak ek kod yazmadan veya belirli bir ana bilgisayara geliştirme sırasında yürüten olmadan bir WCF Hizmeti sınayabilirsiniz.

 WCF hizmet konağı hakkında daha fazla bilgi için bkz: [WCF hizmet Konağı (WcfSvcHost.exe)](http://msdn.microsoft.com/library/8643a63d-a357-4c39-bd6c-cdfdf71e370e).

#### <a name="wcf-test-client"></a>WCF Test İstemcisi
 WCF Test İstemcisi aracı test parametreleri giriş, bir WCF hizmeti için girdi gönderme sağlar ve hizmet geri gönderir yanıtı görüntüleyin. Bu deneyimi ile WCF hizmet konağı birleştirdiğinizde test uygun bir hizmet sağlar. Aracı sürücüde yüklü Visual Studio 2015 için C: İşte \Common7\IDE klasöründe bulunabilir: **C:\Program Files (x86) \Microsoft Visual Studio 14.0\Common7\IDE\\**.

 Bir WCF Hizmeti projede hata ayıklamak için F5 tuşuna bastığınızda, WCF Test İstemcisi açılır ve yapılandırma dosyasında tanımlanan hizmet uç noktaları listesini görüntüler. Test parametreleri ve hizmeti başlatın ve sürekli olarak test edin ve hizmetinizi doğrulamak için bu işlemi yineleyin.

 WCF Test İstemcisi hakkında daha fazla bilgi için bkz: [WCF Test İstemcisi (WcfTestClient.exe)](http://msdn.microsoft.com/library/d4302855-677f-4640-aa90-c5d785d72fb7).

### <a name="accessing-wcf-services-in-visual-studio"></a>Visual Studio'da WCF hizmetlerine erişme
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] WCF istemcileri otomatik olarak bir ara sunucu ve aracılığıyla eklediğiniz Hizmetleri için uç nokta oluşturma, oluşturma görevini basitleştirir **hizmet Başvurusu Ekle** iletişim kutusu. Tüm gerekli yapılandırma bilgileri, app.config dosyasına eklenir. Çoğu zaman tüm yapmanız gereken olan örneği hizmet kullanmak için.

 **Hizmet Başvurusu Ekle** iletişim kutusu için bir hizmet adresini girin ya da çözümünüz içinde tanımlanan bir hizmet için aranacak sağlar. İletişim kutusu, hizmetleri ve bu hizmetlerin sunduğu işlemleri listesini döndürür. Ayrıca kod Hizmetleri'nde başvurur ad alanı tanımlamanıza olanak sağlar.

 **Yapılandırma hizmet başvuruları** iletişim kutusu, hizmet yapılandırmasını özelleştirmenizi sağlar. Hizmet adresini değiştirmek, erişim düzeyi, zaman uyumsuz davranış ve ileti anlaşması türleri belirtin ve tür yeniden yapılandırın.

## <a name="how-to-select-a-service-endpoint"></a>Nasıl yapılır: bir hizmet uç noktası seçin
 Bazı Windows Communication Foundation (WCF) Hizmetleri bir istemci hizmeti ile iletişim kurabilir birden çok uç noktalarını kullanıma sunar. Örneğin, bir hizmeti bir HTTP bağlaması ve kullanıcı adını kullanan bir uç nokta kullanıma sunabileceğinize / parola güvenlik ve FTP ve Windows kimlik doğrulaması kullanan ikinci bir uç nokta. İkinci bir intranet üzerinde kullanılabilir ise ilk uç hizmeti bir güvenlik duvarı dışından erişen uygulamalar tarafından kullanılıyor olabilir.

 Böyle bir durumda, belirttiğiniz `endpointConfigurationName` bir parametresi olarak bir hizmet başvurusu için oluşturucu.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-select-a-service-endpoint"></a>Hizmet uç noktası seçin

1.  Çözüm Gezgini'nde proje düğümüne sağ tıklayıp seçerek bir WCF hizmeti bir başvuru ekleyin **hizmet Başvurusu Ekle**

2.  Kod Düzenleyicisi'nde hizmet başvurusu için bir oluşturucu ekleyin:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    >  Değiştirin *ServiceReference* değiştirin ve hizmet başvurusu için ad alanı ile *Service1Client* hizmetin adı.

3.  Bir IntelliSense listesi için oluşturucu aşırı yüklemeleri ile görüntülenir. Seçin `endpointConfigurationName As String` aşırı yükleme.

4.  Aşırı yükleme yazın `=` *ConfigurationName*burada *ConfigurationName* kullanmak istediğiniz uç noktaya adıdır.

    > [!NOTE]
    >  Kullanılabilir uç noktalar adını bilmiyorsanız, app.config dosyasında bulabilirsiniz.

#### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Bir WCF hizmeti için kullanılabilir uç noktalar bulmak için

1.  İçinde **Çözüm Gezgini**, hizmet başvurusunu içeren proje için app.config dosyasına sağ tıklayın ve ardından **açık**. Dosya Kod düzenleyicisinde görüntülenir.

2.  Arama `<Client>` dosyasındaki etiketi.

3.  Altındaki arama `<Client>` etiketi ile başlayan etiket `<Endpoint>`.

     Hizmet başvurusu birden fazla uç nokta sağlıyorsa, olacaktır iki veya daha fazla `<Endpoint` etiketler.

4.  İçinde `<EndPoint>` bulacaksınız etiketi bir `name="` *SomeService* `"` parametresi (burada *SomeService* bir uç nokta adı temsil eder). Geçirilebilir uç nokta unvanıdır `endpointConfigurationName As String` bir hizmet başvurusu için bir oluşturucu aşırı yüklemesi.

## <a name="how-to-call-a-service-method-asynchronously"></a>Nasıl yapılır: bir hizmet yöntemini zaman uyumsuz olarak çağırma
 Windows Communication Foundation (WCF) hizmetlerini çoğu yöntemleri zaman uyumlu veya zaman uyumsuz olarak çağrılabilir. Zaman uyumsuz bir yöntemi çağırmak uygulamanızın yavaş bir bağlantı üzerinden çalıştığında yöntemi Aranan çalışmaya devam olanak tanır.

 Bir hizmet başvurusu için bir proje eklendiğinde varsayılan olarak, zaman uyumlu yöntemleri çağırmak için yapılandırılır. Bir ayarı değiştirerek zaman uyumsuz yöntemleri çağırma davranışını değiştirebilirsiniz **hizmet başvurusu yapılandırma** iletişim kutusu.

> [!NOTE]
>  Bu seçenek, bir hizmet başına temelinde ayarlanır. Zaman uyumsuz olarak bir hizmet için bir yöntem çağrılırsa, tüm yöntemlerin zaman uyumsuz olarak çağrılmalıdır.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-call-a-service-method-asynchronously"></a>Bir hizmet yöntemini zaman uyumsuz olarak çağırma

1.  İçinde **Çözüm Gezgini**, hizmet başvurusunu seçin.

2.  Üzerinde **proje** menüsünü tıklatın **hizmet başvurusu Yapılandır**.

3.  İçinde **hizmet başvurusu yapılandırma** iletişim kutusunda **zaman uyumsuz işlemler oluşturma** onay kutusu.

## <a name="how-to-bind-data-returned-by-a-service"></a>Nasıl yapılır: bir hizmet tarafından döndürülen veri bağlama
 Yalnızca bir denetim için herhangi bir veri kaynağını bağlayabilirsiniz gibi bir denetim için bir Windows Communication Foundation (WCF) hizmeti tarafından döndürülen veriler bağlayabilirsiniz. Hizmet veri döndüren bileşik türler içeriyorsa bir WCF hizmeti bir başvuru eklediğinizde, otomatik olarak eklenen **veri kaynakları** penceresi.

#### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Bir WCF hizmeti tarafından döndürülen tek bir veri alanı denetim Bağlanılacak

1.  Üzerinde **veri** menüsünü tıklatın **veri kaynaklarını Göster**. **Veri kaynakları** penceresi görünür.

2.  İçinde **veri kaynakları** penceresinde, hizmet başvurusu düğümünü genişletin. Hizmet tarafından döndürülen herhangi bir bileşik türler görüntülenir.

3.  Bir tür için bir düğümünü genişletin. Bu tür için veri alanları görüntülenir.

4.  Bir alan seçin ve veri türü için uygun olan denetimler listesini görüntülemek için açılan oka tıklayın.

5.  Bağlamak istediğiniz denetim türünü tıklayın.

6.  Alanı form üzerine sürükleyin. Denetimin form ile birlikte eklenir bir <xref:System.Windows.Forms.BindingSource> bileşeni ve bir <xref:System.Windows.Forms.BindingNavigator> bileşeni.

7.  6 herhangi diğer alanları ancak 4 arasındaki adımları yineleyin bağlamak istediğiniz.

#### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Bir WCF hizmeti tarafından döndürülen bileşik türü bir denetim Bağlanılacak

1.  Üzerinde **veri** menüsünde **veri kaynaklarını Göster**. **Veri kaynakları** penceresi görünür.

2.  İçinde **veri kaynakları** penceresinde, hizmet başvurusu düğümünü genişletin. Hizmet tarafından döndürülen herhangi bir bileşik türler görüntülenir.

3.  Bir tür için bir düğüm seçin ve kullanılabilir seçeneklerin bir listesini görüntülemek için açılan oka tıklayın.

4.  Tıklayın **DataGridView** veri kılavuzunda görüntülemek için veya **ayrıntıları** bireysel denetimlerinde verileri görüntülemek için.

5.  Düğümü form üzerine sürükleyin. Denetimleri form ile birlikte eklenir bir <xref:System.Windows.Forms.BindingSource> bileşeni ve bir <xref:System.Windows.Forms.BindingNavigator> bileşeni.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Nasıl yapılır: Varolan türleri yeniden kullan bir hizmetini yapılandırma
 Bir hizmet başvurusu için bir proje eklendiğinde, hizmette tanımlanan herhangi bir türü yerel projede oluşturulur. Bir hizmet kullanırken çoğu durumda bu yinelenen tür ortak oluşturur [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] türü veya türleri bir paylaşılan kitaplıkta zaman tanımlanır.

 Bu sorunu önlemek için bütünleştirilmiş kodlardaki türleri varsayılan olarak paylaşılır. Tür için bir veya daha fazla derlemeleri paylaşımı devre dışı bırakmak isterseniz, bu nedenle, bunu yapabilirsiniz **yapılandırma hizmet başvuruları** iletişim kutusu.

#### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Tek bir bütünleştirilmiş kod paylaşımı türü devre dışı bırakmak için

1.  İçinde **Çözüm Gezgini**, hizmet başvurusunu seçin.

2.  Üzerinde **proje** menüsünü tıklatın **hizmet başvurusu Yapılandır**.

3.  İçinde **yapılandırma hizmet başvuruları** iletişim kutusunda **belirtilen bütünleştirilmiş kodlardaki türleri yeniden**.

4.  Tür paylaşımını etkinleştirmek istediğiniz her derleme için onay kutusunu seçin. Bir derleme için paylaşım türü devre dışı bırakmak için onay kutusunu temizleyin.

#### <a name="to-disable-type-sharing-in-all-assemblies"></a>Tüm derlemelerde paylaşım türü devre dışı bırakmak için

1.  İçinde **Çözüm Gezgini**, hizmet başvurusunu seçin.

2.  Üzerinde **proje** menüsünü tıklatın **hizmet başvurusu Yapılandır**.

3.  İçinde **yapılandırma hizmet başvuruları** iletişim kutusu, NET **bütünleştirilmiş kodlardaki türleri yeniden** onay kutusu.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[İzlenecek yol: Windows Forms içinde basit bir WCF Hizmeti oluşturma](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|Oluşturma ve WCF hizmetleri kullanarak adım adım bir gösterim sağlar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[İzlenecek Yol: WPF ve Entity Framework ile WCF Veri Hizmeti Oluşturma](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|Oluşturma ve kullanma konusunda adım adım bir gösterim sağlar [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] içinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[WCF Geliştirme Araçlarını Kullanma](http://msdn.microsoft.com/library/054adb87-c244-4d5a-83d1-0b2b44bd454b)|WCF hizmetlerinde oluşturup anlatılmaktadır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Nasıl yapılır: ekleme, güncelleştirme veya hizmet başvurusunu Kaldır](http://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)|Ekleme, güncelleştirme veya WCF hizmetleri projeden açıklar.|
|[Nasıl Yapılır: WCF Veri Hizmeti Başvurusunu Güncelleme veya Kaldırma](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|Nasıl başvurulacağını ve anlatılmaktadır [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] içinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Hizmet Başvurularında Sorun Giderme](../data-tools/troubleshooting-service-references.md)|Hizmet başvuruları ve bunların nasıl ile ortaya çıkabilecek bazı yaygın hatalar gösterir.|
|[WCF Hizmetlerinde Hata Ayıklama](../debugger/debugging-wcf-services.md)|Genel hata ayıklama sorunları ve WCF hizmetlerinde hata ayıklama sırasında karşılaşabileceğiniz teknikleri açıklar.|
|[Windows Communication Foundation kimlik doğrulama hizmeti genel bakış](http://msdn.microsoft.com/library/6e121a28-89e8-4974-88a8-70aaa6a7d52b)|WCF Web sitesi için bir rol hizmeti sağlamak için nasıl kullanılacağını açıklar.|
|[İzlenecek Yol: N Katmanlı Bir Veri Uygulaması Oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|Türü belirtilmiş veri kümesi oluşturma ve birden çok projelere TableAdapter ve veri kümesi kodunu ayırmak için adım adım yönergeler sağlar.|
|[Hizmet Başvurusu Yapılandır İletişim Kutusu](../data-tools/configure-service-reference-dialog-box.md)|Kullanıcı arabirimi öğelerini açıklar **hizmet başvurusu yapılandırma** iletişim kutusu.|

## <a name="reference"></a>Başvuru
 <xref:System.ServiceModel>

 <xref:System.Data.Services>

## <a name="see-also"></a>Ayrıca Bkz.
 [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
