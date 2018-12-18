---
title: Ekleme dizinleri Yeni Öğe Ekle iletişim kutusu | Microsoft Docs
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
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d094f9911b80f3cff3e648da2593c62e0429fb54
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751495"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Yeni Öğe Ekleme İletişim Kutusuna Dizin Ekleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aşağıdaki kod örneği, dizinler için yeni bir dizi kaydettirmek gösterilmektedir **Yeni Öğe Ekle** iletişim kutusu. Dizinler için **Yeni Öğe Ekle** iletişim kutusunda her proje için farklıdır. Bu nedenle, dizinleri bulunan projeler alt anahtarı altında kayıtlı \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects >:  
  
## <a name="the-registry-script"></a>Kayıt betiği  
  
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
  
 Template_Path değeri proje şablonları içeren dizinin tam yolunu belirtir. .Vsz dosyaları veya Prototipik şablon dosyaları kopyalamak için bu şablonları olabilir.  
  
 SortPriority değeri bir sıralama önceliği belirtir.  
  
## <a name="adding-items-to-an-existing-project"></a>Varolan bir projeye öğe ekleme  
 Mevcut bir projeyi öğeleri de ekleyebilirsiniz. Örneğin, bir [!INCLUDE[csprcs](../../includes/csprcs-md.md)] proje öğeleri ekleyebilir \<kök > \Program Visual Studio \VC#\CSharpProjectItems\LocalProjectItems klasörüne gidin. Bu durumda `%GUID_Project%` bir C# projesi ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}) GUID değeridir.  
  
 Ayrıca, mevcut bir projeyi bir proje alt programlayarak genişletebilirsiniz. Proje alt türü ile yeni bir proje türü yazmak zorunda kalmadan bir proje genişletebilirsiniz. Proje alt türleri hakkında daha fazla bilgi için bkz: [proje alt türleri](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Öğeler ekleme yeni öğe Ekle iletişim kutuları](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Yeni Proje İletişim Kutusuna Dizin Ekleme](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

