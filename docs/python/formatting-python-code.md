---
title: Python kodu biçimlendirme
description: Visual Studio otomatik olarak Python kodu aralığı, deyimleri, sarmalama ve açıklamalar gibi biçimlendirebilirsiniz.
ms.date: 10/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 452dc1104147e5b29dd38790cbfa726ad0de7b1f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052199"
---
# <a name="format-python-code"></a>Python kodu biçimlendirme

Visual Studio, hızlı bir şekilde önceden yapılandırılmış biçimlendirme seçeneklerini eşleşecek şekilde yeniden biçimlendirme kodu sağlar.

- Bir seçim biçimlendirmek için: seçin **Düzenle** > **Gelişmiş** > **seçimi Biçimlendir** veya basın **Ctrl** + **E** > **F**.
- Tüm dosya biçimine: seçin **Düzenle** > **Gelişmiş** > **belgeyi Biçimlendir** veya basın **Ctrl** + **E** > **D**.

Seçenekleri aracılığıyla ayarlanır **Araçları** > **seçenekleri** > **metin düzenleyici** > **Python**  >  **Biçimlendirme** ve onun iç içe geçmiş sekmeler. Seçmenize gerek **tüm ayarları göster** görünmesini Bu seçenekler için:

![Biçimlendirme seçenekleri Visual Studio'da Python](media/options-editor-formatting.png)

Biçimlendirme seçenekleri varsayılan olarak ayarlanmış bir üst eşleştirilecek [CESARETLENDİRİCİ 8 Stil Kılavuzu](https://www.python.org/dev/peps/pep-0008/). **Genel** sekmesini biçimlendirme uygulandığında belirler; diğer üç sekme ayarları, bu makalede açıklanmıştır.

[Visual Studio'da Python desteği](installing-python-support-in-visual-studio.md) de faydalı ekler [ **dolgu açıklama paragraf** ](#fill-comment-paragraph-command) komutunu **Düzenle**  >   **Gelişmiş** bir sonraki bölümde açıklandığı gibi menüsü.

## <a name="spacing"></a>Aralığı

**Aralık** denetimler burada boşluklar eklenir veya çeşitli dil yapılarının kaldırıldı. Her bir seçeneğin üç olası değer vardır:

- Denetleme: aralık uygulanan sağlar.
- Temizlenmiş: herhangi bir boşluğu kaldırır.
- Belirsiz: özgün biçimlendirme yerinde bırakır.

Örnek çeşitli seçenekleri için aşağıdaki tabloda verilmiştir:

| Sınıf tanımları seçeneği | İşaretli | Temizlenmiş |
| --- | --- | --- | 
| **Tabanları listesi ile bir sınıf bildirimin adı arasındaki boşluk Ekle** | `class X (object): pass` | `class X(object): pass` | 
| **Tabanları listesi parantezlerinin içine boşluk Ekle** | `class X( object ): pass` | `class X(object): pass` |
| **Boş tabanları listesi parantezlerinin içine boşluk Ekle** | `class X( ): pass` | `class X(): pass` |

<br/>

| İşlev tanımları seçeneği | İşaretli | Temizlenmiş |
| --- | --- | --- |
| **Bir işlev bildiriminin adı ve parametre listesi arasına boşluk Ekle** | `def X (): pass` | `def X(): pass` | 
| **Parametre listesi parantezlerinin içine boşluk Ekle** | `def X( a, b ): pass` | `def X(a, b): pass` |
| **Boş parametre listesi parantezlerinin içine boşluk Ekle** | `def X( ): pass` | `def X(): pass` |
| **Varsayılan parametre değerlerini '=' çevresinde boşluk Ekle** | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| **Dönüş ek açıklama işleçlerden önce ve sonra boşluk Ekle** | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| İşleçler seçeneği | İşaretli | Temizlenmiş |
| --- | --- | --- |
| **İkili işleçler etrafına boşluklar Ekle** | `a + b` | `a+b` |
| **Atamalar etrafına boşluklar Ekle** | `a = b` | `a=b` |

<br/>

| İfade boşluk seçeneği | İşaretli | Temizlenmiş |
| --- | --- | --- |
| **Bir işlev çağrısı kişinin adı ve bağımsız değişken listesinin arasına boşluk Ekle** | `X ()` | `X()` |
| **Boş bağımsız değişken listesi parantezlerinin içine boşluk Ekle** | `X( )` | `X()` |
| **Bağımsız değişken listesi parantezlerinin içine boşluk ekleyin** | `X( a, b )` | `X(a, b)` |
| **İfade parantezlerinin içine boşluk ekleyin** | `( a )` | `(a)` |
| **Boş demet parantezlerinin içine boşluk Ekle** | `( )` | `()` |
| **Tanımlama grubu parantezlerinin içine boşluk Ekle** | `( a, b )` | `(a, b)` |
| **Boş köşeli ayraçların içine boşluk Ekle** | `[ ]` | `[]` |
| **Listelerin köşeli ayraçlar içine boşluk Ekle** | `[ a, b ]` | `[a, b]` |
| **Açma köşeli ayraç önce boşluk Ekle** | `x [i]` | `x[i]` |
| **Köşeli ayraçlar içine boşluk Ekle** | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>Deyimler

**Deyimleri** seçenekleri denetlemek diğer Pythonic formlar çeşitli açıklamaalarını otomatik yeniden yazma.

| Seçenek | Biçimlendirme önce | Biçimlendirme sonrasında |
| --- | --- | --- |
| **İçeri aktarılan modülleri yeni satıra Yerleştir** | `import sys, pickle` | `import sys`<br/>`import pickle` |
| **Gereksiz noktalı Kaldır** | `x = 42;` | `x = 42` |
| **Birden çok deyim yeni satırlara Yerleştir** | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |

## <a name="wrapping"></a>Sarmalama

**Sarmalama** , ayarlamanıza imkan sağlar **en fazla açıklama genişlik** (varsayılan: 80). Varsa **kaydırma çok geniş açıklamalar** seçeneği ayarlanır, Visual Studio, en fazla genişlik aşmayacak şekilde açıklamaları yeniden biçimlendirir.

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```

## <a name="fill-comment-paragraph-command"></a>Yorum paragraf komutu doldurun

**Düzen** > **Gelişmiş** > **dolgu açıklama paragraf** (**Ctrl**+**E**  >  **P**) yeniden akış ve kısa çizgiler birbirine birleştirmek ve uzun olanlarla bozucu açıklama metni biçimlendirir.

Örneğin:

```python
# foo
# bar
# baz
```

yapılan değişiklikler:

```python
# foo bar baz
```

```python
# This is a very long long long long long long long long long long long long long long long long long long long comment
```

yapılan değişiklikler:

```python
# This is a very long long long long long long long long long long long long
# long long long long long long long comment
```
