---
title: Saydamlığından ~ SAK dosyalarının | Microsoft Docs
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
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 930ee0690e14431298461f50387a94dd4bb0ce7d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780470"
---
# <a name="elimination-of-sak-files"></a>~SAK Dosyalarının Ortadan Kaldırılması
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kaynak Denetimi Eklentisi API 1.2, ~ SAK dosyalarının, özellik bayrakları ve kaynak denetimi eklentisi MSSCCPRJ dosyasını ve paylaşımlı kullanıma Almalarla destekleyip desteklemediğini algılamak yeni işlevleri tarafından değiştirildi.  
  
## <a name="sak-files"></a>~ SAK dosyalarının  
 Visual Studio .NET 2003 oluşturulan geçici dosyalar ön ekine sahip ~ SAK. Bu dosyalar kaynak denetimi eklentisi destekleyip desteklemediğini belirlemek için kullanılır:  
  
- MSSCCPRJ. SCC dosyası.  
  
- Birden çok (paylaşılan) kullanıma alma.  
  
  Kaynak Denetimi Eklentisi API 1.2 ile sağlanan gelişmiş işlevleri destekleyen eklentileri için yeni özellikler, bayraklar ve İşlevler, aşağıdaki bölümlerde ayrıntılı kullanımı geçici dosyalar oluşturmadan bu özellikler IDE algılayabilir.  
  
## <a name="new-capability-flags"></a>Yeni özellik bayrakları  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Yeni işlevleri  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Kaynak Denetimi Eklentisi birden çok (paylaşılan) kullanıma destekler ve ardından bunu bildirir, `SCC_CAP_MULTICHECKOUT` yetenek ve uygular `SccIsMultiCheckOutEnabled` işlevi. Kaynak denetimli projelerin herhangi bir kullanıma alma işlemi oluştuğunda, bu işlev çağrılır.  
  
 Kaynak Denetimi Eklentisi oluşturma ve bir MSSCCPRJ kullanımını destekliyorsa. SCC dosyasını ve ardından bildirir `SCC_CAP_SCCFILE` yetenek ve uygular [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Bu işlev, dosyaların bir listesini çağrılır. İşlev döndürür `TRUE/FALSE` Visual Studio bir MSSCCPRJ kullanması gerekip gerekmediğini belirtmek her bir dosya için. SCC dosyasının. Kaynak denetimi eklentisi şu yeni özellikleri ve işlevleri desteklemiyor seçerse bu dosyalarının oluşturulmasını devre dışı bırakmak için aşağıdaki kayıt defteri anahtarını kullanabilirsiniz:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateTemporaryFilesInSourceControl" = dword: 00000001  
  
> [!NOTE]
>  Bu kayıt defteri anahtarı DWORD: 00000000 ayarlarsanız, varolmayan olan anahtarına eşdeğerdir ve geçici dosyalar oluşturmak Visual Studio hala çalışır. Ancak, kayıt defteri anahtarı DWORD: 00000001 ayarlarsanız, geçici dosyalar oluşturmak Visual Studio denemez. Bunun yerine kaynak denetimi eklentisi MSSCCPRJ desteklemediğini varsayar. SCC dosya ve paylaşımlı kullanıma Almalarla desteklemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

