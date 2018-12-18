---
title: 'CA1704: Tanımlayıcılar doğru yazılmalıdır'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 710e18f4ce8199c76c34683c510d3a64160544e6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916914"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: Tanımlayıcılar doğru yazılmalıdır

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Kategori|Microsoft.Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep

Tanımlayıcı adı Microsoft Yazım kitaplığı tarafından tanınmayan bir veya daha fazla sözcükler içeriyor. Bu kural değil oluşturucular veya özel adlı üyeleri get gibi denetleyin ve özellik erişimcisi ayarlayın.

## <a name="rule-description"></a>Kural açıklaması

Bu kural tanımlayıcısını belirteçlere ayrıştırır ve her belirteç yazımını denetler. Ayrıştırma algoritması şu dönüşümleri gerçekleştirir:

- Büyük harfler, yeni bir belirteç başlatın. Örneğin, MyNameIsJoe "Benim", "Ad", "", "Can" için tokenizes.

- Birden çok büyük harfler için yeni bir belirteç son büyük harf başlatır. Örneğin, "GUI", "Düzenleyicisi" GUIEditor tokenizes.

- Baştaki ve sondaki kesme kaldırılır. Örneğin, "gönderene" 'sender' tokenizes.

- Alt çizgi, bir belirteç sonu belirtmek ve kaldırılır. Örneğin, "Hello", Hello_world tokenizes "world".

- Katıştırılmış ve işaretlerini kaldırılır. Örneğin, & mat tokenizes "biçimlendirmek için".

## <a name="language"></a>Dil

Yazım denetimi şu anda yalnızca İngilizce tabanlı kültürü sözlükler karşı denetler. Proje dosyası projenizde kültürünü ekleyerek değiştirebilirsiniz **CodeAnalysisCulture** öğesi.

Örneğin:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Bir İngilizce tabanlı kültürü dışında her şey için kültürü ayarlama, bu kod analizi kural sessiz bir şekilde devre dışı bırakılır.

## <a name="how-to-fix-violations"></a>İhlallerini düzeltmek nasıl

Bu kural ihlal düzeltmek için Word yazımı düzeltin veya sözcüğü özel sözlüğe ekleyin.

### <a name="to-add-words-to-a-custom-dictionary"></a>Özel bir sözlüğe sözcükler eklemek için

Özel sözlük XML dosya adı *CustomDictionary.xml*. Proje dizininin aracı yükleme dizini veya kullanıcı profili altındaki aracı ile ilişkili dizinde sözlük yerleştirin (*%USERPROFILE%\Application veri\\...* ). Visual Studio'da projeye özel sözlük eklemeyi öğrenmek için bkz: [nasıl yapılır: Kod Analizi dizinini özelleştirme](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

- Sözcükler/sözlük/Recognized yolunda bir ihlali oluşmamalıdır sözcükleri ekleyin.

- Sözcükler/sözlük/tanınmayan yolunda ihlaline neden sözcükleri ekleyin.

- Sözlük/sözcükler/kullanım dışı yolunda artık kullanılmayan olarak işaretlenen sözcükleri ekleyin. İlgili kural konusuna [CA1726: tercih edilen terimleri kullanın](../code-quality/ca1726-use-preferred-terms.md) daha fazla bilgi için.

- Özel durumlar kısaltma büyük/küçük harf kuralları kısaltmalar/sözlük/CasingExceptions yoluna ekleyin.

Özel sözlük dosyasının yapısı örneği verilmiştir:

```xml
<Dictionary>
   <Words>
      <Unrecognized>
         <Word>cb</Word>
      </Unrecognized>
      <Recognized>
         <Word>stylesheet</Word>
         <Word>GotDotNet</Word>
      </Recognized>
      <Deprecated>
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>
      </Deprecated>
   </Words>
   <Acronyms>
      <CasingExceptions>
         <Acronym>CJK</Acronym>
         <Acronym>Pi</Acronym>
      </CasingExceptions>
   </Acronyms>
</Dictionary>
```

## <a name="when-to-suppress-warnings"></a>Ne zaman uyarıları bastırma

Bu kural bir uyarıdan yalnızca word bilerek yanlış yazılmış ise ve sınırlı sayıda kitaplığı için Word'ün uyguladığı engelleyin. Doğru yazılmış kelimeler için yeni yazılım kitaplıklar gereklidir öğrenme eğrisini düşürebilir.

## <a name="related-rules"></a>İlgili kuralları

- [CA2204: Değişmez değerler doğru yazılmalıdır](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
- [CA1703: Kaynak dizeler doğru yazılmalıdır](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1709: Tanımlayıcıların büyük/küçük harfleri doğru yazılmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Tanımlayıcılar örnekten daha fazla farklı olmalıdır](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Tanımlayıcılar alt çizgi içermemelidir](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1726: Tercih edilen terimleri kullanın](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Kod Çözümleme Dizinini Özelleştirme](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
