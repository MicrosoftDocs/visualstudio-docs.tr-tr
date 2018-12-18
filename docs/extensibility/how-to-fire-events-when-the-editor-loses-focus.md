---
title: 'Nasıl yapılır: Düzenleyici odağı kaybettiğinde olayları yangın | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af6abf503bec94cb45638b1e059f545f005cb318
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639662"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Nasıl yapılır: Düzenleyici odağı kaybettiğinde olayları yangın
Bazen bir düzenleyici penceresi çerçevesinde odağı kaybettiğinde öğrenmek gereklidir. Örneğin, düzenleyici artık üzerinde odaklanmıştır sonra bir kod penceresinde kodu ayıklamak gerekebilir. Aşağıdaki yordam, odak kaybetme Düzenleyicisi bildirim almak için izlemeniz gereken adımlar sağlar.  
  
## <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Bir olay yanıt odak kaybetmeden bir düzenleyici olarak harekete geçirmek için  
  
1.  İzleme seçimi olayları elde ederek bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> nesnesinden <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> ve verin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> nesne.  
  
3.  Çağrıda <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, Aranan `elementid==SEID_WindowFrame`.  
  
4.  Test `varValueNew` parametresi iki şey için:  
  
    1.  Aradığınız pencere çerçevesi.  
  
    2.  Bu pencere çerçevesinin seçimi, programınızı kaybeder noktası.