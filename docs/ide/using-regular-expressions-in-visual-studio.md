---
title: Normal ifadeler kullanma
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vsregularexpressionhelp
- vs.regularexpressionhelp
- vs.wildcardsbuilder
- vs.netregularexpressionhelp
- vs.wildcards
helpviewer_keywords:
- regular expressions [Visual Studio]
- regular expressions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40983e4180db9530983217d581b898806dd85d27
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063804"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Visual Studio'da normal ifadeler kullanma

Visual Studio kullanan [.NET Framework normal ifadeleri](/dotnet/standard/base-types/regular-expressions) metin bulma ve değiştirme için.

## <a name="replacement-patterns"></a>Değiştirme desenleri

Numaralandırılmış yakalama grubu kullanmak için normal ifade deseninde ayraç grubuyla alın. Kullanım `$number`burada `number` bir değiştirme deseninde belirli, numaralı grubu belirtmek için 1'den başlayarak bir tamsayıdır. Örneğin, gruplanan normal ifadeyle `(\d)([a-z])` iki grupları tanımlar: ilk grubu tek bir ondalık basamak içeren ve ikinci grubu arasında tek bir karakter içeren **bir** ve **z**. İfade, aşağıdaki dizede dört eşleşme bulur: **1a 2b 3c 4d**. Değiştirme dizesi `z$1` yalnızca ilk grubu başvuruyor ve bir dizeye dönüştürür **z1 z2 z3 z4**.

Değiştirme desenlerinde kullanılan düzenli ifadeler hakkında daha fazla bilgi için bkz: [(.NET Kılavuzu) normal ifadelerdeki değişimler](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="regular-expression-examples"></a>Normal ifade örnekleri

Bazı örnekler şunlardır:

|Amaç|İfade|Örnek|
|-------------|----------------|-------------|
|(Satır sonu hariç) tek bir karakterle eşleştir|biçimindeki telefon numarasıdır.|`a.o` "Around" öğesinde "ARO" ve "about" öğesinde "abo" ancak değil "eri" "arasında" ile eşleşir.|
|Önünde gelen ifadenin sıfır veya daha çok tekrarı ile eşleştir (mümkün olduğu kadar çok karakterle Eşleştir)|*|`a*r` "rack" daki "r", "ark" içinde "ar" ve "aardvark", "aar" ile eşleşir.|
|Sıfır veya daha fazla kez herhangi bir karakterle eşleştir (joker karakter *)|.*|`c.*e` "comme" "racket", "comment" "comme" ve "Code" ve "code" ile eşleşir.|
|Önünde gelen ifadenin bir veya daha çok tekrarı ile eşleştir (mümkün olduğu kadar çok karakterle Eşleştir)|+|`e.+d` "eed" içindeki "eede" ile eşleşir ancak değil "ed" eşleşir.|
|Bir veya daha fazla (joker?) herhangi bir karakterle eşleştir|.+|`e.+e` "eede" ile eşleşir ancak değil "ee" içindeki "eede" ile eşleşir.|
|Önünde gelen ifadenin sıfır veya daha çok tekrarı ile eşleştir (mümkün olduğu kadar az karakterle Eşleştir)|*?|`e.*?e` "eede" ile eşleşir ancak "eede" içinde "ee" ile eşleşir.|
|Önünde gelen ifadenin bir veya daha çok tekrarı ile eşleştir (mümkün olduğu kadar az karakterle Eşleştir)|+?|`e.+?e` "Telefo" ve "erprise" ile "Kurumsal" ancak değil tüm "enterprise" kelimesinin eşleşir.|
|Eşleşme dizesini bir satırın veya dizenin başına bağlantı|^|`^car` yalnızca satırın başında göründüğünde "car" sözcüğü eşleştirir.|
|Eşleşme dizesini bir satırın sonuna Bağla|\r?$|`end\r?$` "yalnızca, bir satırın sonunda göründüğünde end" ile eşleşir.|
|Eşleşme dizesini dosyanın sonuna bağlantı|$|`end$` "yalnızca bu dosyanın sonunda göründüğünde end" ile eşleşir.|
|Bir kümedeki tek bir karakterle eşleştir|[abc]|`b[abc]` "ba", "bb" ve "bc" ile eşleşir.|
|Karakter aralığındaki herhangi bir karakterle eşleştir|[a-f]|`be[n-t]` "içinde"between","beneath"içinde" ben"ve"bes""beside", ancak"below"bet" eşleşir.|
|Yakalama ve parantez içinde yer alan ifadesi örtük olarak numaralandır|()|`([a-z])X\1` "aXa" ve "bXb" ancak değil "aXb" ile eşleşir. "\1", ilk ifade grubu "[a-z]" anlamına gelir.|
|Eşlemeyi geçersiz kıl|(?!abc)|`real(?!ity)` "gerçek" bir "realty" ve "really" eşleşir ancak değil içinde "gerçeklik." Ayrıca ikinci "real" (ancak değil ilk "real") "realityreal" içinde bulur.|
|Belirli bir karakter kümesinde olmayan herhangi bir karakterle eşleştir|[^ abc]|`be[^n-t]` "önce", "behind", "beh" içinde "bef" ile eşleşir ve "BEh" "below", ancak "beneath".|
|Önce ifadesi veya bir sonraki eşleştirin.|&#124;|`(sponge\|mud) bath` "sponge bath" ve "mud bath" ile eşleşir|
|Eğik çizgiyi takip eden karakterden çıkış yapın| \\ |`\^` bir karakterle eşleşir ^.|
|Önceki karakterin veya grubun oluşum sayısını belirtin|{x}, burada x oluşum sayısıdır|`x(ab){2}x` "xababx" ile eşleşir ve `x(ab){2,3}x` "xababx" ve "xabababx ile eşleşir" ancak değil "xababababx" ile eşleşir.|
|Bir Unicode karakter sınıfı metinde eşleştirin. Unicode karakter sınıfları hakkında daha fazla bilgi için bkz.<br /><br /> [Unicode standart 5.2 karakter özellikleri](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}, "X" değerinin Unicode numarası olduğu.|`\p{Lu}` "T" ve "Thomas Doe" içinde "D" ile eşleşir.|
|Bir sözcük sınırını eşleştir|\b (bir karakter sınıfı dışında `\b` bir sözcük sınırını belirler ve bir karakter sınıfı içinde `\b` Geri Al ile eşleşir.)|`\bin` "içinde" inside "içinde" değil "pinto" eşleşir.|
|Satır sonu (yeni bir satır tarafından izlenen diğer bir deyişle, bir satır başı) eşleştirin.|\r?\n|`End\r?\nBegin` "Son" ve "olduğunda yalnızca"End"bir satırdaki son dizeyse ve"Begin"sonraki satırdaki ilk dizedir Begin" ile eşleşir.|
|Herhangi bir alfasayısal karakteri eşleştir|\w|`a\wd` eşleşme "Ekle" ve "a1d ile eşleşir" ancak "a d".|
|Bir boşluk karakteriyle Eşleştir.|(? ([^ \r\n])\s)|`Public\sInterface` ' % s'ifadesinin "Ortak arabirim" ile eşleşir.|
|Bir sayısal karakterle eşleştir|\d|`\d` eşleşiyor ve "3", "3456" 23" içinde" 2"ve"1"içinde"1".|
|Unicode karakterini eşleştir|\uXXXX nerede XXXX Unicode karakter değerini belirtir.|`\u0065` "e" karakteriyle eşleşir.|
|Tanımlayıcı eşleştir|\b [\_\w-[0-9]] [\_\w]*\b|Eşleşme "type1" değil "& type1" veya "#define".|
|Tırnak işaretleri içindeki bir dizeyle eşleştir|((\\".+?\\")&#124;('.+?'))|Tek veya çift tırnak içindeki herhangi bir dizeyle eşleşir.|
|Onaltılık bir sayıyla eşleştir|\b0[xx]([0-9a-FA-F]\)\b|"0xc67f ile eşleşir" ancak "0xc67fc67f" ile eşleşir.|
|Eşleşme tamsayıları ve ondalık sayıları|\b[0-9]*\\.\*[0-9]+\b|"1.333" eşleşir.|

> [!TIP]
> Windows işletim sistemlerinde satırların çoğu "\r\n" (bir yeni satırın izlediği bir satır başı) bitmelidir. Bu karakterler görünür değildir ancak düzenleyicide bulunur ve .NET normal ifade hizmetine iletilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Metin bulma ve değiştirme](../ide/finding-and-replacing-text.md)
