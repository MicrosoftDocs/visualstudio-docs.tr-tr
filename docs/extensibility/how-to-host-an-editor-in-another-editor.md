---
title: 'Nasıl yapılır: başka bir düzenleyici bir düzenleyicide konak | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 53b4f02135b18c4641d4e802df3d1124a5d06b47
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058392"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Nasıl yapılır: başka bir düzenleyici bir düzenleyicide ana bilgisayar

Visual Studio'da bir üst pencere olarak barındırma penceresi belirterek içinde başka bir düzenleyici barındırabilir. Bunu yapmak için parametreleri ayarlayın <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentHwnd> ve <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentFrame> alt pencere çerçevesi.

## <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Bir düzenleyici barındırmak için Pencere çerçevesi ayarlamak için

1.  Bir düzenleyici bir alt pencere bölmesine oluşturarak barındırılan düzenleyicisi olarak belirleyin.

     Bu bölme, düzenleyicinin metni nereye ' dir.

2.  Kullanarak barındırma Düzenleyicisi oluşturma <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> yöntemi.

3.  Ayarlama <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentHwnd> ve <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentFrame> için parametre olarak bu özellikleri geçirerek barındırılan Düzenleyicisi penceresini çerçeve uyarlamasını özelliklerinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> yöntemi, sırasıyla.

     Bu parametreleri almak gerekiyorsa, bu özellikler geçirmek <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> yöntemi.

4.  Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> kapsanan Düzenleyicisi için yöntem.

     Düzenleyici içeren Düzenleyicisi barındırılan bölmesinde görüntülenir.

## <a name="robust-programming"></a>Güçlü programlama

**Uygulama Tasarımcısı** Mimarlar için Visual Studio Team Edition'ın başka bir düzenleyici barındıran bir düzenleyici pencere çerçevesi örneğidir. **Uygulama Tasarımcısı** sağ bölmesinde diğer tasarımcılar barındırır. Bir tasarımcı panel (veya **özellikleri** sayfası) her kapsanan tasarımcıları içeren pencere çerçevesinin eklenir.