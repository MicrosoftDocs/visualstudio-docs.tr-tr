---
title: 'Nasıl yapılır: IIS özellik ayarlarını doğrulama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4639055fe9320c8fd1bf1b2575bca323642dd17f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742070"
---
# <a name="how-to-verify-iis-property-settings"></a>Nasıl Yapılır: IIS Özellik Ayarlarını Doğrulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IIS Yönetim Aracı'nı kullanarak bir Web uygulaması için özellikleri ayarlayabilirsiniz. Bu ayarlar doğrulanıyor genellikle sorun giderme gerekli bir adım, bu nedenle bu özellikleri çalıştırmak, uygulama için doğru şekilde ayarlamanız gerekir.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-check-iis-settings-for-the-web-application"></a>IIS Web uygulamasının ayarlarını denetlemek için  
  
1.  Açık **Yönetimsel Araçlar** penceresi: üzerinde **Başlat** menüsünde **programlar**ve ardından **Yönetimsel Araçlar**. Varsa **Yönetimsel Araçlar** görünmez **programlar** menüsü, ardından içinde Ara **Denetim Masası**.  
  
    -   Windows 2000'de seçin **Internet Hizmetleri Yöneticisi'ni**.  
  
    -   Windows XP'de seçin **Internet Information Services**.  
  
    -   Windows Server 2003'te çift **sunucunuzu yönetin**.  
  
         **Sunucunuzu yönetin** penceresi açılır. Altında **uygulama sunucusu**, tıklayın **bu uygulama sunucusunu yönetmek**.  
  
         **Uygulama sunucusu** penceresi açılır. Açık **Internet Information Services (IIS) Yöneticisi'ni** sol bölmedeki düğüm.  
  
2.  İletişim kutusunda, ağaç denetimi düğümü makineniz için tıklayın. Tıklayın **Web siteleri** düğümünü ve Web uygulamasının düğümünü seçin. Bir Web sitesi düğümü ve bu nedenle bir eşdüzeyi ya da olacak **varsayılan Web sitesi** düğümü veya bir sanal dizin düğümü altında varolan bir Web sitesi düğümü.  
  
3.  Web uygulamasına sağ tıklayın ve kısayol menüsünde **özellikleri**.  
  
4.  Web uygulaması için güvenlik ayarlarını doğrulayın:  
  
    1.  Web uygulamasındaki **özellikleri** penceresinde tıklayın **dizin güvenliği** sekmesine ve tıklayın **Düzenle**.  
  
    2.  İçinde **kimlik doğrulama yöntemleri** iletişim kutusunda **anonim erişimi etkinleştir** ve **tümleşik Windows kimlik doğrulaması** henüz seçili değilse.  
  
    3.  Tıklayın **Tamam** kapatmak için **kimlik doğrulama yöntemleri** iletişim kutusu.  
  
5.  Bir ATL Sunucu uygulaması için DEBUG fiilini, ISAPI uzantısı ile ilişkili olduğunu doğrulayın. Daha fazla bilgi için [nasıl yapılır: uzantı ile hata ayıklama fiili ilişkilendirmek](http://msdn.microsoft.com/en-us/50d261d3-4bd4-41c0-b44e-3591086f121e).  
  
6.  İçin bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uygulama, uygulama kümesinde bir uygulama adı için sanal klasör emin **Internet Information Services (IIS) Yöneticisi'ni**, **Internet Hizmetleri Yöneticisi'ni** veya  **Internet Information Services**.  
  
    1.  Web uygulamasındaki **özellikleri** penceresinde **dizin** sekmesinde, uygulamayı sanal bir dizinde ise veya **giriş dizini** sekmesinde uygulama ise, bir Web sitesi.  
  
    2.  Doğrulayın adlarında **yerel yol** uygulamanın gerçekten dağıtılacağı dizinin adıyla aynıdır.  
  
    3.  Altında **uygulama ayarları**, uygulamayı içeren kök dizinin adını yazın.  
  
    4.  Tıklayın **Tamam** kapatmak için **özellikleri** iletişim kutusu.  
  
7.  İçin bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uygulama tıklayın **ASP.NET** doğrulayın ve sekme doğru sürümünü [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] belirtilir.  
  
8.  Tıklayın **Tamam** kapatmak için **özellikleri** iletişim kutusu.  
  
9. Tıklayın **Tamam** kapatmak için **Internet Information Services (IIS) Yöneticisi'ni**, **Internet Hizmetleri Yöneticisi'ni**, veya **Internet Information Services**iletişim kutusu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorun giderme](../debugger/debugging-web-applications-troubleshooting.md)



