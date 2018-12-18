---
title: VSIX paketlerini yerelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f6bc666e244fed2bc2922ce4878434730a643e5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750595"
---
# <a name="localizing-vsix-packages"></a>VSIX Paketlerini Yerelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Her hedef dil için bir Extension.vsixlangpack dosyası oluşturma ve ardından bunları doğru klasöre koyarak bir VSIX paketi yerelleştirebilirsiniz. Yerelleştirilmiş bir paket yüklendikten sonra uzantı yerelleştirilmiş adı yerelleştirilmiş bir açıklama ile birlikte görüntülenir. Yerelleştirilmiş lisans dosyası ya da yerelleştirilmiş bilgi işaret eden bir URL sağlarsanız, bunlar da görüntülenir.  
  
 İçerik ekleyen bir VSPackage'ı, VSIX paketi içeriyorsa, menü komutlarını veya diğer kullanıcı Arabirimi [menü komutlarını yerelleştirme](../extensibility/localizing-menu-commands.md) yerelleştirme yeni kullanıcı Arabirimi öğeleri hakkında bilgi.  
  
## <a name="directory-structure"></a>Dizin yapısı  
 Bir kullanıcı bir uzantı yüklendiğinde **Uzantılar ve güncelleştirmeler** en üst düzey bir klasör adıyla eşleşen hedef bilgisayarın Visual Studio yerel ayar için VSIX paketi denetler. Varsa **Uzantılar ve güncelleştirmeler** bulur .vsixlangpack bir klasörde dosya, yerelleştirilmiş değerler .vsixmanifest dosyasının karşılık gelen değerleri için bu dosyayı değiştirir. Uzantı yüklendiğinde bu değerleri görüntülenir. Aşağıdaki örnek, İspanyolca (es-ES) ve Fransızca (fr-FR) halinde yerelleştirilmiş bir VSIX paketi için dizin yapısını gösterir.  
  
 MyExtension.dll  
  
 Extension.vsixmanifest  
  
 [Content_Types] .xml  
  
 es-ES  
  
 Extension.vsixlangpack  
  
 fr-FR  
  
 Extension.vsixlangpack  
  
> [!NOTE]
>  VSIX tarafından desteklenen proje şablonlarında [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] bir VSIX bildirim oluşturmak ve source.extension.vsixmanifest adlandırın. Visual Studio projeyi oluşturduğunda VSIX paketinde Extension.VsixManifest bu dosyanın içeriğini kopyalar.  
  
## <a name="the-extensionvsixlangpack-file"></a>Extension.vsixlangpack dosyası  
 Extension.vsixlangpack dosya izleyen [VSIX Dil Paketi şeması](../extensibility/vsx-language-pack-schema-reference.md). Bu şemaya sahip bir [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) kök öğe ve şu dört alt öğeleri: [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md), ve [lisans](../extensibility/license-element-vsix-language-pack-schema.md). Bu alt öğeleri karşılık gelen `Name`, `Description`, `MoreInfoURL`, ve `License` alt öğelerinin `Identifier` .vsixmanifest uzantı dosyası öğesidir.  
  
 Bir vsixlangpack dosyası oluşturduğunuzda, ayarlamalısınız `Include in Vsix` özelliğini `true`. Aksi takdirde, yerelleştirilmiş yükleme metin göz ardı edilir.  
  
#### <a name="to-set-the-include-in-vsix-property"></a>Eklemede VSIX özelliğini ayarlamak için  
  
1.  İçinde **Çözüm Gezgini**Extension.vsixlangpack dosyaya sağ tıklayın ve ardından **özellikleri**.  
  
2.  Özellik kılavuzunda tıklayın **VSIX Ekle**ve değerini ayarlamak `true`.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, bir Extension.vsixmanifest dosyası, İspanyolca için karşılık gelen Extension.vsixlangpack dosyasıyla birlikte ilgili kısımlarını gösterir. Hedef bilgisayarın Visual Studio yerel ayar için İspanyolca olarak ayarlanmışsa değerleri dil paketi bildirimi değerleri değiştirin.  
  
### <a name="code"></a>Kod  
 [Extension.vsixmanifest]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VSIX ...>  
  <Identifier ...>  
    <Name>Family Tree</Name>  
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>  
    <License>EULA.rtf</License>  
    <MoreInfoURL>http://www.contoso.com/products/FamilyTree.htm</MoreInfoURL>  
    ...  
  </Identifier>  
  <References .../>  
  <Content .../>  
</VSIX>  
```  
  
 [Extension.vsixlangpack]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSIX LanguagePack öğesi](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [Bir VSIX paketinin anatomisi](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX Proje Şablonu](../extensibility/vsix-project-template.md)

