---
title: ClickOnce uygulamalarında yerel ve uzak veri erişimi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- data access, ClickOnce applications
ms.assetid: be5cbe12-6cb6-49c9-aa59-a1624e1eef3d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b6f25bb2920f8f50afbd8bfb820e7c852e160865
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49943056"
---
# <a name="access-local-and-remote-data-in-clickonce-applications"></a>ClickOnce uygulamalarında yerel ve uzak veri erişimi
Çoğu uygulama veri üretir veya tüketir. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Okuma ve yerel olarak ve uzaktan veri yazma için çeşitli seçenekler sunar.  
  
## <a name="local-data"></a>Yerel veriler  
 İle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], aşağıdaki yöntemlerden birini kullanarak yerel olarak veri depolamak ve yükleyin:  
  
- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Veri dizini  
  
- Yalıtılmış Depolama  
  
- Diğer yerel dosyaları  
  
### <a name="clickonce-data-directory"></a>ClickOnce veri dizini  
 Her [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yerel bir bilgisayarda yüklü uygulama kullanıcının belgeler ve ayarlar klasöründe depolanan bir veri dizinine sahip. Dahil herhangi bir dosyayı bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama ve işaretli bir "veri" dosyası, bir uygulama yüklendiğinde bu dizine kopyalanır. Veri dosyaları en sık kullanılan bir dosya türünde olabilir metin, XML ve Microsoft Access .mdb dosyaları gibi veritabanı dosyaları.  
  
 Veri dizini uygulama açıkça depolar ve tutar veriler, yönetilen uygulama verileri için tasarlanmıştır. Tüm statik uygulama bildiriminde "veri" olarak işaretlenen değil (nondependency) dosyalar yerine uygulama dizininde bulunur. Burada uygulamanın yürütülebilir dosyasına katıştırılıp dizin olur (*.exe*) dosyaları ve derlemeleri bulunur.  
  
> [!NOTE]
>  Olduğunda bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulaması kaldırıldığında, kendi veri dizini de kaldırılır. Hiçbir zaman son-kullanıcıya yönetilen belgeler gibi verilerini depolamak için veri dizini kullanın.  
  
#### <a name="mark-data-files-in-a-clickonce-distribution"></a>ClickOnce dağıtımında işareti veri dosyaları  
 Mevcut bir dosyayı veri dizini içine koymak için var olan dosyayı bir veri dosyası olarak işaretlemelisiniz, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanın uygulama bildirim dosyası. Daha fazla bilgi için [nasıl yapılır: ClickOnce uygulamasına bir veri dosyası dahil](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
#### <a name="read-from-and-write-to-the-data-directory"></a>Okuma ve yazma için veri dizini  
 Veri dizini okuma gerektirir, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama isteği okuma izni; benzer şekilde, dizine yazma izni gerektirir. Tam güven ile çalışacak şekilde yapılandırılmışsa, uygulamanızın otomatik olarak bu izne sahip. İzin yükseltilmesi ya da güvenilir uygulama dağıtımı'nı kullanarak uygulamanız için yükseltme yaptığınıza izinler hakkında daha fazla bilgi için bkz. [güvenli ClickOnce uygulamaları](../deployment/securing-clickonce-applications.md).  
  
> [!NOTE]
>  Kuruluşunuz güvenilen uygulama dağıtımı kullanmaz ve izin yükseltme devre dışı bırakılmış ise, izinleri sunduğundan başarısız olur.  
  
 Uygulamanızın bu izinlere sahip olduktan sonra veri dizini içindeki sınıflarda yöntem çağrıları kullanarak erişebildiğinizi <xref:System.IO>. Bir Windows Forms içinde veri dizini yolunu elde edebilirsiniz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kullanarak uygulama <xref:System.Deployment.Application.ApplicationDeployment.DataDirectory%2A> tanımlanan özellik <xref:System.Deployment.Application.ApplicationDeployment.CurrentDeployment%2A> özelliği <xref:System.Deployment.Application.ApplicationDeployment>. Verilerinize erişmek için en uygun ve önerilen yöntem budur. Aşağıdaki kod örneğinde adlı bir metin dosyası için bunun nasıl yapılacağını gösterir *alan ve csv.txt olarak* dağıtımınızdaki bir veri dosyası dahil.  
  
 [!code-csharp[ClickOnce.OpenDataFile#1](../deployment/codesnippet/CSharp/accessing-local-and-remote-data-in-clickonce-applications_1.cs)]
 [!code-vb[ClickOnce.OpenDataFile#1](../deployment/codesnippet/VisualBasic/accessing-local-and-remote-data-in-clickonce-applications_1.vb)]  
  
 Veri dosyaları olarak dağıtımınızdaki dosyalardan işaretleme daha fazla bilgi için bkz: [nasıl yapılır: ClickOnce uygulamasına bir veri dosyası dahil](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
 İlgili değişkenleri kullanarak veri dizini yolunu de edinebilirsiniz <xref:System.Windows.Forms.Application> gibi sınıf <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A>.  
  
 Diğer dosya türlerini yönetmek için ek izinler gerektirebilir. Örneğin, bir Access veritabanının kullanmak istiyorsanız (*.mdb*) dosyası, uygulamanızı gerekir assert tam güven ilgili kullanmak için \<xref:System.Data > sınıfları.  
  
#### <a name="data-directory-and-application-versions"></a>Veri dizini ve uygulama sürümleri  
 Bir uygulamanın her sürümü diğer sürümlerden yalıtılmış kendi veri dizini vardır. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] böylece uygulamanın çalışma zamanında yeni veri dosyalarını oluşturmak için bir konum ister tüm veri dosyalarını dağıtımdaki bağımsız olarak bu dizin oluşturur. Bir uygulamanın yeni bir sürümü yüklü olduğunda [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tüm dosyaları önceki sürümün Veri Dizininden yeni sürümün veri dizinine kopyalar; oluşturan veya orijinal Dağıtımdaki uygulama.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir veri dosyası, farklı karma değeri uygulamanın yeni sürümü eski bir sürümü varsa dosyanın eski bir sürümünü daha yeni bir sunucu sürümüyle yerini alır. Ayrıca, yeni oluşturulan uygulama'nın önceki bir sürümüne sahip bir dosya aynı ada yeni sürümün dağıtımdaki bir dosya olarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] eski sürümün dosya yeni dosyanın üzerine yazar. Her iki durumda da, eski dosyaları içinde veri dizini adlı bir alt eklenecek `.pre`, böylece uygulama geçiş amacıyla eski verileri erişmeye devam edebilirsiniz.  
  
 Daha ayrıntılı veri geçişini gerekiyorsa, kullanabileceğiniz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım için yeni veri dizini eski veriler dizininden özel geçiş yapmak API. Mevcut bir yüklemeyi kullanarak test gerekecektir <xref:System.Deployment.Application.ApplicationDeployment.IsFirstRun%2A>, güncelleştirme kullanarak indirin <xref:System.Deployment.Application.ApplicationDeployment.Update%2A> veya <xref:System.Deployment.Application.ApplicationDeployment.UpdateAsync%2A>, ve herhangi bir özel veri geçişi iş güncelleştirme sonrası kendi tamamlandı.  
  
### <a name="isolated-storage"></a>Yalıtılmış Depolama  
 Yalıtılmış Depolama oluşturmak ve basit bir API kullanarak dosyalara erişmek için bir API sağlar. Depolanan dosyaların konumunu gerçek hem geliştiriciler hem de kullanıcı gizlenir.  
  
 Yalıtılmış Depolama works tüm sürümlerinde [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Yalıtılmış Depolama ayrıca kısmen güvenilir uygulamaların ek izin verilmesine gerek kalmadan çalışır. Uygulamanızı kısmi güvende çalıştırmanız gerekir, ancak uygulamaya özgü verileri korumalıdır yalıtılmış depolama kullanmanız gerekir.  
  
 Daha fazla bilgi için [yalıtılmış depolama](/dotnet/standard/io/isolated-storage).  
  
### <a name="other-local-files"></a>Diğer yerel dosyaları  
 Uygulamanızı veya bunları raporlar, resimler, müzik ve benzeri gibi son kullanıcı verilerini kaydetmesi çalışmanız gerekiyorsa, uygulamanızı gerektirecek <xref:System.Security.Permissions.FileIOPermission> okuyup verileri yerel dosya sistemine yazma.  
  
## <a name="remote-data"></a>Uzak Veri  
 Belirli bir noktada, uygulamanız müşteri verileri veya market bilgileri gibi uzak bir Web sitesinden bilgi almak büyük olasılıkla gerekir. Bu bölümde, uzak veri almak için en yaygın teknikleri açıklar.  
  
### <a name="access-files-with-http"></a>HTTP ile erişim dosyaları  
 Kullanarak bir Web sunucusundan veri erişebilirsiniz <xref:System.Net.WebClient> veya <xref:System.Net.HttpWebRequest> sınıfını <xref:System.Net> ad alanı. Veriler, statik dosyalar olabilir veya [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ham metin veya XML verisi döndüren uygulamalar. Verilerinizi XML biçiminde verileri almanın en hızlı yolu kullanarak ise, <xref:System.Xml.XmlDocument> sınıf ayarlanmış <xref:System.Xml.XmlDocument.Load%2A> yöntemi bağımsız değişken olarak bir URL alır. Bir örnek için bkz. [DOM'da XML belgesi okuma](/dotnet/standard/data/xml/reading-an-xml-document-into-the-dom).  
  
 Uygulamanızın HTTP üzerinden uzak verilere eriştiğinde, güvenlik düşünmek zorunda. Varsayılan olarak, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanın erişim için ağ kaynaklarına, uygulamanızın nasıl dağıtıldığına bağlı olarak, kısıtlanmış olabilir. Bu kısıtlamalar, kötü amaçlı programlar ayrıcalıklı uzak veri erişimini veya bir kullanıcının bilgisayarına ağdaki diğer bilgisayarlara saldırmak için kullanmasını önlemek için uygulanır.  
  
 Aşağıdaki tabloda, kullanabileceğinize dağıtım stratejilerini ve varsayılan Web izinlerini listeler.  
  
|Dağıtım türü|Varsayılan ağ izinleri|  
|---------------------|---------------------------------|  
|Web yüklemesi|Yalnızca uygulamanın yüklendiği Web sunucusuna erişebilirsiniz|  
|Dosya Paylaşımı yükleme|Tüm Web sunucularına erişemiyor|  
|CD-ROM yükleme|Tüm Web sunucularına erişebilir|  
  
 Varsa, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama, bir Web sunucusu güvenlik kısıtlamaları nedeniyle erişemez, uygulama onay gerekir <xref:System.Net.WebPermission> bu Web sitesi için. Güvenlik izinlerini artırma hakkında daha fazla bilgi için bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulaması, bakın [güvenli ClickOnce uygulamaları](../deployment/securing-clickonce-applications.md).  
  
### <a name="access-data-through-an-xml-web-service"></a>XML Web hizmeti verilerine erişim  
 Verilerinizi XML Web hizmeti olarak kullanıma sunma, verileri bir XML Web hizmeti proxy'si kullanarak erişebilirsiniz. Proxy bir [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] sınıfı kullanarak oluşturduğunuz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. XML Web hizmeti işlemleri — müşteriler, yerleştirme siparişler ve benzeri alma gibi — proxy üzerinde yöntemler olarak sunulur. Bu Web Hizmetleri ham metin veya XML dosyaları çok daha kolay hale getirir.  
  
 Aynı güvenlik kısıtlamalara göre XML Web hizmeti HTTP üzerinden çalışırsa, hizmet kısıtlanacaktır <xref:System.Net.WebClient> ve <xref:System.Net.HttpWebRequest> sınıfları.  
  
### <a name="access-a-database-directly"></a>Bir veritabanına doğrudan erişim  
 Sınıfları için kullanabileceğiniz <xref:System.Data> ağınızı, ancak SQL Server için güvenlik sorunları hesaba gibi bir veritabanı sunucusu ile doğrudan bağlantı kurmak için ad alanı. HTTP isteklerinin tersine, veritabanı bağlantı isteklerini kısmi güven altında varsayılan olarak her zaman Yasak; yüklerseniz bu izin varsayılan olarak yalnızca bulunur, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ROM'dan uygulama. Bu, uygulama tam güven verir. Belirli bir SQL Server veritabanına erişimi etkinleştirmek için uygulamanızın istemelisiniz <xref:System.Data.SqlClient.SqlClientPermission> ona; SQL Server dışındaki bir veritabanına erişimi etkinleştirmek için bunu istemelisiniz <xref:System.Data.OleDb.OleDbPermission>.  
  
 Çoğu zaman, veritabanına doğrudan erişim gerekmez, ancak bunun yerine yazılan bir Web sunucusu uygulaması aracılığıyla erişirsiniz [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] veya bir XML Web hizmeti. Bu şekilde tüm veritabanı erişimlerinin ise genellikle en iyi yöntem, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bir Web sunucusundan dağıtılır. Kısmi güven Server'da uygulamanızın izinlerini yükseltme olmadan erişebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: ClickOnce uygulamasına bir veri dosyası Ekle](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)