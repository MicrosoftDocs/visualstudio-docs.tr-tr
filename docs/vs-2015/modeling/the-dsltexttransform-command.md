---
title: DslTextTransform komutu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 882d2c8d0dec5e4673b24436067bd6255c2052be
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853161"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform Komutu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslTextTransform.cmd TextTransform.exe çağırır ve sık kullanılan seçenekleri ile çalışan bir komut dosyasıdır. DslTextTransformation.cmd, gecelik bir derleme otomatikleştirmek için kullanabileceğiniz, [!INCLUDE[dsl](../includes/dsl-md.md)] projeleri. Daha fazla bilgi için [TextTransform yardımcı programı ile dosya oluşturma](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd şu dizinde bulunur:  
  
 **\<Visual Studio SDK'sını yükleme yolu > \VisualStudioIntegration\Tools\Bin**  
  
 Şu bağımsız değişkenler DslTextTransform.cmd giriş olarak belirtebilirsiniz:  
  
- Etki alanı modeli projenin çıkış dizini.  
  
- Tasarımcı tanımı projenin çıkış dizini.  
  
- Metin şablonu dosyasının konumu.  
  
  Varsayılan yönerge işlemcileri ve derlemeler kullanılarak belirtilen bir metin şablonu dosyasını DslTextTransform.cmd işler. Özel yönerge işlemcileri oluşturma, TextTransform.exe çağıran kendi toplu iş dosyası oluşturabilirsiniz. Bu toplu iş dosyasında bütünleştirilmiş kodlarınızı ve ilişkili özel yönerge işlemcisi belirtebilirsiniz.



