---
title: Özel projelerini yükseltme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading project systems
- projects [Visual Studio SDK], upgrading
- project system upgrades [Visual Studio]
ms.assetid: 262ada44-7689-44d8-bacb-9c6d33834d4e
caps.latest.revision: 11
manager: douge
ms.openlocfilehash: 12b99770a7ab884e077ad6ba051a35d6e5316a49
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844685"
---
# <a name="upgrading-custom-projects"></a>Özel projelerini yükseltme
Değiştirirseniz, ürünün farklı Visual Studio sürümleri arasında proje dosyasındaki bilgileri kalıcı sonra proje dosyası eski sürümden yeni sürüme yükseltme desteklemeniz gerekiyor. Katılmak izin veren yükseltmeyi desteklediği için **Visual Studio Dönüştürme Sihirbazı**, uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> arabirimi. Bu arabirim, kopyalama yükseltmek için yalnızca mekanizması kullanılabilir içerir. Proje yükseltme açılır çözümün bir parçası olarak gerçekleşir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Arabirimi proje fabrikası tarafından uygulanan ya da proje fabrikadan elde edilebilir en az olmalıdır.  
  
 Kullanan eski mekanizması <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> arabirimi hala desteklenmektedir, ancak kavramsal olarak proje sistemi proje açıkken bir parçası olarak yükseltir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Arabirimi tarafından bu nedenle çağrılır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] olsa bile ortamı <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> arabirimi adlı veya uygulandığında. Bu yaklaşım kullanmanıza olanak tanır <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> yerinde (muhtemelen en yeni konum) yapılacak işleri geri kalanı tarafından temsilci kopyalama uygulamak ve yalnızca yükseltme bölümlerini proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> arabirimi.  
  
 Bir örnek uygulaması için <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, bkz: [VSSDK örnekleri](../misc/vssdk-samples.md).  
  
 Aşağıdaki senaryolarda, proje yükseltmeleriyle ortaya çıkar:  
  
-   Dosyayı proje destekleyebileceğinden daha yeni bir biçimde varsa, bunu bildiren bir hata döndürmelidir. Bu olduğunu varsayar, ürünün eski sürümü — Örneğin, Visual Studio .NET 2003 — sürümü denetlemek için kod içerir.  
  
-   Varsa <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> bayrağı belirtilen <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> yöntemi, yükseltme gittiğini projenin açılış öncesinde yerinde yükseltme olarak uygulanabilir.  
  
-   Varsa <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> bayrağı belirtilen <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> yükseltme yöntemi, bir kopyasını yükseltme olarak uygulanır.  
  
-   Varsa <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> bayrağı belirtilen <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> çağrısında verilmişse, kullanıcı ortamı tarafından proje açıldıktan sonra proje dosyası, yerinde yükseltme yükseltmek için çalışandan. Örneğin, ortam çözümü daha eski bir sürümünü kullanıcı oturum açtığında yükseltmek için kullanıcıya sorar.  
  
-   Varsa <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> bayrağı belirtilmiş değil <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> çağrısında verilmişse, proje dosyası yükseltme kullanıcıdan gerekir.  
  
     Bir örnek yükseltme istemi iletisi aşağıda verilmiştir:  
  
     "'%1' projesi Visual Studio'nun daha eski bir sürümüyle oluşturuldu. Visual Studio'nun bu sürümü ile açın, Visual Studio'nun eski sürümleriyle açmanız mümkün olmayabilir. Devam etmek ve bu projeyi açmak istiyor musunuz?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>IVsProjectUpgradeViaFactory uygulamak için  
  
1.  Yöntemi uygulamak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> arabirimi, özellikle <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> proje fabrikası uygulamanızda yöntemi veya uygulamaları proje fabrikası uygulamadan çağrılabilir.  
  
2.  Açma çözümün bir parçası olarak bir yerinde yükseltme gerçekleştirmek istiyorsanız, bayrak sağlayın <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> olarak `VSPUVF_FLAGS` parametresinde, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> uygulaması.  
  
3.  Açma çözümün bir parçası olarak bir yerinde yükseltme gerçekleştirmek istiyorsanız, bayrak sağlayın <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> olarak `VSPUVF_FLAGS` parametresinde, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> uygulaması.  
  
4.  Her iki adımları için 2 ve 3 gerçek dosyayı yükseltme adımları kullanarak, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, açıklandığı gibi uygulanabilir "uygulama `IVsProjectUpgade`" aşağıda bölümünde veya gerçek dosya yükseltme devredebilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
5.  Yöntemlerini kullanan <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> iletileri Visual Studio Geçiş Sihirbazı'nı kullanarak kullanıcı için ilgili yükseltme sonrası.  
  
6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> arabirimi, her türden proje yükseltmesinin bir parçası gerçekleşmesi dosya yükseltmeyi uygulamak için kullanılır. Bu arabirim, gelen çağrılmaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, ancak proje sistemi, ancak ana proje sisteminin bir parçası olan dosyaları yükseltmek için bir mekanizma doğrudan haberdar olmayabilir olarak sağlanır. Örneğin, dosyaları ve özelliklerini, proje sistemi açıklarsınız aynı geliştirme ekibi tarafından işlenmez derleyici ilgili değilse bu durum meydana gelebilecek.  
  
## <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade uygulama  
 Proje sisteminizi uyguluyorsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> yalnızca katılabilmesi değil **Visual Studio Dönüştürme Sihirbazı**. Ancak, uygulamanız bile <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> arabirimi, dosya yükseltme hala temsil edebilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> uygulaması.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>IVsProjectUpgrade uygulamak için  
  
1. Bir kullanıcı bir projeyi açmayı denediğinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> proje açıldıktan sonra başka bir kullanıcı önce projeye eylemin alınmasından yöntemi ortamı tarafından çağrılır. Kullanıcı zaten çözümünü Yükselt istenirse sonra <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> bayrağı geçirilir `grfUpgradeFlags` parametresi. Kullanıcı bir proje doğrudan böyle açarsa olarak kullanarak **Varolan Proje Ekle** komutu, ardından <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> bayrağı geçirilmedi ve projeyi yükseltmek için kullanıcıdan gerekiyor.  
  
2. Yanıt olarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> çağrı, proje gerekir değerlendirmek için proje dosyasını yükseltilmiş olup olmadığını. Proje, proje türü yeni bir sürüme yükseltmeniz gerekmez. sonra yalnızca döndürebilir <xref:Microsoft.VisualStudio.VSConstants.S_OK> bayrağı.  
  
3. Projenin proje türü yeni bir sürüme yükseltme gerekiyor sonra proje dosyasını çağırarak değiştirilip değiştirilemeyeceğini belirlemelidir <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> yöntemi ve değeri geçirme <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> için `rgfQueryEdit` parametresi. Proje, ardından aşağıdakileri yapması gerekir:  
  
   -   Varsa `VSQueryEditResult` döndürülen değer `pfEditCanceled` parametresi <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>, sonra da proje dosyası yazılabilir olduğundan yükseltme devam.  
  
   -   Varsa `VSQueryEditResult` döndürülen değer `pfEditCanceled` parametresi <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> ve `VSQueryEditResult` değerine sahip <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit kümesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> kullanıcıların izinleri kendilerini sorun gidermeniz gerekir çünkü hatası döndürmesi gerekir. Proje sonra aşağıdakileri yapmanız gerekir:  
  
        Çağırarak hatayı kullanıcıya bildirin <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>. ve dönüş <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> hata koduna <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
   -   Varsa `VSQueryEditResult` değer <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> ve `VSQueryEditResultFlags` değerine sahip <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> biti ayarlanmamış, proje dosyasını çağırarak denetlenmesi gerektiğini sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...).  
  
4. Varsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> dosya kullanıma alınması ve alınması için en son sürümü proje dosyası çağrıda neden olur ve ardından Proje kaldırılıp yeniden yüklenene. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Yöntemi proje başka bir örneği oluşturulduktan sonra tekrar çağrılır. Bu ikinci çağrıda, proje dosyası yazılabilir diske; projeyi önceki biçiminde proje dosyasının bir kopyasını kaydedin önerilir bir. ESKİ uzantısı, yükseltme gerekli değişiklikleri yapın ve yeni biçiminde proje dosyasını kaydedin. Yükseltme işleminin herhangi bir bölümü başarısız olursa yeniden yöntemi hata döndürerek belirtmelidir <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>. Bu proje, Çözüm Gezgini'nde kaldırılmasına neden olur.  
  
    Durumda ortamda oluşan tam süreci anlamak önemlidir çağrısı <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (sadece rapor değerini belirterek) döner <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> ve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bayrakları.  
  
5. Kullanıcı, proje dosyası açmaya çalışır.  
  
6. Ortam çağrıları, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> uygulaması.  
  
7. Varsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> döndürür `true`, sonra ortamı çağrıları, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> uygulaması.  
  
8. Ortam çağrıları, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> dosyasını açın ve örneğin, project nesnesini başlatmak için Project1 uygulaması.  
  
9. Ortam çağrıları, `IVsProjectUpgrade::UpgradeProject` proje dosyasının yükseltilmesi gerekip gerekmediğini belirlemek için uygulama.  
  
10. Çağırmanızı <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ve bir değer geçirmek <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> için `rgfQueryEdit` parametresi.  
  
11. Ortam döndürür <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> için `VSQueryEditResult` ve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bitinin ayarlanmasıdır `VSQueryEditResultFlags`.  
  
12. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Uygulama çağrıları `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>).  
  
    Bu çağrı bir kopyasını kullanıma alınması için proje dosyanızı neden olabilir ve proje dosyanızı yeniden yüklemek için bir gereksinim yanı sıra en son sürümü alınır. Bu noktada, ikisinden biri gerçekleşir:  
  
- Ardından, kendi proje yeniden işlemek, ortam çağırır, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT) uygulama. Bu çağrı aldığında, projenize (Project1) ilk örneğinin yeniden yüklemeniz ve proje dosyanız yükseltmeye devam edin. Ortam döndürürse, kendi proje yeniden işlemek bilir `true` için <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>).  
  
- Kendi proje yeniden işlememesi sonra iade ettiğiniz `false` için <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>). Bu durumda, önce <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>([QEF_ForceEdit_NoPrompting](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True), [QEF_DisallowInMemoryEdits](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True),) döndürür, ortam olarak başka bir yeni, örneğin, Project2, projenize bir örneğini oluşturur aşağıdaki gibidir:  
  
  1.  Ortam çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> ilk proje nesneniz üzerinde Project1, bu nedenle etkin olmayan bir durumda bu nesne yerleştirme.  
  
  2.  Ortam çağrıları, `IVsProjectFactory::CreateProject` Project2 projenizi ikinci bir örneğini oluşturmak için uygulama.  
  
  3.  Ortam çağrıları, `IPersistFileFormat::Load` uygulama dosyasını açın ve Project2 ikinci project nesnesini başlatır.  
  
  4.  Ortam çağrıları `IVsProjectUpgrade::UpgradeProject` project nesnesini yükseltilmesi olup olmadığını belirlemek ikinci bir kez. Ancak, bu çağrı yeni, ikinci projesi Project2 örneğini yapılır. Bu çözümde açık projedir.  
  
      > [!NOTE]
      >  İlk projenizi, Project1, etkin olmayan duruma yerleştirilir ve ardından döndürmesi gereken örneğinde <xref:Microsoft.VisualStudio.VSConstants.S_OK> ilk çağrısından, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> uygulaması. Bkz: [temel proje](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) uygulaması için `IVsProjectUpgrade::UpgradeProject`.  
  
  5.  Çağırmanızı <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ve bir değer geçirmek <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> için `rgfQueryEdit` parametresi.  
  
  6.  Ortam döndürür <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> ve proje dosyasının yazılabilir olduğundan yükseltme devam.  
  
  Yükseltme başarısız olursa, dönüş <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> gelen `IVsProjectUpgrade::UpgradeProject`. Yükseltme gerekli olan veya yükseltme, kabul için seçtiğiniz `IVsProjectUpgrade::UpgradeProject` bir İşlemsiz çağırın. Size dönüş yaparsa <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>, çözüm projeniz için bir yer tutucu düğümünün eklenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Dönüştürme Sihirbazı](http://msdn.microsoft.com/en-us/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Proje öğeleri yükseltme](../misc/upgrading-project-items.md)   
 [Projeler](../extensibility/internals/projects.md)