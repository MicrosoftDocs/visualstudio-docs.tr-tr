---
title: GenerateDeploymentManifest görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateDeploymentManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateDeploymentManifest task
- GenerateDeploymentManifest task [MSBuild]
ms.assetid: 0734ebda-734d-49c4-9642-8d9d919d45fd
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ad0b9919c5c567662d78573573f1bf046c93552
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49261898"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Oluşturur bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım bildirimi. A [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtımı için benzersiz bir kimliği tanımlayarak dağıtım bildirimini bir uygulama dağıtımını açıklar, tanımlayıcı dağıtım özellikleri yükleme veya uygulama belirtme çevrimiçi modu gibi ayarları ve konumları, güncelleştirme ve ilgili [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama bildirimi.  
  
## <a name="parameters"></a>Parametreler  
 Parametreler için aşağıdaki tabloda açıklanmıştır `GenerateDeploymentManifest` görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AssemblyName`|İsteğe bağlı `String` parametresi.<br /><br /> Belirtir `Name` oluşturulan bildirim için derlemenin kimliğinin alan. Bu parametre belirtilmemişse, ad alanından algılanır `EntryPoint` veya `InputManifest` parametreleri. Ad gösterilemiyorsa görev bir hata oluşturur.|  
|`AssemblyVersion`|İsteğe bağlı `String` parametresi.<br /><br /> Belirtir `Version` oluşturulan bildirim için derlemenin kimliğinin alan. Bu parametre belirtilmezse görev "1.0.0.0" değerini kullanır.|  
|`CreateDesktopShortcut`|İsteğe bağlı `Boolean` parametresi.<br /><br /> TRUE ise, simge ClickOnce uygulaması yüklendiği sırada masaüstünde oluşturulur.|  
|`DeploymentUrl`|İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın güncelleştirme konumunu belirtir. Bu parametre belirtilmemişse, hiçbir güncelleştirme konumu uygulama için tanımlanır. Ancak, varsa `UpdateEnabled` parametresi `true`, güncelleştirme konumu belirtilmelidir. Belirtilen değer, tam bir URL veya UNC yolu olmalıdır.|  
|`Description`|İsteğe bağlı `String` parametresi.<br /><br /> Uygulama için isteğe bağlı bir açıklama belirtir.|  
|`DisallowUrlActivation`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Bir URL üzerinden açıldığında uygulama otomatik olarak çalıştırılıp çalıştırılmayacağını belirtir. Bu parametre `true`, uygulama yalnızca Başlat menüsünden başlatılabilir. Bu parametrenin varsayılan değeri `false`. Bu giriş, yalnızca geçerli `Install` parametre değeri `true`.|  
|`EntryPoint`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Üretilen bildirim derlemesi için giriş noktasını belirtir. İçin bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım bildirimi, bu giriş belirtir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama bildirimi.<br /><br /> İçinde [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)], [GenerateApplicationManifest görevi](../msbuild/generateapplicationmanifest-task.md) gerekli bir `EntryPoint` bir uygulama bildirimi oluşturmak için. (Derleme veya yerel bildirimler gerektirmez bir `EntryPoint`.) Bu gereksinim, şu yapı hatasıyla zorlandı: "MSB3185: giriş noktası için bildirimi belirtilmedi."<br /><br /> [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Bu hata kesmez olduğunda `EntryPoint` görev parametresi belirtilmedi. Bunun yerine, \<customHostSpecified > etiketi, bir alt öğesi olarak eklenir \<entryPoint > etiketinin, örneğin:<br /><br /> `<entryPoint xmlns="urn:schemas-`<br /><br /> `microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> Aşağıdaki adımları kullanarak, uygulama bildirimine DLL bağımlılıkları ekleyebilirsiniz:<br /><br /> 1.  Bir çağrı ile derleme başvurularını çözümlemek <xref:Microsoft.Build.Tasks.ResolveAssemblyReference>.<br />2.  Önceki görev ve derleme çıkışını geçirmek için <xref:Microsoft.Build.Tasks.ResolveManifestFiles>.<br />3.  Kullanarak bağımlılıkları geçirin `Dependencies` parametresi <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>.|  
|`ErrorReportUrl`|İsteğe bağlı [String] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) parametre.<br /><br /> ClickOnce yüklemeleri sırasında iletişim kutularında görüntülenen Web sayfasının URL'sini belirtir.|  
|`InputManifest`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Bildirim oluşturucu için bir temel olarak hizmet verecek girdi XML belgesini belirtir. Bu, çıktı bildiriminde yansıtılmasını özel bildirim tanımları gibi yapılandırılmış verilerin sağlar. XML belgesi kök öğesi asmv1 ad alanı içerisinde bir derleme düğümü olmalıdır.|  
|`Install`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Uygulamanın yüklü bir uygulama ya da yalnızca çevrimiçi bir uygulama olup olmadığını belirtir. Bu parametre `true`, uygulama kullanıcının Başlat menüsüne yüklenir ve Program Ekle veya Kaldır iletişim kutusu kullanılarak kaldırılabilir. Bu parametre `false`, uygulama bir Web sayfasından çevrimiçi kullanılması amaçlanmıştır. Bu parametrenin varsayılan değeri `true`.|  
|`MapFileExtensions`|İsteğe bağlı `Boolean` parametresi.<br /><br /> .Deploy dosya adı uzantısı eşlemesinin kullanılıp kullanılmayacağını belirtir. Bu parametre `true`, her program dosyası .deploy dosya adı uzantısıyla yayımlanır. Bu seçenek, Web sunucusu güvenliği etkinleştirme engelinin kaldırılması gerekir ve dosya adı uzantıları sayısını sınırlamak kullanışlıdır [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama dağıtımı. Bu parametrenin varsayılan değeri `false`.|  
|`MaxTargetPath`|İsteğe bağlı `String` parametresi.<br /><br /> İçinde bir dosya yolunun uzunluğu izin verilen üst sınırı belirtir bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama dağıtımı. Bu parametre belirtilmişse uygulamadaki her dosya yolunun uzunluğu bu limite karşı denetlenir. Sınırı aşan öğeler bir yapı uyarısına neden olur. Bu giriş belirtilmezse veya sıfırsa hiçbir denetim yapılmaz.|  
|`MinimumRequiredVersion`|İsteğe bağlı `String` parametresi.<br /><br /> Kullanıcının güncelleştirmeyi atlayıp atlayamayacağını belirtir. Kullanıcının gerekli en düşük'dan küçük bir sürüm varsa, o güncelleştirmeyi atlama seçeneği yoktur. Bu giriş yalnızca olduğunda geçerlidir değerini `Install` parametresi `true`.|  
|`OutputManifest`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Oluşturulan çıktı bildirim dosyasının adını belirtir. Bu parametre belirtilmemişse, çıkış dosyasının adı oluşturulan bildirim kimliğinden gösterilir.|  
|`Platform`|İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın hedef platformu belirtir. Bu parametre aşağıdaki değerleri içerebilir:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Varsayılan değer `AnyCPU` şeklindedir.|  
|`Product`|İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın adını belirtir. Bu parametre belirtilmemişse, ad oluşturulan bildirim kimliğinden gösterilir. Bu ad Başlat menüsündeki kısayol adı için kullanılır ve Program Ekle veya Kaldır iletişim kutusunda görünen adın bir parçasıdır.|  
|`Publisher`|İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın yayımcısını belirtir. Bu parametre belirtilmemişse, ad kayıtlı kullanıcıdan veya oluşturulan bildirim kimliği algılanır. Bu ad Başlat menüsündeki klasör adı için kullanılır ve Program Ekle veya Kaldır iletişim kutusunda görünen adın bir parçasıdır.|  
|`SuiteNamel`|İsteğe bağlı `String` parametresi.<br /><br /> Başlat menüsünde uygulama ClickOnce dağıtımından sonra bulunduğu klasörün adını belirtir.|  
|`SupportUrl`|İsteğe bağlı `String` parametresi.<br /><br /> Uygulama için Program Ekle veya Kaldır iletişim kutusunda görünen bağlantıyı belirtir. Belirtilen değer, tam bir URL veya UNC yolu olmalıdır.|  
|`TargetCulture`|İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın kültürünü tanıtır ve belirten `Language` oluşturulan bildirim için derlemenin kimliğinin alan. Bu parametre belirtilmemişse uygulamanın kültür sabiti olduğu varsayılır.|  
|`TrustUrlParameters`|İsteğe bağlı `Boolean` parametresi.<br /><br /> URL sorgu dizesi parametreleri uygulamaya kullandırılıp kullandırılmayacağını belirtir. Bu parametrenin varsayılan değeri `false`, gösteren parametreleri uygulamaya kullanılabilir olmayacak.|  
|`UpdateEnabled`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Uygulama güncelleştirmeleri için etkin olup olmadığını gösterir. Bu parametrenin varsayılan değeri `false`. Bu parametre yalnızca olduğunda geçerlidir değerini `Install` parametresi `true`.|  
|`UpdateInterval`|İsteğe bağlı `Int32` parametresi.<br /><br /> Uygulama için güncelleştirme aralığını belirtir. Bu parametrenin varsayılan değeri sıfırdır. Bu parametre yalnızca olduğunda geçerlidir değerlerini `Install` ve `UpdateEnabled` parametrelerinin `true`.|  
|`UpdateMode`|İsteğe bağlı `String` parametresi.<br /><br /> Uygulama başlatıldığında veya uygulama arka planda çalışan önce güncelleştirmeleri ön planda denetlenip denetlenmeyeceğini belirtir. Bu parametre aşağıdaki değerleri içerebilir:<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> Bu parametrenin varsayılan değeri `Background`. Bu parametre yalnızca olduğunda geçerlidir değerlerini `Install` ve `UpdateEnabled` parametrelerinin `true`.|  
|`UpdateUnit`|İsteğe bağlı `String` parametresi.<br /><br /> Birimlerini belirtir `UpdateInterval` parametresi. Bu parametre aşağıdaki değerleri içerebilir:<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Bu parametre yalnızca olduğunda geçerlidir değerlerini `Install` ve `UpdateEnabled` parametrelerinin `true`.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.GenerateManifestBase> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.Task> sınıfı. Görev sınıfı parametrelerinin bir listesi için bkz. [görev temel sınıf](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [GenerateApplicationManifest görevi](../msbuild/generateapplicationmanifest-task.md)   
 [SignFile görevi](../msbuild/signfile-task.md)   
 [Görev Başvurusu](../msbuild/msbuild-task-reference.md)



