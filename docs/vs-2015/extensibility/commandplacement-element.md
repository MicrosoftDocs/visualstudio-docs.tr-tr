---
title: CommandPlacement öğesi | Microsoft Docs
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
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 53a60949cdda6d026525dcc8be5bab8f82a0fb73
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741541"
---
# <a name="commandplacement-element"></a>CommandPlacement Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

CommandPlacement öğesi düğmeler, grupları ve menüler birden fazla grup veya menüdeki dahil edilmesini sağlar. CommandPlacement öğesi kullanarak tam bir kullanıcı arabirimi görünümünü değiştirmek için bu öğeleri bulunabileceğini gerekmez.  
  
 Daha fazla bilgi için [, yeniden kullanılabilir grupları düğmeler oluşturma](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|GUID|Gerekli. Sınıfında tanımlandığı gibi komut kümesi GUID'si [Symbols öğesi](../extensibility/symbols-element.md).|  
|kimlik|Gerekli. Menü, Grup veya sınıfında tanımlandığı gibi yerleştirilmesini komut kimliğini `Symbols Element`.|  
|önceliği|Gerekli. Üst öğesi görsel öğe konumunu belirler.|  
|Koşul|İsteğe bağlı. Bkz: [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Üst|Gerekli. Menü veya yerleştirilecek öğesi barındıran grup.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[CommandPlacements Öğesi](../extensibility/commandplacements-element.md)|CommandPlacements ve CommandPlacement öğelerin grupları belirtir.|  
  
## <a name="example"></a>Örnek  
  
```  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CommandPlacements öğesi](../extensibility/commandplacements-element.md)   
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

