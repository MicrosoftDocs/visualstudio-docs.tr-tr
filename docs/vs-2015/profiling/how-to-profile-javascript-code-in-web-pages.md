---
title: 'Nasıl yapılır: Web sayfalarında JavaScript kod profil | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
ms.assetid: 37d02aad-ca4d-4eb0-bf66-ca3ecef31fbe
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f9def923e0cc012a37c02d24b67e807668ae976
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792118"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Nasıl yapılır: Web sayfalarında JavaScript kodu profili
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profil oluşturma araçları yürütülen JavaScript kodu için performans verilerini toplayabilir bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulaması, bir rastgele Web sayfası veya JavaScript uygulaması yöntemi profil oluşturma Araçları'nı kullanarak.  
  
 **Gereksinimler**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
-   Internet Explorer 8 veya üzeri.  
  
> [!WARNING]
>  Windows Store uygulamalarında JavaScript profili oluşturmak için aşağıdaki konulardan birine bakın:  
> 
> - [JavaScript işlev zamanlaması](http://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03) [uzak bir cihazda JavaScript işlev zamanlaması](http://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
>   -   [JavaScript işlev zamanlaması verilerini çözümleme](http://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
>   -  
  
 Performans oturumu oluşturmak için profil oluşturma Sihirbazı'nı kullanabilirsiniz. Araçlar yöntemini belirtin ve ardından JavaScript profil oluşturma performans oturumu Özellikleri iletişim kutusunun izleme sayfasındaki seçeneğini belirtin.  
  
 JavaScript profil oluşturma belirttiğinizde, her iki JavaScript kodu, yürütür tarayıcıda ve [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] sunucu üzerinde yürütülen kodu profili.  
  
-   İçin bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulaması, tarayıcıda yürüten iki JavaScript kodunu ve [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] sunucu üzerinde yürütülen kodu profili.  
  
-   Rastgele bir Web sayfası için tarayıcı içinde yürütülen JavaScript kod profil oluşturulan.  
  
### <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Bir ASP.NET Web uygulaması projesinde JavaScript profili oluşturmak için  
  
1.  İçinde [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]açın [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web projesi.  
  
2.  Üzerinde **Çözümle** menüsünü tıklatın **performans Sihirbazını Başlat**.  
  
3.  Performans Sihirbazı'nın ilk sayfasında belirttiğiniz **izleme** yöntemi profil oluşturma ve ardından **sonraki**.  
  
4.  Sihirbazın ikinci sayfasında, geçerli projenin hedefleri listesinde seçili olduğundan emin olun ve ardından **sonraki.**  
  
5.  Sihirbazın üçüncü sayfasında **JavaScript profili** onay kutusunu işaretleyin ve ardından **sonraki**.  
  
6.  Sihirbazının dördüncü sayfasında tıklayın **son** tarayıcıda Web uygulamasını başlatmak için.  
  
7.  Profil oluşturmak istediğiniz işlevi çalıştırın.  
  
8.  Profil oluşturma oturumunu sona erdirmek için tarayıcıyı kapatın.  
  
### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Tek tek Web sayfalarında JavaScript veya JavaScript uygulamaları profilini çıkarmak için  
  
1.  Açık [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)].  
  
2.  Üzerinde **Çözümle** menüsünü tıklatın **performans Sihirbazını Başlat**.  
  
3.  Performans Sihirbazı'nın ilk sayfasında belirttiğiniz **izleme** yöntemi profil oluşturma ve ardından **sonraki**.  
  
4.  Bir ASP.NET veya JavaScript uygulama sihirbazının ikinci sayfasında tıklayın ve ardından **sonraki.**  
  
5.  Sihirbazın üçüncü sayfasında:  
  
    1.  Sayfanın URL'sini yazın **uygulamanız hangi URL'de çalışacak** kutusu.  
  
    2.  Seçin **JavaScript profili** onay kutusunu işaretleyin ve ardından **sonraki**.  
  
6.  Sihirbazının dördüncü sayfasında tıklayın **son** tarayıcıda Web sayfasını başlatmak için.  
  
7.  Profil oluşturmak istediğiniz işlevi çalıştırın.  
  
8.  Profil oluşturma oturumunu sona erdirmek için tarayıcıyı kapatın.



