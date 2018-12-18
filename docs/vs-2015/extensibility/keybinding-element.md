---
title: KeyBinding öğesi | Microsoft Docs
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
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 32dafc1b16282657db40531e34d1eccb02841481
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780938"
---
# <a name="keybinding-element"></a>KeyBinding Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Komut için klavye kısayolları KeyBinding öğesi belirtir.  
  
 Komutlar tek ve çift tuş bağlamaları ilişkili olabilir. Tek bir anahtar bağlaması, CTRL + S örneğidir **Kaydet** komutu. Bir komut tetiklemek için iki ardışık tuş birleşimleri çift anahtar bağlamalarını gerektirir. CTRL + K, CTRL + K, bir yer işareti ayarlamak için bir çift anahtar bağlama örneğidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|GUID|Gerekli.|  
|kimlik|Gerekli.|  
|düzenleyici|Gerekli. GUID Düzenleyici klavye kısayolu etkin olacağı düzenleme bağlamı gösterir. Genel bağlama kapsam "guidVSStd97" değeridir.|  
|key1|Gerekli. Geçerli değerler tüm typable alfasayısal karakterler ve ayrıca 0 x ve VK_constants önünde iki basamaklı onaltılık değerlerini içerir.|  
|Değişiklik1|İsteğe bağlı. Herhangi bir bileşimini boşlukla ayrılmış SHIFT CTRL ve ALT.|  
|key2|İsteğe bağlı. Geçerli değerler tüm typable alfasayısal karakterler ve ayrıca 0 x ve VK_constants önünde iki basamaklı onaltılık değerlerini içerir.|  
|mod2|İsteğe bağlı. Herhangi bir bileşimini boşlukla ayrılmış SHIFT CTRL ve ALT.|  
|Öykünücü|İsteğe bağlı.|  
|Koşul|İsteğe bağlı. Bkz: [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Üst||  
|Ek Açıklama||  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[KeyBindings Öğesi](../extensibility/keybindings-element.md)|Tuş öğeleri gruplandırır ve diğer KeyBindings gruplandırmaları.|  
  
## <a name="example"></a>Örnek  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [KeyBindings öğesi](../extensibility/keybindings-element.md)   
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

