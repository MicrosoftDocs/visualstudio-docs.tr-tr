---
title: Yeni Öğe Ekle İletişim Kutusuna Dizin Ekleme | Microsoft Docs
description: Dizinleri kaydetmek için kayıt defteri betiği kullanarak yeni Visual Studio Ekle iletişim kutusuna dizinler ekleme hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dab135f8e8632755674d7b3ddf5972592f74d315
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904366"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Yeni Öğe Ekle iletişim kutusuna dizin ekleme
Aşağıdaki kod örneği, Yeni Öğe Ekle iletişim kutusu için yeni bir dizin kümesi **kaydetmeyi** gösterir. Yeni Öğe Ekle **iletişim kutusunun dizinleri** her proje için farklıdır. Bu nedenle dizinler, projesinde bulunan **Projeler** alt anahtarı altında **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects.**

## <a name="registry-script"></a>Kayıt defteri betiği

```
NoRemove Projects
{
  NoRemove %GUID_Project%
  {
    NoRemove AddItemTemplates
    {
      NoRemove TemplateDirs
      {
        ForceRemove %CLSID_Package%
        {
      ForceRemove /1 = s '#%Folder_Label_ResID%'
          {
            val TemplatesDir = s '%Template_Path%'
            val SortPriority = d 2000
          }
        }
      }
    }
  }
}
```

 `%Template_Path%`değeri, proje şablonlarını içeren dizinin tam yolunu belirtir. Bu şablonlar kopyalanan *.vsz* dosyaları veya prototik şablon dosyaları olabilir.

 değeri `SortPriority` bir sıralama önceliğini belirtir.

## <a name="add-items-to-an-existing-project"></a>Mevcut projeye öğe ekleme
 Var olan bir projeye öğe de eklemek için kullanabilirsiniz. Örneğin, bir [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] proje için *\<root> \Program Files\Microsoft Visual Studio\VC#\CSharpProjectItems\LocalProjectItems* klasörüne öğe eklersiniz. Bu durumda, `%GUID_Project%` bir C# projesinin GUID değeridir ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 Ayrıca, bir proje alt türü programlamak tarafından mevcut bir projeyi genişleterek. Proje alt türüyle, yeni bir proje türü yazmadan projeyi genişletin. Proje alt türleri hakkında daha fazla bilgi için [bkz. Proje alt türleri.](../../extensibility/internals/project-subtypes.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)
- [Yeni Öğe Ekle iletişim kutusuna öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Yeni Proje iletişim kutusuna dizin ekleme](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
