---
title: Gecikmeli belge yüklemesi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 94d79af00fced81dc7da38f323598ade926d26f4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755484"
---
# <a name="delayed-document-loading"></a>Gecikmeli Belge Yüklemesi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir kullanıcı bir Visual Studio çözümü yeniden açana, ilişkili belgelerin çoğu hemen yüklü değil. Belge pencere çerçevesi başlatma bekleyen durumda oluşturulur ve çalıştırılan Belge tablosu'de (RDT) (bir saplama çerçeve olarak adlandırılır) bir yer tutucu belge yerleştirilir.  
  
 Uzantınızı yüklenmeden önce öğeleri belgelerde sorgulayarak gereksiz yere yüklenmesi proje belgelerini neden olabilir. Bu, Visual Studio için genel bellek Ayak izi artırabilir.  
  
## <a name="document-loading"></a>Belge yükleme  
 Saplama çerçeve ve belge pencere çerçevesi sekmesini seçerek örneğin kullanıcı, belge eriştiğinde, tam olarak başlatılır. Belge Ayrıca, belgenin verilerini, doğrudan belge verileri almak için RDT erişme veya aşağıdaki çağrıları yaparak RDT dolaylı olarak erişmek isteyen bir uzantı tarafından başlatılabilir:  
  
- Pencere çerçevesi gösterilemedi yöntemi: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>.  
  
- Pencere çerçevesi GetProperty yöntemi <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> herhangi birinde aşağıdaki özellikleri:  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  Uzantınızı yönetilen kod kullanıyorsa değil, çağırmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> emin olmadığınız sürece belgeyi başlatma bekleyen durumda değil veya tam olarak başlatılması için belgeyi istediğiniz... Bu yöntem her zaman belge döndürür olmasıdır gerekiyorsa, oluşturma, veri nesnesi. Bunun yerine, IVsRunningDocumentTable4 arabirimde yöntemlerden birini çağırmalıdır.  
  
  Uzantınızı C++ kullanıyorsa, geçirebilirsiniz `null` istemediğiniz parametreleri.  
  
  Gereksiz belge yüklemesi için ilgili özellikleri sormadan önce aşağıdaki yöntemlerden birini çağırarak önleyebilirsiniz: önce diğer özelliklerini isteyin.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> kullanarak <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Bu yöntem döndürür bir <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> için bir değer içeren bir nesne <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , belgenin henüz başlatılmadı.  
  
  Bir belge tam olarak başlatıldığında başlatan RDT olaya abone olarak bir belge yüklendiğinde bilgi edinebilirsiniz. İki olasılık vardır:  
  
- Olay havuzu uyguluyorsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, abone olabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
- Aksi takdirde, abone olabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  
  Bir kuramsal belge erişim senaryo aşağıda verilmiştir. Bir uzantı açık belgeler hakkında bazı bilgiler görüntülemek istediğiniz VisualStudio, örneği için Düzen kilit sayısı ve belge verilerini hakkında bir şey. Belgeleri kullanarak RDT numaralandırır <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, sonra çağıran <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> düzenleme kilit sayısı ve belge verilerini almak için her belge için. Belge başlatma bekleyen durumda ise, belge verileri isteyen, gereksiz yere yeniden başlatılmasına neden olur.  
  
  Bunun yapılması, daha verimli bir şekilde bu kullanmaktır <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> düzenleme kilit sayacını alın ve ardından <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> belge başlatılmış olup olmadığını belirlemek için. Bayrakları dahil etmezseniz <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, belge zaten başlatılmış ve belge verilerini ile isteyen <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> gereksiz sıfırlamaları neden olmaz. Bayrakları dahil etmezseniz <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, uzantıyı belge başlatılana kadar belge verileri isteyen kaçınmanız gerekir. Bu OnAfterAttributeChange(Ex) olay işleyicisi algılanabilir.  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Başlatma zorla görmek için uzantılarını test etme  
 Bir belge başlatılmış olup olmadığını, uzantınızı başlatma başlatılmasına gerek olmadığını bulmanın zor olabilir, böylece belirtmek için görünür hiçbir işaret yoktur. Metin tam olarak başlatılmadı her belgenin başlığını neden olduğundan doğrulama kolaylaştırır bir kayıt defteri anahtarı ayarlayabilirsiniz `[Stub]` başlık.  
  
 İçinde **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad]** ayarlayın **StubTabTitleFormatString** için  **{0} [Stub]**.

