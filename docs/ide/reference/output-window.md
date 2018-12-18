---
title: Çıktı Penceresi
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.build.output
- vs.debug.output
- vs.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51fcd9ece62afca8c5369c813d5ca8e5314dafe6
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670890"
---
# <a name="output-window"></a>Çıktı penceresi

**Çıkış** penceresi, tümleşik geliştirme ortamında (IDE) çeşitli özellikler için durum iletilerini görüntüler. Açmak için **çıkış** menü çubuğunda, pencere **görünümü** > **çıkış**, veya basın **Ctrl** +  **Alt**+**O**.

## <a name="toolbar"></a>Araç Çubuğu

Aşağıdaki denetimler araç çubuğunda gösterilen **çıkış** penceresi.

### <a name="show-output-from"></a>Çıktıyı Göster

Görüntülemek için bir veya daha fazla çıkış bölmeleri görüntüler. Birkaç bölmeleri bilgilerinin hangi Araçlar IDE içinde kullanılan bağlı olarak, kullanılabilir **çıkış** pencere iletilerini kullanıcıya teslim etmek için.

### <a name="find-message-in-code"></a>Kodda ileti Bul

Ekleme noktasını, Kod Düzenleyicisi'nde seçili derleme hatası içeren satıra taşır.

### <a name="go-to-previous-message"></a>Önceki iletiye Git

Odak değişiklikleri **çıkış** penceresinde önceki derleme hatası ve ekleme noktasını Kod Düzenleyicisi'nde hata oluşturan içeren satıra taşır.

### <a name="go-to-next-message"></a>Sonraki iletiye Git

Odak değişiklikleri **çıkış** sonraki pencereyi derleme hatası ve ekleme noktasını Kod Düzenleyicisi'nde hata oluşturan içeren satıra taşır.

### <a name="clear-all"></a>Tümünü temizle

Tüm metni temizler **çıkış** bölmesi.

### <a name="toggle-word-wrap"></a>Sözcük kaydırmayı Aç/Kapat

Sözcük kaydırma özelliğini açar ve kapatır **çıkış** bölmesi. Sözcük kaydırma etkin olduğunda, uzun girdileri görüntüleme alanının genişletir metin satırında görüntülenir.

## <a name="output-pane"></a>Çıkış bölmesi

**Çıkış** bölmesinde seçili **çıktıyı Göster** liste belirtilen kaynak çıktı görüntüler.

## <a name="route-messages-to-the-output-window"></a>Rota iletilerini çıkış penceresine

Görüntülenecek **çıkış** içinde bir proje oluşturduğunuzda penceresi **seçenekleri** iletişim kutusundaki **projeler ve çözümler** > **genel**  sayfasında **derleme başladığında çıkış Göster penceresi**. Düzenleme için bir kod dosyası açıkken, ardından **sonraki iletiye Git** ve **önceki ileti** üzerinde **çıkış** girişleri seçilecek penceresi araç çubuğu  **Çıkış** bölmesi. Bunu yaparken, ekleme noktasını, seçilen sorunun oluştuğu kod satırına Kod Düzenleyicisi atlar.

Bazı IDE özellikleri ve içinde çağrılan komutlarda [komut penceresi](../../ide/reference/command-window.md) çıktılarını için teslim **çıkış** penceresi. Dış çıktısını araçları gibi *.bat* ve *.com* genellikle komut penceresinde gösterilen dosyaları yönlendirileceğini bir **çıkış** seçtiğinizdebölmesi **Çıkış penceresini kullanma** seçeneğini [dış araçları yönetme](../../ide/managing-external-tools.md). İletileri diğer birçok türde görüntülenebilen **çıkış** bölmelerinde. Hedef veritabanında bir saklı yordamda Transact-SQL söz dizimi işaretlendiğinde, örneğin, sonuçları görüntülenir **çıkış** penceresi.

Kendi uygulamalarınızı çalışma zamanında tanılama iletileri yazmak için de programlayabileceğiniz bir **çıkış** bölmesi. Bunu yapmak için üyeleri kullanan <xref:System.Diagnostics.Debug> sınıfı veya <xref:System.Diagnostics.Trace> sınıfını <xref:System.Diagnostics> ad alanı .NET Framework sınıf kitaplığı. Üyeleri <xref:System.Diagnostics.Debug> çözüm veya projenin hata ayıklama yapılandırmaları oluşturduğunuzda sınıfı görünen çıkış; üyeleri <xref:System.Diagnostics.Trace> sınıfı görüntü çıktısı hata ayıklama veya yayın yapılandırmaları oluşturduğunuzda. Daha fazla bilgi için [çıkış penceresindeki tanılama iletileri](../../debugger/diagnostic-messages-in-the-output-window.md).

C++'da, özel derleme adımları oluşturma ve derleme olayları, uyarıları ve hataları görüntülenir ve sayılı **çıkış** bölmesi. Tuşuna basarak **F1** uygun bir Yardım konusu, bir çıkış satıra görüntüleyebilirsiniz. Daha fazla bilgi için [özel derleme adımı çıkışını biçimlendirmek](/cpp/ide/formatting-the-output-of-a-custom-build-step-or-build-event).

## <a name="scroll-behavior"></a>Kaydırma davranışı

İçinde autoscrolling kullanırsanız **çıkış** penceresi ve ardından autoscrolling durdurur, fareyi veya ok tuşlarını kullanarak gidin. Autoscrolling sürdürmek için basın **Ctrl**+**son**.

## <a name="see-also"></a>Ayrıca bkz.

- [Çıkış penceresindeki tanılama iletileri](../../debugger/diagnostic-messages-in-the-output-window.md)
- [Nasıl yapılır: çıkış penceresini denetleme](https://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858)
- [Derleme ve oluşturma](../../ide/compiling-and-building-in-visual-studio.md)
- [Derleme yapılandırmalarını anlama](../../ide/understanding-build-configurations.md)
- [Sınıf kitaplığına genel bakış](/dotnet/standard/class-library-overview)