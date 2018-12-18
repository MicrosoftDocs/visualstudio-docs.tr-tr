---
title: CommandTable öğesi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1adc3e8f8c7894cfb3a55617ce594f52a60f2498
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817379"
---
# <a name="commandtable-element"></a>CommandTable Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

CommandTable .vsct dosyası kök öğesidir. Bu gerçek düzeni ve IDE VSPackage sağlayan komut türü tanımlayan dosyasıdır. Komutlarını, menü öğeleri, menüler, araç çubukları ve birleşik giriş kutuları içerebilir. Daha fazla bilgi için [Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
| Öznitelik |                                                                                                                   Açıklama                                                                                                                   |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   xmlns   |                                   Gerekli. XML ad alanları:<br /><br /> xmlns = "<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"<br /><br /> xmlns:XS = "<http://www.w3.org/2001/XMLSchema>"                                   |
| dil  | İsteğe bağlı. Language özniteliği, tüm varsayılan dili belirtmek için kullanılabilir \<dizeleri > komut tablosu öğeleri.  Dil belirtilmezse, geçerli işlemin dil kullanılır:<br /><br /> Dil = "en-us" |
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Extern Öğesi](../extensibility/extern-element.md)|İsteğe bağlı. Derleyici için ön işlemci yönergeleri içerir.|  
|[Include Öğesi](../extensibility/include-element.md)|İsteğe bağlı. Derleme içinde içerecek şekilde tüm dosyalara olan yolları içerir.|  
|[Define Öğesi](../extensibility/define-element.md)|İsteğe bağlı. Kendi ad ve değer verilen bir sembolü tanımlar.|  
|[Commands Öğesi](../extensibility/commands-element.md)|İsteğe bağlı. Tüm diğer öğeleri içeren bir VSPackage için tüm komutları tanımlayan üst öğe.|  
|[CommandPlacements Öğesi](../extensibility/commandplacements-element.md)|İsteğe bağlı. Komut çubuğundaki komutları yerleştirilecek nerede tanımlar.|  
|[VisibilityConstraints Öğesi](../extensibility/visibilityconstraints-element.md)|İsteğe bağlı. Komutlar ve araç çubukları statik görünürlüğünü belirler.|  
|[KeyBindings Öğesi](../extensibility/keybindings-element.md)|İsteğe bağlı. Kısayol tuş birleşimleri, komutları belirtir.|  
|[UsedCommands Öğesi](../extensibility/usedcommands-element.md)|İsteğe bağlı. İsteğe bağlı olarak kendi özgün diğer VSPackage'ları tarafından desteklenen sürümüne uygulamak bir VSPackage sağlar.|  
|[Symbols Öğesi](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|İsteğe bağlı. Derleyici için herhangi bir sembol verilerini--GUID'leri, kimlikleri ve benzeri--içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Yok.||  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

