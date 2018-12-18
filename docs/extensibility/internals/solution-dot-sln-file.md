---
title: Çözüm (. Sln) dosyası | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f01657d1053f2172f421bf6e265aa836f930c438
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49864939"
---
# <a name="solution-sln-file"></a>Çözüm (.Sln) Dosyası
Çözüm Projeleri Visual Studio'da düzenleme yapısıdır. Çözüm projeleri (metin tabanlı, paylaşılan) .sln ve .suo (ikili, kullanıcıya özel bir çözüm seçenekleri) dosyaları için durum bilgilerini tutar. .Suo dosyaları hakkında daha fazla bilgi için bkz. [çözüm kullanıcı seçenekleri (. Suo) dosyası](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 Ortam, VSPackage .sln dosyasında başvurulan bir sonucu olarak yüklenirse çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> .sln dosyasını okuma için.  
  
 .Sln dosyasını bulup ad-değer parametreleri kalıcı veri ve ' % s'projesinin başvurduğu VSPackage yükleme ortamı kullanan metin tabanlı bilgiler içerir. Bir çözüm bir kullanıcı oturum açtığında, ortam aracılığıyla döngüleri `preSolution`, `Project`, ve `postSolution` çözümü yüklemek için .sln dosyasında bilgilerini çözüm projeleri ve kalıcı bilgileri çözüme eklenmiş.  
  
 Her proje dosyası, bu proje öğelerini bir hiyerarşiyle doldurmak için ortamı tarafından okunur ek bilgiler içerir. Hiyerarşi veri kalıcılığı, proje tarafından denetlenir; Bunu yapmayı tercih ederseniz proje bilgileri .sln dosyasına kasıtlı olarak yazabilirsiniz, ancak veri .sln dosyasında normalde depolanmaz. Kalıcılık için ilgili daha fazla bilgi için bkz. [proje kalıcılığı](../../extensibility/internals/project-persistence.md) ve [açma ve kaydetme proje öğeleri](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="solution-file-contents"></a>Çözüm dosyası içeriği  
 .Sln dosyasını aşağıdaki kodda gösterildiği gibi birkaç bölümden oluşur.  
  
```  
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
EndProject  
Global  
  GlobalSection(SolutionNotes) = postSolution  
  EndGlobalSection  
  GlobalSection(SolutionConfiguration) = preSolution  
       ConfigName.0 = Debug  
       ConfigName.1 = Release  
  EndGlobalSection  
  GlobalSection(ProjectDependencies) = postSolution  
  EndGlobalSection  
  GlobalSection(ProjectConfiguration) = postSolution  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86  
  EndGlobalSection  
  GlobalSection(ExtensibilityGlobals) = postSolution  
  EndGlobalSection  
  GlobalSection(ExtensibilityAddIns) = postSolution  
  EndGlobalSection  
EndGlobal  
```  
  
 Bir çözümü yüklemek için aşağıdaki görev dizisi ortamı gerçekleştirir.  
  
1. Ortam genel bölümünü .sln dosyasını okur ve işaretlenmiş tüm bölümleri işleyen `preSolution`. Bu durumda, bir ifade vardır:  
  
   ```  
   GlobalSection(SolutionConfiguration) = preSolution  
        ConfigName.0 = Debug  
        ConfigName.1 = Release  
   ```  
  
    Zaman ortam okur `GlobalSection('name')` etiketi, adıyla eşleşir Vspackage'a kayıt defterini kullanarak. Kayıt defteri anahtarı adı bulunmalıdır [HKLM\\< Uygulama kimliği kayıt defteri kökü\>\SolutionPersistence\AggregateGUIDs]. Paket GUID'si (REG_SZ) girişleri yazdı VSPackage'ı, anahtarları varsayılan değerdir.  
  
2. VSPackage çağrıları ortam yükler `QueryInterface` VSPackage için üzerinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> arabirimi ve çağrılarını <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> biçimde Vspackage'i verileri depolayabilirsiniz bölümünde verilerle yöntemi. Ortam her biri için bu işlemi yineler `preSolution` bölümü.  
  
3. Ortamı proje kalıcılığı blokları boyunca yinelenir. Bu durumda, bir proje yok.  
  
   ```  
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
   EndProject  
   ```  
  
    Bu ifade, benzersiz GUID proje ve proje türü GUID içerir. Bu bilgiler proje dosyası veya çözüme ait dosyaları bulmak için ortamı tarafından kullanılır ve VSPackage'ı her proje için gerekli. GUID geçirilen proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> projeyle ilgili belirli VSPackage'ı yüklemek için ardından projeyi VSPackage'ı tarafından yüklenir. Bu durumda, bu proje için yüklenen VSPackage'ı Visual Basic ' dir.  
  
    Böylece iş çözümdeki diğer projelerin gerektiği şekilde erişilebilir her proje bir benzersiz proje örnek kimliği kalıcı hale getirebilirsiniz. İdeal olarak, çözüm ve projeler kaynak kod denetimi altında ise, yolun projeye çözüme göreli olmalıdır. Çözüm ilk yüklendiğinde, proje dosyalarını kullanıcının makinesine olamaz. Proje dosyasını çözüm dosyasına göreli sunucusunda depolanan sağlayarak, proje dosyası bulundu ve kullanıcının makineye kopyalandı görece basit. Bunu daha sonra kopyalar ve proje için gerekli dosyaları geri kalanı yükler.  
  
4. .Sln dosyasını Proje bölümünde yer alan bilgileri bağlı olarak, ortam her proje dosyası yükler. Proje, ardından Proje hiyerarşisi doldurma ve tüm iç içe projeler yükleniyor sorumludur.  
  
5. Tüm bölümlerini .sln dosyası işlendikten sonra çözüm Çözüm Gezgini'nde görüntülenir ve kullanıcı tarafından değiştirilmek üzere ayrıldığı için hazırdır.  
  
   Herhangi bir proje çözümde uygulayan VSPackage'ı yüklemek, başarısız olursa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> yöntemi çağrılır ve her bir proje çözümde, yapmış yükleme sırasında Değişiklikleri yoksaymak için bir fırsat verildi. Ayrıştırma hataları oluşursa, mümkün olduğunca fazla bilgi ile çözüm dosyalarını korunur ve ortam çözüm bozuk kullanıcıya uyarı iletişim kutusu görüntüler.  
  
   Çözüm kaydedildi ya da kapatıldığında <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> yöntemi çağrılır ve .sln dosyasına girilmesi gerekir çözüme değişiklikler yapılıp yapılmadığını görmek için hiyerarşi geçirilir. İçin geçirilen bir null değer `QuerySaveSolutionProps` içinde <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>, çözüm bilgilerinin kalıcı olduğunu gösterir. Değer null değilse, kalıcı işaretçisi tarafından belirlenen, belirli bir projenin bilgilerdir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> arabirimi.  
  
   Kaydedilecek, bilgiler varsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> arabirim işaretçisi volat <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> yöntemi. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> Yöntemi ad-değer çiftlerinden almak için ortamı tarafından sonra çağrılır `IPropertyBag` arabirim ve .sln dosyasına yazmak.  
  
   `SaveSolutionProps` ve `WriteSolutionProps` nesneleri çağrılır yinelemeli olarak gelen kaydedilecek bilgi almak için ortamı tarafından `IPropertyBag` tüm değişiklikleri .sln dosyasına girilene kadar arabirim. Bu şekilde, bilgileri çözüm ve çözüm kullanılabilir sonraki açılışında ile kalıcı olmasını sağlamak.  
  
   Yüklenen her VSPackage .sln dosyasına kaydetmek için herhangi bir şey olup olmadığını öğrenmek için numaralandırılmış alan şeklinde. Yalnızca kayıt defteri anahtarlarını sorgulanır yükleme sırasında dir. Çözüm kaydedildiğinde bellekte çünkü ortam tüm yüklenen paketler hakkında bilir.  
  
   .Sln dosyasını girişler yalnızca `preSolution` ve `postSolution` bölümler. Benzer bölüm yok .suo dosyasında çözüm düzgün bir şekilde yüklemek için bu bilgiye sonun. .Suo dosya paylaşılan ya da kaynak kodu denetimi altında yerleştirilmiş amaçlanmayan özel notları gibi kullanıcıya özgü seçenekleri içerir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Çözüm kullanıcı seçenekleri (. Suo) dosyası](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Çözümler](../../extensibility/internals/solutions.md)