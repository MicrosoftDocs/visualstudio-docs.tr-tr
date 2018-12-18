---
title: Proje Üreteçlerini kullanarak proje örnekleri oluşturma | Microsoft Docs
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
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 358c13bdc8bc312a479b9c316fa516ad68b10630
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736257"
---
# <a name="creating-project-instances-by-using-project-factories"></a>Proje Üreteçlerini Kullanarak Proje Örnekleri Oluşturma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Proje türlerinde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kullanan bir *proje fabrikası* proje nesnelerin örneklerini oluşturmak için. Bir proje fabrikası cocreatable COM nesneleri için bir standart sınıf üreteci benzer. Ancak, proje nesnelerini cocreatable değildir: Bunlar yalnızca proje Fabrika kullanılarak oluşturulabilir.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE bir kullanıcı, mevcut bir projeyi yüklediğinde veya yeni bir proje oluşturur, VSPackage içinde uygulanan proje fabrikası çağırır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Çözüm Gezgini doldurmak için yeterli bilgi IDE'ye yeni proje nesneyi sağlar. Yeni proje nesne IDE tarafından başlatılan tüm ilgili UI eylemlerini desteklemek için gereken arabirimler de sağlar.  
  
 Uygulayabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> projenizdeki bir sınıf içinde arabirim. Genellikle, kendi modülünde yer alıyor.  
  
 Uygulaması örneği için `IVsProjectFactory` bulunan PrjFac.cpp bkz arabirim [temel proje](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) örnek dizin.  
  
 Bir sahibi tarafından toplanan destekleyen projeler, proje dosyasında bir sahibi anahtarı kalıcı gerekir. Zaman <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> yöntemi bir sahibi anahtara sahip bir proje üzerinde çağrılır, sahip olunan proje sahibi anahtarıyla GUID sonra çağıran bir proje fabrikası dönüştürür `CreateProject` gerçek oluşturma yapmak için bu proje fabrika yöntemi.  
  
## <a name="creating-an-owned-project"></a>Sahip olunan bir proje oluşturma  
 Bir sahip iki aşamada sahibi bir proje oluşturur:  
  
1. Çağırarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> yöntemi. Bu sahibi proje giriş kontrol etme hakkındaki bağlı bir toplu proje nesne oluşturmak için bir şans verir `IUnknown`. Sahip olunan proje iç geçirir `IUnknown` ve tekrar sahibi projeye toplanan nesne. Bu sahibi proje iç depolamak için bir şans verir `IUnknown`.  
  
2. Çağırarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> yöntemi. Çağırmak yerine bu yöntem çağrıldığında, sahip olunan proje tüm örnekleme mu `IVsProjectFactory::CreateProject` sahibi olmayan projeler için durum olduğu gibi. Giriş `VSOWNEDPROJECTOBJECT` sabit listesi, genellikle toplu sahip olunan proje. Sahip olunan proje proje nesne zaten oluşturulmuş olup olmadığını belirlemek için bu değişkeni kullanın (tanımlama bilgisi eşit değil NULL) veya (tanımlama bilgisi eşittir NULL) oluşturulması gerekir.  
  
   Proje türleri, benzersiz bir proje GUID cocreatable bir COM nesnesi CLSID'sini benzer tarafından tanımlanır. Genellikle, bir proje fabrikası mümkün olsa bir tek proje türünün örneğini oluşturmak bir proje fabrikası işleyen birden fazla proje türü GUID işleyin.  
  
   Proje türleri belirli dosya adı uzantısı ile ilişkilendirilir. Bir kullanıcı var olan bir proje dosyasını açmaya veya şablon kopyalayarak yeni bir proje oluşturma girişimi şu IDE uzantısı dosyada karşılık gelen proje GUID'i belirlemek için kullanır.  
  
   Belirli bir türün varolan bir projeyi açın veya yeni bir proje oluşturmak gerekir yoksa IDE bilgileri [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects] sistem kayıt defteri, bulmak için kullandığı IDE belirler hemen sonra VSPackage'ı gerekli proje fabrikası uygular. IDE bu VSPackage'ı yükler. İçinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> yöntemi VSPackage'ı kaydetmeniz gerekir, proje fabrikası IDE ile çağırarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> yöntemi.  
  
   Birincil yöntemi `IVsProjectFactory` arabirimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> olduğu iki senaryo ele: mevcut bir projeyi açmak ve yeni proje oluşturma. Çoğu proje proje durumlarına proje dosyasında depolar. Genellikle, yeni projeler şablon dosyasının bir kopyasını geçirilen yapma tarafından oluşturulan `CreateProject` yöntemi ve sonra bu kopyayı açabilirler. Mevcut projeleri örneği tarafından geçirilen proje dosyası açılırken doğrudan `CreateProject` yöntemi. `CreateProject` Yöntemi, kullanıcıya gerekli olarak ek kullanıcı Arabirimi özelliklerini görüntüleyebilirsiniz.  
  
   Proje hiçbir dosya da kullanabilir ve bunun yerine, bir veritabanı veya Web sunucusu gibi dosya sistemi dışındaki bir depolama mekanizması proje durumunu depolar. Dosya adı parametresi bu durumda, geçirilen `CreateProject` yöntemi aslında bir dosya sistemi yolu ancak benzersiz bir dize değil; bir URL — proje verilerini tanımlamak için. Geçirilen şablon dosyaları kopyalama gerekmez `CreateProject` uygun Oluşturma sırası yürütülecek tetiklemek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Denetim Listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)

