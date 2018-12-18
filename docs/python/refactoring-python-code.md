---
title: Python kodu yeniden düzenleyin
description: Visual Studio tanımlayıcıları yeniden adlandırarak Python kodu yeniden düzenleme içeri aktarmalar ekleme yöntemleri ayıklama kolaylaştırır ve kullanılmayan kaldırma içeri aktarır.
ms.date: 11/12/2018
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
ms.openlocfilehash: 7293e966f937368df62dc9fa0049ac1d75a19b45
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063023"
---
# <a name="refactor-python-code"></a>Python kodu yeniden düzenleyin

Visual Studio otomatik olarak dönüştürmek ve Python kaynak kodunuzu Temizleme için çeşitli komutlar sağlar:

- [Yeniden adlandırma](#rename) seçilen bir sınıf, yöntem veya değişken adı yeniden adlandırır.
- [Extrahovat metodu](#extract-method) seçilen kod yeni bir yöntem oluşturur
- [İçeri aktarma eklemek](#add-import) eksik bir içeri aktarma eklemek için bir akıllı etiket sağlar
- [Kullanılmayan içeri aktarmaları Kaldır](#remove-unused-imports) kullanılmayan içeri aktarmaları kaldırır

## <a name="rename"></a>Rename

1. Seçin ve yeniden adlandırmak istediğiniz tanımlayıcısı sağ **Yeniden Adlandır**, o tanımlayıcıda giriş işaretini yerleştirin veya seçin **Düzenle** > **yeniden düzenleyin**  >  **Yeniden Adlandır** menü komutu (**F2**).
2. İçinde **Yeniden Adlandır** görüntülenen iletişim tanıtıcısı ve seçin için yeni bir ad girin **Tamam**:

   ![Yeni bir tanımlayıcı ad sor yeniden adlandır](media/code-refactor-rename-1.png)

3. Sonraki iletişim kutusunda, dosyaları ve kodunuzu yeniden adlandırma uygulanacağı durumlarda seçin; Değişikliğinizi önizlemek için herhangi tek bir örneğine seçin:

   ![Yeniden adlandırma değişiklikleri uygulamak yeri seçmek için iletişim kutusu](media/code-refactor-rename-2.png)

4. Seçin **Uygula** kaynak kod dosyalarınızı değişiklik yapma. (Bu eylem geri alınabilir.)

## <a name="extract-method"></a>Ayıklama metodu

1. Kod veya ayrı bir yöntem ayıklamak için ifade satırları seçin.
2. Seçin **Düzenle** > **yeniden düzenleme** > **yöntemi Ayıkla** menü komutu ya da türü **Ctrl** + **R** > **M**.
3. Görüntülenen iletişim kutusunda, ayıklayın ve herhangi bir kapanış değişkeni konumu gösteren yeni bir yöntem adı girin. Değişkenleri Kapatılmak üzere işaretli değil yöntem bağımsız değişkenleri ile etkinleştirilir:

   ![İletişim yöntemi Ayıkla](media/code-refactor-extract-method-1.png)

4. Seçin **Tamam** ve kodu uygun şekilde değiştirilir:

   ![Yöntemi ayıklama etkisi](media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>İçeri aktarma ekleyin

Giriş işaretini bir tanımlayıcıda oturumda bilgi türü yerleştirdiğinizde, Visual Studio komutlarının gerekli bir Akıllı Etiket Ekle (kod solundaki ampul simgesini) sağlar. `import` veya `from ... import` deyimi:

![İçeri aktarma akıllı etiket ekleme](media/code-refactor-add-import-1.png)

Visual Studio sunar `import` en üst düzey paketler ve geçerli proje ve standart kitaplık modülleri için tamamlamalar. Visual Studio'nun sunduğu `from ... import` modülü üyelerinin yanı sıra alt modüller ve subpackages için tamamlamalar. Tamamlamalar, İşlevler, sınıflar veya dışarı aktarılan verileri içerir. İki seçenekten birini seçerek ekler deyime dosyasının en üstüne diğer içeri aktarmalar sonra ya da mevcut bir uygulamasına `from ... import` aynı modül zaten içeri aktarılmış IF ifadesi.

![Bir içeri aktarma ekleme sonucu](media/code-refactor-add-import-2.png)

Visual Studio, diğerinin içine alınır ancak içeri aktarma yapmak Modül alt olmayan modüller gibi bir modülde gerçekte tanımlanmayan üyeleri filtrelemek çalışır. Örneğin, birçok modülleri kullanan `import sys` yerine `from xyz import sys`, içeri aktarma tamamlama görmüyor `sys` modülleri eksik olması durumunda bile diğer modüllerden bir `__all__` dışlar üye `sys`.

Benzer şekilde, Visual Studio diğer modüllerden veya yerleşik ad alanı içeri aktarılan işlevleri filtreler. Örneğin bir modülü içeri aktarır `settrace` işlevini `sys` ardından aldığınız, o modülden teorik modülü. Ancak kullanmak en iyisidir `import settrace from sys` doğrudan ve Visual Studio, özellikle o ifadeyi sunar.

Son olarak, bir normal dışlanıp ancak diğer değerleri, (adı modülünde bir değer örneğin atandığından) dahil, Visual Studio hala sahip alma dışlar. Bu davranış, değeri, başka bir modülde tanımlandı ve bu nedenle ek atama dışa verilmediğinden ayrıca bir kukla değer olabilir çünkü olarak aktarılması olmamalıdır varsayar.

## <a name="remove-unused-imports"></a>Kullanılmayan içeri aktarmaları Kaldır

Kod yazarken, sonunda daha kolaydır `import` deyimleri hiç kullanılmayan modüller için. Visual Studio kodunuzu analiz eder, çünkü otomatik olarak belirleyebilir olup olmadığını bir `import` deyimi, içeri aktarılan ad ifade oluştuğu kapsamı içinde aşağıdaki mı kullanıldığına bakarak gereklidir.

Herhangi bir yeri seçin ve Düzenleyici içinde sağ **içeri aktarmaları Kaldır**, size sağlayan kaldırmak için seçenekleri **tüm kapsamlar** veya yalnızca **geçerli kapsamdaki**:

![İçeri aktarmalar menü Kaldır](media/code-refactor-remove-imports-1.png)

Visual Studio, ardından kod uygun değişiklikleri yapar:

![İçeri aktarmalar'ı kaldırmanın etkisi](media/code-refactor-remove-imports-2.png)

Visual Studio için denetim akışı hesaplamaz dikkat edin. önce bir adı kullanarak bir `import` deyimi adı aslında kullanıldıysa olarak kabul edilir. Visual Studio ayrıca yoksayar tüm `from __future__` alır, bir sınıf tanımı içinde de gerçekleştirilen içeri aktarmalar `from ... import *` deyimleri.
