---
title: 'Nasıl yapılır: başka bir düzenleyicide bir düzenleyicide konak | Microsoft Docs'
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
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fead1aa7b1094fe5bcd1cac989b6853d3564b00b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803168"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Nasıl yapılır: başka bir düzenleyicide bir düzenleyicide barındırın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da barındırma penceresi bir üst pencere olarak belirterek, içinde başka bir düzenleyicide barındırabilirsiniz. Bunu yapmak için parametreleri ayarlayın <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> ve <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> alt pencere çerçevesi.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Bir düzenleyici barındırmak için Pencere çerçevesi ayarlamak için  
  
1.  Bir düzenleyici bir alt pencere bölmesi oluşturarak barındırılan bir düzenleyici olarak belirleyin.  
  
     Bu bölme, düzenleyicinin metni gidecekleri ' dir.  
  
2.  Kullanarak barındırma Düzenleyicisi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> yöntemi.  
  
3.  Ayarlama <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> ve <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> bu özellikler için parametre olarak geçirerek barındırılan Düzenleyicisi penceresi çerçeve uygulama özelliklerinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> yöntemi, sırasıyla.  
  
     Bu parametreleri almanız gerekiyorsa, bu özelliklerin geçirmek <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> yöntemi.  
  
4.  Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> kapsanan Düzenleyicisi için yöntemi.  
  
     Düzenleyici içeren Düzenleyicisi barındırılan bölmesinde görünür.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 **Uygulama Tasarımcısı** mimarları için Visual Studio Team Edition, başka bir düzenleyicide barındıran bir düzenleyici pencere çerçevesi örneğidir. **Uygulama Tasarımcısı** diğer tasarımcılar, sağ bölmede barındırır. Tasarımcı bölmesi (veya **özellikleri** sayfası) her biri bağımsız tasarımcıları içeren pencere çerçevesi için eklenir.

