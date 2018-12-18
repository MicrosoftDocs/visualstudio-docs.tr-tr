---
title: Tür tanımlarını görüntüleme
ms.date: 01/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code editor, view definition
- go to definition
- peek definition
- type definition [Visual Studio]
- member definition [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e7b159eb48e995fa0bca6ea86299d09c1a10cf27
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062088"
---
# <a name="view-type-and-member-definitions"></a>Görünüm türü ve üye tanımları

Geliştiriciler genellikle kendi kodlarında türler veya sınıf üyeleri kullandıkları için kaynak kod tanımlarını görüntülemek gerekir. Visual Studio'da **tanıma** ve **Özet tanım** özelliklerini kolayca tür veya üyenin tanımı görüntülemek etkinleştirin. Meta veri, kaynak kodu kullanılabilir durumda değilse, bunun yerine görüntülenir.

## <a name="go-to-definition"></a>Tanıma Git

**Tanıma** özellik bir türe veya üyeye kaynağına gider ve sonuç yeni bir sekmede açılır. Klavye kullanıcısıysanız yere tuşuna basın ve sembol adını içinde metin imleci yerleştirmeniz **F12**. Fare kullanıcısıysanız seçin **tanıma** bağlam menüsünden veya kullanım **Ctrl tuşuna basıp** aşağıdaki bölümde anlatılan işlevi.

### <a name="ctrl-click-go-to-definition"></a>CTRL tuşunu tanımına Git

Visual Studio 2017 sürüm 15.4, hızlı erişim için fare kullanıcılar için daha kolay bir yolu yoktur **tanıma**. Semboller hale tıklanabilir bastığınızda **Ctrl** ve türe veya üyeye üzerine gelin. Sembol tanımını hızlıca gezinmek için basın **Ctrl** anahtar ve üzerine tıklayın. Bu kadar kolay!

![Fare tıklatın tanımı animasyon Git](../ide/media/click_gotodef.gif)

Fare tıklatın değiştirici tuş değiştirebilirsiniz **tanıma** giderek **Araçları** > **seçenekleri** > **metin düzenleyicisi**   >  **Genel**ve seçim **Alt** veya **Ctrl + Alt** gelen **değiştiricisi anahtar kullan**açılır. Fare tıklatın de devre dışı bırakabilirsiniz **tanıma** kaldırarak **tanıma gerçekleştirmek için fare tıklamasını etkinleştir** onay kutusu.

![Fare tıklatın etkinleştirme tanımına Git](../ide/media/editor_options_mouse_click_gotodef.png)

## <a name="peek-definition"></a>Tanıma göz at

**Özet tanım** özellik Düzenleyicisi'nde geçerli konumunuzu çıkmadan bir tür tanımı Önizleme olanak sağlar. Klavye kullanıcısıysanız yere tuşuna basın ve tür veya üye adı içindeki metin imleci yerleştirmeniz **Alt + F12**. Fare kullanıcısıysanız seçebileceğiniz **Özet tanım** bağlam menüsünden. Visual Studio 2017 sürüm 15.4 ve üzeri, yoktur göz atma görünümünde bir tanımı için yeni bir yol fareyi kullanarak. İlk olarak, Git **Araçları** > **seçenekleri** > **metin düzenleyici** > **genel**. Seçeneğini **tanımı Özet Görünümü'nde açın** tıklatıp **Tamam** kapatmak için **seçenekleri** iletişim kutusu.

![Fare tıklatın gözlem tanım seçeneği ayarlama](../ide/media/editor_options_peek_view.png)

Daha sonra basın **Ctrl** (veya hangi değiştirici tuşa seçili olduğundan **seçenekleri**), türe veya üyeye tıklayın.

![Özet tanım animasyon](../ide/media/peek_definition.gif)

Başka bir açılan pencere tanımından Özet varsa daire ve açılan menüsü görünen okları kullanarak gidebilirsiniz bir içerik haritası yol başlar.

Daha fazla bilgi için [nasıl yapılır: Özet tanım (Alt + F12) kullanarak kodu görüntüleme ve düzenleme](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="view-metadata-as-source-code-c"></a>Kaynak kodu olarak meta verileri görüntüleme (C#)

Tanımı görüntülediğinizde C# türleri veya üyeleri kaynak kodu kullanılabilir değil, meta veriler görüntüleniyor. Türleri ve üyeleri, ancak kendi uygulamalarını bildirimlerini görebilirsiniz.

Çalıştırdığınızda **tanıma** veya **Özet tanım** kaynak kodu kullanılamıyor, bir öğenin bu öğeye ait meta verilerin, kaynak kodu görüntülenen bir görünüm içeren sekmeli belge komutu Kod Düzenleyicisi'nde görünür. Türün adını ve ardından **[meta verilerden]**, belgenin sekmesinde görünür.

Örneğin çalıştırırsanız, **tanıma** komutunu <xref:System.Console>, meta verileri <xref:System.Console> Kod Düzenleyicisi görünür C# kaynak kodu. Kod bildiriminden benzer, ancak bir uygulama göstermez.

![Kaynak olarak Meta Veriler](../ide/media/metadatasource.png)

> [!NOTE]
> Çalıştırılacak çalıştığınızda **tanıma** veya **Özet tanım** komut türleri veya iç olarak işaretlenmiş üyeleri için Visual Studio görüntülemez meta verilerinin bağımsız olarak, kaynak kodu başvuru bütünleştirilmiş kod veya arkadaş olur.

### <a name="view-decompiled-source-definitions-instead-of-metadata-c"></a>Kaynak koda dönüştürülmüş kaynak tanımları yerine meta verileri görüntüleme (C#)

Yeni Visual Studio 2017 sürüm 15.6, bir seçenek tanımı görüntülediğinizde, kaynak koda dönüştürülmüş kaynak kodu görmek için ayarlayabileceğiniz bir C# tür veya üye, kaynak kodu kullanılamaz. Bu özelliği etkinleştirmek için seçin **Araçları** > **seçenekleri** menü çubuğundan. Ardından, **metin düzenleyici** > **C#** > **Gelişmiş**seçip **kaynak koda dönüştürülmüş kaynaklara gezintiyi etkinleştir** .

![Kaynak koda dönüştürülmüş tanımını görüntüleme](media/go-to-definition-decompiled-sources.png)

> [!NOTE]
> Visual Studio metot gövdeleri yetenek ılspy kullanarak yeniden oluşturur. Bu özellik, erişim ilk kez ticari marka yasaları ve yazılım lisans ve telif hakkı ile ilgili yasal Sorumluluklar kabul gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod gidin](../ide/navigating-code.md)
- [Nasıl yapılır: Özet tanım (Alt + F12) kullanarak kodu görüntüleme ve düzenleme](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)