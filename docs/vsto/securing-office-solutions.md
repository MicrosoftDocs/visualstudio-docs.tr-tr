---
title: Office çözümleri güvenliğini sağlama
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- security [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 13b0680e9222302feab8a7cbe1ad375a1f7255be
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846206"
---
# <a name="secure-office-solutions"></a>Office çözümleri güvenliğini sağlama
  Office çözümleri için güvenlik modeli birçok teknoloji içerir: [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)], Microsoft Office ve Internet Explorer Yasak siteler bölgesi Güven Merkezi'nde. Aşağıdaki bölümlerde, farklı güvenlik özelliklerinin nasıl çalıştığı açıklanmaktadır:  
  
- [Office çözümlerine güven verme](#GrantingTrustToSolutions)  
  
- [Belgelere güven verme](#GrantingTrustToDocuments)  
  
- [Windows Installer'ı kullanırken, güven verme](#GrantingTrustWindowsInstaller)  
  
- [Office çözümleriyle ilgili belirli güvenlik konuları](#Security)  
  
- [Güvenlik geliştirme sırasında](#SecurityDuringDeployment)  
  
- [Office çalışma zamanı için Visual Studio Araçları](#VisualStudioToolsForOfficeRuntime)  
  
  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="GrantingTrustToSolutions"></a> Office çözümlerine güven verme  
 Office çözümlerine güven her son kullanıcıya aşağıdaki kanıta göre Office çözümünün güven güvenlik ilkesini değiştirmek anlamına gelir:  
  
- Dağıtım bildirimi imzalamak için kullanılan sertifika.  
  
- Dağıtım bildirimi URL'si.  
  
  Daha fazla bilgi için [Office çözümlerine güven verme](../vsto/granting-trust-to-office-solutions.md).  
  
##  <a name="GrantingTrustToDocuments"></a> Belgelere güven verme  
 Belge düzeyi özelleştirmesi belge güvenli bir konuma atanan bir dizinde olması gerekir. Daha fazla bilgi için [belgelere güven verme](../vsto/granting-trust-to-documents.md).  
  
##  <a name="GrantingTrustWindowsInstaller"></a> Windows Installer'ı kullanırken, güven verme  
 Yönetici hakları gerektirir Program Files dizini Office çözümlerini yüklemek için MSI dosyasını oluşturmak için Windows Installer'ı kullanabilirsiniz. Office çözümlerinde Program Files dizini, Office çalışma zamanı için Visual Studio 2010 Araçları güvenilmesi için bu Office çözümleri göz önünde bulundurur ve ClickOnce güven istemi göstermez.  
  
##  <a name="Security"></a> Office çözümleriyle ilgili belirli güvenlik konuları  
 Tarafından sağlanan güvenlik özelliklerine [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], ve Microsoft Office çeşitli Office çözümlerinde olası güvenlik tehditlerine karşı korumaya yardımcı olabilir. Daha fazla bilgi için [Office çözümleriyle ilgili belirli güvenlik konuları](../vsto/specific-security-considerations-for-office-solutions.md).  
  
##  <a name="SecurityDuringDeployment"></a> Güvenlik geliştirme sırasında  
 Geliştirme sürecinizi kolaylaştırmak için Visual Studio çalıştırmak ve çözümünüzü bilgisayarınızdaki bir projeyi her seferinde hata ayıklamak için gerekli olan güvenlik ilkesini ayarlar. Bazı senaryolarda projeyi geliştirmek için ek güvenlik adımlar gerekebilir.  
  
### <a name="document-level-solutions"></a>Belge düzeyi çözümleri  
 Aşağıdaki türlerde projeler geliştiriyorsanız bir belgenin tam yolu, Microsoft Office uygulamasının güvenilen konumlar listesine eklenmesi gerekir:  
  
- Belge düzeyi gibi bir ağ dosya paylaşımında olan çözümler  *\\\servername\sharename*.  
  
- Belge düzeyi çözümleri kullanmak için Word *.doc* veya *.docm* dosyaları.  
  
  Sizin için belge konumunu güvenilir konumlar listesine ekleyin veya özellikle hata ayıklama ve klasörleri yapı alt dizinleri içerir. Daha fazla bilgi için Microsoft Office Çevrimiçi Yardım makalesine bakın [oluşturma, kaldırma veya değişiklik dosyalarınız için güvenilen bir konum](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
### <a name="temporary-certificates"></a>Geçici sertifikalar  
 İmzalama sertifikası zaten mevcut değilse visual Studio geçici bir sertifika oluşturur. Bu geçici bir sertifika yalnızca geliştirme sırasında kullanmak ve dağıtım için resmi bir sertifika satın alın.  
  
 Bir Office projesi ilk oluşturulduktan sonra geçici bir sertifika oluşturulur. Bir sonraki basışınızda **F5**, proje sertifika eklendiğinde değiştirilmiş olarak işaretlendiği için projeyi yeniden oluşturulur.  
  
 Olabilir birçok geçici sertifikalar bir süre sonra için geçici sertifikalar bazen temizlemeniz gerekir.  
  
##  <a name="VisualStudioToolsForOfficeRuntime"></a> Office çalışma zamanı için Visual Studio Araçları  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Yayımcı ve özelleştirme verilen izinleri kimliğini doğrulamak için özelliklere sahiptir. Bu izinleri bir dizi güvenlik denetimleri doğrular.  
  
### <a name="security-during-customization-loading"></a>Yüklemeyi özelleştirme sırasında güvenlik  
 Belge düzeyi özelleştirmesi yüklendiğinde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] her zaman belge güvenilen konumlar listesine olup olmadığını denetler. Ayrıca, çalışma zamanı çözümü uygulama bildiriminde FullTrust istekleri olup olmadığını denetler. Özelleştirme yüklenirken herhangi bir ek güvenlik denetimi gerçekleştirir.  
  
### <a name="sequence-of-security-checks-during-installation"></a>Güvenlik denetimleri yükleme sırasında bir dizi  
 Office çözümünü yüklendiğinde veya güncellendiğinde, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] güven karar vermek için belirli bir sırayla bir dizi güvenlik denetimleri gerçekleştirir. Bir çözüm yüklendiğinde veya yalnızca çalışma zamanı çözümü güvenilir olduğunu belirlerse güncelleştirildi.  
  
 Yükleme işlemi dört yoldan biriyle başlayabilirsiniz: Kurulum programını çalıştırarak, dağıtım bildirimini açarak, Microsoft Office uygulama konağı açarak veya çalıştırarak *VSTOInstaller.exe*.  
  
 İlk güvenlik denetimi yalnızca belge düzeyi çözümleri için geçerlidir. Belge düzeyi bir çözümün belgesini güvenilir bir konumda olması gerekir. Belge bir uzak ağ dosya paylaşımında ise veya varsa bir *.doc* veya *.docm* dosya adı uzantısı, belgenin konumu güvenilir konumlar listesine eklenmesi gerekir. Daha fazla bilgi için [belgelere güven verme](../vsto/granting-trust-to-documents.md).  
  
 ![VSTO güvenlik - Microsoft Office'ten yükleme](../vsto/media/host-install.png "VSTO güvenlik - Microsoft Office'ten yükleme")  
  
 Sonraki güvenlik denetimleri kümesini Bilgisi'nden [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ve ClickOnce. Bu denetimler geçirmek için Office çözümleri FullTrust izin istemesi gerekir, güvenilmeyen yayımcı listede olmayan bir sertifika ile imzalanmış ve Internet Explorer Yasak bölgede değil bir konumda olması. Sertifika güvenilir yayımcı listede yer alıyorsa, çözüm hemen yüklenir. Aksi takdirde, biri de, başarısız olmadı, çözüm denetimleri son kümesine devam eder.  
  
 ![VSTO güvenlik çözümlerini yükleme için](../vsto/media/installing.png "VSTO güvenlik çözümleri yüklemek için")  
  
 Varsa [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] güven istemi izin verilir ve çözümün güven henüz verilmedi, çalışma zamanı güven kararının, son kullanıcı tarafından yapılmasına izin verir. Bir giriş, kullanıcı çözüme güven verirse, kullanıcı listesine eklenir. Kullanıcı ekleme listesindeki tüm çözümleri tam güven ve yüklenebilir ve çalıştırın.  
  
 Office çözümünün Program Files dizinine Windows Installer (MSI) kullanarak yüklediyseniz, Visual Studio 2010'da başlıyor, ekleme listesi atlanır. Daha fazla bilgi için [ekleme listelerini kullanarak Office güven çözümleri](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 ![VSTO güvenlik - yüklemek için Kurulum programını kullanarak](../vsto/media/setup-vstoinstaller.png "VSTO güvenlik - yüklemek için Kurulum programını kullanma")  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümlerine güven verme](../vsto/granting-trust-to-office-solutions.md)   
 [Belgelere güven verme](../vsto/granting-trust-to-documents.md)   
 [Ekleme listelerini kullanarak Office çözümlerine güven](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Nasıl yapılır: ekleme listesi güvenliğini yapılandırma](../vsto/how-to-configure-inclusion-list-security.md)   
 [Nasıl yapılır: Office çözümlerini imzalama](../vsto/how-to-sign-office-solutions.md)   
 [Office çözüm güvenliğinde sorunlarını giderme](../vsto/troubleshooting-office-solution-security.md)   
 [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)   
 [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Başvurusu](/visualstudio/deployment/clickonce-reference)   
 [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)  
  
  