---
title: Eski dil hizmeti, model | Microsoft Docs
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
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 76838d6beb5d24f7586ddd44f7bd5400dec4f355
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795193"
---
# <a name="model-of-a-legacy-language-service"></a>Eski Dil Hizmetinin Modeli
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dil hizmeti belirli bir dil özellikleri ve öğeleri tanımlar ve bilgileri o dile özgü Düzenleyici sağlamak için kullanılır. Örneğin, düzenleyici söz dizimi renklendirmesi desteklemek için öğeleri ve dil anahtar sözcükleri bilmesi gerekir.  
  
 Dil hizmeti metin arabelleğini yöneten Düzenleyicisi ve düzenleyici içeren görünümü ile yakın bir tümleştirmede çalışır. Microsoft IntelliSense **hızlı bilgi** seçeneği dil hizmeti tarafından sağlanan bir özellik örneğidir.  
  
## <a name="a-minimal-language-service"></a>Bir Minimal dil hizmeti  
 En temel dil hizmeti, aşağıdaki iki nesne içerir:  
  
- *Dil hizmeti* uygulayan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> arabirimi. Bir dil hizmeti adı, dosya adı uzantıları, kod penceresi Yöneticisi ve Renklendirici dahil dil hakkında bilgi içerir.  
  
- *Renklendirici* uygulayan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> arabirimi.  
  
  Aşağıdaki kavramsal çizimi temel dil hizmetinin modeli gösterilmektedir.  
  
  ![Dil hizmetinin Modeli grafiği](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
  Temel dil hizmetinin modeli  
  
  Belge penceresi konakları *belge görünümü* bu durumda düzenleyicinin [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] çekirdek Düzenleyici. Düzenleyici tarafından belge görünümü ve metin arabelleğini sahibi olur. Bu nesneler ile çalışma [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] adlı bir özel belge penceresi bir *kod penceresi*. Kod penceresi bulunan bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> oluşturulur ve IDE tarafından denetlenen nesne.  
  
  Düzenleyici belirli bir uzantıya sahip bir dosya yüklendiğinde, bu uzantıyla ilişkili dil hizmeti bulur ve kod penceresinde çağırarak geçirir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> yöntemi. Dil hizmeti döndürür bir *kod penceresinde Yöneticisi*, uygulayan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> arabirimi.  
  
  Aşağıdaki tablo modelindeki nesneler genel bir bakış sağlar.  
  
|Bileşen|Nesne|İşlev|  
|---------------|------------|--------------|  
|Metin arabelleği|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Unicode okuma/yazma metin akışına. Bu, diğer kodlamaları kullanılacak metin için mümkündür.|  
|Kod penceresi|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|Bir veya daha fazla metin görünümlerini içeren bir belge penceresi. Zaman [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] olan çok Belgeli Arabirim (MDI) modunda bir MDI alt kod penceredir.|  
|Metin görünümü|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|Kullanıcının gidin ve klavyeyi ve fareyi kullanarak metin görüntüleme sağlayan bir pencere. Metin görünümü kullanıcı için bir düzenleyici olarak görüntülenir. Metin görünümlerde sıradan Düzenleyici pencerelerini ve çıktı penceresini komut penceresi kullanabilirsiniz. Ayrıca, kod penceresi içinde bir veya daha fazla metin görünümlerini yapılandırabilirsiniz.|  
|Metin Yöneticisi|Tarafından yönetilen <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> hizmeti, hangi elde gelen bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> işaretçi|Daha önce açıklanan tüm bileşenleri tarafından paylaşılan ortak bilgisini tutar bileşeni.|  
|Dil hizmeti|Uygulamaya bağlıdır; uygulayan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|Düzenleyici söz dizimi vurgulama, ifade tamamlama ve Ayraç eşleştirme gibi dile özgü bilgiler sağlayan bir nesne.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Düzenleyicilerde Belge Verileri ve Belge Görünümü](../../extensibility/document-data-and-document-view-in-custom-editors.md)

