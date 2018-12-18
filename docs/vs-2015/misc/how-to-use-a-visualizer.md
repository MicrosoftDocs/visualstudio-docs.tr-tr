---
title: 'Nasıl yapılır: Görselleştirici kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.dataviewer
- vs.debug.stringviewer
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, about visualizers
ms.assetid: d2611385-0134-4387-8c5a-979fe625a462
caps.latest.revision: 37
ms.author: mikejo
manager: douge
ms.openlocfilehash: f50dba2f236127bd2e155ea13cb8646f18de0e92
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721914"
---
# <a name="how-to-use-a-visualizer"></a>Nasıl Yapılır: Görselleştirici Kullanma
Görselleştirici, veri türü için anlamlı bir şekilde bir değişken veya nesne içeriğini görüntülemek için kullanabilirsiniz. Görselleştiriciler dan kullanabileceğiniz **DataTips**, **izleme** penceresinde **Otolar** penceresinde veya **Yereller** penceresi.  
  
 Görselleştiriciler Compact Framework'te desteklenmez.  
  
> [!NOTE]
>  İçinde **Store** uygulamalar, yalnızca standart metin, HTML, XML ve JSON görselleştiriciler desteklenir. Özel (kullanıcı tarafından oluşturulmuş) görselleştiriciler desteklenmez.  
  
### <a name="to-open-a-visualizer"></a>Görselleştirici açmak için  
  
1.  Bir değişken adı ile yanında Büyüteç simgesine tıklayarak **DataTips**, **Watch** penceresinde veya **Otolar**, **Yereller**, veya **Hızlı Bakış** penceresi.  
  
     Görselleştiriciler listesi görüntülenir.  
  
2.  Kullanmak istediğiniz Görselleştirici'a tıklayın.  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>Uzaktan hata ayıklama sırasında yönetilen kod için Görselleştirici kullanmak için  
  
-   Hata ayıklama oturumu başlatmadan önce DLL Görselleştirici, uzak bilgisayara kopyalayın.  
  
     DLL yolu hem uzak ve yerel bilgisayarlardan aynı olmalıdır. Bu yolu aşağıdaki konumlarda olabilir:  
  
     *Visual Studio yükleme yolu* `\Common7\Packages\Debugger\Visualizers`  
  
     veya  
  
     `My Documents\Visual Studio 2010\Visualizers` *Visual Studio sürümü* `\Visualizers`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Görselleştiriciler oluşturma](../debugger/create-custom-visualizers-of-data.md)   
 [Nasıl yapılır: Görselleştiriciyi yükleme](../debugger/how-to-install-a-visualizer.md)   
 [Nasıl yapılır: Görselleştirici yazma](../debugger/how-to-write-a-visualizer.md)   
 [Veri İpuçları'ndaki veri değerlerini görüntüleme](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)