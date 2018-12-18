---
title: CommandTable öğesi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8c2adca249ba245825f9b664b46e1b4674d0ea50
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879915"
---
# <a name="commandtable-element"></a>CommandTable öğesi
CommandTable olan kök öğesini *.vsct* dosya. Bu gerçek düzeni ve IDE VSPackage sağlayan komut türü tanımlayan dosyasıdır. Komutlarını, menü öğeleri, menüler, araç çubukları ve birleşik giriş kutuları içerebilir. Daha fazla bilgi için [Visual Studio komut tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >  
  <Extern>... </Extern>  
  <Include>... </Include>  
  <Define>... </Define>  
  <Commands>... </Commands>  
  <CommandPlacements>... </CommandPlacements>  
  <VisibilityConstraints>... </VisibilityConstraints>  
  <KeyBindings>... </KeyBindings>  
  <UsedCommands... </UsedCommands>  
  <Symbols>... </Symbols>  
</CommandTable>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
| Öznitelik | Açıklama |
|-----------| - |
| xmlns | Gerekli. XML ad alanları:<br /><br /> xmlns = "<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"<br /><br /> xmlns:XS = "<http://www.w3.org/2001/XMLSchema>" |
| dil | İsteğe bağlı. Language özniteliği, tüm varsayılan dili belirtmek için kullanılabilir \<dizeleri > komut tablosu öğeleri.  Dil belirtilmezse, geçerli işlemin dil kullanılır:<br /><br /> Dil = "en-us" |
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Extern öğesi](../extensibility/extern-element.md)|İsteğe bağlı. Derleyici için ön işlemci yönergeleri içerir.|  
|[Öğe Ekle](../extensibility/include-element.md)|İsteğe bağlı. Derleme içinde içerecek şekilde tüm dosyalara olan yolları içerir.|  
|[Define öğesi](../extensibility/define-element.md)|İsteğe bağlı. Kendi ad ve değer verilen bir sembolü tanımlar.|  
|[Commands öğesi](../extensibility/commands-element.md)|İsteğe bağlı. Tüm diğer öğeleri içeren bir VSPackage için tüm komutları tanımlayan üst öğe.|  
|[CommandPlacements öğesi](../extensibility/commandplacements-element.md)|İsteğe bağlı. Komut çubuğundaki komutları yerleştirilecek nerede tanımlar.|  
|[VisibilityConstraints öğesi](../extensibility/visibilityconstraints-element.md)|İsteğe bağlı. Komutlar ve araç çubukları statik görünürlüğünü belirler.|  
|[KeyBindings öğesi](../extensibility/keybindings-element.md)|İsteğe bağlı. Kısayol tuş birleşimleri, komutları belirtir.|  
|[UsedCommands öğesi](../extensibility/usedcommands-element.md)|İsteğe bağlı. İsteğe bağlı olarak kendi özgün diğer VSPackage'ları tarafından desteklenen sürümüne uygulamak bir VSPackage sağlar.|  
|[Symbols öğesi](https://www.microsoft.com/download/details.aspx?id=55984)|İsteğe bağlı. Derleyici için herhangi bir sembol verilerini--GUID'leri, kimlikleri ve benzeri--içerir.|  
  
### <a name="parent-elements"></a>Üst öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Yok.||  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio komut tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)