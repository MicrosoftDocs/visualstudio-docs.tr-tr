---
title: Simgenin tarama araçları destekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 08185f64310da610253dc35e69323b17ab0177fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134597"
---
# <a name="supporting-symbol-browsing-tools"></a>Simgenin tarama araçları destekleme
**Nesne Tarayıcısı**, **sınıf görünümü**, **çağrısı tarayıcı** ve **Bul simgesi sonuçlarınızı** araçları Visual Studio özellikleri gözatma simgesi sunar. Bu araçları simgelerin hiyerarşik ağaç görünümleri görüntülemek ve simgeleri ağacında arasındaki ilişkileri gösterir. Simgeleri ad alanları, nesneler, sınıflar, sınıf üyeleri ve çeşitli bileşenlerinde bulunan diğer dil öğeleri temsil edebilir. Visual Studio projeleri, dış bileşenler dahil [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] bileşenleri ve tür (.tlb) kitaplıkları. Daha fazla bilgi için bkz: [kodunu yapısı görüntüleme](../../ide/viewing-the-structure-of-code.md).  
  
## <a name="symbol-browsing-libraries"></a>Simgenin tarama kitaplıkları  
 Dil uygulayan bileşenlerinizi sembolleri izlemek ve arabirimleri kümesi aracılığıyla Visual Studio nesne Yöneticisi'ni listeler simgelerin sağlamak kitaplıkları oluşturarak simgenin tarama Visual Studio özelliklerini genişletebilirsiniz. Bir kitaplık tarafından açıklanan <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> arabirimi. Visual Studio nesne Yöneticisi'ni yeni veri istekleri simgenin Tarama Araçları'ndan kitaplıklarından verileri alma ve onu düzenleme yanıt verir. Daha sonra doldurur veya Araçlar istenen verilerle güncelleştirir. Visual Studio nesne Yöneticisi ' ni bir başvuru almak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, geçirmek <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> kimliği için hizmet `GetService` yöntemi.  
  
 Her kitaplık tüm kitaplıkları'nı bilgileri toplar Visual Studio nesnesi Yöneticisi ile kaydetmeniz gerekir. Bir kitaplık kaydetmek için arama <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> yöntemi. Hangi aracı isteği başlatır, bağlı olarak Visual Studio nesne Yöneticisi'ni uygun kitaplığı bulur ve verileri ister. Veri kitaplıklar arasında geçen ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Nesne Yöneticisi tarafından açıklanan simgelerin listelerindeki <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> arabirimi.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Nesne yöneticisidir kitaplıklarınızın en güncel verileri yansıtacak şekilde araçları simgenin tarama düzenli aralıklarla yenileme için sorumlu.  
  
 Aşağıdaki diyagramda, istekleri/veri değişim süreci kitaplık ve Visual Studio nesne Yöneticisi'ni arasındaki temel öğeleri örneği içerir. Diyagramdaki arabirimleri yönetilen kod uygulamasına bir parçasıdır.  
  
 ![Bir kitaplık nesnesi Yöneticisi arasındaki veri akışını](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 Simge listesi Visual Studio nesnesi Yöneticisi sağlamak için öncelikle kitaplığı ile Visual Studio nesne Yöneticisi'ni çağırarak kaydetmeniz gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> yöntemi. Kitaplık kaydedildikten sonra Visual Studio nesne Yöneticisi'ni kitaplığı özellikleri hakkında bazı bilgileri ister. Örneğin, kitaplık bayrakları ister ve çağırarak kategorileri desteklenen <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> yöntemleri. Bu kitaplıktan araçlardan birini veri istediğinde, belirli bir noktada Nesne Yöneticisi'ni en üst düzey listesini simgeleri çağırarak ister <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> yöntemi. Yanıt, kitaplık sembolleri listesini üreten ve Visual Studio nesne Yöneticisi üzerinden kullanıma sunar <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> arabirimi. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Nesne Yöneticisi'ni belirler çağırarak kaç öğe listede bulunan <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> yöntemi. Tüm aşağıdaki isteklerini listedeki belirli bir öğe için ilgili ve her istekte öğesi dizin numarasını sağlayın. Çağırarak türü, erişilebilirlik ve öğenin diğer özellikleri hakkında bilgi toplamak için Visual Studio nesne Yöneticisi'ni geçer <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> yöntemi.  
  
 Çağırarak öğesinin adını belirler <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> yöntemi ve simge bilgilerini çağırarak istekleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> yöntemi. Simge öğe adı solunda görüntülenir ve öğe, erişilebilirlik ve diğer özellikleri türünü gösterir.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Nesnesi Yöneticisi çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> verilen liste öğesi genişletilemez olup olmadığını ve alt öğeleri olup belirlemek amacıyla yöntemi. UI öğenin genişletmek için bir istek gönderdiğinde, Nesne Yöneticisi'ni simgeleri alt listesini çağırarak ister <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> yöntemi. İşlem, isteğe bağlı olarak oluşturulmakta ağaç farklı kısımlarını ile devam eder.  
  
> [!NOTE]
>  Yerel kod simgesi sağlayıcısı uygulamak için kullandığınız <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> arabirimleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: bir kitaplık nesnesi Yöneticisi ile kaydetme](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Nasıl yapılır: kullanıma nesnesi Yöneticisi kitaplığı tarafından sağlanan simgelerin listeler](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [Nasıl Yapılır: Bir Kitaplıktaki Sembolleri Tanımlama](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)