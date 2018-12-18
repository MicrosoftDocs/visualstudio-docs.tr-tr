---
title: Eski dil Service1 parametre bilgilerini | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50450d1968c626e0a5b32dee4c6f03d005d6ede9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132769"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Eski dil hizmetindeki parametre bilgisi
Bir dil yapısı oldukları hakkında ipuçları kullanıcılara IntelliSense parametre bilgileri araç ipucu sağlar.  
  
 Eski dil hizmetler bir VSPackage bir parçası olarak uygulanır, ancak dil hizmet özellikleri uygulamak için daha yeni MEF uzantıları kullanmak için bir yoludur. Daha fazla bilgi bulmak için bkz: [Düzenleyicisi ve dil Hizmetleri genişletme](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Yeni Düzenleyicisi API mümkün olan en kısa sürede kullanmaya başlamanızı öneriyoruz. Bu dil hizmetinizin performansını ve yeni Düzenleyicisi özelliklerden yararlanmak sağlar.  
  
## <a name="how-parameter-info-tooltips-work"></a>Parametre bilgisi araç ipuçları nasıl çalışır  
 Düzenleyici'de bir ifadeyi yazın, VSPackage yazılan deyimi tanımını içeren bir küçük araç ipucu pencere görüntüler. Örneğin, bir Microsoft Foundation sınıfları (MFC) deyimi yazarsanız (gibi `pMainFrame ->UpdateWindow`) ve parantez tuşuna tanımını görüntüleme yöntemi ipucu görünür parametreleri listeleme başlamaya `UpdateWindow` yöntemi.  
  
 Parametre bilgisi araç ipuçları genellikle deyim tamamlama ile birlikte kullanılır. Bunlar parametreleri veya diğer biçimlendirilmiş bilgileri yöntem adı ya da anahtar sözcük sonra diller için en kullanışlıdır.  
  
 Parametre bilgisi araç ipuçları komutu kişiler tarafından ele aracılığıyla dil hizmeti tarafından başlatılır. Kullanıcı karakter kesmeye dil hizmeti nesnesi uygulamalıdır <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirim ve metin görünümü için bir işaretçi geçirin, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> çağırarak uygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> yönteminde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> arabirimi. Komut filtresi kodu penceresine yazdığınız komutları kesintiye uğratır. Kullanıcıya parametre bilgilerini görüntülemek ne zaman bilmek komut bilgilerini izleyin. Deyim tamamlama, hata işaretçileri ve benzeri için aynı komutu filtresini kullanabilirsiniz.  
  
 Kendisi için dil hizmeti ipuçları sağlayabilir bir anahtar sözcük yazdığınızda dil hizmeti oluşturur bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> nesne ve çağrıları <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> yönteminde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> bir ipucu görüntülemek için IDE bildirmek için arabirim. Oluşturma <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> kullanarak nesne `VSLocalCreateInstance` ve coclass'ı belirterek `CLSID_VsMethodTipWindow`. `VsLocalCreateInstance` çağıran üstbilgi dosyası vsdoc.h içinde tanımlanan bir işlev `QueryService` yerel kayıt defterinde ve aramalar için `CreateInstance` için bu nesnede `CLSID_VsMethodTipWindow`.  
  
## <a name="providing-a-method-tip"></a>Bir yöntem ipucu sağlama  
 Bir yöntem ipucu sağlamak için arama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> yönteminde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> arabirimi, uygulamanıza geçirme <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> arabirimi.  
  
 Olduğunda, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> sınıfı çağrıldığında, yöntemlerinden aşağıdaki sırayla çağrılır:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     Konumu ve ilgili verileri uzunluğu geçerli metin arabelleğini döndürür. Bu araç ipucu penceresi verilerle saklamasını değil IDE bildirir.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     Başlangıçta görüntülenmesini istediğiniz yöntemi (sıfır tabanlı dizini) döndürür. Sıfır döndürürse, örneğin, daha sonra ilk aşırı yüklenmiş yöntemin başlangıçta sunulur.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     Geçerli bağlamda geçerli olan aşırı yüklenmiş yöntemler sayısını döndürür. Bu yöntem için 1'den büyük bir değer döndürürse, daha sonra metin görünümü yukarı ve aşağı ok sizin için görüntüler. Aşağı oku tıklatın, IDE çağırır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> yöntemi. Yukarı Ok tıklarsanız, IDE çağırır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> yöntemi.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     Parametre bilgisi araç ipucu metninin birkaç çağrı sırasında oluşturulan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> yöntemleri.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     Yönteminde görüntülemek için parametre sayısını döndürür.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     Görüntülenmesini istediğiniz aşırı ile karşılık gelen bir yöntem sayı döndürürse, bu yöntem, bir çağrı tarafından izlenen çağrılır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> yöntemi.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     Dil hizmetinizin yöntemi ipucu görüntülendiğinde Düzenleyicisi'ni güncelleştirmek için sizi bilgilendirir. İçinde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> yöntemi, aşağıdaki çağrı:  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     Çağrı aldığınız <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> yöntemi ipucu penceresini kapattığınızda yöntemi.