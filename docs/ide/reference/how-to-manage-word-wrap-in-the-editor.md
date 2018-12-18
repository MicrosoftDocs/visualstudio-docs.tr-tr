---
title: Sözcük kaydırma
ms.date: 11/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- editors, text viewing
- Code Editor, word wrap
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fc38d1ee5a8e5543675700c35cc0cb298aefad9
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349120"
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>Nasıl yapılır: düzenleyicide sözcük kaydırmayı yönetme

Ayarlayın ve silebileceği **sözcük kaydırmayı** seçeneği. Bu seçenek ayarlandığında, geçerli Kod Düzenleyicisi penceresinin genişliğini aşan bir uzun satır bölümü ve sonraki satırda görüntülenir. Örneğin, numaralandırma, satır kullanımını kolaylaştırmak için bu seçeneği temizlenirse, uzun satırları ucunda görmek için sağa kaydırma yapabilirsiniz.

> [!NOTE]
> Bu konu yalnızca Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio, sözcük kaydırma şu anda desteklemiyor.

## <a name="to-set-word-wrap-preferences"></a>Sözcük kaydırmayı tercihleri ayarlamak için

1.  Üzerinde **Araçları** menüsünde **seçenekleri**.

2.  İçinde **metin düzenleyici** klasörü seçin **genel** seçeneklerini **tüm diller** genel olarak bu seçeneği ayarlamak için alt.

     — veya —

     Seçin **genel** alt programlama dili için Seçenekler.

3.  Altında **ayarları**seçin veya temizleyin **sözcük kaydırmayı** seçeneği.

     Zaman **sözcük kaydırmayı** seçeneği belirlenmişse **sözcük kaydırma için görsel karakterleri Göster** seçeneği etkinleştirilir.

4.  Seçin **sözcük kaydırma için görsel karakterleri Göster** burada bir uzun satır sarmalar ikinci satıra bir dönüş ok göstergesi görüntülenmesini isterseniz seçeneği. Gösterge oklar görüntülenmemesi isterseniz bu seçeneği temizleyin.

    > [!NOTE]
    > Bu anımsatıcı okları kodunuza eklenmez; yalnızca görüntüleme amaçları için değildirler.

## <a name="known-issues"></a>Bilinen sorunlar

Burada Visual Studio için diğer düzenleyiciler farklı davranır sözcük kaydırmayı Not Defteri ++, Sublime Text veya Visual Studio Code biliyorsanız, aşağıdaki sorunlarından haberdar olmalı:

* [Tüm satırı Üçlü seçmek değil](https://developercommunity.visualstudio.com/content/problem/268989/triple-click-doesnt-select-whole-line-when-word-wr.html)
* [Kes komutu tüm satırı silmez.](https://developercommunity.visualstudio.com/content/problem/138259/cut-command-should-delete-logical-line.html)
* [End tuşuna basarak iki kez hareket sonlandırmak için imleci satırın](https://developercommunity.visualstudio.com/content/problem/138274/pressing-end-key-twice-should-move-cursor-to-end-o.html)

## <a name="see-also"></a>Ayrıca bkz.

- [Düzenleyiciyi Özelleştirme](../../ide/customizing-the-editor.md)
- [Metin Düzenleyici Seçenekleri iletişim Kutusu](../../ide/reference/text-editor-options-dialog-box.md)
- [Kod Düzenleyicisi özellikleri](../../ide/writing-code-in-the-code-and-text-editor.md)
