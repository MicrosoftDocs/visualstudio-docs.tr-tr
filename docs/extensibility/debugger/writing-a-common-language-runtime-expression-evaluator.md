---
title: Bir ortak dil çalışma zamanı ifade değerlendiricisi yazma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d93299702db0c56963eb8f404d05e8e67ab08b0
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276825"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Bir ortak dil çalışma zamanı ifade değerlendiricisi yazma
> [!IMPORTANT]
>  Visual Studio 2015'te, bu şekilde ifade değerlendiricisi uygulama kullanım dışı bırakılmıştır. CLR ifade değerlendiricisi uygulama hakkında daha fazla bilgi için bkz: [CLR ifade değerlendiricilerini](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendiricisi örnek](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 İfade değerlendiricisi (EE) sözdizimi işleme hata ayıklama altyapısı (DE) ve hata ayıklaması yapılan kod üretilen programlama dilini semantikleri parçasıdır. İfadeler bir programlama dili bağlamında değerlendirilmelidir. Örneğin, bazı dillerde, ' % s'ifadesi "A + B" anlamına gelir "sum a ve b" Diğer dillerde aynı ifadesi "A veya b" gelebilir. Bu nedenle, ayrı bir EE Visual Studio IDE içinde hata ayıklama için nesne kodu oluşturan her programlama dili için yazılmış olmalıdır.  
  
 Visual Studio hata ayıklama paketi bazı yönlerini programlama dilini bağlamında kodu yorumlayan gerekir. Örneğin, ne zaman yürütmeyi durduran içine kullanıcı tarafından yazılan tüm ifadeleri bir kesme noktasında bir **Watch** penceresi değerlendirilir ve görüntülenir. Kullanıcı, bir ifadeyi yazarak yerel değişkenin değerini değiştirebilir bir **Watch** penceresi veya **hemen** penceresi.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [Ortak dil çalışma zamanı ve ifade değerlendirme](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Visual Studio IDE'ye özel programlama dilini tümleştirdiğinizde bir EE yazma özel dil ifadeleri bağlam içinde değerlendirme yeteneğine bir Microsoft Ara dili (MSIL) derleme olanak açıklar hata ayıklama altyapısı yazmak zorunda kalmadan.  
  
 [İfade değerlendirici mimarisi](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Gerekli EE arabirimi uygulayan ve ortak dil çalışma zamanı sembol sağlayıcısı (SP) ve bağlayıcı arabirimleri çağırmak nasıl ele alınmaktadır.  
  
 [İfade değerlendiricisi kaydetme](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 EE kendisi ortak dil çalışma zamanı ve çalışma zamanı ortamlarını Visual Studio ile bir sınıf üreteci olarak kaydetmeniz gerekir, notlar.  
  
 [İfade değerlendiricisi uygulama](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 Bir ifade değerlendirme işlemi, hata ayıklama altyapısı (DE), sembol sağlayıcısı (SP), bağlayıcı nesnesi ve ifade değerlendiricisi (EE) nasıl içerir açıklar.  
  
 [Görüntü yerel öğeler](../../extensibility/debugger/displaying-locals.md)  
 Yürütme durakladığında, hata ayıklama paketi yerel değişkenleri ve bağımsız değişkenler listesini almak için DE çağırması açıklar.  
  
 [Gözcü penceresi ifadesini değerlendirme](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Visual Studio hata ayıklama paketi kendi izleme listesindeki her bir ifadenin geçerli değerini belirlemek için DE çağırması belgeler.  
  
 [Yerel bir değiştirin](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Yerel bir değerinin değiştirilmesi her satırı için Yereller penceresine adını, türünü ve yerel geçerli değerini sağlayan ilişkili nesne olduğunu açıklar.  
  
 [Tür görselleştiricileri ve özel görüntüleyiciler uygulama](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Hangi arabirim tür görselleştiricileri ve özel görüntüleyiciler desteklemek için hangi bileşen tarafından uygulanması gereken açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio hata ayıklayıcı genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md)