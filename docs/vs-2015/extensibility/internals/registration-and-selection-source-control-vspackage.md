---
title: Kayıt ve seçim (kaynak denetimi VSPackage'ı) | Microsoft Docs
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
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 636e70357c23059a505d657af0078653de413976
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764457"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Kayıt ve Seçim (Kaynak Denetimi VSPackage’ı)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kaynak denetimi VSPackage'ı kayıtlı, kendisine kullanıma sunmak için [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Birden fazla kaynak denetimi VSPackage'ı kayıtlı değilse, kullanıcı uygun zamanlarda yüklemek için hangi VSPackage'ı seçebilirsiniz. Bkz: [VSPackages](../../extensibility/internals/vspackages.md) VSPackages ve bunları kaydetme hakkında daha fazla bilgi.  
  
## <a name="registering-a-source-control-package"></a>Bir kaynak denetim paketi kaydediliyor  
 Kaynak Denetim paketi kayıtlı böylece [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ortam ve sorgu için desteklenen özellikleri bulabilirsiniz. Bir paketin bir örneği yalnızca özelliği veya komutları gereklidir veya açıkça istenen oluşturulduğu bir gecikme yükleme düzenini uygun olarak budur.  
  
 VSPackage hkey_local_machıne\software\microsoft\visualstudio bir sürüme özgü kayıt defteri anahtarında bilgi Yerleştir\\*X.Y*burada *X* ana sürüm numarası ve *Y* ikincil sürüm numarasıdır. Bu yöntem, birden çok sürümünü yan yana yüklenmesini destekler olanağı sağlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Kullanıcı arabirimi (UI), kaynak denetimi VSPackage'ları yanı sıra birden çok yüklü kaynak denetimi eklentileri (aracılığıyla kaynak denetimi bağdaştırıcısı paketi) arasından seçim destekler. Olabilir yalnızca bir etkin kaynak denetimi eklentisi veya VSPackage'ı aynı anda. Ancak, aşağıda açıklandığı gibi IDE bir otomatik çözüm tabanlı paket takas etme mekanizması kaynak denetimi eklentileri VSPackage'ları arasında geçiş sağlar. Bu seçim mekanizmasını etkinleştirmek için kaynak denetimi VSPackage'ı yoluna bazı gereksinimler vardır.  
  
### <a name="registry-entries"></a>Kayıt defteri girdileri  
 Bir kaynak denetim paketi üç özel GUID'leri gerekir:  
  
- Paket GUID'si: (Bu bölümde ID_Package olarak adlandırılır) kaynak denetimi uyarlamasını içeren paket için ana GUID budur.  
  
- Kaynak Denetim GUID'i: Bu kaynak denetimi VSPackage'ı ile Visual Studio kaynak denetimi saplama kaydetmek için kullanılan bir GUID değeridir ve ayrıca komut UI bağlamı GUID olarak kullanılır. Kaynak denetimi hizmetini GUID GUID kaynak denetiminde kayıtlı. Örnekte, kaynak denetim GUID'i ID_SccProvider çağrılır.  
  
- Kaynak denetimi hizmeti GUID: özel hizmet (Bu bölümde SID_SccPkgService olarak adlandırılır) Visual Studio tarafından kullanılan GUID budur. Buna ek olarak, diğer GUID'leri VSPackages, araç pencerelerini tanımlamak ve benzeri kaynak denetim paketi gerekir.  
  
  Aşağıdaki kayıt defteri girdilerini kaynak denetimi VSPackage'ı tarafından yapılması gerekir:  
  
|Anahtar adı|Girdileri|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|(varsayılan) rg_sz =: {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|(varsayılan) rg_sz =:\<paketin kolay adı ><br /><br /> Hizmet rg_sz =: {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|(varsayılan) rg_sz =: #\<kaynak kimliği için yerelleştirilmiş adı ><br /><br /> Paket rg_sz =: {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Unutmayın anahtar adı `SourceCodeControl`, tarafından kullanılan [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ve bir seçimi olarak kullanılamıyor \<PackageName >.)|(varsayılan) rg_sz =: {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>Bir kaynak denetim paketi seçme  
 Çeşitli kaynak denetimi eklentisi API tabanlı eklentiler ve kaynak denetimi VSPackage'ları eşzamanlı olarak kaydedilmesi. Kaynak Denetimi Eklentisi veya VSPackage'ı seçme işleminin emin olmanız gerekir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] eklentiyi yükler veya uygun zamanda VSPackage'ı ve gerekli olmadıkça gereksiz Bileşenler yüklenirken erteleyin. Ayrıca, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tüm kullanıcı Arabirimi menü öğeleri, iletişim kutuları ve araç çubukları gibi diğer etkin olmayan VSPackages kaldırın ve etkin VSPackage için kullanıcı arabirimini görüntüleyen gerekir.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Aşağıdaki işlemlerden biri gerçekleştirilirken bir kaynak denetimi VSPackage'ı yükler:  
  
- Çözüm (Çözüm kaynak denetimi altında olduğunda) açılır.  
  
   IDE bir çözüm veya proje kaynak denetimi altında açıldığında kaynak denetimi bu çözüm için yüklenecek belirlendiyse VSPackage'ı neden olur.  
  
- Herhangi bir kaynak denetimi VSPackage'ı menü komutlarını yürütülür.  
  
  Kaynak denetimi VSPackage'ı yalnızca bunlar gerçekten olacak gerektiğinde tüm bileşenleri yüklenecektir (Gecikmeli yüklemeyi aksi bilinen) kullanılır.  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>Otomatik çözüm tabanlı VSPackage değiştirme  
 Kaynak denetimi VSPackage'ları el ile takas edebilirsiniz aracılığıyla [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **seçenekleri** iletişim kutusunun altında **kaynak denetimi** kategorisi. Bu çözüm açıldığında belirli bir çözüm için belirlenmiş bir kaynak denetim paketi otomatik olarak etkin olarak ayarlandığında otomatik çözüm tabanlı paket değiştirme anlamına gelir. Her kaynak denetim paketi uygulamalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] her ikisi arasında geçiş yapma işleme kaynağı (kaynak denetimi eklentisi API uygulama) denetimi eklentileri ve kaynak denetimi VSPackage'ları.  
  
 Her kaynak denetimi eklentisi API tabanlı geçiş yapmak için kullanılan kaynak denetimi bağdaştırıcısı paketi eklenti. Ara kaynak denetimi bağdaştırıcısı paket geçişi ve hangi kaynak denetimi eklentisi belirleme işlemini etkin veya etkin olmayan kullanıcı için saydamdır ayarlanmalıdır. Herhangi bir kaynak denetimi Eklentisi etkin olduğunda bağdaştırıcısı paketi her zaman etkindir. Yalnızca yükleniyor ve eklenti DLL'i kaldırma iki kaynak denetimi eklentileri miktarları arasında geçiş yapma. Kaynak denetimi VSPackage'ı geçiş, ancak uygun VSPackage'ı yüklemek için IDE ile etkileşim içerir.  
  
 VSPackage için kayıt defteri anahtarı çözüm dosyasıdır ve hiçbir çözüm açık kaynak denetimi VSPackage'ı çağrılır. Çözüm açıldığında [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kayıt defteri değerini bulur ve uygun kaynak denetimi VSPackage'ı yükler. Tüm kaynak denetimi VSPackage'ları, yukarıda açıklanan kayıt defteri girdilerini olması gerekir. Kaynak denetimi altındaki bir çözümü, belirli bir kaynak denetimi VSPackage'ı ile ilişkili olarak işaretlenir. Kaynak denetimi VSPackage'ları uygulanmalı <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> otomatik çözüm tabanlı VSPackage takas etkinleştirmek için.  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Visual Studio Paket seçimi ve geçişi için kullanıcı Arabirimi  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Kaynak denetimi VSPackage'ı için kullanıcı Arabirimi ve Eklenti Seçimi sağlar **seçenekleri** iletişim kutusunun altında **kaynak denetimi** kategorisi. VSPackage ve etkin kaynak denetimi eklentisi seçmesini sağlar. Aşağı açılan liste aşağıdakileri içerir:  
  
- Tüm kaynak denetimi paketleri yüklü  
  
- Tüm kaynak denetimi eklentileri yüklü  
  
- "none", hangi kaynak kodu denetimi devre dışı bırakır seçeneği  
  
  Yalnızca kullanıcı Arabirimi etkin kaynak denetimi seçimi için görünür durumdadır. VSPackage Seçimi önceki VSPackage için kullanıcı arabirimini gizler ve yeni bir kullanıcı Arabiriminde gösterilir. Kullanıcı başına esasına göre etkin VSPackage'ı seçilmedi. Bir kullanıcının birden çok kopyasını varsa [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] eşzamanlı olarak açın, her biri farklı bir etkin VSPackage potansiyel olarak kullanabilirsiniz. Birden çok kullanıcı aynı bilgisayarda oturum açtıysanız, her kullanıcının ayrı örneklerini olabilir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] açın, her biri farklı bir etkin VSPackage. Zaman birden çok örneğini [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kaynak denetimi için varsayılan kaynak denetimi VSPackage yeniden etkin olarak ayarlanması, son açık çözüme dönüşür etkindi VSPackage bir kullanıcı tarafından kapatıldı.  
  
  Önceki sürümlerinden farklı olarak [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], bir IDE yeniden başlatma artık kaynak denetimi VSPackage'ları geçiş yapmak için tek yoludur. VSPackage seçimi otomatik olarak yapılır. Paketleri geçiş Windows kullanıcı ayrıcalıkları (yönetici veya İleri kullanıcı) gerektirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [Özellikleri](../../extensibility/internals/source-control-vspackage-features.md)   
 [Kaynak Denetimi Eklentisi oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [VSPackage’lar](../../extensibility/internals/vspackages.md)

