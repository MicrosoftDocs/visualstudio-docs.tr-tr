---
title: Güvenilir Uygulama dağıtımına genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- ClickOnce deployment, security
- trusted application deployment
ms.assetid: b24a1702-8fbe-45b1-87a0-9618a0708f1d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c1be49bb015334ed37326fbe301ac2035a6f3269
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49848793"
---
# <a name="trusted-application-deployment-overview"></a>Güvenilir Uygulama dağıtımına genel bakış
Bu konu nasıl dağıtılacağı hakkında genel bakış sağlar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] güvenilir uygulama dağıtımı teknolojisini kullanarak yükseltilmiş izinlere sahip uygulamalar.  
  
 Güvenilir uygulama dağıtımı, parçası [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım teknolojisi, kuruluşların kullanıcıya sormadan daha güvenli bir şekilde yönetilen bir uygulama için ek izinler vermek için her boyuttaki kolaylaştırır. Güvenilir uygulama dağıtımı ile bir kuruluş yalnızca Authenticode sertifikaları kullanarak tanımlanan güvenilir yayımcılar, bir listesi için bir istemci bilgisayarı yapılandırabilirsiniz. Bundan sonra tüm [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bunlardan biri tarafından imzalanmış bir uygulamaya güvenilen yayımcılar, daha yüksek bir güven düzeyi alır.  
  
> [!NOTE]
>  Güvenilir uygulama dağıtımı tek seferlik bir kullanıcının bilgisayarına yapılandırılmasını gerektirir. Yönetilen Masaüstü ortamlarında, bu yapılandırma genel ilke kullanılarak gerçekleştirilebilir. İzin yükseltilmesi, bu uygulama için istediğinize değil ise, bunun yerine kullanın. Daha fazla bilgi için [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md).  
  
## <a name="trusted-application-deployment-basics"></a>Güvenilen uygulama dağıtımıyla ilgili temel bilgiler  
 Aşağıdaki tabloda nesneleri ve söz konusu olan rolleri güvenilir uygulama dağıtımı'gösterilmektedir.  
  
|Nesne veya rol|Açıklama|  
|--------------------|-----------------|  
|Yönetici|Güncelleştirme ve istemci bilgisayarları korumak için sorumlu kurumsal varlığı|  
|Güven Yöneticisi|Ortak dil çalışma zamanı (CLR) istemci uygulama güvenliği uygulamaktan sorumlu alt sistem.|  
|Yayımcı|Yazar ve uygulamayı tutar varlık.|  
|Dağıtıcı|Paketler ve uygulamayı kullanıcıya dağıtır varlık.|  
|sertifika|Genel ve özel anahtarı içeren bir şifreleme imzası; genellikle orijinalliği bir sertifika yetkilisi (CA) tarafından verilmiş.|  
|Authenticode sertifikası|Bir sertifika ile katıştırılmış meta verileri tanımlayan, diğerlerinin yanı sıra sertifika çalıştırılacağı kullanır.|  
|Sertifika yetkilisi|Yayımcılar kimliğini doğrular ve bunları sertifika veren bir kuruluş yayımcının meta verileriyle katıştırılmış.|  
|kök yetkilisi|Diğer sertifika yetkilileri sertifika vermek için yetki veren sertifika yetkilisi.|  
|anahtar kapsayıcısı|Sertifikaları depolamak için bir mantıksal depolama alanında Microsoft Windows.|  
|Güvenilir yayımcı|Bir yayımcı Authenticode sertifikası istemci bilgisayarda bir sertifika güven listesi (CTL) eklendi.|  
  
 Daha büyük kuruluşlarda yayımcı ve dağıtıcı sık iki ayrı varlık şunlardır:  
  
- Yayımcı oluşturan grubudur [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama.  
  
- Dağıtıcı dağıtan genellikle bilgi teknolojisi (BT) departmanı, grubudur [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kurumsal masaüstü bilgisayarlar için uygulama.  
  
Güvenilir uygulama dağıtımı yararlanmak için şu adımları izlemelisiniz:  
  
1. Yayımcı için bir sertifika edinin.  
  
2. Yayımcı tüm istemcilerde Güvenilen Yayımcılar deposuna ekleyin.  
  
3. Oluşturma, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama.  
  
4. Dağıtım bildirimi yayımcının sertifika ile oturum açın.  
  
5. Uygulama dağıtımı, istemci bilgisayarlar için yayımlayın.  
  
### <a name="obtain-a-certificate-for-the-publisher"></a>Yayımcı için bir sertifika alın  
 Dijital sertifikalar Microsoft Authenticode kimlik doğrulama ve güvenlik sistemi temel bileşenidir. Authenticode, Windows işletim sistemi, standart bir parçasıdır. Tüm [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamaları güvenilir uygulama dağıtımı'na katılıp katılmadığına bağımsız olarak bir dijital sertifika ile imzalanmalıdır. Authenticode'ile nasıl çalıştığına ilişkin tam açıklama için [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], bkz: [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md).  
  
### <a name="add-the-publisher-to-the-trusted-publishers-store"></a>Güvenilen Yayımcılar deposuna yayımcı ekleme  
 İçin [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] daha yüksek bir güven düzeyi almak üzere uygulama sertifikanızı güvenilen bir yayımcı uygulamanın çalışacağı her istemci bilgisayara eklemeniz gerekir. Bu görevi gerçekleştirme tek seferlik bir yapılandırmadır. Bu tamamlandıktan sonra kadar dağıtabilirsiniz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamaları ve tüm yüksek güven ile çalışır, yayımcının sertifika ile imzalanmış.  
  
 Uygulamanızı Masaüstü yönetilen bir ortamda dağıtıyorsanız; Windows işletim sistemi çalıştıran Örneğin, bir Kurumsal intranet; Grup İlkesi ile yeni bir sertifika güven listesi (CTL) oluşturarak, bir istemcinin depoya Güvenilen Yayımcılar ekleyebilirsiniz. Daha fazla bilgi için [bir sertifika güven listesi için bir Grup İlkesi nesnesi oluşturmak](http://go.microsoft.com/fwlink/?LinkId=102576).  
  
 Uygulamanızı Masaüstü yönetilen bir ortamda dağıtıyorsanız değil, bir sertifika güvenilen bir yayımcı deposuna eklemek için aşağıdaki seçenekleri vardır:  
  
-   <xref:System.Security.Cryptography?displayProperty=fullName> Ad alanı.  
  
-   *CertMgr.exe*, Internet Explorer'ın bir bileşeni olan ve bu nedenle Windows 98 ve sonraki tüm sürümlerinde bulunmaktadır. Daha fazla bilgi için [Certmgr.exe (Sertifika Yöneticisi Aracı)](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool).  
  
### <a name="create-a-clickonce-application"></a>ClickOnce uygulaması oluşturma  
 A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bir [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] istemci uygulaması uygulamayı tanımlayan ve yükleme parametrelerini sağlayan bildirim dosyaları ile birlikte. Programınıza kapatabilirsiniz bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kullanarak uygulama **Yayımla** komutunu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Alternatif olarak, gerekli tüm dosyaları oluşturabilirsiniz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bulunan araçları kullanarak dağıtım [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Ayrıntılı adımlar için [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım bkz [izlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
 Güvenilir uygulama dağıtımı için belirli [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]ve yalnızca birlikte kullanılan [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamalar.  
  
### <a name="sign-the-deployment"></a>Dağıtım oturum  
 Sertifikanızı aldıktan sonra dağıtımınız imzalamak için kullanmanız gerekir. Uygulamanızı kullanarak dağıtıyorsanız [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Yayımlama Sihirbazı, bir sertifikayı kendiniz değil belirttiyseniz Sihirbazı otomatik olarak bir test sertifikası sizin için oluşturur. Ayrıca [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Proje Tasarımcısı penceresinde, ancak bir CA tarafından sağlanan bir sertifika sağlamak için.  Ayrıca bkz: [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
> [!CAUTION]
>  Uygulama bir test sertifikası ile dağıtılması önermiyoruz.  
  
 Uygulamayı kullanarak da oturum açabilirsiniz *Mage.exe* veya *MageUI.exe* SDK Araçları. Daha fazla bilgi için [izlenecek yol: bir ClickOnce uygulamasını el ile dağıtmak](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Dağıtım imzalama ile ilgili komut satırı seçeneklerinin tam listesi için bkz. [Mage.exe (bildirim üretme ve düzenleme aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
### <a name="publish-the-application"></a>Uygulama yayımlama  
 Oturum açmış olan hemen sonra [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bildirimleri, uygulama, yükleme konumunuz için yayımlamaya hazır. Yükleme konumu, bir Web sunucusu, bir dosya paylaşımına veya yerel disk olabilir. Bir istemci, dağıtım bildirimini ilk kez eriştiğinde, güven yöneticisi seçmelisiniz olmadığını [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama authorities veya daha yüksek bir güven düzeyinde bir yüklü çalışmak için güvenilir yayımcı. Güven Yöneticisi depolamak karşılaştırarak dağıtım istemcinin güvenilir yayımcı olarak depolanan sertifikaları imzalamak için kullanılan sertifikanın bu seçenek bulunur. Güven Yöneticisi bir eşleşme bulduğunda, uygulamanın yüksek güven ile çalışır.  
  
## <a name="trusted-application-deployment-and-permission-elevation"></a>Güvenilir uygulama dağıtımı ve izin yükseltme  
 Geçerli yayımcı güvenilen bir yayımcı değilse, güven yöneticisi izin yükseltilmesi uygulamanızı yükseltilmiş izinleri vermek izinli olup olmadığını istediği hakkında kullanıcıyı sorgulamak için kullanır. Ancak, izin yükseltilmesi yönetici tarafından devre dışı bırakılırsa, uygulamayı çalıştırma izni alınamıyor. Uygulama çalışmaz ve kullanıcıya bildirim görüntülenir. İzin yükseltilmesi hakkında daha fazla bilgi için bkz: [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md).  
  
## <a name="limitations-of-trusted-application-deployment"></a>Güvenilir uygulama dağıtımı sınırlamaları  
 Güvenilir uygulama dağıtımı için yükseltilmiş güven kazandırmak için kullanabileceğiniz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Web üzerinden veya bir kurumsal dosya paylaşımını aracılığıyla dağıtılan uygulamalar. Güvenilir uygulama dağıtımı için kullanmak zorunda değilsiniz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] CD üzerinde varsayılan olarak, bu uygulamaların tam güven verildiğinden, dağıtılmış uygulamalar.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Mage.exe (bildirim üretme ve düzenleme aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [İzlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
