---
title: Dotfuscator Community Edition (CE)
ms.date: 10/10/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive koruma, koruma, community edition, gizleme, .NET, ücretsiz, Visual Studio 2017
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Visual Studio 2017'de dahil edilen ücretsiz Dotfuscator Community Edition ile .NET uygulamalarınızı nasıl Koruyabileceğiniz hakkında bilgi edinin.
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: douge
ms.openlocfilehash: d6cac51aaa73053dc0e1f306288d8198fdacccfd
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219063"
---
# <a name="dotfuscator-community-edition-ce"></a>Dotfuscator Community Edition (CE)

*PreEmptive koruma - Dotfuscator* kapsamlı .NET uygulama koruması, bir kolayca güvenli yazılım geliştirme yaşam döngünüzü içine sığar sağlar.
Masaüstü, mobil, sunucu ve güvenli ticari sırlar ve diğer fikri mülkiyet (IP) yardımcı olmak için katıştırılmış uygulamalar Ayıkla sağlamlaştırmak ve korumak için korsanlığı ve sahtekarlığın azaltmak ve yetkisiz hata ayıklama ve izinsiz kullanıma karşı koruma kullan.
Dotfuscator derlenmiş bütünleştirilmiş ek programlama veya hatta kaynak koduna erişim iznine gerek kalmadan çalışır.

![PreEmptive koruma - Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>Koruma neden önemlidir

Önemlidir **fikri mülkiyetinizi korumanıza** (IP).
Uygulama kodlarınızdaki IP kabul edilebilir, tasarım ve uygulama ayrıntılarını içerir.
Ancak, .NET Framework üzerinde yerleşik uygulamaları [önemli meta verileri ve üst düzey Ara kod içeren][assemblies], bunları tersine mühendislik daha kolay hale getirir, yalnızca birini çoğu ücretsiz kullanarak otomatik Araçlar.
Kesintiye ve durdurma tersine mühendislik, yetkisiz IP açığa çıkmasını önlemek, yapabilir kodunuzu ticari sırlar içerdiğini gösterir.
Dotfuscator olabilir [karartmak] [ obfuscation] .NET derlemelerinizin tersine mühendislik, özgün uygulamanın davranışını korurken azaltabilir.

Ayrıca önemlidir **uygulamanızı bütünlüğünü korumak**.
Ters mühendislik ek olarak, uygulamanızı korsanlığını, çalışma zamanında uygulamanın davranışını değiştirmek veya verileri işlemek kötü aktörleri deneyebilir.
Dotfuscator yeteneği uygulamanızla ekleme [algılama ve yanıtlama yetkisiz kullanım][checks]oynama, üçüncü taraf hata ayıklama ve kökü belirtilmiş cihazlar dahil olmak üzere.

Dotfuscator güvenli yazılım geliştirme yaşam döngüsü içinde nasıl uyguladığı hakkında daha fazla bilgi için bkz: PreEmptive Solutions [SDL uygulama koruma sayfası][sdl-protection].

## <a name="about-dotfuscator-ce"></a>Dotfuscator CE'yi hakkında

Kopyanızı Microsoft Visual Studio 2017'in bir kopyasını içeren  **_PreEmptive koruma - Dotfuscator_ Community Edition**, Dotfuscator CE, kişisel kullanım için ücretsiz olarak da bilinir.
Dotfuscator CE ile Visual Studio 2017 dahil sürümü yükleme hakkında yönergeler için bkz: [yükleme sayfasına][install].

Dotfuscator CE sunan bir dizi [yazılım koruması ve sağlamlaştırma] [ software-protection] geliştiriciler, mimarlar ve test edenler için hizmetleri.
Örnekleri [.NET karartma] [ obfuscation] ve diğer [uygulama koruması] [ app-protection] Dotfuscator CE içinde bulunan özellikleri şunlardır:

* *[Yeniden adlandırma] [ renaming]*  ters mühendislik derlenmiş derlemelerin daha zor hale getirmek için tanımlayıcı.
* *[Koruma kurcalamaya] [ tamper]*  değiştirilen uygulamaların yürütülmesini algılamak ve sonlandırma veya yanıt oturumları değiştirilmiş.
* *[Anti-hata ayıklama] [ debug]*  ek bir hata ayıklayıcı, çalışan bir uygulama algılama ve yanıt sonlandırmak için hata ayıklama oturumları.
* *[Cihaza hologram] [ root]*  uygulamayı kök erişim izni verilmiş Android cihazında çalışıp çalışmadığını algılar ve sonlandırma veya bu cihazlarda oturum yanıt vermesi için.
* *[Uygulama sona erme davranışları] [ shelflife]*  "son yaşam" tarih kodlamak ve süresi dolan uygulama oturumlarını sonlandırır.

Bunlar, uygulama koruma stratejinizi nasıl uyduğunu dahil olmak üzere, bu özellikler hakkında ayrıntılar için bkz. [özellikleri sayfasında][capabilities].

Dotfuscator CE temel korumayı,-hazır sunar.
Daha fazla uygulama koruma önlemleri Dotfuscator CE kayıtlı kullanıcıları ve kullanıcıları için kullanılabilir *PreEmptive koruma - Dotfuscator* Professional Edition, dünyanın önde gelen [.NET belirsizleştirici] [net-obfuscator].
Dotfuscator geliştirme hakkında daha fazla bilgi için bkz: [yükseltmeler sayfasında][upgrades].

## <a name="getting-started"></a>Başlarken

Visual Studio'dan Dotfuscator CE'ı kullanmaya başlamak için yazın `dotfuscator` içine **hızlı başlatma** Arama çubuğuna (Ctrl + Q).

* Dotfuscator CE zaten yüklü değilse, **hızlı başlatma** getirir *menü* Dotfuscator CE kullanıcı arabirimini başlatmak için seçeneği. Ayrıntılar için bkz [tam Dotfuscator CE Kullanıcı Kılavuzu'nun Başlarken sayfası][get-started].
* Dotfuscator CE henüz yüklü değilse **hızlı başlatma** ilgili getirir *yükleme* seçeneği. Bkz: [yükleme sayfasına] [ install] Ayrıntılar için.

Ayrıca Al **en son sürümü** Dotfuscator CE, [preemptive.com Dotfuscator yüklemeler sayfasında][download].

## <a name="full-documentation"></a>Tüm belgeler

Bu sayfada ve onun alt Dotfuscator CE'ın özellikleri, üst düzey bir genel bakış sağlayan yanı [aracı yüklemek için yönergeler][install].

Bkz: [preemptive.com adresindeki tam Dotfuscator CE Kullanıcı Kılavuzu] [ full] dahil olmak üzere, ayrıntılı kullanım yönergeleri için [Dotfuscator CE kullanıcı arabirimi kullanmaya başlamak nasıl] [ get-started].

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/dotnet/standard/assembly-format
[software-protection]:  https://www.preemptive.com/software-protection
[obfuscation]:  https://www.preemptive.com/obfuscation
[app-protection]:  https://www.preemptive.com/application-protection
[sdl-protection]:  https://www.preemptive.com/solutions/SDL-App-Protection
[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[install]:  install.md
[capabilities]:  capabilities.md
[upgrades]:  upgrades.md

[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/index.html
