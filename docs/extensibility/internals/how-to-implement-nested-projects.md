---
title: 'Nasıl yapılır: iç içe Projeler uygulama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bee3b5bebb8067ecc4bd1115f46d4b668b114c50
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512906"
---
# <a name="how-to-implement-nested-projects"></a>Nasıl yapılır: iç içe Projeler uygulama

Bir iç içe proje türü oluşturduğunuzda, uygulanması gereken birkaç ek adım vardır. Bazı iç içe geçmiş (alt) projeleri için çözüm olan aynı sorumluluklarını ana proje alır. Ana proje, proje çözüm benzer bir kapsayıcıdır. Özellikle, çözüm ve iç içe projeler hiyerarşisini üst projeleri tarafından oluşturulması gereken çeşitli olaylar vardır. Bu olaylar için iç içe projeler oluşturmaya yönelik aşağıdaki işlem açıklanmaktadır.

## <a name="create-nested-projects"></a>İç içe projeler oluşturma

1.  Tümleşik geliştirme ortamı (IDE) çağırarak üst projenin proje dosyası ve başlangıç bilgileri yükler <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> arabirimi. Ana proje oluşturulur ve çözüme eklenir.

    > [!NOTE]
    > Bu noktada, ana proje alt projeler oluşturulmadan önce oluşturulması gerektiğinden, iç içe proje oluşturmak ana proje işleminde çok erken. Bu sıra ana proje alt projeler için ayarları uygulayabilirsiniz ve alt projeleri, gerekirse üst projelerinden bilgileri elde edebilirsiniz. Bu sırası üzerinde kaynak kodu denetimi (SCC) gibi istemcileri tarafından gerekli durumunda olduğundan ve **Çözüm Gezgini**.

     Ana proje beklemelisiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> iç içe geçmiş (alt) projede veya projelerde oluşturmadan önce IDE tarafından çağrılacak yöntem.

2.  IDE çağrıları `QueryInterface` için ana projedeki <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>. Bu çağrı başarılı olursa, IDE çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> tüm iç içe projeler için ana proje açmak için üst yöntemi.

3.  Ana proje çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> projeleri iç içe geçmiş dinleyicileri bildirmek için yöntemi olan hakkında oluşturulacak. SCC, örneğin, çözüm ve proje oluşturma işlemi adımları sırayla ortaya çıkan öğrenmek için bu olayları dinler. Adımları sıralamaya meydana gelirse, çözümün kaynak kod denetimi ile doğru şekilde kaydedilmemiş olabilir.

4.  Ana proje çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> yöntemi veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> yöntemi her alt projeleri.

     Geçirdiğiniz <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> için `AddVirtualProject` yöntemi sanal (iç içe geçmiş) proje yapı tarafından çıkarıldı proje penceresi eklenmesi belirtmek için kaynak kodu denetimi ve benzeri eklendi. `VSADDVPFLAGS` iç içe proje görünürlüğünü denetleme ve işlevler ile ilişkili olduğunu belirten olanak sağlar.

     Bir proje üst projenin proje dosyasında, ana proje çağrıları depolanan GUID olan önceden var olan bir alt projeyi yeniden yükleyin, `AddVirtualProjectEx`. Arasındaki tek fark `AddVirtualProject` ve `AddVirtualProjectEX` olan `AddVirtualProjectEX` belirtmek ana proje etkinleştirmek için bir parametreye sahip bir örnek başına `guidProjectID` etkinleştirmek alt proje için <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> işlevi doğru.

     Yoksa hiçbir GUID kullanılabilir gibi yeni bir iç içe geçmiş projesi eklediğinizde, çözüm bir proje için üst eklenen zaman oluşturur. Proje GUID, proje dosyasında kalıcı hale getirmek için üst projenin sorumluluğundadır. İç içe proje silerseniz, bu proje için GUID da silinebilir.

5.  IDE çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> üst projenin her bir alt projeyi yöntemi.

     Ana proje uygulamalıdır `IVsParentProject` projeleri iç içe istiyorsanız. Ancak hiçbir zaman çağrıları proje üst `QueryInterface` için `IVsParentProject` üst projeleri altındaki olsa bile. Çözüm çağrısını işler `IVsParentProject` ve uygulanmışsa, çağıran `OpenChildren` iç içe projeler oluşturmak için. `AddVirtualProjectEX` her zaman çağrılır `OpenChildren`. Hiyerarşi oluşturma olayları düzenini korumak için ana proje tarafından hiçbir zaman çağrılmalıdır.

6.  IDE çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> alt projedeki yöntemi.

7.  Ana proje çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> dinleyicileri üst alt projeler oluşturulduğunu bildirmek için yöntemi.

8.  IDE çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> üst projedeki tüm alt projelerini açtıktan sonra yöntemi.

     Zaten yoksa, ana proje iç içe her proje için bir GUID çağırarak oluşturur `CoCreateGuid`.

    > [!NOTE]
    > `CoCreateGuid` bir COM API, oluşturulacak bir GUID olduğunda çağrılır. Daha fazla bilgi için `CoCreateGuid` ve MSDN Kitaplığı'nda GUID.

     Ana proje bu GUID IDE'de açıldığında bir sonraki açışınızda alınacak kendi proje dosyasında depolar. 4. adım, arama için ilgili daha fazla bilgi için bkz. `AddVirtualProjectEX` alınacak `guidProjectID` alt proje için.

9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Yöntemi ardından üst öğe kimliği adlı Kural gereği, içinde iç içe geçmiş projeye devretmenizi. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Katmandan üst öğe üzerinde çağrıldığında, temsilci atamak istediğiniz bir proje düğümü özelliklerini alır.

     Bu noktada üst ve alt projeleri program aracılığıyla örneği olduğundan, iç içe projeler için özellikleri ayarlayabilirsiniz.

    > [!NOTE]
    > Yalnızca iç içe geçmiş projeden bağlam bilgisi alır, ancak üst projeyi her bağlam için bu öğe olup olmadığını kontrol ederek sorabilir <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>. Bu şekilde, tek bir iç içe projeler için ek dinamik Yardım özniteliklerini ve belirli menü seçenekleri ekleyebilirsiniz.

10. Hiyerarşi görüntülenmek üzere oluşturulmuş **Çözüm Gezgini** çağrısıyla <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> yöntemi.

     Ortamı üzerinden hiyerarşisine geçirdiğiniz `GetNestedHierarchy` hiyerarşi için Çözüm Gezgini'nde görüntü oluşturmak için. Bu şekilde, çözüm, proje var ve yapı için yapı yöneticisi tarafından yönetilebilir veya kaynak kodu denetimi altında koymak için proje dosyalarında izin verebilirsiniz bilir.

11. İç içe projeler için Project1 oluşturduktan sonra Denetim çözümü geri geçirilir ve Project2 için işlem tekrarlanır.

     Bir alt öğesi olan bir alt proje için iç içe projeler oluşturmak için bu aynı işlem gerçekleşir. Project1 alt olan BuildProject1 alt projeler varsa, bu durumda, bunlar BuildProject1 sonra ve Project2 önce oluşturulması. Yinelemeli bir işlemdir ve hiyerarşinin üstünden aşağı oluşturulmuştur.

     Ne zaman bir iç içe proje kapatıldığında kullanıcı çözümü kapalı veya belirli proje kendisi, başka bir yöntem üzerinde olduğundan `IVsParentProject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>, çağrılır. Ana proje çağrılarını sarmalar <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> yöntemiyle <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> iç içe projeler kapalı dinleyicileri çözüm olayları bildirmek için yöntemleri.

Aşağıdaki konular, iç içe projeler uygularken dikkate alınması gereken çeşitli diğer kavramlar ile Dağıt:

- [Konuları kaldırma ve iç içe projeler yeniden yükleniyor](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [İç içe projeler için sihirbaz desteği](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [İç içe projeler için komut işleme uygulama](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [İç içe projeler için addItem iletişim kutusunu filtreleme](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeni Öğe Ekle iletişim kutusu öğeleri Ekle](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)
- [Denetim listesi: Yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Bağlam parametreleri](../../extensibility/internals/context-parameters.md)
- [Sihirbaz (.vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)