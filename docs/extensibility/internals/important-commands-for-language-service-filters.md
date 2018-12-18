---
title: Dil için önemli komutları hizmet filtreleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1e7affdbcad2b935a05420a2817c5d8bda5cd9cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130691"
---
# <a name="important-commands-for-language-service-filters"></a>Dil hizmeti filtreleri için önemli komutları
Tam özellikli dil hizmet filtresi oluşturmak istiyorsanız, aşağıdaki komutları işleme göz önünde bulundurun. Komut tanımlayıcıları tam listesini tanımlanan <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> numaralandırması için yönetilen kodu ve Stdidcmd.h üstbilgi dosyası yönetilmeyen [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] kodu. Stdidcmd.h dosyasında bulabilirsiniz *Visual Studio SDK yükleme yolu*\VisualStudioIntegration\Common\Inc.  
  
## <a name="commands-to-handle"></a>İşlenecek komutları  
  
> [!NOTE]
>  Aşağıdaki tabloda her komut için filtre uygulamak için zorunlu değildir.  
  
|Komut|Açıklama|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı tıklattığında gönderilir. Bu komut, bir kısayol menüsü sağlamak için zaman olduğunu gösterir. Bu komutu işlemek değil, metin düzenleyici varsayılan kısayol menüsü tüm dile özgü komutlar olmadan sağlar. Bu menüdeki kendi komutları eklemek için komutu işlemek ve kendiniz bir kısayol menüsünü görüntüler.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı CTRL + J yazdığında genellikle gönderdi. Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> deyimi tamamlama kutusunu göstermek için.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı bir karakter yazdığında gönderdi. Bir tetikleyici karakter yazılır ve deyimi sağlamak için tamamlama, yöntemi ipuçları ve sözdizimi renklendirmesi gibi metin işaretçileri eşleşen küme parantezi belirlemek için bu komutu ve hata işaretçileri izleyin. Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> için ifade tamamlama ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> yöntemi ipuçları için. Metin işaretçileri desteklemek için yazılan karakter, işaretçileri güncelleştirme gerekip gerekmediğini belirlemek için bu komutu izleyin.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı Enter tuşuna yazdığında gönderdi. Çağırarak yöntemi ipucu penceresini kapatmak ne zaman belirlemek için bu komut izleme <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Varsayılan olarak, bu komut metin görünümü işler.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı Geri tuşu yazdığında gönderdi. Çağırarak yöntemi ipucu penceresini kapatmak ne zaman belirlemek için İzleyici <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Varsayılan olarak, bu komut metin görünümü işler.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Bir menüsü veya bir kısayol tuşu gönderdi. Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ipucu penceresi parametre bilgilerle güncelleştirmek için.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı bir değişken gezinen veya bir değişkeni imleç yerleştirir ve seçer gönderilen **hızlı bilgi** gelen **IntelliSense** içinde **Düzenle** menüsü. Çağırarak bir ipucu içinde dönüş değişkeni türü <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Hata ayıklama etkin değilse, ipucu ayrıca değişkenin değerini göstermesi gerekir.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı CTRL + Ara çubuğu yazdığında genellikle gönderdi. Bu komut çağırmak için dil hizmeti bildirir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Menüden, genellikle gönderilen **Açıklama Seçimi** veya **açıklamadan çıkarın seçimi** gelen **Gelişmiş** içinde **Düzenle** menüsü. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> kullanıcının seçili metnin açıklama eklemek istediği gösterir; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> kullanıcı seçili metni açıklamadan çıkarın istediği gösterir. Bu komutlar, yalnızca dil hizmeti tarafından uygulanabilir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski Dil Hizmeti Geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)