---
title: VSCT XML Şeması koşullu öznitelikleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 071f13420fe9482e99189ca29eeb09d319f182bf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49936438"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>VSCT XML Şeması koşullu öznitelikleri
Tüm listeleri ve öğeleri koşullu öznitelikleri uygulayabilirsiniz. Mantıksal işleçler ve sembol genişletme ifadeler true veya false olarak değerlendirin. TRUE ise sonuçta elde edilen çıktıda ilişkili liste veya öğe dahildir.  
  
 Belirteç genişletmeleri diğer belirteç genişletmeleri veya sabitler karşı test edebilirsiniz. İşlev `Defined()` değere sahip olsa bile belirli bir adı tanımlı olup olmadığını sınar.  
  
 Koşul özniteliği bir listesine uygulandığında, koşul listesindeki her alt öğenin uygulanır. Bir alt öğesi bir koşul özniteliğine içeriyorsa, onun koşulu bir AND işlemi tarafından üst ifade ile birleştirilir.  
  
 Değerler 1, '1' ve 'true' true ' değerlendirilir ve 0, '0' ve 'false' false ' değerlendirilir.  
  
## <a name="operators"></a>İşleçler  
 Koşullu ifadeler değerlendirmek için aşağıdaki işleçleri kullanın.  
  
|İşleç|Tanım|  
|--------------|----------------|  
|(,)|Gruplandırma|  
|!|Mantıksal değil|  
|\<, >, \<=, >=, ==, !=|İlişkisel ve eşitlik|  
|and|Boole değeri|  
|veya|Boole değeri|  
  
## <a name="examples"></a>Örnekler  
  
```xml  
<Menu Condition="Defined(DEBUG)" ...  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" ...  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu ...  
        </Menu>  
    </Menus>  
  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)