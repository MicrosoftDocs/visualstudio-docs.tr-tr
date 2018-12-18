---
title: Önemli komutlar için dil hizmeti filtreleri | Microsoft Docs
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
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2c99fdefdd8a215be04bb16b88f56be56b7fff67
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787107"
---
# <a name="important-commands-for-language-service-filters"></a>Dil Hizmeti Filtreleri için Önemli Komutlar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tam özellikli dil hizmeti filtresi oluşturmak istiyorsanız, aşağıdaki komutları işleme göz önünde bulundurun. Tam komut tanımlayıcıları listesini tanımlanan <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> numaralandırması yönetilen kod ve Stdidcmd.h üstbilgi dosyası yönetilmeyen [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] kod. Stdidcmd.h dosyasında bulabilirsiniz *Visual Studio SDK yükleme yolunu*\VisualStudioIntegration\Common\Inc.  
  
## <a name="commands-to-handle"></a>Komutları işlemek için  
  
> [!NOTE]
>  Aşağıdaki tabloda her komut için filtre uygulamak için zorunlu değildir.  
  
|Komut|Açıklama|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı tıkladığında Gönder. Bu komut, bir kısayol menüsü sağlamak için zaman olduğunu gösterir. Bu komut işleyemez, metin düzenleyici olmadan herhangi bir dile özgü komut varsayılan kısayol menüsü sağlar. Bu menüde kendi komutları eklemek için komutu işlemek ve kendiniz bir kısayol menüsünü görüntüleyin.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|CTRL + J kullanıcı türleri genellikle gönderilir. Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodunda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> deyim tamamlama kutusunu göstermek için.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı bir karakter yazdığında gönderilir. Bu komut, bir tetikleyici karakteri yazdıldığında ve deyimi sağlamak için tamamlama yöntemi ipuçları ve söz dizimi renklendirme gibi metin işaretçileri Ayraç eşleştirme belirlerken ve hata işaretçileri izleyin. Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodunda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> için deyim tamamlama ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metodunda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> yöntemi ipuçları için. Metin işaretçileri desteklemek için yazılan karakter, işaretçileri güncelleştirme gerekip gerekmediğini belirlemek için bu komutu izleyin.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı Enter tuşunu yazdığında gönderilir. Çağırarak yöntemi ipucu penceresini kapatmak ne zaman belirlemek için bu komut izleme <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metodunda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Varsayılan olarak, bu komut metni görünümü işler.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı Geri tuşu yazdığında gönderilir. Çağırarak yöntemi ipucu penceresini kapatmak ne zaman belirlemek için İzleyici <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metodunda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Varsayılan olarak, bu komut metni görünümü işler.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Bir menü ya da bir kısayol tuşu Gönder. Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodunda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ipucu penceresi ile parametre bilgileri güncelleştirilecek.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı değişkeninden önce gelir veya bir değişken üzerinde imleç yerleştirir ve seçer gönderilen **hızlı bilgi** gelen **IntelliSense** içinde **Düzenle** menüsü. Çağırarak bir ipucu dönüş türü değişkeni <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodunda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Hata ayıklama etkin olursa, ipucu ayrıca değişkenin değerini göstermelidir.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|CTRL + Ara çubuğu kullanıcı türleri genellikle gönderilir. Bu komut çağırmak için dil hizmeti bildirir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodunda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Genellikle bir menüden gönderilen **yorum seçimi** veya **seçimi işletilir satıra çevir** gelen **Gelişmiş** içinde **Düzenle** menüsü. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> kullanıcının seçili metin düzenini açıklama istediğini gösterir. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> kullanıcı seçili metin açıklamasını istediğini gösterir. Bu komutlar, yalnızca dil hizmeti tarafından uygulanabilir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski Dil Hizmeti Geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)

