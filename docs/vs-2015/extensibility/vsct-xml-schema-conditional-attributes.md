---
title: VSCT XML Şeması koşullu öznitelikleri | Microsoft Docs
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
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9524f1306c86f110498d71d4057378cd834d207b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817249"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>VSCT XML Şeması Koşullu Öznitelikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tüm öğeleri ve listeleri için koşullu öznitelikler uygulanabilir. Mantıksal işleçler ve sembol genişletme ifadeler true veya false olarak değerlendirin. TRUE ise sonuçta elde edilen çıktıda ilişkili liste veya öğe dahildir.  
  
 Belirteç genişletmeleri diğer belirteç genişletmeleri veya sabitler karşı test edilebilir. ' % S'işlevi Defined() değere sahip olsa bile belirli bir adı tanımlı olup olmadığını test etmek için kullanılır.  
  
 Koşul özniteliği bir listesine uygulandığında, koşul listesindeki her alt öğenin uygulanır. Bir alt öğesi bir koşul özniteliğine içeriyorsa, onun koşulu bir AND işlemi tarafından üst ifade ile birleştirilir.  
  
 Değerler 1, '1' ve 'true' true ' değerlendirilir ve 0, '0' ve 'false' false ' değerlendirilir.  
  
## <a name="operators"></a>İşleçler  
 Koşullu ifadeler değerlendirmek için aşağıdaki işleçleri kullanılabilir.  
  
|İşleç|Tanım|  
|--------------|----------------|  
|(,)|Gruplandırma|  
|!|Mantıksal değil|  
|\<, >, \<=, >=, ==, !=|İlişkisel ve eşitlik|  
|and|Boole değeri|  
|veya|Boole değeri|  
  
## <a name="examples"></a>Örnekler  
  
```  
<Menu Condition="Defined(DEBUG)" …  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" …  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu …  
        </Menu>  
    </Menus>  
  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

