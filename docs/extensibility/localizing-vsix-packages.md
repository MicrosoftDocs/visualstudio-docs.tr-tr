---
title: VSIX paketlerini yerelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54de0b219eb1c86a413b7a95e87a48e7f65ac9ec
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636980"
---
# <a name="localizing-vsix-packages"></a>VSIX Paketlerini Yerelleştirme

Oluşturarak VSIX paketini yerelleştirebilirsiniz bir *Extension.vsixlangpack* her hedef dil için dosya ve ardından bunları doğru klasöre koyarak. Yerelleştirilmiş bir paket yüklendikten sonra uzantı yerelleştirilmiş adı yerelleştirilmiş bir açıklama ile birlikte görüntülenir. Yerelleştirilmiş lisans dosyası ya da yerelleştirilmiş bilgi işaret eden bir URL sağlarsanız, bunlar da görüntülenir.

İçerik ekleyen bir VSPackage'ı, VSIX paketi içeriyorsa, menü komutlarını veya diğer kullanıcı Arabirimi [menü komutlarını yerelleştirme](../extensibility/localizing-menu-commands.md) yerelleştirme yeni kullanıcı Arabirimi öğeleri hakkında bilgi.

## <a name="directory-structure"></a>Dizin yapısı

 Bir kullanıcı bir uzantı yüklendiğinde **Uzantılar ve güncelleştirmeler** en üst düzey bir klasör adıyla eşleşen hedef bilgisayarın Visual Studio yerel ayar için VSIX paketi denetler. Varsa **Uzantılar ve güncelleştirmeler** bulur bir *.vsixlangpack* dosya isteğe bağlı olarak klasöründe karşılık gelen değerleri için bu dosyayı yerelleştirilmiş değerleri değiştirir *.vsixmanifest*dosya. Uzantı yüklendiğinde bu değerleri görüntülenir. Aşağıdaki örnek, İspanyolca (es-ES) ve Fransızca (fr-FR) halinde yerelleştirilmiş bir VSIX paketi için dizin yapısını gösterir.  

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> VSIX tarafından desteklenen proje şablonlarında [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] VSIX bildirimi oluşturun ve adlandırın *source.extension.vsixmanifest*. Visual Studio projeyi oluşturduğunda VSIX paketinde Extension.VsixManifest bu dosyanın içeriğini kopyalar.

## <a name="the-extensionvsixlangpack-file"></a>Extension.vsixlangpack dosyası

*Extension.vsixlangpack* dosya aşağıdaki [VSIX Dil Paketi Şeması 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Bu şemaya sahip bir `PackageLanguagePackManifest`, hangi hemen arkasından bir `Metadata` alt öğesi. Meta veri öğesi, en fazla 6 alt öğeleri içerebilir `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, ve `Icon`. Bu alt öğeleri karşılık gelen `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, ve `Icon` alt öğelerinin `Metadata` öğesinin *Extension.vsixmanifest*dosya.

Bir vsixlangpack dosyası oluşturduğunuzda, ayarlamalısınız `Include in Vsix` özelliğini `true`. Aksi takdirde, yerelleştirilmiş yükleme metin göz ardı edilir.

### <a name="to-set-the-include-in-vsix-property"></a>Eklemede VSIX özelliğini ayarlamak için

1. İçinde **Çözüm Gezgini**Extension.vsixlangpack dosyaya sağ tıklayın ve ardından **özellikleri**.

2.  İçinde **özellik kılavuzunda**, tıklayın **VSIX Ekle**ve değerini ayarlamak `true`.

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıdaki örnek, ilgili kısımlarını gösterir. bir *Extension.vsixmanifest* dosya. İlgili dosyayı da içerir *Extension.vsixlangpack* İspanyolca için dosya. Hedef bilgisayarın Visual Studio yerel ayar için İspanyolca olarak ayarlanmışsa değerleri dil paketi bildirimi değerleri değiştirin.

### <a name="code"></a>Kod

 [*Extension.vsixmanifest*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

 [*Extension.vsixlangpack*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>Ayrıca bkz.

|Başlık|Açıklama|
|-----------|-----------------|
|[VSIX Dil Paketi Şeması 2.0 başvurusu](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|VSIX Dil Paketi bir .vsix dağıtım dosyasının yerelleştirme bilgisi açıklar.|
|[Bir VSIX paketinin anatomisi](../extensibility/anatomy-of-a-vsix-package.md)|Bir VSIX paketinin içeriği ve yapısı açıklar.|
|[Menü komutlarını yerelleştirme](../extensibility/localizing-menu-commands.md)|Diğer metin kaynakları bir uzantı, yerelleştirme işlemi gösterilmektedir.|