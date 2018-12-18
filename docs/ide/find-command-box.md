---
title: Bulma komut kutusu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c5e11d83ea0c87bae058f5421c424922fa389a9c
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752417"
---
# <a name="findcommand-box"></a>Bul/Komut kutusu

Aramak için metin ve Visual Studio komutları çalıştırmak **Bul/komut** kutusu. **Bul/komut** kutusu araç çubuğu denetimi olarak hala kullanılabilir, ancak artık varsayılan olarak görünür. Görüntüleyebileceğiniz **Bul/komut** seçerek kutusunu **Düğme Ekle veya Kaldır** üzerinde **standart** araç çubuğu ve ardından seçme **Bul**.

Çalıştırmak için bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] komutu, büyüktür ile yazdığınızdan daha (**>**) oturum.

**Bul/komut** kutusuna girilen son 20 öğeleri korur ve bir aşağı açılan listede görüntüler. Seçerek listeyi gidebilirsiniz **ok tuşları**.

![Bul&#47;komut kutusu](../ide/media/findcommandbox.png)

## <a name="searching-for-text"></a>Metin arama

Varsayılan olarak metinde belirttiğinizde, **Bul/komut** kutusuna ve ardından **Enter** anahtar, Visual Studio belirtilenseçeneklerinikullanarakgeçerlibelgeveyaaraçpenceresiarar**Dosyalarda Bul** iletişim kutusu. Daha fazla bilgi için bkz: [bulma ve metin değiştirme](../ide/finding-and-replacing-text.md).

## <a name="entering-commands"></a>Komutları girme

Kullanılacak **Bul/komut** tek bir sorun için kutusunu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] komutunu veya diğer ad metin arama yerine, bir büyük komutuyla yazdığınızdan daha (**>**) simgesi. Örneğin:

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

Alternatif olarak, ayrıca kullanabileceğiniz **komutu** girin ve tek veya birden çok komut yürütmek için penceresi. Bazı komutlar veya diğer adlar girilen ve tek başına yürütülebilir; Başkalarının kendi sözdizimi değişkenlerinde gerekli sahip. Bağımsız değişkenleri sahip komutları bir listesi için bkz: [Visual Studio komutları](../ide/reference/visual-studio-commands.md).

## <a name="escape-characters"></a>Çıkış karakterleri

Bir şapka (**^**) karakter komutunda anlamına karakter hemen sonrasında tam anlamıyla yerine bir denetim karakteri olarak yorumlanır. Bu düz tırnak işaretleri eklemek için kullanılabilir (**"**), boşluk, başında Yatık çizgi, belirliyorsanız düzeltme işaretleri veya diğer değişmez değer karakterleri bir parametre veya anahtar değeri, anahtar adlarını dışında. Örneğin:

```
>Edit.Find ^^t /regex
```

İç veya dış tırnak işaretleri olup bir şapka aynı çalışır. Bir şapka satırında son karakter ise, yoksayılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Komut penceresi](../ide/reference/command-window.md)
- [Metin bulma ve değiştirme](../ide/finding-and-replacing-text.md)