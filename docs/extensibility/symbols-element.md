---
title: Symbols öğesi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4186f53ec84c44b97acbc3a59d663404a52dd255
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856743"
---
# <a name="symbols-element"></a>Symbols Öğesi
GUID'leri ve kimlikleri diğer VSCT öğeleri tarafından kullanılan tanımlar. Yönetilmeyen kod için bu bilgiler genellikle tarafından belirtilen üst bilgi dosyaları geldiği [Extern öğesi](../extensibility/extern-element.md). Kod kullanan bu bilgileri tanımlamak için semboller öğenin alt öğeleri yönetilen.  
  
 Mevcut bir .cto dosyadan .vsct dosyası oluşturma simgeleri Symbols öğesi alt öğesi olarak oluşturulur. Daha fazla bilgi için [nasıl yapılır: oluşturma bir. Vsct mevcut bir dosya. Cto dosya](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).  
  
 Symbols öğesi ile karıştırılmamalıdır [tanımlama öğesi](../extensibility/define-element.md), önişlemci tarafından kullanılmak üzere ad-değer çiftleri tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<Symbols>  
  <GuidSymbol>... </GuidSymbol>  
  <GuidSymbol>... </GuidSymbol>  
</Symbols>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Yok.||  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|GuidSymbol|Bir GUID sembolünü tanımlar. GuidSymbol iki gerekli özniteliklere sahip: ad ve değer. Simgenin adını adıdır ve değeri bir dize olarak GUID değeridir.<br /><br /> Örneğin:\<GuidSymbol name = "guidVsPackage1Pkg" value = "{c5f54698-101a-4846-84d3-dc748f9cd848}" / >|  
|Idsymbol|Bir sembolü tanımlar. Idsymbol iki gerekli özniteliklere sahip: ad ve değer. Simgenin adını adıdır ve değer bir dize olarak sembol değerdir.<br /><br /> Örneğin:\<Idsymbol name = "MyMenuGroup" value = "0x1020" / >|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[CommandTable Öğesi](../extensibility/commandtable-element.md)|.Vsct dosyası kök öğesi.|  
  
## <a name="example"></a>Örnek  
  
```  
<Symbols>  
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />  
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
    <IDSymbol name="cmdidMyTool" value="0x0101" />  
  </GuidSymbol>  
</Symbols>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)