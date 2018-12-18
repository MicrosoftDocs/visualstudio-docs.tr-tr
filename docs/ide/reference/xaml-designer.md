---
title: XAML Tasarımcısı seçenekler sayfası
ms.date: 03/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.XAMLDesigner
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 52691c0b49c74bd39fa97ec8d297ffb823ba705c
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388367"
---
# <a name="xaml-designer-options-page"></a>XAML Tasarımcısı seçenekler sayfası

Kullanım **XAML Tasarımcısı** öğeler ve öznitelikler XAML belgelerinizde nasıl biçimlendirileceğini belirtmek için bir seçenekler sayfası. Bu sayfayı açmak için seçin **Araçları** menüsünü seçip **seçenekleri**. Erişim için **XAML Tasarımcısı** özellik sayfasında **XAML Tasarımcısı** düğümü. Belgeyi açtığında, XAML Tasarımcısı ayarları uygulanır. Bu nedenle ayarlarında değişiklik yaparsanız, değişiklikleri görmek için Visual Studio'yu kapatıp gerekir.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [ayarlarına](../environment-settings.md#reset-settings).

## <a name="enable-xaml-designer"></a>XAML Tasarımcısı'nı etkinleştir

Bu ayar, seçili olduğunda, XAML Tasarımcısı'nı etkinleştirir. XAML Tasarımcısı bir görsel çalışma alanı için XAML belgeleri düzenlemesine olanak sağlar. Visual Studio'da, kaynakları ve veri bağlama, IntelliSense gibi belirli işlevleri XAML Tasarımcısı etkinleştirilmesini gerektirir.

Aşağıdaki ayarlar, yalnızca XAML Tasarımcısı etkin olduğunda geçerlidir. Bu seçeneği değiştirirseniz, Visual Studio ayarın etkili olması için yeniden başlatmanız gerekir.

## <a name="default-document-view"></a>Varsayılan belge görünümü

Tasarım görünümü XAML belgeleri yüklendiğinde görünür olup olmadığını denetlemek için bu ayarı kullanın.

|||
|-|-|
|**Kaynak Görünümü**|Yalnızca XAML kaynak XAML Görünümü'nde görüntülenip görüntülenmeyeceğini belirtir. Bu, büyük belge yüklenirken kullanışlıdır.|
|**Tasarım görünümü**|Yalnızca bir görsel XAML görünümünde XAML Tasarımcısı görüntülenip görüntülenmeyeceğini belirtir.|
|**Bölünmüş Görünüm**|Hem visual XAML Tasarımcısı ve XAML kaynak diğerinden XAML Görünümü'nde görünüp görünmeyeceğini belirtir (konum temelinde **bölünmüş yönlendirmesi** ayar).|

## <a name="split-orientation"></a>Bölünmüş yönlendirmesi

XAML Tasarımcısı'nı ne zaman ve nasıl bir XAML belgesi düzenlenirken görünür denetlemek için bu ayarı kullanın. Bu ayarlar yalnızca geçerli **varsayılan belge görünümü** ayarlanır **Bölünmüş Görünüm**.

|||
|-|-|
|**Dikey**|XAML kaynak XAML görünümü sol tarafında görünür ve XAML Tasarımcısı'nı diğer tarafta görüntülenir.|
|**Yatay**|XAML Tasarımcısı'nı XAML görünümü üst kısmında görünür ve XAML kaynak altında görünür.|
|**Default**|XAML belgesi belgenin projenin hedeflediği platform için önerilen bölünmüş yönlendirmesi kullanır. Çoğu platformda bunun eşdeğeri olan **yatay**.|

## <a name="zoom-by-using"></a>Kullanarak Yakınlaştır

Yakınlaştırma bir XAML belgesi düzenlenirken nasıl çalıştığını belirlemek için bu ayarı kullanın.

|||
|-|-|
|**Fare tekerleği**|XAML Tasarımcısı'nda, fare tekerleğini kaydırarak yakınlaştırın.|
|**CTRL + fare tekerleği**|XAML Tasarımcısı'nda, fare tekerleğini kaydırma yaparken CTRL tuşuna basarak yakınlaştırın.|
|**Alt + fare tekerleği**|XAML Tasarımcısı'nda, fare tekerleğini kaydırma yaparken ALT tuşuna basarak yakınlaştırın.|

Bu ayarlar, bir XAML belgesi düzenlenirken Tasarımcısı davranışını belirler.

|||
|-|-|
|**Oluşumda etkileşimli öğeleri otomatik olarak adlandırın**|Bir tasarımcı eklediğinizde, varsayılan bir ad için yeni bir etkileşimli öğesi sağlanıp sağlanmayacağını belirtir.|
|**Düzen özelliklerini öğe oluşturma sırasında otomatik olarak Ekle**|Eklediğinizde, Tasarımcı için düzen özelliklerini yeni bir öğe için sağlanan olup olmadığını belirtir.|
|**Başarımız düzeni kullanma**|Şu anda seçili denetimi en yakın üst kapsayıcının kenarlarına hizalar olup olmadığını belirtir. Bu onay kutusu işaretli değilse, Denetim hizalamaları taşıma işlemi sırasında değiştirmeyin veya oluşturma işlemi.|
|**Araç kutusu öğeleri otomatik olarak doldurur.**|Kullanıcı denetimleri ve geçerli çözüme özel denetimleri araç kutusunda otomatik olarak gösterilip gösterilmeyeceğini belirtir.|

## <a name="settings-blend-only"></a>Ayarları (yalnızca Blend)

Blend kullanarak XAML dosyalarını düzenlerken ayarlarını belirlemek için bu seçenekleri kullanın.

|||
|-|-|
|**Kullanarak Yakınlaştır**|XAML Tasarımcısı'nda, fare tekerleğini kaydırarak veya fare tekerleğini kaydırma yaparken CTRL ya da ALT tuşuna basarak yakınlaştırın.|
|**Birim türü**|Tasarımcı üzerinde ölçümleri noktaları veya piksel göre belirtir. Evrensel Windows uygulamaları noktaları desteklenmediği, birimi otomatik olarak piksel ise dönüştürülür **noktaları** seçilir.|

## <a name="artboard-blend-only"></a>Çalışma yüzeyine (yalnızca Blend)

Blend'de XAML belgeleri düzenlerken XAML Tasarımcısı davranışını belirlemek için bu ayarları kullanın.

### <a name="snapping"></a>Yaslama

|||
|-|-|
|**Yaslama kılavuzunu göster**|Bu seçenek belirlendiğinde, kılavuz çizgiler denetimleri hizalamanıza yardımcı olmak için tasarımcıda görünür. Bu kılavuz için tasarımcı ek eklenen denetimleri olduğunda **çizgilerine ya** seçeneği belirlenir.|
|**Kılavuz çizgilerine Daya**|Denetimler eklendiğinde veya tasarımcı geçici bir çözüm taşınmış, bunlar çizgilerine Daya.|
|**Kılavuz çizgisi aralığı**|Kılavuz çizgilerinin piksel veya noktaları arasındaki boşluğu belirtir (tarafından belirlenen şekilde **tür birimleri** ayar).|
|**Dayama çizgilerine Daya**|Denetimleri dayama çizgilerine birleştirilip birleştirilmeyeceğini belirtir.|
|**Varsayılan kenar boşluğu**|Zaman **dayama çizgilerine Daya** etkinleştirildiğinde, piksel veya nokta cinsinden denetim ve dayama çizgileri arasındaki boşluğu belirtir (tarafından belirlenen şekilde **tür birimleri** ayar).|
|**Varsayılan doldurma**|Zaman **dayama çizgilerine Daya** etkinleştirildiğinde, Denetim ve dayama çizgileri arasında ek boşluk piksel veya noktaları belirtir (tarafından belirlenen şekilde **tür birimleri** ayar).|

### <a name="animation"></a>Animasyon

Bir uyarı bağımlı (hızlandırılmayan) görünüp görünmediği Blend içinde animasyon etkinleştirilip belirlemek için bu ayarı kullanın.

### <a name="effects"></a>Etkiler

XAML Tasarımcısı'nda dosyaları XAML düzenleme olduğunda efektler Blend kullanarak işlenir olup olmadığını belirlemek için bu ayarları kullanın.

|||
|-|-|
|**Efektler Oluştur**|Etkileri XAML tasarımcıdaki XAML dosyaları düzenlerken Blend kullanarak işlenip işlenmeyeceğini belirtir.|
|**Yakınlaştırma eşiği**|Yakınlaştırma yüzdesini belirtir hangi etkileri ne zaman işleme içinde **işleme etkileri** onay kutusunun seçili. Bu ayar ötesinde yakınlaştırma, efektler artık XAML Tasarımcısı'nda oluştur.|

## <a name="see-also"></a>Ayrıca bkz.

- [WPF'de XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [İzlenecek Yol: İlk WPF masaüstü uygulamam](/dotnet/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application)