---
title: Etki Alanına Özgü Dil Çözümü Şablonu Seçme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: d2977d546d463a8c21446a3643cff7ef49a01fb1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908848"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Etki Alanına Özgü Dil Çözümü Şablonu Seçme
Bir etki alanına özgü dil çözümü oluşturmak için etki alanına özgü dil Tasarımcısı Sihirbazı'nda kullanılabilir olan çözüm şablonlarından birini seçin. Oluşturmak istediğiniz dili en çok benzeyen bir şablon seçerek başlangıç çözüme yapmanız değişiklikleri en aza indirebilirsiniz.

 Aşağıdaki çözüm şablonları, etki alanına özgü dil Tasarımcısı Sihirbazı'nda mevcuttur.

|Şablon|Özellikler|Açıklama|
|-|-|-|
|Sınıf diyagramları|-Bölme şekilleri<br />-Sınıf devralma<br />-İlişki devralma<br />-Şekil devralma<br />-İlişki özellikleri|Varlıklar ve ilişkiler özelliklere sahip, etki alanına özgü dil içeriyorsa, bu çözüm şablonu kullanın. Bu şablon, UML sınıf diyagramları benzer bir etki alanına özgü dil oluşturur. Temel sınıflar ve arabirimler, ilişkilendirme, Genelleştirme ve uygulama ilişkileri birlikte varlıklardır. Bir sınıf veya arabirim öznitelik listesini içeren bir kutu olarak görünür.|
|Bileşen diyagramları|-Bağlantı noktaları|Alana özgü dilinizi bileşenleri, diğer bir deyişle, bir yazılım sisteminin bölümleri içeriyorsa, bu çözüm şablonu kullanın. Bu şablon, UML Bileşen diyagramları benzer bir etki alanına özgü dil oluşturur. Ana bileşenlerini ve dış bileşenlerin küçük şekiller görünür olan bağlantı noktaları varlıklardır.|
|Görev akış diyagramları|-Resim ve geometrik şekiller<br />-   *Kulvarlar*|İş akışları, durumları ve dizileri, etki alanına özgü dil içeriyorsa, bu çözüm şablonu kullanın. Bu şablon, UML etkinlik diyagramları benzer bir etki alanına özgü dil oluşturur. Bir etkinlik temel aldığı varlıktır ve etkinlikler arasında geçiş ana ilişkidir. Şablonu diğer başlangıç durumu, son duruma ve bir eşitleme çubuğu gibi çeşitli öğeleri içerir.|
|Minimal dil|-Bir sınıfı ve şekli<br />-Bir ilişkisi ve Bağlayıcısı|Bu çözüm şablonu, etki alanına özgü dil diğer şablon benzemez kullanın. Bu şablon, iki sınıf ve temsil edilen bir ilişki sahip bir etki alanına özgü dil oluşturur **araç kutusu** olarak **kutusu** ve **satırı**. Sınıfı ve ilişki her bir örnekte dize özelliği vardır.|
|En az WinForm Tasarımcısı|-Küçük bir model.<br />-Modeli görüntüler bir Windows formu.|Bir DSL grafik Tasarımcı yerine bir Windows Form bağlanır, bir uygulama oluşturmak istiyorsanız bu şablonu kullanın.<br /><br /> Dil için kullanıcı arabirimi olarak görev yapar form Dsl\UI klasöründedir.<br /><br /> Form tasarımcısı açmadan önce projeyi oluşturmalısınız.<br /><br /> Daha fazla bilgi için [Windows Forms-Based etki alanına özgü dil oluşturma](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|En az bir WPF Tasarımcısı|-Küçük model<br />-Modeli görüntüler bir Windows Presentation Foundation kullanıcı arabirimi|Bir DSL bir WPF kullanıcı arabirimi yerine bir grafik Tasarımcı bağlanır, bir uygulama oluşturmak istiyorsanız bu şablonu kullanın.<br /><br /> Kullanıcı arabirimi için tasarımcı Dsl\UI klasöründedir.<br /><br /> Kullanıcı Arabirimi Tasarımcısı açmadan önce projeyi oluşturmalısınız.<br /><br /> Daha fazla bilgi için [WPF-Based etki alanına özgü dil oluşturma](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|DSL kitaplığı|-En az kitaplığı|Diğer DSL tanımlarına aktarılabilen bir kısmi bir DSL tanımını oluşturmak istiyorsanız bu şablonu kullanın.|

## <a name="see-also"></a>Ayrıca Bkz.

- [Etki Alanına Özgü Dil Araçlarına Genel Bakış](../modeling/overview-of-domain-specific-language-tools.md)
