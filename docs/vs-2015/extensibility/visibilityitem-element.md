---
title: Visibilityıtem öğesi | Microsoft Docs
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
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab4d1fef60ce8b11a23a9d3afd30bcf6b89715d9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779261"
---
# <a name="visibilityitem-element"></a>VisibilityItem Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`VisibilityItem` Komutları ve araç çubuklarını statik görünürlüğünü belirler. Her giriş, bir komut veya menü ve ayrıca bir ilişkili komut UI bağlamı tanımlar. Visual Studio, bunları tanımlama VSPackage'ları yüklemeden komutlar, menüler ve araç çubukları ve kendi görünürlük algılar. IDE kullanır <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> komut UI bağlamı etkin olup olmadığını belirlemek için yöntemi.  
  
 VSPackage'ı yüklendikten sonra Visual Studio komut görünürlük VSPackage'ı tarafından belirlenecek bekliyor yerine `VisibilityItem`. Komutun görünürlüğü belirlemek için ya da uygulayabilirsiniz <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> olay işleyicisi veya <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> komutunuz nasıl uyguladıysanız bağlı olarak yöntemi.  
  
 Bir komut veya sahip menü bir `VisibilityItem` öğesi, yalnızca ilişkili bağlam etkin olduğunda görünür. Her bir bağlam içi komut bileşimi için bir giriş ekleyerek, bir veya daha fazla komut UI bağlamı ile tek bir komut, menü veya araç ilişkilendirebilirsiniz. Bir komut veya menü birden fazla komut UI bağlamı ile ilişkili ise, ilişkili komut UI bağlamları herhangi biri etkin olduğunda ardından bir komut veya menüyü görülebilir.  
  
 `VisibilityItem` Öğesi uygulandığı yalnızca komutlar, menüler ve araç çubuklarını, grupları uygulanmaz. İlgili olmayan bir öğe `VisibilityItem` öğesi, kendi üst menü etkin olduğunda görülebilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|GUID|Gerekli. GUID/ID komut tanımlayıcısı GUİD'si.|  
|kimlik|Gerekli. GUID/ID komut tanımlayıcısı kimliği.|  
|bağlam|Gerekli. UI bağlamı komutu görülebilir.|  
|Koşul|İsteğe bağlı. Bkz: [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[VisibilityConstraints Öğesi](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints` Komutları ve araç çubukları grupları statik görünürlüğünü belirler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Standart bir Visual Studio UI bağlamları içinde tanımlanan *Visual Studio SDK yükleme yolunu*\VisualStudioIntegration\Common\Inc\vsshlids.h dosyasında da olarak <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> ve <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> sınıfları. UI bağlamları daha eksiksiz bir kümesini tanımlanan <xref:Microsoft.VisualStudio.VSConstants> sınıfı.  
  
## <a name="example"></a>Örnek  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [VisibilityConstraints öğesi](../extensibility/visibilityconstraints-element.md)   
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

