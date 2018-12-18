---
title: Web projesi temel bileşenleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb69eeb701ed5ce24259d203c0320c2635c96e4a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934528"
---
# <a name="web-project-essentials"></a>Web Projesi Temel Bileşenleri
Web projeleri, Web uygulamaları oluşturun. Akıllı Web sayfaları bir Web uygulaması oluşturmak için bir Web projesi kullanabilirsiniz. Akıllı bir Web sayfasında, isteğe bağlı Web sayfasını işler sunucu tarafındaki kod vardır.  
  
 Geleneksel programlama dilleri gibi kullanarak [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] veya [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], toplamak ve kullanıcıdan bilgi işlem, bir veritabanında saklamak ve benzeri için akıllı Web sayfaları oluşturabilirsiniz.  
  
- Arka plan kod model dosya uzantısı .aspx veya .asmx Web sayfalarıyla bağımlı kaynak kodu dosyaları ilişkilendirir. Örneğin, HelloWorld.aspx bağımlı kaynak kodu dosyası hello.aspx.cs olabilir.  
  
- Akıllı bir Web sayfasıyla ilgili sunucu tarafı kod Web sitesi/Bin klasöründe bulunan bir yürütülebilir dosyasına derlenir.  
  
- Belirli bir Web sayfası ile ilişkili olmayan yardımcı sınıfları gibi ek kaynak kodu dosyaları, Web sitesi /App_Code klasöründe bulunur.  
  
  -   Bir Web sitesi projesi (WSP) her akıllı Web sayfası için bir yürütülebilir dosya oluşturur. Ek yürütülebilir dosyalar /App_Code klasöründeki tüm kaynak kodu dosyasından oluşturulur.  
  
  -   Bir Web uygulaması projesi (WAP) tüm akıllı Web sayfalarının yanı sıra /App_Code klasördeki tüm kaynak dosyaları için kod birleştiren tek bir yürütülebilir dosya oluşturur.  
  
- Ayrı olarak Web sitesinin kendisinde bir Web projesi için çözüm dosyası bulunur. Varsayılan olarak çözüm dosyaları \Documents ve ayarları bulunur\\*hesabınız*\My belgeleri\\*\<Visual Studio ### >* \Projects\\ *YourWebSite*.  
  
  > [!NOTE]
  >  Web sitesinin Çözüm dosyasıyla tutmak istiyorsanız, hemen taşıyın ve yeniden açın.  
  
- Hiçbir çözüm dosyasını Visual Studio'da bir Web sitesini açın, yeni bir çözüm dosyası için otomatik olarak oluşturulur.  
  
- Web projeleri hiçbir proje dosyası var. Proje bilgileri çözüm dosyası, web.config dosyasını ve başka bir yerde saklanır.  
  
- Genel Özellikler otomatik olarak bir Web projesine eklerken Web Proje çözüm klasöründe bir depolama dosyası oluşturur.  
  
- Sayfa yönergesi kullanarak akıllı bir Web sayfası bir sunucu tarafı programlama dili ile ilişkilendirilmiş olabilir veya \<betik runat = "server" > etiketi.  
  
- Ayrıca, Web sayfaları, herhangi bir sayıda istemci tarafı komut dosyası blokları herhangi bir komut dosyası dilinde yazılmış olabilir.  
  
- Bir Web sitesi proje sistemi proje ve öğe şablonları ve kayıt ekleyerek uygulanan [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] proje.  
  
- WAP sistem bir proje türü olarak da adlandırılan bir proje alt uygulanır. [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] Proje WAP sistem oluşturmak için WAP alt tarafından markdown'lar. Proje alt türleri hakkında daha fazla bilgi için bkz. [proje alt türleri](../../extensibility/internals/project-subtypes.md).  
  
- Akıllı Web sayfası, HTML sunucu tarafı programlama dili ile birleştirir. Sunucu tarafı dil bağımsız dil adı verilir. Kapsanan bir dil desteği için Web Proje sistemi uygulamalıdır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> arabirimlerin ailesi.  
  
  -   Bir düzenleyicide kapsanan dili desteklemek için HTML dil hizmeti kapsanan dil kodu bir bağımsız dil hizmeti için görüntüleme erteleme gerekir.  
  
  -   Hata işaretçileri (kırmızı squigglies) her zaman, Kod Düzenleyicisi'nin birincil arabellek oluşturulmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Web Projeleri](../../extensibility/internals/web-projects.md)