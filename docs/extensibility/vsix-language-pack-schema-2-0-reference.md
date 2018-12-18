---
title: VSIX Dil Paketi Şeması 2.0 başvurusu | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
ms.author: dagriffe
author: dgriffen
manager: douge
ms.workload:
- dagriffe
ms.openlocfilehash: 3c1dfa0e3de06bcd6c61472a085ea3c4cdeeac27
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780795"
---
# <a name="vsix-language-pack-schema-20-reference"></a>VSIX Dil Paketi Şeması 2.0 başvurusu

VSIX Dil Paketi şeması VSIX paketlerini yerelleştirilmiş yükleme bilgilerini sağlar. Bu şema 2.0 sürümünü ek yerelleştirme öğeleri destekler.

## <a name="language-pack-schema"></a>Dil Paketi şeması

Dil paketi dosyasının kök öğe `<PackageLanguagePackManifest>`, özniteliğine sahip `Version`, dil paketi biçimi sürümünü olduğu. Bu makalede ayarlayarak bildiriminde belirtilen dil paketi biçiminde 2.0 sürümünü `Version` öznitelik değerine `Version="2.0.0"`. Tam olarak bir alt öğesi kök öğe içeren `<Metadata>` öğesi.

### <a name="packagelanguagepackmanifest-element"></a>PackageLanguagePackManifest öğesi

İçinde `<PackageLanguagePackManifest>` öğesi şu öğe bulunmalıdır:

|Başlık|Açıklama|
|-----------|-----------------|
|`<Metadata>`| Tüm yerelleştirilmiş paket meta verileri için kapsayıcı öğe

### <a name="metadata-element"></a>Meta veri öğesi

İçinde `<Metadata>` öğesi aşağıdaki öğelere sahip olabilir:

|Başlık|Açıklama|
|-----------|-----------------|
|`<DisplayName>`|Yerelleştirilmiş adı uzantısının yüklenmesi|
|`<Description>`|Yerelleştirilmiş açıklama uzantısının yüklenmesi|
|`<License>`| Uzantının lisans yerelleştirilmiş bir sürümünü bir yolu|
|`<MoreInfo>`| Yerelleştirilmiş uzantısı hakkında bilgi almak için bir bağlantı|
|`<ReleaseNotes>`| Bir yol veya sürüm notlarını yerelleştirilmiş bir sürümünü Bağla|
|`<Icon>`| Uzantıları simgesi yerelleştirilmiş bir sürümünü bir yolu|

### <a name="sample-manifest"></a>Örnek bildirimi

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</LocalizedName>
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
|[VSIX paketlerini yerelleştirme](../extensibility/localizing-vsix-packages.md)|Bir VSIX paketi için yerelleştirilmiş yükleme desteğini sağlamak nasıl gösterir.|
|[VSIX Uzantı Şeması 2.0 başvurusu](../extensibility/vsix-extension-schema-2-0-reference.md)|VSIX bildirim içeriğini açıklayan bir *.vsix* dağıtım dosyası. Dağıtım dosyası kullanarak bir Visual Studio uzantısı yüklemenizi sağlayan **Uzantılar ve güncelleştirmeler** iletişim kutusu.|
|[Visual Studio uzantıları bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md)|Nasıl kullanılacağını gösterir **Uzantılar ve güncelleştirmeler** yükleme, kaldırma, etkinleştirmek ve uzantıları devre dışı bırakmak için iletişim kutusu.|