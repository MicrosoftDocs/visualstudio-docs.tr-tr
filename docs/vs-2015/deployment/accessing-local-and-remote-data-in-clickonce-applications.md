---
title: ClickOnce uygulamalarında yerel ve uzak veri erişimi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- data access, ClickOnce applications
ms.assetid: be5cbe12-6cb6-49c9-aa59-a1624e1eef3d
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 4fe0c0b1cd7659a5887f267181ffd6fa7bb5e8d4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218849"
---
# <a name="accessing-local-and-remote-data-in-clickonce-applications"></a>ClickOnce Uygulamalarında Yerel ve Uzak Veri Erişimi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çoğu uygulama veri üretir veya tüketir. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Okuma ve yerel olarak ve uzaktan veri yazma için çeşitli seçenekler sunar.  
  
## <a name="local-data"></a>Yerel veriler  
 İle [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], aşağıdaki yöntemlerden birini kullanarak yerel olarak veri depolamak ve yükleyin:  
  
-   [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Veri dizini  
  
-   Yalıtılmış Depolama  
  
-   Diğer yerel dosyaları  
  
### <a name="clickonce-data-directory"></a>ClickOnce veri dizini  
 Her [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] yerel bir bilgisayarda yüklü uygulama kullanıcının belgeler ve ayarlar klasöründe depolanan bir veri dizinine sahip. Dahil herhangi bir dosyayı bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama ve işaretli bir "veri" dosyası, bir uygulama yüklendiğinde bu dizine kopyalanır. Veri dosyaları en sık kullanılan bir dosya türünde olabilir metin, XML ve Microsoft Access .mdb dosyaları gibi veritabanı dosyaları.  
  
 Veri dizini uygulama açıkça depolar ve tutar veriler, yönetilen uygulama verileri için tasarlanmıştır. Tüm statik uygulama bildiriminde "veri" olarak işaretlenen değil (nondependency) dosyalar yerine uygulama dizininde bulunur. Uygulamanın yürütülebilir (.exe) dosyaları ve derlemeleri bulunduğu bu dizindir.  
  
> [!NOTE]
>  Olduğunda bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulaması kaldırıldığında, kendi veri dizini de kaldırılır. Hiçbir zaman son kullanıcı tarafından yönetilen belgeler gibi verilerini depolamak için veri dizini kullanın.  
  
#### <a name="marking-data-files-in-a-clickonce-distribution"></a>ClickOnce dağıtım veri dosyalarında işaretleme  
 Mevcut bir dosyayı veri dizini içine koymak için var olan dosyayı bir veri dosyası olarak işaretlemelisiniz, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamanın uygulama bildirim dosyası. Daha fazla bilgi için [nasıl yapılır: ClickOnce uygulamasına bir veri dosyası dahil](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
#### <a name="reading-from-and-writing-to-the-data-directory"></a>Okuma ve yazma için veri dizini  
 Veri dizini okuma gerektirir, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama isteği okuma izni; benzer şekilde, dizine yazma izni gerektirir. Tam güven ile çalışacak şekilde yapılandırılmışsa, uygulamanızın otomatik olarak bu izne sahip. İzin yükseltilmesi ya da güvenilir uygulama dağıtımı'nı kullanarak uygulamanız için yükseltme yaptığınıza izinler hakkında daha fazla bilgi için bkz. [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md).  
  
> [!NOTE]
>  Kuruluşunuz güvenilen uygulama dağıtımı kullanmaz ve izin yükseltme devre dışı bırakılmış ise, izinleri sunduğundan başarısız olur.  
  
 Uygulamanızın bu izinlere sahip olduktan sonra veri dizini içindeki sınıflarda yöntem çağrıları kullanarak erişebildiğinizi <xref:System.IO>. Bir Windows Forms içinde veri dizini yolunu elde edebilirsiniz [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] kullanarak uygulama <xref:System.Deployment.Application.ApplicationDeployment.DataDirectory%2A> tanımlanan özellik <xref:System.Deployment.Application.ApplicationDeployment.CurrentDeployment%2A> özelliği <xref:System.Deployment.Application.ApplicationDeployment>. Verilerinize erişmek için en uygun ve önerilen yöntem budur. Aşağıdaki kod örneği, bir veri dosyası olarak dağıtımınızda bulunan alan ve csv.txt olarak adlı bir metin dosyası için bunun nasıl yapılacağını gösterir.  
  
 [!code-csharp[ClickOnce.OpenDataFile#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.OpenDataFile/CS/Form1.cs#1)]
 [!code-vb[ClickOnce.OpenDataFile#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.OpenDataFile/VB/Form1.vb#1)]  
  
 Veri dosyaları olarak dağıtımınızdaki dosyalardan işaretleme daha fazla bilgi için bkz: [nasıl yapılır: ClickOnce uygulamasına bir veri dosyası dahil](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
 İlgili değişkenleri kullanarak veri dizini yolunu de edinebilirsiniz <xref:System.Windows.Forms.Application> gibi sınıf <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A>.  
  
 Diğer dosya türlerini yönetmek için ek izinler gerektirebilir. Bir Access (.mdb) veritabanı dosyası kullanmak istiyorsanız, örneğin, uygulama tam güven ilgili kullanmak için onay gerekir <xref:System.Data> sınıfları.  
  
#### <a name="data-directory-and-application-versions"></a>Veri dizini ve uygulama sürümleri  
 Bir uygulamanın her sürümü diğer sürümlerden yalıtılmış kendi veri dizini vardır. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] böylece uygulamanın çalışma zamanında yeni veri dosyalarını oluşturmak için bir konum ister tüm veri dosyalarını dağıtımdaki bağımsız olarak bu dizin oluşturur. Bir uygulamanın yeni bir sürümü yüklü olduğunda [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tüm dosyaları önceki sürümün Veri Dizininden yeni sürümün veri dizinine kopyalar; oluşturan veya orijinal Dağıtımdaki uygulama.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bir veri dosyası, farklı karma değeri uygulamanın yeni sürümü eski bir sürümü varsa dosyanın eski bir sürümünü daha yeni bir sunucu sürümüyle yerini alır. Ayrıca, yeni oluşturulan uygulama'nın önceki bir sürümüne sahip bir dosya aynı ada yeni sürümün dağıtımdaki bir dosya olarak [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] eski sürümün dosya yeni dosyanın üzerine yazar. Her iki durumda da, eski dosyaları içinde veri dizini adlı bir alt eklenecek `.pre`, böylece uygulama geçiş amacıyla eski verileri erişmeye devam edebilirsiniz.  
  
 Daha ayrıntılı veri geçişini gerekiyorsa, kullanabileceğiniz [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım için yeni veri dizini eski veriler dizininden özel geçiş yapmak API. Mevcut bir yüklemeyi kullanarak test gerekecektir <xref:System.Deployment.Application.ApplicationDeployment.IsFirstRun%2A>, güncelleştirme kullanarak indirin <xref:System.Deployment.Application.ApplicationDeployment.Update%2A> veya <xref:System.Deployment.Application.ApplicationDeployment.UpdateAsync%2A>, ve herhangi bir özel veri geçişi iş güncelleştirme sonrası kendi tamamlandı.  
  
### <a name="isolated-storage"></a>Yalıtılmış Depolama  
 Yalıtılmış Depolama oluşturmak ve basit bir API kullanarak dosyalara erişmek için bir API sağlar. Depolanan dosyaların konumunu gerçek hem geliştiriciler hem de kullanıcı gizlenir.  
  
 Yalıtılmış Depolama works tüm sürümlerinde [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Yalıtılmış Depolama ayrıca kısmen güvenilir uygulamaların ek izin verilmesine gerek kalmadan çalışır. Uygulamanızı kısmi güvende çalıştırmanız gerekir, ancak uygulamaya özgü verileri korumalıdır yalıtılmış depolama kullanmanız gerekir.  
  
 Daha fazla bilgi için [yalıtılmış depolama](http://msdn.microsoft.com/library/aff939d7-9e49-46f2-a8cd-938d3020e94e).  
  
### <a name="other-local-files"></a>Diğer yerel dosyaları  
 Uygulamanızı veya bunları raporlar, resimler, müzik ve benzeri gibi son kullanıcı verilerini kaydetmesi çalışmanız gerekiyorsa, uygulamanızı gerektirecek <xref:System.Security.Permissions.FileIOPermission> okuyup verileri yerel dosya sistemine yazma.  
  
## <a name="remote-data"></a>Uzak Veriler  
 Belirli bir noktada, uygulamanız müşteri verileri veya market bilgileri gibi uzak bir Web sitesinden bilgi almak büyük olasılıkla gerekir. Bu bölümde, uzak veri almak için en yaygın teknikleri açıklar.  
  
### <a name="accessing-files-by-using-http"></a>HTTP kullanarak dosyalara erişme  
 Kullanarak bir Web sunucusundan veri erişebilirsiniz <xref:System.Net.WebClient> veya <xref:System.Net.HttpWebRequest> sınıfını <xref:System.Net> ad alanı. Veriler, statik dosyalar olabilir veya [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ham metin veya XML verisi döndüren uygulamalar. Verilerinizi XML biçiminde verileri almanın en hızlı yolu kullanarak ise, <xref:System.Xml.XmlDocument> sınıf ayarlanmış <xref:System.Xml.XmlDocument.Load%2A> yöntemi bağımsız değişken olarak bir URL alır. Bir örnek için bkz. [DOM'da XML belgesi okuma](http://msdn.microsoft.com/library/a4fb291f-5630-49ba-a49a-5b66c3b71e49).  
  
 Uygulamanızın HTTP üzerinden uzak verilere eriştiğinde, güvenlik düşünmek zorunda. Varsayılan olarak, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamanın erişim için ağ kaynaklarına, uygulamanızın nasıl dağıtıldığına bağlı olarak, kısıtlanmış olabilir. Bu kısıtlamalar, kötü amaçlı programlar ayrıcalıklı uzak veri erişimini veya bir kullanıcının bilgisayarına ağdaki diğer bilgisayarlara saldırmak için kullanmasını önlemek için uygulanır.  
  
 Aşağıdaki tabloda, kullanabileceğinize dağıtım stratejilerini ve varsayılan Web izinlerini listeler.  
  
|Dağıtım türü|Varsayılan ağ izinleri|  
|---------------------|---------------------------------|  
|Web yüklemesi|Yalnızca uygulamanın yüklendiği Web sunucusuna erişebilirsiniz|  
|Dosya Paylaşımı yükleme|Tüm Web sunucularına erişemiyor|  
|CD-ROM yükleme|Tüm Web sunucularına erişebilir|  
  
 Varsa, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama, bir Web sunucusu güvenlik kısıtlamaları nedeniyle erişemez, uygulama onay gerekir <xref:System.Net.WebPermission> bu Web sitesi için. Güvenlik izinlerini artırma hakkında daha fazla bilgi için bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulaması, bakın [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md).  
  
### <a name="accessing-data-through-an-xml-web-service"></a>Bir XML Web hizmeti aracılığıyla verilere erişme  
 Verilerinizi XML Web hizmeti olarak kullanıma sunma, verileri bir XML Web hizmeti proxy'si kullanarak erişebilirsiniz. Proxy bir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sınıfı kullanarak oluşturduğunuz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. XML Web hizmeti işlemleri — müşteriler, yerleştirme siparişler ve benzeri alma gibi — proxy üzerinde yöntemler olarak sunulur. Bu Web Hizmetleri ham metin veya XML dosyaları çok daha kolay hale getirir.  
  
 Aynı güvenlik kısıtlamalara göre XML Web hizmeti HTTP üzerinden çalışırsa, hizmet kısıtlanacaktır <xref:System.Net.WebClient> ve <xref:System.Net.HttpWebRequest> sınıfları.  
  
### <a name="accessing-a-database-directly"></a>Bir veritabanına doğrudan erişme  
 Sınıfları için kullanabileceğiniz <xref:System.Data> ağınızı, ancak SQL Server için güvenlik sorunları hesaba gibi bir veritabanı sunucusu ile doğrudan bağlantı kurmak için ad alanı. HTTP isteklerinin tersine, veritabanı bağlantı isteklerini kısmi güven altında varsayılan olarak her zaman Yasak; yüklerseniz bu izin varsayılan olarak yalnızca bulunur, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ROM'dan uygulama. Bu, uygulama tam güven verir. Belirli bir SQL Server veritabanına erişimi etkinleştirmek için uygulamanızın istemelisiniz <xref:System.Data.SqlClient.SqlClientPermission> ona; SQL Server dışındaki bir veritabanına erişimi etkinleştirmek için bunu istemelisiniz <xref:System.Data.OleDb.OleDbPermission>.  
  
 Çoğu zaman, veritabanına doğrudan erişim gerekmez, ancak bunun yerine yazılan bir Web sunucusu uygulaması aracılığıyla erişirsiniz [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] veya bir XML Web hizmeti. Bu şekilde tüm veritabanı erişimlerinin ise genellikle en iyi yöntem, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama bir Web sunucusundan dağıtılır. Kısmi güven Server'da uygulamanızın izinlerini yükseltme olmadan erişebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ClickOnce Uygulamasına bir Veri Dosyası Dahil Etme](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)



