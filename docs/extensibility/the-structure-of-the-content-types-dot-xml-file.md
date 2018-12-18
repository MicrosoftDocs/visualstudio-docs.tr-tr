---
title: '[Content_types] .xml dosyasının yapısı | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 538a518d1186dc50a9e5e89635af0a07c2542041
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893279"
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>[Content_types].xml Dosyasının Yapısı
Bir VSIX paketi, içerik türleri hakkındaki bilgileri içerir. Visual Studio paketi yüklemek için [Content_Types] .xml dosyasını kullanır, ancak dosyayı yüklemez.  
  
> [!NOTE]
>  Bu konuda, VSIX paketinde kullanılan [Content_Type] .xml dosyaları için geçerli olsa da, [Content_Types] .xml dosya türü parçasıdır *açık paketleme kuralları (OPC)* standart. Daha fazla bilgi için [OPC: A yeni standart için paketleme verilerinizi](http://go.microsoft.com/fwlink/?LinkID=148207) MSDN Web sitesinde.  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Kök öğe ve öznitelikler ve alt öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="root-element"></a>Kök öğe  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`Types`|VSIX paketini dosya türlerini listeleme alt öğeleri içerir.|  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Xmlns`|(Gerekli) Bu [Content_Types] .xml dosyası için kullanılan şema konumu.|  
  
### <a name="attribute-name-attribute"></a>{Öznitelik adı} Özniteliği  
  
| Değer | Açıklama |
| - | - |
| http://schemas.openformats.org/package/2006/content-types | İçerik türleri şema konumu. |
  
### <a name="child-elements"></a>Alt Öğeler  
 `Types` Herhangi bir sayıda öğe içerebilir `Default` öğeleri.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`Default`|VSIX paketinde bir içerik türü açıklar. Paketteki her dosya türü kendi olmalıdır `Default` öğesi.|  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Extension`|VSIX paketini bir dosyanın dosya adı uzantısı.|  
|`ContentType`|Dosya adı uzantısıyla ilişkili olan içerik türünü açıklar.|  
  
### <a name="attribute-name-attribute"></a>{Öznitelik adı} Özniteliği  
 Visual Studio aşağıdaki tanır `ContentType` ilişkili değerleri `Extension` türleri.  
  
|Uzantı|contentType|  
|---------------|-----------------|  
|txt|metin/düz|  
|pkgdef|metin/düz|  
|XML|metin/xml|  
|vsixmanifest|metin/xml|  
|htm veya html|metin/html|  
|RTF|Uygulama/rtf|  
|PDF|Uygulama/pdf|  
|GIF|Görüntü/gif|  
|JPG veya jpeg|Görüntü/jpg|  
|TIFF|Görüntü/TIFF|  
|vsix|Uygulama/zip'i|  
|Zip|Uygulama/zip'i|  
|dll|Uygulama/octet-akış|  
|diğer tüm dosya türleri|Uygulama/octet-akış|  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki [Content_Types] .xml dosyasının tipik bir VSIX paketi açıklar.  
  
### <a name="code"></a>Kod  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
    <Default Extension="vsixmanifest" ContentType="text/xml" />   
    <Default Extension="dll" ContentType="application/octet-stream" />   
    <Default Extension="png" ContentType="application/octet-stream" />   
    <Default Extension="txt" ContentType="text/plain" />   
    <Default Extension="pkgdef" ContentType="text/plain" />   
</Types>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir VSIX paketinin anatomisi](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX Uzantı Şeması 1.0 başvurusu](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Verilerinizi paketleme için yeni bir standart](http://go.microsoft.com/fwlink/?LinkID=148207)