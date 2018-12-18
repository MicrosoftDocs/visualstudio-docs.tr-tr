---
title: 'Nasıl yapılır: Visual Studio 2015 dağıtırken ürün anahtarlarını otomatik olarak uygulama | Microsoft Docs'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 11
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 32f8845790168aae784f3659f54c89e000681a15
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53050233"
---
# <a name="how-to-automatically-apply-product-keys-when-deploying-visual-studio"></a>Nasıl Yapılır: Visual Studio’yu dağıtırken ürün anahtarlarını otomatik olarak uygulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 için en son belgeler için bkz. [Visual Studio'yu dağıtırken ürün anahtarlarını otomatik olarak uygulama](/visualstudio/install/automatically-apply-product-keys-when-deploying-visual-studio).

Ürün anahtarınızı program aracılığıyla Visual Studio 2015'in dağıtımını otomatikleştirmek için kullanılan bir komut dosyası bir parçası olarak uygulayabilirsiniz. Ürün anahtarları bir cihazda program aracılığıyla Visual Studio'nun veya bir tamamlandıktan sonra yükleme sırasında ayarlanabilir.

## <a name="apply-the-license-during-installation"></a>Lisans Yükleme sırasında Uygula
 Visual Studio Kurulum işlemi sırasında bir ürün anahtarı uygulamak için / Set-Edition parametresini kullanın. Bu kurulum parametresi/silent kullanılabilir bir son kullanıcı için zaten lisanslı bir durumda Visual Studio'yu yüklemek için parametre. / Set-Edition parametresini kullanmak için bir komut istemi açın. (Örn. vs_enterprise.exe veya vs_professional.exe) Kurulum programını çalıştırın ve çizgi içermeyen içeren bir ürün anahtarı ile (25 karakter) / Set-Edition parametresini ayarlayın:

 Bu ürün anahtarıyla AAAAABBBBBCCCCCDDDDDEEEEEEE Visual Studio 2015 Enterprise'ı yüklemek için bir örnek komutu.

 `vs_enterprise.exe [any other setup parameters] /ProductKey AAAAABBBBBCCCCCDDDDDDEEEEEE`

## <a name="apply-the-license-after-installation"></a>Yüklemeden sonra lisans Uygula
 Visual Studio'nun yüklü bir sürümü ürün anahtarıyla sessiz modda hedef makinelerde storePID.exe yardımcı programını kullanarak etkinleştirebilirsiniz. StorePID.exe olduğundan Visual Studio ile yüklenen bir yardımcı program  **\<sürücü >:\\\Program dosyaları (x86) \Microsoft Visual Studio 14.0\Common7\IDE\StorePID.exe**.

 StorePID.exe System Center aracı veya ürün anahtarı (tireler dahil) ve Microsoft ürün kodu (MPC) yükseltilmiş bir komut istemi, kullanılarak yükseltilmiş ayrıcalıklarla çalıştırın. Ürün anahtarı tireler dahil ettiğinizden emin olun!

 `StorePID.exe [product key including the dashes] [MPC]`

 Bu bir MPC 07060 biri olan Visual Studio 2015 Enterprise, bir ürün anahtarı "AAAAA-BBBBB-CCCCC-GGGGGG-EEEEEE" yüklemek için bir örnek komut satırı.

 `C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 07060`

 Aşağıdaki tablo, Visual Studio'nun her sürümü için MPC kodları listeler:

|Visual Studio sürümü|MPC|
|---------------------------|---------|
|Visual Studio Enterprise 2015|07060|
|Visual Studio Professional 2015|07062|
|Visual Studio Test Professional 2015|07066|
|Visual Studio Ultimate 2013|06181|
|Visual Studio Premium 2013|06191|
|Visual Studio Professional 2013|06177|
|Visual Studio Test Professional 2013|06194|

 Bir ürün anahtarı alma hakkında daha fazla bilgi için lütfen bkz [nasıl yapılır: Visual Studio ürün anahtarını bulmak](../install/how-to-locate-the-visual-studio-product-key.md).

 StorePID.exe ürün anahtarı başarıyla uygulandığında, 0 döndürür. Hatalarla karşılaştığında, 1-6 arasında bir sayı döndürür.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'yu yükleyin](../install/install-visual-studio-2015.md)