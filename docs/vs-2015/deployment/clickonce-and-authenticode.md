---
title: ClickOnce ve Authenticode | Microsoft Docs
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
- .pfx files
- ClickOnce deployment, Authenticode
- Authenticode, ClickOnce
- ClickOnce deployment, certificates
- ClickOnce deployment, security
ms.assetid: ab5b6712-f32a-4e33-842f-e88ab4818ccf
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: df3d87e240476aa02f5129f2238a1df55eb3be79
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49289491"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce ve Authenticode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Authenticode * uygulama kodu uygulama yayımcısının özgünlüğünü doğrulamak dijital sertifika ile imzalamak için endüstri standardı şifreleme kullanan bir Microsoft teknolojisidir. Uygulama dağıtımı için Authenticode kullanılarak [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Truva atı riskini azaltır. Truva atı, virüs veya kötü amaçlı bir üçüncü taraf kurulu olan güvenilir bir kaynaktan gelen yasal bir program olarak görünen diğer zararlı programı değil. İmzalama [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bir dijital sertifika ile dağıtımları derlemeleri ve dosyaları değil doğrulamak için isteğe bağlı bir adımdır.  
  
 Aşağıdaki bölümlerde Authenticode içinde kullanılan dijital sertifikalar farklı türleri açıklanmaktadır, sertifikalar kullanılarak doğrulandı nasıl sertifika yetkilileri (CA'lar), zaman damgası sertifikaları rolünü ve yöntemleri için kullanılabilir depolama sertifikalar.  
  
## <a name="authenticode-and-code-signing"></a>Authenticode ve kod imzalama  
 A *dijital sertifika* yayımcıya açıklayan meta verileri yanı sıra şifreleme ortak/özel bir anahtar çifti içeren bir dosyadır sertifikanın verildiği ve sertifikayı veren Aracısı.  
  
 Authenticode sertifika çeşitli türleri vardır. Her biri farklı imzalama yapılandırılır. İçin [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamalar, kod imzalama için geçerli olan Authenticode sertifikası olması gerekir. Oturum denerseniz bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama başka türde bir dijital e-posta sertifikası gibi bir sertifika ile çalışmaz. Daha fazla bilgi için [kod imzalama giriş](http://go.microsoft.com/fwlink/?LinkId=179452).  
  
 Kod üç yoldan biriyle imzalama için bir sertifika edinebilirsiniz:  
  
-   Bir sertifika satıcıdan satın alın.  
  
-   Dijital sertifikalar oluşturmaktan sorumlu, kuruluşunuzdaki bir gruptan alırsınız.  
  
-   Dahil olan MakeCert.exe ile kendi sertifikanızı oluşturmak [!INCLUDE[winsdklong](../includes/winsdklong-md.md)].  
  
### <a name="how-using-certificate-authorities-helps-users"></a>Sertifika yetkililerini kullanarak kullanıcıların nasıl yardımcı  
 MakeCert.exe yardımcı programını kullanılarak oluşturulan sertifika yaygın olarak adlandırılan bir *self-cert* veya *test cert*. Bu tür bir sertifika bir .snk dosyası çalışan .NET Framework'teki Server'dakine benzer şekilde çalışır. Yalnızca bir ortak/özel şifreleme anahtar çiftinden oluşur ve doğrulanabilir hiçbir yayımcı bilgilerini içerir. Kendi kendine sertifikaları dağıtmak için kullanabileceğiniz [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] intranet yüksek güven uygulamaları. Ancak, bu uygulamaların çalıştırdığınızda bir istemci bilgisayara [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bunları Bilinmeyen bir yayımcıdan gelen olarak tanımlar. Varsayılan olarak, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] self-certs ile imzalanmış ve Internet üzerinden dağıtılan uygulamaları, güvenilir uygulama dağıtımı faydalanamaz.  
  
 Bunun aksine, bir sertifika bir CA'dan bir sertifika satıcısı ya da bir bölüm gibi kuruluşunuzda alırsanız, sertifika kullanıcılarınız için daha fazla güvenlik sağlar. Yalnızca imzalı yazılım yayımcısını tanımlar, ancak bunu imzalayan CA'ya ile kontrol ederek bu kimliğini doğrular. CA kök yetkilisi değil ise, Authenticode ayrıca "CA sertifika vermeye yetkili olduğunu doğrulamak için geri kök yetkilisine zincirler". Daha fazla güvenlik için mümkün olduğunda bir CA tarafından verilen bir sertifika kullanmanız gerekir.  
  
 Self-cert oluşturma hakkında daha fazla bilgi için bkz. [Makecert.exe (sertifika oluşturma aracı)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).  
  
### <a name="timestamps"></a>Zaman damgaları  
 Oturum açmak için kullanılan sertifikaları [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamaları süresi zaman bir belirli bir süre sonra genellikle on iki aylık. Yeni sertifikalar uygulamaları sürekli yeniden imzalama için gereken kaldırmak için [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zaman damgası destekler. Bir uygulama zaman damgasıyla imzalandığında sertifikasını sürdürecektir kabul dolduktan sonra bile, zaman damgası geçerli sağlanır. Böylece [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] süresi dolmuş sertifikaları, ancak karşıdan yüklemek ve çalıştırmak için geçerli zaman damgaları uygulamalarla. Ayrıca, güncelleştirmeleri indirmek ve yüklemek devam etmek yüklenmiş uygulamalara sahip süresi dolmuş sertifikaları sağlar.  
  
 Uygulama sunucusuna bir zaman damgası eklemek için zaman damgası sunucusunun kullanılabilir olması gerekir. Zaman damgası sunucusu seçme hakkında daha fazla bilgi için bkz: [nasıl yapılır: oturum uygulama ve dağıtım bildirimlerini](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
### <a name="updating-expired-certificates"></a>Süresi dolan sertifikaları güncelleştirme  
 Önceki .NET Framework sürümlerinde, sertifikanın süresi dolmuş uygulamayı güncelleştirme, Uygulama çalışmayı durdurmasına neden olabilir. Bu sorunu çözmek için aşağıdaki yöntemlerden birini kullanın:  
  
-   .NET Framework sürüm 2.0 SP1 veya daha sonra Windows XP veya sürüm 3.5 veya Windows Vista için daha sonra güncelleştirin.  
  
-   Uygulamayı kaldırın ve yeni bir sürümünü geçerli bir sertifika ile yeniden yükleyin.  
  
-   Sertifika güncelleştirmeleri bir komut satırı derlemesi oluşturun. Bu işlem hakkında adım adım bilgiler bulunabilir [Microsoft destek makalesi 925521](http://go.microsoft.com/fwlink/?LinkId=179454).  
  
### <a name="storing-certificates"></a>Sertifika depolama  
  
-   Dosya sisteminizde bir .pfx dosyası olarak sertifikaları depolayabilirsiniz veya bir anahtar kapsayıcısı içinde depolayabilirsiniz. Bir kullanıcı bir Windows etki alanındaki bir anahtar kapsayıcı sayısı olabilir. Bu bir .pfx dosyasına bunun yerine kaydetmeniz gerekir, belirtmediğiniz sürece varsayılan olarak, sertifikaları MakeCert.exe, kişisel anahtar kapsayıcısı içinde saklamak. Mage.exe ve MageUI.exe [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] oluşturmaya yönelik Araçlar [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtımları, her iki şekilde depolanan sertifikaları kullanmak etkinleştirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md)   
 [Güvenilir Uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md)   
 [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)



