---
title: Visual Studio SDK yükleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- visual-studio-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9e5546b07ef9917590daa573efd99377339412c7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793561"
---
# <a name="installing-the-visual-studio-sdk"></a>Visual Studio SDK'sını yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Visual Studio SDK, Visual Studio yüklemesinin bir parçası yükleme  
 Visual Studio yüklemenizin VSSDK eklemek istiyorsanız, özel bir yükleme yapmanız gerekir.  
  
> [!NOTE]
>  Yürütülebilir Kurulum, Visual Studio SDK çağrılır **Visual Studio genişletilebilirlik Araçları**.  
  
1.  Visual Studio 2015 yüklemesini başlatın. Visual Studio Express dışında herhangi bir sürümünü yükleyebilirsiniz.  
  
2.  İlk ekranda seçin **özel**değil **varsayılan**. **İleri**'ye tıklayın.  
  
3.  Özel özellikler ağaç görünümünü görürsünüz. Açık **ortak Araçlar**. Görmelisiniz **Visual Studio genişletilebilirlik Araçları** .  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4.  Denetleme **Visual Studio genişletilebilirlik Araçları** , ardından **sonraki** yüklemeye devam edin.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Visual Studio yüklendikten sonra Visual Studio SDK'sını yükleme  
 Visual Studio yüklemenizin tamamladıktan sonra Visual Studio SDK'sı yüklemeye karar verirseniz, aşağıdaki yordamı izlemeniz gerekir:  
  
1.  Git **Denetim Masası / programları / programlar ve Özellikler**ve Ara **Visual Studio 2015**. Visual Studio SDK'sı için Visual Studio 2015 Express dışında herhangi bir sürümünü yükleyebilirsiniz.  
  
2.  Sağ **Visual Studio 2015**ve ardından **değişiklik**. Yükleme sayfası görmeniz gerekir.  
  
3.  Olarak aynı yordamı izleyin **Visual Studio yüklemesinin bir parçası Visual Studio SDK'sını yükleme** yukarıda.  
  
4.  Tıklayın **Visual Studio genişletilebilirlik Araçları** Visual Studio SDK'yı yüklemek için bağlantı.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Bir çözümü Visual Studio SDK'sını yükleme  
 VSSDK yüklemeden bir genişletilebilirlik projesi bir çözüm açarsanız, Çözüm Gezgini'nde üzerindeki bir vurgulanan bilgi çubuğuna tarafından istenir. Aşağıdaki gibi görünmelidir:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Komut satırından Visual Studio SDK'sını yükleme  
 VSSDK kullanarak komut satırından yükleyebilirsiniz **/ınstallselectableıtems** Visual Studio Yükleyicisi ile geçiş yapın. Yükleyici ile komut satırı parametrelerini kullanma hakkında daha fazla ayrıntı için bkz [yükleme Visual Studio 2015](../install/install-visual-studio-2015.md).  
  
 VSSDK sessizce Visual Studio 2015 Community yükleyicisini kullanarak yüklemek nasıl aşağıda verilmiştir:  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Yüklü Visual Studio sürümünüzle eşleşen Visual Studio yükleyicisi kullanmanız gerektiğini unutmayın. Örneğin, Visual Studio Enterprise yüklü varsa, Visual Studio Enterprise Yükleyici (vs_enterprise.exe) çalıştırmanız gerekir.







