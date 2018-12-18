---
title: Bir uzantıyı güncelleştir | Microsoft Docs
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
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 586a9f803fc8a02693951db6bf3718235b92497c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059333"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Nasıl yapılır: Visual Studio uzantısını güncelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanarak, sisteminizde Visual Studio uzantısı güncelleştirebilirsiniz **Uzantılar ve güncelleştirmeler** güncelleştirilmiş sürümünü yüklemek için. Bir uzantının güncelleştirilmiş bir sürümü oluşturursanız, geldiğiniz VSIX bildirimi sürüm numarasını artırılarak güncelleştirilmiş gibi.

 Updates are Installed gelen uzantının VSIX bildirimini aynı olduğunda `ID` olarak yüklenen bir ve daha yüksek bir `Version` sayı. Varsa `Version` sayıdır aynı veya daha düşükse paket yüklenemiyor. Varsa `ID` değerleri eşleşmiyor, henüz yüklenmemiş paketi ayrı bir uzantı kabul edilir.

 Geliştirme sırasında çakışmaları önlemek için uzantıları sürüyor, eski sürümlerini kaldırın ve ayrıca kaldırma veya diğer potansiyel olarak çakışan uzantıları devre dışı öneririz.

### <a name="to-update-an-extension-on-your-system"></a>Sisteminizde bir uzantı güncelleştirmek için

1.  Üzerinde **Araçları** menüsünü tıklatın **Uzantılar ve güncelleştirmeler**.

2.  Sol bölmede **güncelleştirmeleri**.

3.  Orta bölmede, yüklemek istediğiniz Güncelleştirme'ye tıklayın.

     Uzantının güncelleştirilmiş sürüm numarası, sağ bölmede, diğer bilgileriyle birlikte görüntülenir.

4.  Sağ bölmenin altında tıklatın **güncelleştirme**.

### <a name="to-publish-an-update-of-an-extension"></a>Bir güncelleştirme uzantı yayımlamak için

1.  Visual Studio'da, güncelleştirmek istediğiniz uzantısı için çözümü açın. Değişiklikleri yapın.

    > [!IMPORTANT]
    >  İmzalanmamış tüm kullanıcı uzantıları otomatik olarak güncelleştirilmesini değil. Her zaman uzantılarınızı imzalamanız gerekir.

2.  İçinde **Çözüm Gezgini**, source.extension.manifest açın.

3.  Bildirim Tasarımcısı'nda sayı değerini artırın **sürüm** alan.

4.  Çözümü kaydetmek ve derleyin.

5.  Yeni .vsix dosyasını (projenin \bin\Debug\ klasöründe) yükleyin [Visual Studio Galerisi](http://go.microsoft.com/fwlink/?LinkID=123847) Web sitesi.

     Uzantı önceki bir sürümü olan bir kullanıcı açıldığında **Uzantılar ve güncelleştirmeler**, yeni sürümü görünür **güncelleştirmeleri** aracı güncelleştirme otomatik olarak aramak için ayarlanmış olması koşuluyla, liste.

     Etkinleştirebilir veya alt kısmındaki güncelleştirmeleri için otomatik denetimini devre dışı bırakmak **güncelleştirmeleri** bölmesinde (**etkinleştir/devre dışı bırak mevcut güncelleştirmeleri otomatik olarak algılanmasını**), hangi değişikliklerin **denetle güncelleştirmeleri** ayarı **Araçlar / Seçenekler / ortam / Uzantılar ve güncelleştirmeler**.

    > [!NOTE]
    >  Visual Studio 2015 güncelleştirme 2'de başlayarak, belirtebilirsiniz (içinde **Araçlar / Seçenekler / ortam / Uzantılar ve güncelleştirmeler**) kullanıcı başına uzantılar, tüm kullanıcı uzantıları veya hem de (varsayılan ayar) için Otomatik Güncelleştirmeler isteyip istemediğinizi.

## <a name="see-also"></a>Ayrıca Bkz.
 [Bir VSIX paketinin anatomisi](../extensibility/anatomy-of-a-vsix-package.md) [bulma ve Visual Studio uzantıları kullanma](../ide/finding-and-using-visual-studio-extensions.md)
