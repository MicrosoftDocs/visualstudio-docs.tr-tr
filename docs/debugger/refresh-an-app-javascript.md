---
title: Bir UWP uygulaması yenileme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: a45564f34fe0167821febb511a023c01f7c38358
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476286"
---
# <a name="refresh-a-uwp-app-in-visual-studio"></a>Visual Studio'da bir UWP uygulaması Yenile
  
 Hatalarını ayıkladığınız ve seçerek JavaScript kullanarak bir UWP uygulaması yenileme sırasında kodunuzu değişiklik yapabilirsiniz **yenileme Windows uygulaması** düğmesini **hata ayıklama** araç. Bu düğmesini seçerek uygulama hata ayıklayıcı durdurup olmadan yeniden yükler. Yenileme özelliği HTML, CSS ve JavaScript kodu değiştirin ve hızlı bir şekilde sonucunu görmenizi sağlar. Bu özellik, UWP uygulamaları için desteklenir.  
  
 Yenileme değil, uygulama durumunu korumak veya uygulamanız için aşağıdaki değişiklikleri yansıtacak:  
  
-   Paket bildiriminde belirtilen görüntülerine değişiklikler dahil, paket bildirim dosyasının değişiklikleri.  
  
-   Başvuru ekleme veya bir SDK başvurusu kaldırılması gibi değişiklikler veya Windows çalışma zamanı bileşenleri (.winmd dosyaları) değiştirir.  
  
-   Kaynak dizeleri .resjson dosyalarında değişiklikler gibi değiştirir.  
  
-   Proje dosyası yolu adı değişiklikleri, yeni proje dosyalarını veya silinen dosyaların sonucunda ortaya çıkan değiştirir.  
  
-   Proje ve öğe özelliği gibi değişiklikler seçilen hata ayıklama cihazdaki değişiklikler veya paket eylemi (Özellikler penceresinde) bir dosya için yapılan değişiklikler.  
  
> [!IMPORTANT]
>  Başvuruları değiştirme, paket bildirimi değiştirin ya da önceki listesinde belirtilen diğer değişiklik durdurun ve HTML, CSS ve JavaScript kaynak dosyalarını güncelleştirmek için hata ayıklayıcı yeniden sahip.  
  
### <a name="to-refresh-an-app"></a>Bir uygulama yenilemek için  
  
1.  Visual Studio'da açıkken, UWP projesini ile seçin **yerel makine** hata ayıklama hedefi olarak.
  
     ![Select hata ayıklama hedef listesi](../debugger/media/js_select_target.png "JS_Select_Target")  
  
3.  Uygulamayı hata ayıklama modunda çalıştırmak için F5 tuşuna basın.  
  
4.  Visual Studio'ya geçin. 
  
5.  UWP uygulamanızı giriş sayfasının HTML bazıları düzenleyin.
  
7.  Tıklatın **yenileme Windows uygulaması** düğmesi, bu gibi görünen: ![yenileme Windows Uygulama düğmesi](../debugger/media/js_refresh.png "JS_Refresh"). (Veya F4 tuşuna basın.)  
  
8.  Uygulamasına geçin. Uygulama geri yüklenir ve güncelleştirilmiş HTML uygulamayı işlemek için kullanılır.
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hızlı Başlangıç: HTML ve CSS hata ayıklama](../debugger/quickstart-debug-html-and-css.md)