---
title: Sözcük kaydırma
description: Kod düzenleyicisinde sözcük kaydır seçeneğini açma ve kapatma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/07/2018
ms.topic: how-to
helpviewer_keywords:
- word wrap
- editors, text viewing
- Code Editor, word wrap
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 57e218dadfe04d8cad034f2638ffefb9346e5a41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894601"
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>Nasıl yapılır: düzenleyicide sözcük kaydırmayı yönetme

**Sözcük kaydır** seçeneğini ayarlayabilir ve temizleyebilirsiniz. Bu seçenek ayarlandığında, uzun bir çizginin, kod düzenleyici penceresinin geçerli genişliğini aşan kısmı sonraki satırda görüntülenir. Örneğin, satır numaralandırma kullanımını kolaylaştırmak için bu seçenek temizlendiğinde, uzun çizgilerin uçlarını görmek için sağa kaydırma yapabilirsiniz.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [kaynak Düzenleyicisi: sözcük kaydır](/visualstudio/mac/source-editor#word-wrap).

## <a name="to-set-word-wrap-preferences"></a>Sözcük kaydırmayı tercihleri ayarlamak için

1. **Araçlar** menüsünde **Seçenekler**’i belirleyin.

2. **Metin düzenleyici** klasöründe, bu seçeneği küresel olarak ayarlamak Için **tüm diller** alt klasöründeki **genel** seçenekleri seçin.

     veya

     Programlamadaki dilin alt klasöründeki **genel** seçenekleri seçin.

3. **Ayarlar** altında **sözcük kaydır** seçeneğini belirleyin veya temizleyin.

     **Sözcük kaydır** seçeneği belirlendiğinde **sözcük kaydırması Için görsel glifleri göster** seçeneği etkinleştirilmiştir.

4. Uzun bir çizginin ikinci bir satıra kaydırılacağını gösteren bir dönüş oku göstergesini görüntülemeyi tercih ediyorsanız, **sözcük kaydırma için görsel glifleri göster** seçeneğini belirleyin. Gösterge oklarını görüntülememayı tercih ediyorsanız bu seçeneği temizleyin.

    > [!NOTE]
    > Bu anımsatıcı okları kodunuza eklenmez; Bunlar yalnızca görüntüleme amaçlıdır.

## <a name="known-issues"></a>Bilinen sorunlar

Not defteri + +, alt açık metin veya Visual Studio Code Word sarması hakkında bilgi sahibiyseniz, Visual Studio 'Nun diğer düzenleyicilerle farklı davrandığı aşağıdaki sorunlardan haberdar olun:

* [Üçlü tıklama tüm satırı seçmeyin](https://developercommunity.visualstudio.com/content/problem/268989/triple-click-doesnt-select-whole-line-when-word-wr.html)
* [Bitiş tuşuna iki kez basıldığında imleç satır sonuna taşınamaz](https://developercommunity.visualstudio.com/content/problem/138274/pressing-end-key-twice-should-move-cursor-to-end-o.html)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../../ide/writing-code-in-the-code-and-text-editor.md)
