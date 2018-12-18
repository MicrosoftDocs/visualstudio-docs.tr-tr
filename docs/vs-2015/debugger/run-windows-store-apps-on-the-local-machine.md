---
title: Yerel makinede çalıştırma Windows Store apps | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 40fafcbdacac8a63a4aba70526a473d091b35de8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766838"
---
# <a name="run-windows-store-apps-on-the-local-machine"></a>Yerel makinede Windows Store uygulamaları çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yalnızca Windows için geçerlidir] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Hata ayıklama, test veya bir Windows Store uygulaması Performans Analizi çalıştırmak için Visual Studio barındıran aynı makine üzerinde uygulamayı çalıştırabilirsiniz. Görüntü cihazda Dokunmatik özellikli ise, uygulama tam işlevselliğini alıştırma yapabilirsiniz; Aksi takdirde, fare ve klavye hareketlerine sınırlı olacaktır.  
  
##  <a name="BKMK_In_this_topic"></a> Bu konudaki  
 Şunları öğrenebilirsiniz:  
  
 [Yerel makine üzerinde çalıştırmayı öğrenin](#BKMK_How_to_run_on_a_local_machine)  
  
 [Tek bir izleyicinin bir Windows Store uygulaması ve Visual Studio arasında geçiş yapma](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
##  <a name="BKMK_How_to_run_on_a_local_machine"></a> Yerel makine üzerinde çalıştırmayı öğrenin  
 Uygulamayı yerel makinede çalıştırmak için seçin **yerel makine** hata ayıklayıcı hata ayıklamayı Başlat düğmesinin yanındaki aşağı açılan listeden **standart** araç çubuğu.  
  
 ![Yerel makinede çalıştırma](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")  
  
 Göremiyorsanız **standart** araç çubuğunda tıklatın **görünümü** menüsünde **araç çubukları**ve ardından **standart**.  
  
 Aşağı açılan listeden yaptığınız seçim, proje özellikleri dosyasında kalıcı hale getirilir ve varsayılan hedef çalışma olur.  
  
 Proje Özellikleri dosyası doğrudan çalışma hedef de ayarlayabilirsiniz. İçinde proje adınıza sağ **Çözüm Gezgini** seçip **özellikleri**. Ardından aşağıdakilerden birini yapın:  
  
-   C# ve Visual Basic projelerinde tıklayın **hata ayıklama** seçip **yerel makine** gelen **hedef cihaz** aşağı açılan listesi.  
  
     ![C&#35; ve Visual Basic proje özellik sayfası](../debugger/media/vsrun-cs-vb-projprop-local.png "VSRUN_CS_VB_ProjProp_Local")  
  
-   C++ ve JavaScript projelerinde genişletin **yapılandırma özellikleri** düğümünü tıklatın **hata ayıklama**ve ardından **yerel hata ayıklayıcı** gelen **hata ayıklayıcı başlatmak için** listesi.  
  
     ![C&#43; &#43; ve JavaScript proje özellikleri sayfasında](../debugger/media/vsrun-cpp-js-projprop-local.png "VSRUN_CPP_JS_ProjProp_Local")  
  
##  <a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> Tek bir izleyicinin bir Windows Store uygulaması ve Visual Studio arasında geçiş yapma  
 **Çalışan bir örneğini bir Windows Store uygulaması Visual Studio'ya geçmek için**  
  
 Yerel makine üzerindeki bir Windows Store uygulaması çalıştırın ve yalnızca tek bir izleyici kullandığınızda, uygulamayı çalıştıran bırakarak Visual Studio'ya dönün geçiş yapmak isteyebilirsiniz. Örneğin, uygulama tarafından bir olay bekleniyor gibi bir kesme noktasına ulaşıldı veya uzun veya sonsuz bir döngüde yakalanan bir durumda olabilir. Visual Studio'ya dönmek için ALT + SEKME tuşuna basın.



