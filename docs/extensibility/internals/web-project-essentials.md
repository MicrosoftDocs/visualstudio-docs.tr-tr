---
title: Web projesi temelleri | Microsoft Docs
description: Web projelerinin Visual Studio 'da nasıl çalıştığı hakkında iç ayrıntıları öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9442dcdd460e1213c3c07ee87a5ea2e0d7099072
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085708"
---
# <a name="web-project-essentials"></a>Web Projesi Temel Bileşenleri
Web projeleri Web uygulamaları oluşturur. Web projesini, akıllı Web sayfaları olan bir Web uygulaması oluşturmak için kullanabilirsiniz. Akıllı bir Web sayfasında, Web sayfasını istek üzerine işleyen sunucu tarafı kodu vardır.

 Veya gibi geleneksel programlama dillerini kullanarak, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] bir kullanıcıdan bilgi toplamak ve işlemek, bir veritabanında depolamak ve bu şekilde devam etmek Için akıllı Web sayfaları oluşturabilirsiniz.

- Arka plan kod modeli, bağımlı kaynak kodu dosyalarını. aspx veya. asmx uzantılı web sayfalarıyla ilişkilendirir. Örneğin, Hello. aspx bağımlı kaynak kodu dosyası Hello. aspx. cs olabilir.

- Akıllı bir Web sayfasıyla ilişkili sunucu tarafı kodu, Web sitesi/bin klasöründe bulunan yürütülebilir bir dosyaya derlenir.

- Belirli bir Web sayfasıyla ilişkilendirilmemiş yardımcı sınıflar gibi ek kaynak kodu dosyaları Web sitesi/App_Code klasöründe bulunur.

  - Web sitesi projesi (WSP) her akıllı Web sayfası için bir yürütülebilir dosya oluşturur. Ek yürütülebilir dosyalar/App_Code klasöründeki herhangi bir kaynak kod dosyasından oluşturulur.

  - Web uygulaması projesi (WAP), tüm akıllı Web sayfaları için kodu ve/App_Code klasöründeki tüm kaynak dosyaları birleştiren tek bir yürütülebilir dosya oluşturur.

- Web projesinin çözüm dosyası, Web sitesinden ayrı olarak bulunur. Varsayılan olarak, çözüm dosyaları \Documents yolunda ve Settings \\  \\ *\<Visual Studio ####>* \Documents \projects \\ *yourwebsite* konumundadır.

  > [!NOTE]
  > Çözüm dosyasını Web sitesiyle birlikte tutmak istiyorsanız, dosyayı buraya taşıyın ve yeniden açın.

- Visual Studio 'da çözüm dosyası olmayan bir Web sitesi açarsanız, bu dosya için otomatik olarak yeni bir çözüm dosyası oluşturulur.

- Web projelerinin proje dosyaları yok. Proje bilgileri çözüm dosyasında, web.config dosyasında ve başka bir yerde saklanır.

- Web projesine genel özellikler eklemek, otomatik olarak Web projesi çözüm klasöründe bir depolama dosyası oluşturur.

- Akıllı bir Web sayfası, Page yönergesini veya etiketini kullanarak sunucu tarafı programlama diliyle ilişkilendirilebilir \<script runat="server"> .

- Ayrıca, Web sayfalarında herhangi bir komut dosyası dilinde yazılmış sayıda istemci tarafı betik bloğu bulunabilir.

- Proje ve öğe şablonları ve projeye kayıt eklenerek bir Web sitesi proje sistemi uygulanır [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] .

- WAP sistemi, proje türü olarak da adlandırılan bir proje alt türü olarak uygulanır. [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)]WAP sistemi oluşturmak için proje WAP alt türü tarafından düzlüyor. Proje alt türleri hakkında daha fazla bilgi için bkz. [Proje alt türleri](../../extensibility/internals/project-subtypes.md).

- Bir akıllı Web sayfası, HTML 'yi sunucu tarafı programlama diliyle birleştirir. Sunucu tarafı diline, içerilen dil denir. Kapsanan bir dili desteklemek için, Web projesi sisteminin arabirimlerin ailesini uygulaması gerekir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> .

  - Bir düzenleyicide bulunan dili desteklemek için, HTML dil hizmetinin içerilen dil kodunu içerilen dil hizmetine görüntülemesi gerekir.

  - Hata işaretçileri (kırmızı dalgalı Glar), her zaman kod düzenleyicisinin birincil arabelleğinde oluşturulmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Projeleri](../../extensibility/internals/web-projects.md)
