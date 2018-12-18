---
title: Metin işaretçileri eski API'si ile kullanma | Microsoft Docs
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
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 600e9635fb0ee5ea78226277860ac41e183f47b5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745916"
---
# <a name="using-text-markers-with-the-legacy-api"></a>Metin işaretçileri eski API'si ile kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir metin işaretçisi görüntülenmesini etkileyebilecek arabellekteki metni kayan bir dizi ve bir bölgeye metin davranışını ' dir. Kesme noktaları, yer işaretleri, dalgalı alt çizgiler ve salt okunur bölgelere işaretçileri içerir. Metin işaretçileri temel söz dizimi renklendirmesi öğesinden farklıdır. Söz dizimi renklendirme, metnin bir bölgeyle ilişkili dil söz dizimi iletişim kurmak için hızlı bir yoludur. Hız önemlidir, Windows ekran halinde yeniden boyar olduğunda söz dizimi renklendirmesi genellikle istenir. Söz dizimi renklendirmesi yalnızca metin rengini değiştirir. Metin işaretçileri birçok diğer metin özellikleri değiştirebilirsiniz. Metin işaretçileri "kaydırabilirsiniz" ve özel davranışı uygulamak ve renklendirme.  
  
 Metin işaretçileri ile ilişkili performans yükü nedeniyle, metin arabelleği için çok sayıda işaretçileri oluşturmayın. Kullanıcı arabelleği içeriği düzenler her zaman her işaret güncelleştirilir.  
  
> [!NOTE]
>  Kullanıcılara görünür işaret türü ancak kendi şekil ve stil rengini değiştirebilirsiniz. Daha fazla bilgi için [yazı tipleri ve renkler, ortam, Seçenekler iletişim kutusu](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl Yapılır: Standart Metin İşaretçileri Ekleme](../extensibility/how-to-add-standard-text-markers.md)|Bir standart metin işaretçisi türü tarafından sağlanan eklemeyi açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] metni görünümü çekirdek Düzenleyici.|  
|[Nasıl Yapılır: Hata İşaretçilerini Uygulama](../extensibility/how-to-implement-error-markers.md)|Uygulama örneğini açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kırmızı dalgalı alt çizgiler kullanarak hataları göstermek için kullanılan işaretçisi.|  
|[Nasıl yapılır: Özel Metin İşaretçileri Oluşturma](../extensibility/how-to-create-custom-text-markers.md)|Oluşturma ve bir özel metin işaretçisi türü metin görünümü ekleme işlemini açıklamaktadır.|  
|[Nasıl Yapılır: Metin İşaretçileri Kullanma](../extensibility/how-to-use-text-markers.md)|Metin işaretçileri ekleme işlemi açıklanmaktadır.|  
|[Temel Düzenleyicinin İçinde](../extensibility/inside-the-core-editor.md)|Çekirdek Düzenleyici özelliklerini açıklar ve çekirdek Düzenleyici özelleştirme hakkında ayrıntılar sağlar.|  
|[Düzenleyici Özellikleri](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Uygulamasında kullanılabilen özellikleri açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çekirdek Düzenleyici.|  
  
## <a name="reference"></a>Başvuru  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Düzenleyici tarafından önceden tanımlanmış veya kayıtlı bir VSPackage tarafından belirli bir metne işaret türü hakkında bilgi almak için Tekdüzen bir mekanizma sağlar.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Erişim sağlar ve iki boyutlu koordinatlarını kullanarak bir metin arabelleği bir metin işaretçisi konumunu ayarlar.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Metin işaretçileri yönetmek için yöntemler sağlar.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Geri çağırmalar için sağlar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE ve bir metin işaretçisi ayarlamak için kullanılan diğer işlemler.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Aracılığıyla kullanılabilir olan işlevselliği genişletir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> ek geri çağırmaları sağlayarak arabirimi.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Aracılığıyla kullanılabilir olan işlevselliği genişletir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> ek geri çağırmaları sağlayarak arabirimi.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Diğer işaretçi türleri aynı renkleri sahip olup olmadığını belirlemek bir işaretçi türü sağlar.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Çekirdek Düzenleyici içindeki metin işaretçileri için bağlam sağlar. Çekirdek Düzenleyicisi'nde olduğu her metin işaretçisi türü için ayrı bir IDE oluşturur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> nesne.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Sürükle ve bırak düzenleme, karakter desteği işaretçileri için sağlanan bir işleyici. Bir karakter, bir işaretçisi konumunu gösteren bir simge bulunur.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Döndürür bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> arabiriminden bir metin işaretçileri diğer Vspackage'lar için sağlayan bir hizmet.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Erişim sağlar ve tek boyutlu koordinatlarını kullanarak bir metin arabelleği bir metin işaretçisi konumunu ayarlar. Mümkünse, bu arayüzü kullanmayın.

