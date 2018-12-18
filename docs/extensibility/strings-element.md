---
title: Öğe dizeleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5994144f07b8af84f61d7833737f45593c551b2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143897"
---
# <a name="strings-element"></a>Dizeleri öğesi
Dizeleri öğesi en az bir içermelidir **■ ButtonText** alt öğesi. Diğer tüm alt öğeler isteğe bağlıdır. Geçersiz XML karakterleri gibi '&' ve ' <' varlıklar kodlanmış olmalıdır ('&amp;'ve'&lt;' vb.).  
  
 Metin dizesindeki ve işareti komutu için klavye kısayolu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<Strings>  
  <ButtonText>... </ButtonText>  
  <CommandName>... </CommandName>  
</Strings>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|dil|İsteğe bağlı. Dil = ".".|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|■ ButtonText|Bu alan ve bir komut tanımı beş aşağıdaki metin alanları çeşitli menülerde görüntülenen metni belirtmenize olanak tanır. Varsayılan olarak, `ButtonText` alanı menü denetleyicileri görüntülenir. `ButtonText` Alan bir metin alanları boş ise varsayılan de olur. `ButtonText` Diğer metin alanları belirtilmese bile alan boş olamaz.|  
|Tooltıptext|`ToolTipText` Alan menü öğesi için araç ipucunda görünen metni belirtir.<br /><br /> Varsa `ToolTipText` alan boşsa, `ButtonText` alanı kullanılır.|  
|MenuText|`MenuText` Alan bir araç, bir kısayol menüsü veya bir alt ana menüdeki ise bir komut için görüntülenen metin belirtir. Varsa `MenuText` alan boşsa, tümleşik geliştirme ortamını (IDE) kullanan `ButtonText` alan. `MenuText` Alan yerelleştirme için de kullanılabilir.<br /><br /> Kısayol menüleri için `MenuText` kısayol menüleri IDE içinde özelleştirme sağlayan kısayol menüleri araç çubuğunda görüntülenen ad alanıdır. Bu nedenle, kısayol menüsünde ad içinde belirli olabilir; Örneğin, "Kısayol" yerine "pencere öğesi paket kısayol menüsünü" kullanın.<br /><br /> Varsa `MenuText` alan belirtilmezse, `ButtonText` alanı kullanılır.|  
|CommandName|`CommandName` Alan klavye kategorisinde görüntülenen metni belirtir **komutları** sekmesinde **Özelleştir** iletişim kutusu (tıklatılarak **Özelleştir**üzerinde **Araçları** menüsü).|  
|canonicalName|İngilizce `CanonicalName` alan girilebilir İngilizce metin komutun adını belirtir **komutu** menü öğesini yürütmek için penceresi. IDE harf, rakam, alt çizgi veya katıştırılmış nokta olmayan tüm karakterleri kaldırır. Bu metin sonra için birleştirilmiş `ButtonText` komutu tanımlamak için alanı. Örneğin, **yeni proje** üzerinde **dosya** menü komutu, File.NewProject haline gelir.<br /><br /> Varsa İngilizce `CanonicalName` alan belirtilmezse, IDE kullanan `ButtonText` alan ve şeritler harf, rakam, alt çizgi ve katıştırılmış nokta dışında tüm çıkışı. Örneğin, düğme metni DefineCommands nerede ve işareti, boşluk ve üç nokta kaldırılır, "& tanımla komutları..." olur.<br /><br /> Varsa `TextChanges` bayrağı belirtilir ve komut metni değiştirildiğinde, tanınan ilgili komutu **komutu** penceresi değiştirmez; özgün kurallı biçimi kalır `ButtonText` veya İngilizce `CanonicalName` alanları.|  
|LocCanonicalName|`LocCanonicalName` Alan aynı şekilde davrandığını İngilizce'ye `CanonicalName` alanı ancak yerelleştirilmiş komut metni belirtilmesini sağlar. Her iki kurallı alanlar belirtilebilir. IDE içinde girilen metin ayrıştıran çünkü **komutu** penceresini açın ve hem İngilizce hem de İngilizce olmayan metin komutu ile ilişkilendirilebilir aynı komutu ile ilişkilendirir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Button Öğesi](../extensibility/button-element.md)|Kullanıcı ile etkileşim kurabilen bir öğeyi tanımlar.|  
|[Menu Öğesi](../extensibility/menu-element.md)|Tek menü öğesi tanımlar.|  
|[Combos Öğesi](../extensibility/combo-element.md)|Açılan kutuda görünür komutları tanımlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)