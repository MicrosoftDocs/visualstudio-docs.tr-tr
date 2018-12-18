---
title: Gecikmeli belge yüklemesi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03ca02010586711fa1a9af463f2fde5d0f4963a5
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500374"
---
# <a name="delayed-document-loading"></a>Gecikmeli belge yüklemesi
Bir kullanıcı bir Visual Studio çözümü yeniden açana, ilişkili belgelerin çoğu hemen yüklü değil. Belge pencere çerçevesi başlatma bekleyen durumda oluşturulur ve çalıştırılan Belge tablosu (RDT) (bir saplama çerçeve olarak adlandırılır) bir yer tutucu belge yerleştirilir.  
  
Uzantınız, Visual Studio için genel bellek Ayak izi artırabilirsiniz bunlar yüklenmeden önce öğeleri belgelerde sorgulayarak gereksiz yere yüklenmesi proje belgelerini neden olabilir.  
  
## <a name="document-loading"></a>Belge yükleme  
Saplama çerçeve ve belge pencere çerçevesi sekmesini seçerek örneğin kullanıcı, belge eriştiğinde, tam olarak başlatılır. Belge Ayrıca, belgenin verilerini, doğrudan belge verileri almak için RDT erişme veya aşağıdaki çağrıları yaparak RDT dolaylı olarak erişmek isteyen bir uzantı tarafından başlatılabilir:  
  
- Pencere çerçevesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> yöntemi.  
  
- Pencere çerçevesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> aşağıdaki özelliklerden birini yöntemi:  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
- Uzantınızı yönetilen kod kullanıyorsa değil, çağırmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> emin olmadığınız sürece belgeyi başlatma bekleyen durumda değil veya tam olarak başlatılması için belgeyi istediğiniz. Yöntem her zaman belge döndürüldüğünden nedeni gerekiyorsa, oluşturma, veri nesnesi. Üzerinde yöntemlerden birini bunun yerine, çağırmalıdır `IVsRunningDocumentTable4` arabirimi.  
  
- Uzantınızı C++ kullanıyorsa, geçirebilirsiniz `null` istemediğiniz parametreleri.  
  
- Diğer özellikler için sormadan önce ilgili özelliklerini sormadan önce aşağıdaki yöntemlerden birini çağırarak yüklenirken gereksiz belge önleyebilirsiniz:  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> kullanarak <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Bu yöntem döndürür bir <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> için bir değer içeren bir nesne <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , belgenin henüz başlatılmadı.  
  
Bir belge tam olarak başlatıldığında başlatan RDT olaya abone olarak bir belge yüklendiğinde bilgi edinebilirsiniz. İki olasılık vardır:  
  
- Olay havuzu uyguluyorsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, abone olabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
- Aksi takdirde, abone olabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  

 Aşağıdaki örnek, bir kuramsal belge erişim senaryo: bir Visual Studio uzantısı istediği açık belgeler hakkında bazı bilgiler görüntülemek, düzenleme örneği için kilit sayısı ve belge verilerini hakkında bir şey. Belgeleri kullanarak RDT numaralandırır <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, sonra çağıran <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> düzenleme kilit sayısı ve belge verilerini almak için her belge için. Belge başlatma bekleyen durumda ise, belge verileri isteyen, gereksiz yere yeniden başlatılmasına neden olur.  
  
 Bir belgeye erişme daha verimli bir şekilde kullanmaktır <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> düzenleme kilit sayacını alın ve ardından <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> belge başlatılmış olup olmadığını belirlemek için. Bayrakları dahil etmezseniz <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, belge zaten başlatılmış ve belge verilerini ile isteyen <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> gereksiz sıfırlamaları neden olmaz. Bayrakları dahil etmezseniz <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, uzantıyı belge başlatılana kadar belge verileri isteyen kaçınmanız gerekir. Bu başlatma olarak algılanabilir `OnAfterAttributeChange(Ex)` olay işleyicisi.  
  
## <a name="test-extensions-to-see-if-they-force-initialization"></a>Test başlatma zorla görmek için Uzantılar  
 Bir belge başlatılmış olup olmadığını, uzantınızı başlatma başlatılmasına gerek olmadığını bulmanın zor olabilir, böylece belirtmek için görünür hiçbir işaret yoktur. Metin tam olarak başlatılmadı her belgenin başlığını neden olduğundan doğrulama kolaylaştırır bir kayıt defteri anahtarı ayarlayabilirsiniz *[Stub]* başlık.  
  
 İçinde **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad**ayarlayın **StubTabTitleFormatString** için  *{0} [Stub]*.