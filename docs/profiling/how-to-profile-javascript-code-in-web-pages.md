---
title: 'Nasıl yapılır: Web sayfalarında JavaScript kodu profil | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 007603f0695a658b6bfa6c1ab1173b4483004c13
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843929"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Nasıl yapılır: web sayfalarında profili JavaScript kodu

Visual Studio profil oluşturma araçları içinde yürütür JavaScript kodu için performans verilerini toplayabilir bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulaması, rasgele web sayfası ya da izleme profili oluşturma yöntemi kullanarak JavaScript uygulama. Internet Explorer 8 veya sonraki sürümünü gerektirir.

> [!WARNING]
> JavaScript UWP uygulamalarında profil için bkz: [JavaScript belleği](../profiling/javascript-memory.md) 

Performans oturum oluşturmak için profil oluşturma Sihirbazı'nı kullanabilirsiniz. İzleme yöntemini belirtin ve ardından Özellikler iletişim kutusunun araçları sayfasında seçeneğini performans oturumu için profil oluşturma JavaScript belirtin.

JavaScript profil belirttiğinizde, JavaScript kodu yürütmelerinin tarayıcıda ve [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sunucu üzerinde yürütülen kodu profili.

- İçin bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulaması, tarayıcıda yürüten hem JavaScript kodu ve [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sunucu üzerinde yürütülen kodu profili.

- Rastgele bir web sayfasını tarayıcıda yürütür JavaScript kodu profili.

## <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>ASP.NET web uygulaması projesinde profiline JavaScript

1. Açık [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Visual Studio'da web projesi.

2. Üzerinde **Çözümle** menüsünde tıklatın **başlatma performans Sihirbazı**.

3. Performans Sihirbazı'nın ilk sayfasında belirttiğiniz **Araçları** profili oluşturma yöntemi ve ardından **sonraki**.

4. Sihirbazın ikinci sayfasında geçerli proje hedefleri listesinde seçili olduğundan emin olun ve ardından **sonraki.**

5. Sihirbazın üçüncü sayfasında seçin **profil JavaScript** onay kutusunu işaretleyin ve ardından **sonraki**.

6. Sihirbazının dördüncü sayfasında, tıklatın **son** tarayıcıda web uygulamasını başlatmak için.

7. Profil oluşturmayı istediğiniz işlevselliği uygular.

8. Profil oluşturma oturumu sona erdirmek için tarayıcıyı kapatın.

### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Tek tek web sayfalarında JavaScript veya JavaScript uygulamaları profilini

1. Visual Studio'yu açın.

2. Üzerinde **Çözümle** menüsünde tıklatın **başlatma performans Sihirbazı**.

3. Performans Sihirbazı'nın ilk sayfasında belirttiğiniz **Araçları** profili oluşturma yöntemi ve ardından **sonraki**.

4. Sihirbazın ikinci sayfasında ASP.NET veya JavaScript uygulama'yı tıklatın ve ardından **sonraki.**

5. Sihirbazın üçüncü sayfasında:

    1. Sayfanın URL'sini yazın **hangi URL veya yol uygulamanızın çalışacağı** kutusu.

    2. Seçin **profil JavaScript** onay kutusunu işaretleyin ve ardından **sonraki**.

6. Sihirbazının dördüncü sayfasında, tıklatın **son** web sayfasını tarayıcıda başlatmak için.

7. Profil oluşturmayı istediğiniz işlevselliği uygular.

8. Profil oluşturma oturumu sona erdirmek için tarayıcıyı kapatın.