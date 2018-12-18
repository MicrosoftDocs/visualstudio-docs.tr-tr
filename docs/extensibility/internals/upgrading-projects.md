---
title: Projeleri yükseltme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea5c29819d0035e45f97122fd108ea1f51d60806
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057540"
---
# <a name="upgrading-projects"></a>Projeleri Yükseltme

Visual Studio sürümünden sonraki projesi modeli değişiklikler, daha yeni sürümüne çalıştırabilmeniz için projeler ve çözümler yükseltilmesi gerektirebilir. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Yükseltme desteği kendi projelerinde uygulamak için kullanılan arabirimleri sağlar.

## <a name="upgrade-strategies"></a>Yükseltme stratejileri

Yükseltme desteklemek için proje sistem uygulamanızı tanımlamak ve bir yükseltme stratejisini uygula. Stratejinizi belirlemede yan yana (SxS) yedekleme, kopya yedekleme ya da her ikisini de desteklemek seçebilirsiniz.

-   Proje, uygun dosya adı sonek, örneğin, ekleme "eski" yerinde yükseltme gereken dosyaları kopyalar SxS yedekleme anlamına gelir.

-   Kopya yedekleme proje tüm proje öğeleri kullanıcı tarafından sağlanan bir yedekleme konumuna kopyalar anlamına gelir. Özgün proje konumdaki ilgili dosyaları sonra yükseltilir.

## <a name="how-upgrade-works"></a>Yükseltme nasıl çalışır

Visual Studio daha önceki bir sürümünde oluşturulan bir çözüm daha yeni bir sürümünde açıldığında, IDE yükseltilmesi gerekip gerekmediğini belirlemek için çözüm dosyasını denetler. Yükseltme, gerekirse **Yükseltme Sihirbazı** kullanıcı yükseltme sürecinde size yol için otomatik olarak başlatılır.

Bir çözümü yükseltme gerektiğinde, her proje Fabrika yükseltme stratejisini için sorgular. Proje Fabrika kopya yedekleme veya SxS yedekleme destekleyip desteklemediğini stratejisi belirler. Bilgiler gönderilir **Yükseltme Sihirbazı**, yedekleme için gerekli bilgileri toplar ve kullanıcıya uygun seçenekleri sunar.

### <a name="multi-project-solutions"></a>Birden çok proje çözümü

Varsa bir çözüm birden çok proje içerir ve yükseltme stratejileri farklı gibi yalnızca SxS yedekleme destekleyen C++ projesi olduğunda ve yalnızca kopya yedeği destekleyen bir Web projesi, proje fabrikalarını yükseltme stratejisini anlaşmaları gerekir.

Her proje Fabrika için çözüm sorgular <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Daha sonra çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> genel proje dosyalarını yükseltme gerekip gerekmediğini görmek için ve desteklenen yükseltme stratejileri belirlemek için. **Yükseltme Sihirbazı** sonra çağrılır.

Kullanıcı, sihirbaz tamamlandıktan sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> gerçek yükseltme gerçekleştirmek için her proje Fabrika adı verilir. Yedekleme kolaylaştırmak için IVsProjectUpgradeViaFactory yöntemleri sunar <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> yükseltme işleminin ayrıntılarını oturum hizmeti. Bu hizmet önbelleğe alınamaz.

Tüm ilgili genel dosyaları güncelleştirdikten sonra bir proje oluşturmak her proje Fabrika seçebilirsiniz. Proje uygulama desteklemelidir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Yöntemi tüm ilgili proje öğeleri yükseltmek için sonra çağrılır.

> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Yöntemi SVsUpgradeLogger hizmet sağlamaz. Bu hizmet çağırarak elde edilebilir <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.

## <a name="best-practices"></a>En İyi Yöntemler

Kullanım <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> hizmeti, bir dosya düzenleme önce düzenleyebilirsiniz ve kaydetmeden önce kaydedebilirsiniz, kontrol edin. Bu yedekleme yardımcı olur ve yükseltme uygulamaları işlemek proje dosyalarını kaynak denetimi altında yetersiz izinler ve benzeri dosyaları.

Kullanım <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> hizmet yedekleme tüm aşamalarında ve başarı veya başarısızlık yükseltme işleminin hakkında bilgi sağlamak için yükseltin.

Yedekleme ve projeleri yükseltme hakkında daha fazla bilgi için yorumlar için IVsProjectUpgrade içinde vsshell2.idl bakın.

## <a name="upgrading-custom-projects"></a> Özel projelerini yükseltme

Değiştirirseniz ürününüzü farklı Visual Studio sürümleri arasında proje dosyasındaki bilgileri kalıcı sonra proje dosyanızı eski en yeni sürüme yükseltme desteklemesi gerekir. ' Na katılmak izin veren yükseltme desteklemek için **Visual Studio Dönüştürme Sihirbazı**, uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> arabirimi. Bu arabirim kopyalama yükseltme yalnızca mekanizması kullanılabilir içerir. Açılır çözümün bir parçası olarak yükseltme projesi olur. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Arabirimi proje fabrikası tarafından uygulanan veya en azından proje fabrikası'ndan elde edilebilir olmalıdır.

Kullanan eski mekanizması <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> arabirimi hala desteklenmektedir, ancak kavramsal olarak proje sistemini açık projenin bir parçası olarak yükseltir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Arabirimi tarafından olsa bile Visual Studio ortamında bu nedenle adlı <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> arabirimi adlı ya da uygulanır. Bu yaklaşım sayesinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> yerinde (büyük olasılıkla yeni konumda) yapılacak işleri geri kalanı tarafından temsilci kopyalama uygulamak ve yükseltme yalnızca bölümlerini proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> arabirimi.

Bir örnek uygulama için <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, bkz: [VSSDK örnekleri](http://aka.ms/vs2015sdksamples).

Aşağıdaki senaryolar ile proje yükseltmelerinde ortaya:

-   Proje destekleyebileceğinden daha yeni bir biçiminin dosyasıysa bu bildiren bir hata döndürmelidir. Bu, ürününüzü eski sürümü sürümü denetlemek için kod içerdiğini varsayar.

-   Varsa <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> bayrağı belirtilen <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> yöntemi, yükseltme proje açma önce yerinde yükseltme olarak uygulanacak olduğuna.

-   Varsa <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> bayrağı belirtilen <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> yöntemi, yükseltme, bir kopyasını yükseltme olarak uygulanır.

-   Varsa <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> bayrağı belirtilen <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> kullanıcı ortamı tarafından proje açıldıktan sonra yerinde yükseltme proje dosyası yükseltme istenir sonra çağırın. Örneğin, ortam çözümü daha eski bir sürümü kullanıcı oturum açtığında yükseltmek için kullanıcıya sorar.

-   Varsa <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> bayrağı belirtilmiş değil <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> proje dosyası yükseltme kullanıcıdan gerekir sonra çağırın.

     Bir örnek yükseltme komut istemi iletisi şudur:

     "'%1' proje Visual Studio'nun daha eski bir sürümü ile oluşturuldu. Visual Studio'nun bu sürümü açarsanız, Visual Studio'nun daha eski sürümleri açabilmelisiniz olmayabilir. Devam etmek ve bu projeyi açmak istiyor musunuz?"

### <a name="to-implement-ivsprojectupgradeviafactory"></a>IVsProjectUpgradeViaFactory uygulamak için

1.  Yöntemi uygulamak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> arabirimi, özellikle <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> proje Fabrika uygulamanızda yöntemi veya uygulamaları proje Fabrika uygulamanızı çağrılabilen olun.

2.  Açma çözümün bir parçası olarak bir yerinde yükseltme yapmak istiyorsanız, bayrağı tedarik <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> olarak `VSPUVF_FLAGS` parametresinde, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> uygulaması.

3.  Açma çözümün bir parçası olarak bir yerinde yükseltme yapmak istiyorsanız, bayrağı tedarik <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> olarak `VSPUVF_FLAGS` parametresinde, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> uygulaması.

4.  Her iki adımları için 2 ve 3 gerçek dosya yükseltme adımları kullanarak, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, açıklandığı gibi uygulanabilir "Implementing `IVsProjectUpgade`" aşağıda bölümünde veya gerçek dosya yükseltme devredebilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

5.  Yöntemlerini kullanın <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> iletileri Visual Studio Geçiş Sihirbazı'nı kullanarak kullanıcı için ilgili yükseltme sonrası.

6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> arabirim, her türlü proje yükseltmesinin bir parçası gerçekleşmesi dosya yükseltme uygulamak için kullanılır. Bu arabirim gelen çağrılmaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, ancak proje sistemi, ancak ana proje sisteminin bir parçası olan dosyaları yükseltmek için bir mekanizma doğrudan farkında olmayabilir olarak sağlanır. Örneğin, dosyaları ve özelliklerini proje sisteminin rest işleyen aynı geliştirme ekibi tarafından işlenmez derleyici ilgili değilse bu durum meydana gelebilecek.

### <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade uygulama

Proje sisteminizi uyguluyorsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> yalnızca katılabilmesi için değil **Visual Studio Dönüştürme Sihirbazı**. Ancak, uygulamanız olsa bile <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> arabirimi, dosya yükseltme hala temsilci <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> uygulaması.

#### <a name="to-implement-ivsprojectupgrade"></a>IVsProjectUpgrade uygulamak için

1.  Bir kullanıcı bir projeyi açmaya çalıştığında <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> yöntemi, ortamı tarafından çağrıldığında, proje açıldıktan sonra önce başka bir kullanıcı eylemi projede alınabilir. Kullanıcı zaten çözümünü Yükselt istenirse sonra <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> bayrağı geçirilir `grfUpgradeFlags` parametresi. Kullanıcı bir proje doğrudan, bu tür açarsa olarak kullanarak **Varolan Proje Ekle** komutu, sonra <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> bayrağı geçirilmedi ve projeyi yükseltmek için kullanıcıdan gerekiyor.

2.  Yanıt olarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> çağrısı, proje değerlendirmek proje dosyasını yükseltti olup olmadığını gerekir. Proje, proje türü yeni bir sürüme yükseltmeniz gerekmez. sonra yalnızca döndürebilir <xref:Microsoft.VisualStudio.VSConstants.S_OK> bayrağı.

3.  Proje proje türü yeni bir sürüme yükseltmek gereken sonra çağırarak proje dosyası değiştirilip değiştirilemeyeceğini belirlemelidir <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> yöntemi ve değeri geçirerek <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> için `rgfQueryEdit` parametresi. Proje sonra aşağıdakileri yapmanız gerekir:

    -   Varsa `VSQueryEditResult` döndürülen değer `pfEditCanceled` parametresi <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>, sonra da proje dosyası yazılabilir olduğundan yükseltme devam edebilirsiniz.

    -   Varsa `VSQueryEditResult` döndürülen değer `pfEditCanceled` parametresi <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> ve `VSQueryEditResult` değerine sahip <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> biti ayarlanmamış, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> kullanıcıların izinleri kendilerini sorun gidermeniz gerekir çünkü hatası döndürmesi gerekir. Proje sonra aşağıdakileri yapmanız gerekir:

         Çağırarak kullanıcıya hata raporu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> ve geri dönüp <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> hata koduna <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

    -   Varsa `VSQueryEditResult` değer <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> ve `VSQueryEditResultFlags` değerine sahip <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> biti ayarlanmamış, proje dosyası çağırarak denetlenmesi sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>,...).

4.  Varsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> proje dosyası çağrıda neden kullanıma dosyaya ve alınması için en son sürümü sonra projeyi yeniden ve kaldırıldığında. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Yöntemi proje başka bir örneği oluşturulduktan sonra tekrar çağrılır. Bu ikinci çağrıda proje dosyası yazılabilir diske; projeyi önceki biçiminde proje dosyasının bir kopyasını kaydedin önerilir bir. ESKİ uzantısı yükseltme kendi gerekli değişiklikleri yapın ve yeni bir biçimde proje dosyasını kaydedin. Herhangi bir kısmını yükseltme işlemi başarısız olursa yeniden yöntemi hatası döndürerek belirtmelidir <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>. Bu Çözüm Gezgini'nde boşaltılması için projeyi neden olur.

     Bu durumda ortamda oluşan tam süreci anlamak önemlidir çağrısı <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (sadece rapor değerini belirtme) yöntemi döndürür <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> ve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> bayrakları.

5.  Proje dosyasını açmak kullanıcı çalışır.

6.  Ortam çağrıları, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> uygulaması.

7.  Varsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> döndürür `true`, ardından ortamı çağrıları, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> uygulaması.

8.  Ortam çağrıları, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> dosyasını açın ve proje nesnesi, örneğin, başlatma için Project1 uygulama.

9. Ortam çağrıları, `IVsProjectUpgrade::UpgradeProject` proje dosyası yükseltilmesi gerekip gerekmediğini belirlemek için uygulama.

10. Çağırmanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ve bir değer geçirmek <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> için `rgfQueryEdit` parametresi.

11. Ortam döndürür <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> için `VSQueryEditResult` ve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> biti ayarlanmış `VSQueryEditResultFlags`.

12. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Uygulama çağrıları `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>).

Bu çağrı kullanıma alınması için proje dosyasını yeni bir kopyasını neden olabilir ve proje dosyanızı yeniden yüklemek için gerek yanı sıra en son sürümü, alınır. Bu noktada, iki özelliklerinden biri gerçekleşir:

-   Kendi projeyi yeniden işlemek, ortam çağrıları, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT) uygulaması. Bu çağrı aldığınızda, projenizin (Project1) ilk örneğini yeniden yükleyin ve proje dosyanızı yükseltmeye devam etmek. Ortamı, döndürürse kendi projeyi yeniden işlemek bilir `true` için <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>).

-   Kendi projeyi yeniden yükleme işlemini yapmayın sonra geri `false` için <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>). Bu durumda, önce <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) döndürür, ortam başka bir yeni bir örneğini projeniz, örneğin, Project2, aşağıdaki gibi oluşturur:

    1.  Ortam çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> ilk proje nesnenize, Project1, etkin olmayan bir durumda bu nedenle bu nesnenin yerleştirme.

    2.  Ortam çağrıları, `IVsProjectFactory::CreateProject` Project2 projenizi ikinci bir örneğini oluşturmak için uygulama.

    3.  Ortam çağrıları, `IPersistFileFormat::Load` dosyasını açın ve ikinci proje nesneyi Project2 başlatmak için uygulama.

    4.  Ortam çağrıları `IVsProjectUpgrade::UpgradeProject` proje nesnesi yükseltilmesi olup olmadığını belirlemek ikinci kez. Ancak, bu çağrı yeni, ikinci olarak, proje, Project2 örneğini yapılır. Bu çözümde açılan projesidir.

        > [!NOTE]
        > İlk projenizi, Project1, etkin olmayan duruma yerleştirilir ve ardından döndürmesi gerekir örnekteki <xref:Microsoft.VisualStudio.VSConstants.S_OK> ilk çağrıya gelen, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> uygulaması.

    5.  Çağırmanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ve bir değer geçirmek <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> için `rgfQueryEdit` parametresi.

    6.  Ortam döndürür <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> ve proje dosyası yazılabilir olduğundan yükseltme devam edebilirsiniz.

Yükseltme başarısız olursa, dönüş <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> gelen `IVsProjectUpgrade::UpgradeProject`. Hiçbir yükseltme gereklidir veya seçtiğiniz yükseltme, işle `IVsProjectUpgrade::UpgradeProject` no-op çağırın. Dönerseniz <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>, çözüm projeniz için bir yer tutucu düğümü eklenir.

## <a name="upgrading-project-items"></a>Proje öğeleri yükseltme

Ekleme veya öğeleri uygulamaz proje sistemleri içinde yönetmek, proje yükseltme işleminde katılmak gerekebilir. Crystal Reports proje sistemine eklenmiş bir öğenin bir örnektir.

Genellikle, proje öğesi Implementers başvuruları proje ve diğer proje özellikleri var. bir yükseltme karar vermek nelerdir bilmeleri gereken için proje zaten tam olarak oluşturulmuş ve yükseltilmiş faydalanabilir istiyorsunuz.

### <a name="to-get-the-project-upgrade-notification"></a>Proje yükseltme bildirim almak için

1.  Ayarlama <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> proje öğesi uygulamanızda bayrağı (vsshell80.idl içinde tanımlanmış). Visual Studio Kabuğu'nu proje sistemi yükseltme sürecinde olduğunu belirlediğinde, bu proje öğesi VSPackage otomatik yük neden olur.

2.  Öneri <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> aracılığıyla arabirim <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> yöntemi.

3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> Arabirimi proje sistem uygulaması yükseltme işlemlerini tamamladı ve yeni yükseltilen proje oluşturulduktan sonra tetiklenir. Senaryoya bağlı olarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> sonra arabirimi harekete <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> yöntemleri.

### <a name="to-upgrade-the-project-item-files"></a>Proje öğesi dosyalarını yükseltmek için

1.  Proje öğesi uygulamanızda dosya yedekleme işlemi dikkatle yönetmeniz gerekir. Bu, özellikle bir yan yana yedekleme için geçerlidir nerede `fUpgradeFlag` parametresinin <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> yöntemi olarak ayarlanmış <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>, "eski" belirlenmiş yan dosyaları boyunca yedeklenmiş dosyaları nereye yerleştirilir. Proje zaman yükseltilmiştir sistem süreden eski Yedeklenen dosyaları eski belirlenebilir. Bunu önlemek için belirli adımlar sürece Ayrıca, bunların üzerine yazılmış olabilir.

2.  Zaman, proje öğesi proje yükseltme ilişkin bir bildirim alır **Visual Studio Dönüştürme Sihirbazı** görüntülenmeye devam eder. Bu nedenle, yöntemlerinin kullanması gereken <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> arabirimi yükseltme iletiler ve sihirbaz kullanıcı Arabirimi sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Projeler](../../extensibility/internals/projects.md)