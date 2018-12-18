---
title: 'Denetim listesi: eski dil hizmeti oluşturma | Microsoft Docs'
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
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 330270b34d55e88c883b9d8a6270b4abad02d9c1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782992"
---
# <a name="checklist-creating-a-legacy-language-service"></a>Denetim Listesi: Eski Dil Hizmeti Oluşturma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aşağıdaki denetim listesini için dil hizmeti oluşturmak için gerçekleştirmeniz gereken temel adımlar özetlenmektedir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] çekirdek Düzenleyici. Dil hizmetleriyle tümleştirmeye yönelik [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], hata ayıklama ifade değerlendiricisi oluşturmanız gerekir. Daha fazla bilgi için [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) içinde [Visual Studio hata ayıklayıcı genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="steps-for-creating-a-language-service"></a>Dil hizmeti oluşturma adımları  
  
1.  Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> arabirimi.  
  
    -   VSPackage içinde uygulama <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> dil hizmeti sağlamak için arabirim.  
  
    -   Dil hizmetinizi tümleşik geliştirme ortamında (IDE) kullanılabilir hale getirmek, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> uygulaması.  
  
2.  Uygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> ana dil hizmeti sınıfındaki arabirimi.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Arabirimi çekirdek düzenleyici ve dil hizmeti arasındaki etkileşimi başlangıç noktasıdır.  
  
### <a name="optional-features"></a>İsteğe bağlı özellikler  
 Aşağıdaki özellikler isteğe bağlıdır ve herhangi bir sırada uygulanabilir. Bu özellikler, dil hizmeti işlevselliğini artırır.  
  
- Söz dizimi renklendirmesi  
  
   Uygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> arabirimi. Uygulamanız bu arabirimin uygun renk bilgilerini döndürmek için ayrıştırıcı bilgileri gerekir.  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Yöntemi döndürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> arabirimi. Uygulamanız gerekir böylece ayrı Renklendirici örneği her metin arabelleği için oluşturulan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> ayrı ayrı arabirim. Daha fazla bilgi için [eski dil hizmetinde söz dizimi renklerini](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
- Kod penceresi  
  
   Uygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> , yeni bir kod penceresi oluşturulduğunda bildirim almak dil hizmetini etkinleştirme için arabirim.  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> Yöntemi döndürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> arabirimi. Dil hizmeti daha sonra kod penceresinde için özel kullanıcı Arabirimi ekleyebilirsiniz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>. Dil hizmeti metin görünümü filtre ekleme gibi özel işlemi de yapabilirsiniz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>.  
  
- Metin Görünümü Filtresi  
  
   IntelliSense deyim tamamlamada dil hizmetinde sağlamak için metin görünümünü aksi işlemek komutlardan bazıları müdahale gerekir. Bu komutlar komutlarını kesiştirmek için aşağıdaki adımları tamamlayın:  
  
  - Uygulama <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> komut zinciri ve tutamacı Düzenleyici komutlar katılmak için.  
  
  - Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> yöntemi ve geçirin, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> uygulaması.  
  
  - Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> bu komutları artık size geçirilir, böylece görünümden ayırdığınızda yöntemi.  
  
    İşlenmesi gereken komutları sağlanan hizmetlere bağlıdır. Daha fazla bilgi için [dil hizmeti filtreleri için önemli komutlar](../../extensibility/internals/important-commands-for-language-service-filters.md).  
  
  > [!NOTE]
  >  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Arabirim uygulandığında, aynı nesne üzerinde <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi.  
  
- Deyim tamamlama  
  
   Uygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> arabirimi.  
  
   Deyim tamamlama komutunu desteklemez (diğer bir deyişle, <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>) ve çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> yönteminde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> geçirerek arabirimi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> arabirimi. Daha fazla bilgi için [eski dil hizmetinde deyim tamamlama](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).  
  
- Yöntem ipuçları  
  
   Uygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> yöntemi ipucu penceresi veri sağlamak için arabirim.  
  
   Ne zaman gösterileceğini yöntemi veri ipucu penceresi öğrenmek için gerektiği gibi komutları işlemek için metin Görünümü Filtresi yükleyin. Daha fazla bilgi için [eski dil hizmetinde parametre bilgisi](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).  
  
- Hata işaretçileri  
  
   Uygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> arabirimi.  
  
   Uygulayan işaret nesneler oluşturma hatası <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> arabirimi ve çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> yöntemini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> hata işaretçisi nesnenin arabirimi.  
  
   Genellikle her hata işaret görev listesi penceresindeki bir öğeyi yönetir.  
  
- Görev listesi öğeleri  
  
   Bir görev öğesi sınıfı sağlayarak uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> arabirimi.  
  
   Bir görev sağlayıcı sınıfı sağlayarak uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> arabirimi ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> arabirimi.  
  
   Bir görev Numaralandırıcı sınıfı sağlayarak uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> arabirimi.  
  
   Görev listesi ile görev sağlayıcıyı kaydetmek <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> yöntemi.  
  
   Elde <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> dil hizmetin hizmet sağlayıcısı GUID hizmetiyle çağırarak arabirim <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>.  
  
   Görev öğesi nesneleri ve çağrı oluşturma <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> yönteminde <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> arabirim olduğunda yeni veya güncelleştirilmiş görevler.  
  
- Yorum görev öğeleri  
  
   Kullanım <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> arabirimi ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> yorum görev belirteçleri elde etmek için arabirim.  
  
   Elde bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> alanından arabirim <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> hizmeti.  
  
   Elde <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> alanından arabirim <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> yöntemi.  
  
   Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> belirteci listesindeki değişiklikleri dinlemek için arabirim.  
  
- Anahat Oluşturma  
  
   Ana hat oluşturmayı desteklemek için birkaç seçenek vardır. Örneğin, destekleyebilir **tanımlara Daralt** komutu, anahat Düzenleyicisi tarafından denetlenen bölgeleri sağlayın veya istemci tarafından denetlenen bölgeleri destekler. Daha fazla bilgi için [nasıl yapılır: sağlayan genişletilmiş ana hat oluşturma desteği eski dil hizmetinde](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).  
  
- Dil hizmeti kaydı  
  
   Dil hizmeti kaydetme hakkında daha fazla bilgi için bkz. [eski dil hizmetinde kaydetme](../../extensibility/internals/registering-a-legacy-language-service2.md) ve [yönetme VSPackages](../../extensibility/managing-vspackages.md).  
  
- Bağlama duyarlı Yardım  
  
   Aşağıdaki yollardan biriyle Düzenleyici bağlam sağlayın:  
  
  -   Bağlam için metin işaretçileri uygulayarak sağlamak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> arabirimi.  
  
  Tüm kullanıcı bağlamı uygulama tarafından sağlamak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> arabirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski dil hizmeti geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [CLR İfade Değerlendirici Yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

