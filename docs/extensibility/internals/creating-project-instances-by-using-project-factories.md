---
title: Proje Üreteçlerini kullanarak proje örnekleri oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4a02d6dd09ec019ad05404c033889f89ed140dd1
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219503"
---
# <a name="create-project-instances-by-using-project-factories"></a>Proje üreteçlerini kullanarak proje örnekleri oluşturma
Proje türlerinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanan bir *proje fabrikası* proje nesnelerin örneklerini oluşturmak için. Bir proje fabrikası cocreatable COM nesneleri için bir standart sınıf üreteci benzer. Ancak, proje nesnelerini cocreatable değildir; Bunlar, bir proje fabrikası kullanarak yalnızca oluşturulabilir.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE bir kullanıcı, mevcut bir projeyi yüklediğinde veya yeni bir proje oluşturur, VSPackage içinde uygulanan proje fabrikası çağırır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Yeni proje nesne doldurmak için yeterli bilgi IDE'ye sağlar **Çözüm Gezgini**. Yeni proje nesne IDE tarafından başlatılan tüm ilgili UI eylemlerini desteklemek için gereken arabirimler de sağlar.  
  
 Uygulayabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> projenizdeki bir sınıf içinde arabirim. Genellikle, kendi modülünde yer alıyor.  
  
 Bir sahibi tarafından toplanan destekleyen projeler, proje dosyasında bir sahibi anahtarı kalıcı gerekir. Zaman <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> yöntemi bir sahibi anahtara sahip bir proje üzerinde çağrılır, sahip olunan proje sahibi anahtarıyla GUID sonra çağıran bir proje fabrikası dönüştürür `CreateProject` gerçek oluşturma yapmak için bu proje fabrika yöntemi.  
  
## <a name="create-an-owned-project"></a>Sahip olunan bir proje oluşturun  
 Bir sahip iki aşamada sahibi bir proje oluşturur:  
  
1. Çağırarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> yöntemi. Bu sahibi proje giriş kontrol etme hakkındaki bağlı bir toplu proje nesne oluşturmak için bir şans verir `IUnknown`. Sahip olunan proje iç geçirir `IUnknown` ve tekrar sahibi projeye toplanan nesne. Bu sahibi proje iç depolamak için bir şans verir `IUnknown`.  
  
2. Çağırarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> yöntemi. Çağırmak yerine bu yöntem çağrıldığında, sahip olunan proje tüm örnekleme mu `IVsProjectFactory::CreateProject` sahibi olmayan projeler için durum olduğu gibi. Giriş `VSOWNEDPROJECTOBJECT` sabit listesi, genellikle toplu sahip olunan proje. Sahip olunan proje proje nesne zaten oluşturulmuş olup olmadığını belirlemek için bu değişkeni kullanın (tanımlama bilgisi eşit değil NULL) veya (tanımlama bilgisi eşittir NULL) oluşturulması gerekir.  
  
   Proje türleri, benzersiz bir proje GUID cocreatable bir COM nesnesi CLSID'sini benzer tarafından tanımlanır. Genellikle, bir proje fabrikası mümkün olsa bir tek proje türünün örneğini oluşturmak bir proje fabrikası işleyen birden fazla proje türü GUID işleyin.  
  
   Proje türleri belirli dosya adı uzantısı ile ilişkilendirilir. Bir kullanıcı var olan bir proje dosyasını açmaya veya şablon kopyalayarak yeni bir proje oluşturma girişimi şu IDE uzantısı dosyada karşılık gelen proje GUID'i belirlemek için kullanır.  
  
   IDE gereken yeni bir proje oluşturun veya belirli bir türün varolan bir projeyi açın olup olmadığını belirler. hemen sonra IDE sistem kayıt defteri bilgileri kullanır **[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects]**  hangi bulmak için gerekli proje fabrikası VSPackage uygular. IDE bu VSPackage'ı yükler. İçinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> yöntemi VSPackage'ı kaydetmeniz gerekir, proje fabrikası IDE ile çağırarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> yöntemi.  
  
   Birincil yöntemi `IVsProjectFactory` arabirimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, hangi iki senaryo ele: mevcut bir projeyi açmak ve yeni proje oluşturma. Çoğu proje proje durumlarına proje dosyasında depolar. Genellikle, yeni projeler şablon dosyasının bir kopyasını geçirilen yapma tarafından oluşturulan `CreateProject` yöntemi ve sonra bu kopyayı açabilirler. Mevcut projeleri örneği tarafından geçirilen proje dosyası açılırken doğrudan `CreateProject` yöntemi. `CreateProject` Yöntemi, kullanıcıya gerekli olarak ek kullanıcı Arabirimi özelliklerini görüntüleyebilirsiniz.  
  
   Proje hiçbir dosya da kullanabilir ve bunun yerine, bir veritabanı veya Web sunucusu gibi dosya sistemi dışındaki bir depolama mekanizması proje durumunu depolar. Dosya adı parametresi bu durumda, geçirilen `CreateProject` yöntemi aslında bir dosya sistemi yolu ancak benzersiz bir dize değil; bir URL — proje verilerini tanımlamak için. Geçirilen şablon dosyaları kopyalama gerekmez `CreateProject` uygun Oluşturma sırası yürütülecek tetiklemek için.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Denetim listesi: Yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)