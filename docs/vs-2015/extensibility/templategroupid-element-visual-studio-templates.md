---
title: TemplateGroupID öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 53d1f6628ff9df48879a34417b7d89223d848dd8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186432"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID Öğesi (Visual Studio Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Öğe şablonlarının ne tür projenin gösterileceğini belirtir. Bu öğe, [ShowByDefault (Visual Studio şablonları)](../extensibility/showbydefault-visual-studio-templates.md) olarak ayarlandığında önemlidir `false` . [ShowByDefault (Visual Studio şablonları)](../extensibility/showbydefault-visual-studio-templates.md) olarak ayarlandığında `true` , tüm proje türlerinde bir öğe şablonu kullanılabilir.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<TemplateGroupID>  
  
## <a name="syntax"></a>Syntax  
  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Şablonu kategorilere ayırır ve **Yeni proje** veya **Yeni öğe Ekle** iletişim kutusunda nasıl görüntülediğini tanımlar.|  
  
## <a name="text-value"></a>Metin Değeri  
 Bir metin değeri gereklidir.  
  
 Metin bir öğe şablonları kategorisi için tanımlayıcıyı belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `TemplateGroupID` bir öğesidir.  
  
 Öğe değeri, `TemplateGroupID` Proje sistem kaydı (HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \projects) ile birlikte, \\ *\<version number>* \\ **Yeni öğe Ekle** iletişim kutusunda görünen şablonları filtrelemek için kullanılır.  
  
|Visual C++ değeri|Anlamı|  
|------------------------|-------------|  
|VC-yerel|Yerel projeler için kullanılır. Ayrıca, bir proje türü belirlenemiyorsa varsayılan değer.|  
|VC tarafından yönetilen|Yönetilen (/CLR) projeler için kullanılır|  
|VC-Windows|Windows platformunu hedefleyen tüm projeler için kullanılır (Yerel/yönetilen/mağaza)|  
|WinRT-yerel-UAP|Windows 10 mağazası projeleri için kullanılır|  
|CodeSharing-yerel|Paylaşılan öğe projeleri için kullanılır|  
|WinRT-yerel-6,3|Windows 8.1 mağaza projeleri için kullanılır|  
|WinRT-yerel-telefon-6,3|Windows Phone 8,1 projeleri için kullanılır|  
|WinRT-yerel|Windows 8,0 mağaza projeleri için kullanılır|  
|VC-Android|Android projeleri için kullanılır|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
