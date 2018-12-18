---
title: Eski API'yi kullanarak bir dil hizmetinin bağlamına sağlama | Microsoft Docs
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
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 322dc704524a5b0172797c9351e7beb60d778ab4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781939"
---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>Eski API'yi kullanarak bir dil hizmetinin bağlamına sağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanıcı bağlamı kullanarak sağlamak için bir dil hizmeti için iki seçenek [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çekirdek Düzenleyicisi: metin işaretçisi bağlam sağlamak ya da tüm kullanıcı bağlamı sağlar. Her arasındaki farklar aşağıda özetlenmiştir.  
  
 Bağlam sağlamak için kendi düzenleyicinizi bağlı bir dil hizmeti ile ilgili daha fazla bilgi için bkz: [nasıl yapılır: bağlam sağlamak düzenleyiciler için](../extensibility/how-to-provide-context-for-editors.md).  
  
## <a name="provide-text-marker-context-to-the-editor"></a>Düzenleyici metin işaretçisi bağlam sağlayın  
 Derleyici hataları metin işaretçilerini tarafından belirtilen bağlam sağlamak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çekirdek Düzenleyicisi, uygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> arabirimi. İmleç üzerinde bir metin işaretçisi olduğunda bu senaryoda, Dil Hizmet bağlamı sağlar. Bu anahtar sözcüğü için imlecin sağlamak üzere Düzenleyicisi sağlar **dinamik Yardım** penceresi özniteliği yok.  
  
## <a name="provide-all-user-context-to-the-editor"></a>Tüm kullanıcı bağlamı düzenleyicisi sağlar  
 Bir dil hizmeti oluşturma ve kullanıyorsanız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yapabileceğinize dair daha sonra çekirdek Düzenleyicisi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> dil hizmetiniz için bağlam sağlamak için arabirim.  
  
 Yürütmesinin `IVsLanguageContextProvider`, bir içerik paketi (koleksiyon), içerik paketi güncelleştirmekten sorumlu Düzenleyicisi iliştirilmiş. Zaman **dinamik Yardım** penceresi çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> boşta kalma zaman, içerik paketi bu içerik paketi arabirimde sorgular için bir güncelleştirme Düzenleyici. Düzenleyici, ardından bu Düzenleyici güncelleştirmeniz gerekir ve İçerik Paketi için bir işaretçi geçirir dil hizmeti bildirir. Bu çağrılarak gerçekleştirilir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> düzenleyicisinden yöntemi için dil hizmeti. İçerik Paketi için işaretçiyi kullanarak dil hizmeti artık ekleyip öznitelikleri ve anahtar sözcükleri kaldırabilirsiniz. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.  
  
 Uygulamak için iki farklı yolu vardır `IVsLanguageContextProvider`:  
  
- İçerik Paketi için bir anahtar sağlar.  
  
   Düzenleyici bağlam paketini güncelleştirmek için çağrıldığında uygun anahtar sözcüklere ve öznitelikleri geçirin ve ardından dönün `S_OK`. Bu dönüş değeri yerine anahtar sözcüğü ve öznitelik içeriğinizi korumak için İçerik Paketi için imlecin anahtar sözcüğü Düzenleyicisi söyler.  
  
- İmlecin anahtar sözcüğü ile anahtar sözcüğü alın  
  
   Düzenleyici bağlam paketini güncelleştirmek için çağrıldığında, uygun öznitelikleri geçirin ve ardından dönün `E_FAIL`. Bu dönüş değeri, içerik paketi özniteliklerinizin korur, ancak içerik paketi imlecin anahtar sözcüğü ile güncelleştirme Düzenleyici söyler.  
  
  Aşağıdaki diyagramda bağlam uygulayan bir dil hizmeti için nasıl sağlandığını gösterir `IVsLanguageContextProvider`.  
  
  ![LangServiceImplementation2 grafik](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
  Bağlam için bir dil hizmeti  
  
  Diyagramda görüldüğü gibi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] temel metin düzenleyicisi iliştirilmiş bir içerik paketi vardır. Bu içerik paketi için üç ayrı üzere paketleri işaret: dil hizmeti, varsayılan Düzenleyicisi ve metin işaretçisi. Dil hizmeti ve metin işaretçisi üzere paketleri, öznitelikleri ve dil hizmeti için anahtar sözcükler içeren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> arabirimi uygulanır ve metin işaretçileri, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> arabirimi uygulanır. Ya da bu arabirimler uygulayamaz, düzenleyici varsayılan Düzenleyicisi üzere pakette imlecin anahtar sözcüğü için bağlam sağlar.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>Düzenleyiciler ve tasarımcılar için bağlam yönergeleri  
 Tasarımcılar ve düzenleyiciler bir genel anahtar sözcük Düzenleyici veya tasarımcı penceresini sağlamanız gerekir. Bu, böylece kullanıcı F1 tuşuna bastığında genel, ancak uygun bir Yardım konusu Tasarımcı veya düzenleyicide için görüntüler gerçekleştirilir. Bir düzenleyici gerekir Buna ek olarak, geçerli anahtar sözcüğü imlecin sağlayın veya geçerli seçime dayanan bir anahtar terimi sağlayın. Bu, metin veya kullanıcı Arabirimi öğesi için bir Yardım konusu işaret veya kullanıcı F1 tuşuna bastığında görüntüler seçili emin olmak için gerçekleştirilir. Bir tasarımcı, bir düğme gibi bir tasarımcıdan seçili bir öğe için bağlam sağlar. Düzenleyiciler ve tasarımcılar de bağlanması için bir dil hizmeti açıklandığı şekilde [eski dil hizmeti temel bileşenleri](../extensibility/internals/legacy-language-service-essentials.md).

