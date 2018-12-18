---
title: Templategroupıd öğesi (Visual Studio şablonları) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 91631975d48f6e7e13646c428cdd5b5473bbeed2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144443"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID Öğesi (Visual Studio Şablonları)
Ne tür bir proje öğesi şablonları kategoride görüneceğini belirtir. Bu öğe önemlidir [ShowByDefault (Visual Studio şablonları)](../extensibility/showbydefault-visual-studio-templates.md) ayarlanır `false`. Zaman [ShowByDefault (Visual Studio şablonları)](../extensibility/showbydefault-visual-studio-templates.md) ayarlanır `true`, bir öğe şablonu tüm proje türlerinde kullanılabilir olur.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<Templategroupıd >  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<TemplateGroupID> ... </TemplateGroupID>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Şablon kategorilere ayırır ve nasıl ya da görüntüler tanımlar **yeni proje** veya **Yeni Öğe Ekle** iletişim kutusu.|  
  
## <a name="text-value"></a>Metin Değeri  
 Bir metin değeri gereklidir.  
  
 Metin bir öğe şablonları kategorisine tanımlayıcısını belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `TemplateGroupID` bir öğedir.  
  
 Değeri `TemplateGroupID` öğe proje sistemi kaydı ile birlikte kullanılır (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<sürüm numarası >* \Projects\\) görünür filtre şablonlarına **Yeni Öğe Ekle** iletişim kutusu.  
  
|Visual C++ değeri|Açıklama|  
|------------------------|-------------|  
|VC-yerel|Yerel projeleri için kullanılır. Ayrıca bir proje türü belirlenemiyorsa varsayılan.|  
|VC yönetilen|Kullanılan tarafından yönetilen (/ clr) projeleri|  
|VC Windows|Windows Platformu (yerel/yönetilen/deposu) hedef tüm projeleri için kullanılır|  
|WinRT yerel UAP|Windows 10 mağazası projeleri için kullanılır|  
|CodeSharing-yerel|Paylaşılan öğesi projeleri için kullanılır|  
|WinRT yerel 6.3|Windows 8.1 mağazası projeleri için kullanılır|  
|Yerel telefon 6.3 WinRT|Windows Phone 8.1 projeleri için kullanılır|  
|WinRT-yerel|Windows 8.0 mağazası projeleri için kullanılır|  
|VC Android|Android projeleri için kullanılır|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)