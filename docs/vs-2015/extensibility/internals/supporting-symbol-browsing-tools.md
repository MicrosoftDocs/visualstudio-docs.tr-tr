---
title: Sembol tarama araçlarını destekleme | Microsoft Docs
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
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4c4cf9f711990f5b3f1f064aa6311a8b33b64fef
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757686"
---
# <a name="supporting-symbol-browsing-tools"></a>Sembol Tarama Araçlarını Destekleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Nesne Tarayıcısı**, **sınıf görünümü**, **çağrı tarayıcısı** ve **sembol sonuçları Bul** sembol göz atma özellikleri Visual Studio araçları sağlar. Bu araçlar, hiyerarşik ağaç görünümleri simgeleri görüntüler ve simgeler ağacında arasındaki ilişkileri göstermek. Simgeler, ad alanları, nesneler, sınıflar, sınıf üyeleri ve çeşitli bileşenlerinde bulunan diğer dil öğeleri temsil edebilir. Visual Studio projeleri, dış bileşenleri dahil [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] bileşenleri ve tür (.tlb) kitaplıkları. Daha fazla bilgi için [Structure of Code görüntüleme](../../ide/viewing-the-structure-of-code.md).  
  
## <a name="symbol-browsing-libraries"></a>Sembol tarama kitaplıkları  
 Bir dil uygulayan bileşenlerinizi sembolleri izlemek ve bir dizi arabirimleri aracılığıyla Visual Studio nesne yöneticisine sembolleri listesini sağlayan kitaplıkları oluşturarak sembol tarama Visual Studio özelliklerini genişletebilirsiniz. Bir kitaplığı tarafından tanımlanan <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> arabirimi. Visual Studio nesne Yöneticisi'ni yeni veri istekleri için Sembol tarama araçlarını kitaplıklarından veri alma ve düzenleme, yanıt verir. Daha sonra doldurur veya araçları ile istenen verileri güncelleştirir. Visual Studio nesne Yöneticisi ' ni bir başvuru almak <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, geçmesi <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> kimliği için hizmet `GetService` yöntemi.  
  
 Her kitaplık tüm kitaplıklarını temel bilgileri toplar Visual Studio nesnesi Yöneticisi ile kaydetmeniz gerekir. Bir kitaplığını kaydettirmek için çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> yöntemi. Hangi aracın isteği başlatır, bağlı olarak Visual Studio nesne yöneticisine uygun kitaplığı bulur ve verileri ister. Veri kitaplıklar arasında dolaşır ve [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Nesne Yöneticisi tarafından açıklanan simgeleri listelerindeki <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> arabirimi.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Nesne Yöneticisi, sembol tarama araçlarını kitaplıklarda da en güncel verileri yansıtacak şekilde düzenli olarak yenilenmesi için sorumludur.  
  
 Aşağıdaki diyagramda bir örneği arasında bir kitaplık ve Visual Studio nesne yöneticisine istekleri/veri değişim işlemi temel öğeleri içerir. Arabirimler diyagramdaki bir yönetilen kod uygulaması'nın bir parçasıdır.  
  
 ![Veri akışı kitaplığı ve nesne yöneticisine arasında](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 Visual Studio nesne yöneticisine simge listesi sağlamak için önce kitaplığı ile Visual Studio nesne yöneticisi çağırarak kaydetmeniz gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> yöntemi. Kitaplık kaydedildikten sonra Visual Studio nesne yöneticisine kitaplık özellikleri hakkında belirli bilgi ister. Örneğin, kitaplık bayrakları ister ve kategorileri çağırarak desteklenen <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> yöntemleri. Bu kitaplıktan araçlarından biri olan veri istediğinde, belirli bir noktada nesne yöneticisine en üst düzey listesini sembolleri çağırarak ister <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> yöntemi. Yanıt, kitaplık, simge listesi üreten ve Visual Studio nesne yöneticisine kullanıma sunduğu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> arabirimi. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Nesne Yöneticisi belirler çağırarak kaç öğeleri listede olan <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> yöntemi. Aşağıdaki tüm istekleri listesinde belirli bir öğe için ilgili ve her istekte öğesi dizin numarasını sağlayın. Çağırarak türü, erişilebilirlik ve öğenin diğer özellikleri hakkında bilgi toplamak için Visual Studio nesne yöneticisine geçer <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> yöntemi.  
  
 Çağırarak öğenin adını belirler <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> yöntemi ve çağırarak simge bilgisi istekleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> yöntemi. Simge sol tarafında öğe adı görüntülenir ve öğe, erişilebilirlik ve diğer özellikleri türünü gösterir.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Nesnesi Yöneticisi çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> belirtilen liste öğesi genişletilebilir ve alt öğelerine sahip belirlemek için yöntemi. UI öğe genişletmek için bir istek gönderirse, nesne yöneticisine alt simge listesi çağırarak istekleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> yöntemi. İşlem, isteğe bağlı olarak oluşturulmakta ağacı farklı kısımlarını ile devam eder.  
  
> [!NOTE]
>  Yerel kod sembol sağlayıcısı uygulamak için kullanma <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> arabirimleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: nesne yöneticisine kitaplık kaydetme](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Nasıl yapılır: nesne yöneticisine kitaplık tarafından sağlanan sembollerin listelerini kullanıma sunma](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [Nasıl Yapılır: Bir Kitaplıktaki Sembolleri Tanımlama](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)

