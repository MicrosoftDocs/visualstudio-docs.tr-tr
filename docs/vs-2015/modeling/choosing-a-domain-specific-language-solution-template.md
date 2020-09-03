---
title: Etki alanına özgü dil çözümü şablonu seçme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6522e3a1ad10f221f0ed7fc1761559ee9bc3f9b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668345"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Etki Alanına Özgü Dil Çözümü Şablonu Seçme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Alana özgü dil çözümü oluşturmak için Alana Özgü Dil Tasarımcısı sihirbazında bulunan çözüm şablonlarından birini seçin. Oluşturmak istediğiniz dile en yakından benzeyen şablonu seçerek, başlangıç çözümünde yapmanız gereken değişiklikleri en aza indirmenize olanak sağlayabilirsiniz.

 Alana Özgü Dil Tasarımcısı sihirbazında aşağıdaki çözüm şablonları mevcuttur.

> [!NOTE]
> Şablonların amacı, başlangıç DSL sağlamaktır. Sınıf ve Bileşen diyagramları adlı şablonlar tam UML diyagramları değildir. Bir UML modeli oluşturmak isterseniz, tek bir model etrafında tümleştirilmiş bir diyagramlar kümesi sağlayan UML modelleme araçlarını göz önünde bulundurun. Bunlar genişletilebilir ve ModelBus kullanarak DSL 'niz ile tümleştirilebilir. Daha fazla bilgi için bkz. [uygulamanız için modeller oluşturma](../modeling/create-models-for-your-app.md).

|Şablon|Özellikler|Description|
|--------------|--------------|-----------------|
|Sınıf diyagramları|-Bölme şekilleri<br />-Sınıf devralma<br />-İlişki devralma<br />-Shape devralma<br />-İlişki özellikleri|Bu çözüm şablonunu, etki alanına özgü diliniz özellikleri olan varlıklar ve ilişkiler içeriyorsa kullanın. Bu şablon, UML Sınıf Diyagramlarına benzeyen, etki alanına özgü bir dil oluşturur. Ana varlıklar, ilişkilendirme, Genelleştirme ve uygulama ilişkileriyle birlikte sınıflar ve arayüzlerdir. Bir sınıf veya arabirim, özniteliklerin listesini içeren bir kutu olarak görünür.|
|Bileşen diyagramları|-Bağlantı noktaları|Bu çözüm şablonunu, etki alanına özgü diliniz bileşenleri, diğer bir deyişle yazılım sisteminin parçalarını içeriyorsa kullanın. Bu şablon, UML bileşen diyagramlarına benzeyen, etki alanına özgü bir dil oluşturur. Ana varlıklar, bileşenlerin dışında küçük şekiller olarak görünen bileşenler ve bağlantı noktalarıdır.|
|Görev akış diyagramları|-Görüntü ve geometri şekilleri<br />-   *Lardır*|Etki alanına özgü diliniz iş akışları, durumlar veya diziler içeriyorsa bu çözüm şablonunu kullanın. Bu şablon, UML etkinlik diyagramlarını benzeyen, etki alanına özgü bir dil oluşturur. Ana varlık bir etkinliktir ve ana ilişki etkinlikler arasında geçiştir. Şablon, başlangıç durumu, son durum ve eşitleme çubuğu gibi çeşitli diğer öğeleri içerir.|
|En az dil|-Bir sınıf ve şekil<br />-Bir ilişki ve bağlayıcı|Etki alanına özgü diliniz diğer şablonlara benzemezse bu çözüm şablonunu kullanın. Bu şablon iki sınıfa ve bir ilişkiye sahip olan ve **araç** **kutusunda Box** ve **Line**olarak temsil edilen bir etki alanına özgü dil oluşturur. Sınıfının ve ilişkinin her biri bir örnek dize özelliğine sahiptir.|
|Minimal WinForm Tasarımcısı|-Küçük bir model.<br />-Modeli görüntüleyen bir Windows formu.|Bu şablonu, bir DSL 'nin grafik tasarlayıcısı yerine bir Windows form 'a bağlandığı bir uygulama oluşturmak istiyorsanız kullanın.<br /><br /> Dil için Kullanıcı arabirimi olarak davranan form Dsl\uıklasöründedir.<br /><br /> Form tasarımcısını açmadan önce projeyi derlemeniz gerekir.<br /><br /> Daha fazla bilgi için bkz. [Windows Forms tabanlı etki alanına özgü dil oluşturma](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|En az WPF Tasarımcısı|-Küçük bir model<br />-Modeli görüntüleyen bir Windows Presentation Foundation Kullanıcı arabirimi|Bir DSL 'nin grafik tasarlayıcısı yerine WPF Kullanıcı arabirimine bağlandığı bir uygulama oluşturmak istiyorsanız bu şablonu kullanın.<br /><br /> Kullanıcı arabirimine yönelik tasarımcı Dsl\uiklasöründedir.<br /><br /> UI tasarımcısını açmadan önce projeyi derlemeniz gerekir.<br /><br /> Daha fazla bilgi için bkz. [WPF tabanlı etki alanına özgü dil oluşturma](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|DSL kitaplığı|-En az bir kitaplık|Diğer DSL tanımlarına aktarılabilecek kısmi bir DSL tanımı oluşturmak istiyorsanız bu şablonu kullanın.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Etki Alanına Özgü Dil Araçlarına Genel Bakış](../modeling/overview-of-domain-specific-language-tools.md)
