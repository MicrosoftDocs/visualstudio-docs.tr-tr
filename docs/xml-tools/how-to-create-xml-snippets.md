---
title: 'Nasıl yapılır: XML kod parçacıkları oluşturma'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db7d1cc841da888c46342ec25bf28c3af7370be9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867721"
---
# <a name="how-to-create-xml-snippets"></a>Nasıl yapılır: XML kod parçacıkları oluşturma

XML Düzenleyicisi'ni yeni kod parçacıkları oluşturmak için kullanılabilir. "Kod parçacığı" adlı bir XML kod parçacığı Düzenleyici içeren yeni kod parçacıkları oluşturmak için diğer bir deyişle bir ortak kod parçacığı.

## <a name="to-create-a-new-xml-snippet"></a>Yeni bir XML kod parçacığı oluşturmak için

 Yeni bir XML kodu oluşturmak için kod parçacığı yeni bir XML dosyası oluşturun ve kullanın **parçacık Ekle** özelliği.

1.  Üzerinde **dosya** menüsünde tıklatın **yeni** ve ardından **dosya**.

2.  Tıklayın **XML dosyası** ve ardından **açık**.

3.  Düzenleyici bölmesine sağ tıklayıp **parçacık Ekle**.

4.  Seçin **kod parçacığı** tuşuna basın ve liste **Enter**.

5.  Yeni kod parçacığını değişiklikleri yapın.

6.  Gelen **dosya** menüsünü seçin **Kaydet XMLFile.xml**.

     **Dosyayı farklı Kaydet** iletişim kutusu görüntülenir.

7.  Yeni kod parçacığı için bir ad girin ve seçin **kod parçacığı dosyaları** gelen **farklı kaydetme türü** açılır pencere.

8.  Kullanım **kaydetmek** açılır listede dosya konumunu değiştirmek için *My Documents\Visual Studio 2005\Code Snippets\XML\My XML kod parçacıklarını* klasörünü ve ardından ENTER tuşuna **Kaydet**.

## <a name="snippet-description"></a>Kod parçacığı açıklaması

 Bu bölümde Demirbaş kod parçacığında temel öğelerinden bazıları açıklanmaktadır. XML kod parçacıkları tarafından kullanılan şema öğeleri hakkında daha fazla bilgi için bkz: [kod parçacıkları şema başvurusu](../ide/code-snippets-schema-reference.md).

### <a name="snippettype-element"></a>SnippetType öğesi

 Düzenleyici iki kod parçacığı türlerini destekler:

```xml
<SnippetTypes>
  <SnippetType>SurroundsWith</SnippetType>
  <SnippetType>Expansion</SnippetType>
</SnippetTypes>
```

 `Expansion` Türü çağırdığınızda, kod parçacığı görünüp görünmeyeceğini belirler **parçacık Ekle** komutu. `SurroundsWith` Türü çağırdığınızda, kod parçacığı görünüp görünmeyeceğini belirler **Surrounds ile** komutu.

### <a name="code-element"></a>Kod öğesi

 `Code` Öğesi, kod parçacığında çağrıldığında eklenecek XML metni tanımlar.

> [!NOTE]
> XML kod parçacığı metin içinde alınmalıdır bir `<![CDATA[...]]>` bölümü.


 Aşağıdaki `Code` Demirbaş kod parçacığı tarafından oluşturulan öğesi.

```xml
<Code Language="XML">
  <![CDATA[<test>
  <name>$name$</name>
  $selected$ $end$</test>]]>
</Code>
```

 `Code` Öğesi üç değişkenler içerir.

- $name$ kullanıcı tanımlı değişkendir. Oluşturur bir `name` "adı" için varsayılan olarak düzenlenebilir bir değere sahip öğe. Kullanıcı tanımlı değişkenler, kullanılarak tanımlanır `Literal` öğesi.

- Seçili $$ önceden tanımlanmış bir değişkendir. Bu kod parçacığı çağırmadan önce XML Düzenleyicisi'nde seçili metni temsil eder. Bu değişken yerleşimini seçili metin, seçimi çevreleyen kod parçacığında nerede görüneceğini belirler.

- $end$ önceden tanımlanmış bir değişkendir. Kullanıcının bastığında **Enter** kod parçacığı alanları düzenleme işlemini tamamlamak için bu değişkeni şapka (^) burada taşınır belirler.

  Yukarıdaki `Code` öğe aşağıdaki XML metni ekler:

```xml
<test>
  <name>name</name>
</test>
```

 Name öğesi değeri, düzenlenebilir bir bölge işaretlenir.

### <a name="literal-element"></a>Literal öğesi

 `Literal` Öğesi dosyasına eklendikten sonra özelleştirilebilir yerine konacak metin tanımlamak için kullanılır. Örneğin, değişmez değer dizeleri, sayısal değerler ve bazı değişken adları değişmez değer olarak bildirilebilir. Herhangi bir sayıda değişmez değerleri, XML kod parçacığı içinde tanımlayabilirsiniz ve kod parçacığı içinde birden çok kez den başvurabilir. Aşağıdaki örneğidir bir `Literal` varsayılan değeri olan "name" $name$ değişken tanımlayan öğe

```xml
<Literal>
  <ID>name</ID>
  <Default>name</Default>
</Literal
```

 Değişmez değerleri, işleve de başvurabilir. XML Düzenleyicisi adlı işlevi içerir **LookupPrefix**. **LookupPrefix** işlevi bu kod parçacığı çağrılır ve varsa, ad alanı için tanımlanan ad alanı öneki döndürür ve iki nokta üst üste (:) içeren XML belgesindeki konumdan belirtilen ad alanı URI arar ad. Aşağıdaki örneğidir bir `Literal` kullanan öğesi **LookupPrefix** işlevi.

```xml
<Literal Editable="false">
   <ID>prefix</ID>
   <Function>LookupPrefix("namespaceURI")</Function>
</Literal>
```

 $Prefix$ değişken sonra XML kod parçacığı başka bir yerde kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [XML kod parçacıkları](../xml-tools/xml-snippets.md)
- [Nasıl yapılır: kullanım XML kod parçacıkları](../xml-tools/how-to-use-xml-snippets.md)
- [Nasıl yapılır: XML şemasından XML kod parçacığı oluşturma](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)