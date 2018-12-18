---
title: 'Nasıl yapılır: modüller penceresini kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.modules
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
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fea513b7593e260b5f5fb71e40ced98a1f8cc279
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764415"
---
# <a name="how-to-use-the-modules-window"></a>Nasıl Yapılır: Modüller Penceresini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[NOT]
>  Bu özellik, SQL veya komut dosyası hata ayıklama için kullanılamaz.  
  
 **Modülleri** penceresi listeler dll ve EXE, programınız tarafından kullanılan ve her biri için ilgili bilgileri gösterir.  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>Modüller penceresini kesme modunda veya çalıştırma modunda görüntülemek için  
  
-   Üzerinde **hata ayıklama** menüsünde seçin **Windows**ve ardından **modülleri**.  
  
     Varsayılan olarak, **modülleri** penceresi modülleri yükleme sırası tarafından sıralar. Ancak, herhangi bir sütuna göre sıralamak seçebilirsiniz.  
  
### <a name="to-sort-by-any-column"></a>Herhangi bir sütuna göre sıralamak için  
  
-   Sütun üst kısmındaki düğmeye tıklayın.  
  
     Sembolleri yüklemek veya bir sembol yolu belirtin **modülleri** kısayol menüsünü kullanarak pencere.  
  
## <a name="loading-symbols"></a>Semboller yükleniyor  
 İçinde **modülleri** penceresi, hata ayıklama simgeleri yüklü modüllerine sahip görebilirsiniz. Bu bilgiler görünür **sembol durumu** sütun. Durum diyorsa **atlandı loadingCannot bulun veya PDB dosyası açın**, veya **yükleme Ekle/Çıkar ayarı tarafından devre dışı bırakıldı**, hata ayıklayıcının sembolleri Microsoft ortak Sembol ' indirin yönlendirebilirsiniz sunucuları veya bilgisayarınızdaki bir sembol dizinden simgeleri yüklemek için. Daha fazla bilgi için [belirtin sembol (.pdb) ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>Simgeleri el ile yüklemek için  
  
1.  İçinde **modülleri** penceresinde, kendisi için olmayan semboller modülü sağ tıklatın.  
  
2.  İşaret **sembolleri şuradan Yükle** ve ardından **Microsoft sembol sunucuları** veya **sembol yolu**.  
  
#### <a name="to-change-symbol-load-settings"></a>Sembol yükleme ayarlarını değiştirmek için  
  
1.  İçinde **modülleri** penceresinde herhangi bir modülden sağ tıklayın.  
  
2.  Tıklayın **sembol ayarları**.  
  
     Artık açıklandığı gibi sembol yükleme ayarlarını değiştirebilirsiniz [sembol konumlarını belirtin ve yükleme davranışını](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Değişiklikler, hata ayıklama oturumunu yeniden başlatılana kadar etkili olmaz.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Belirli bir modül için Sembol yükleme davranışını değiştirmek için  
  
1.  İçinde **modülleri** penceresinde modülü sağ tıklatın.  
  
2.  İşaret **otomatik sembol yükleme ayarlarını** ve ardından **elle her zaman yük** veya **varsayılan**. Değişiklikler, hata ayıklama oturumunu yeniden başlatılana kadar etkili olmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yürütmeyi kesme](http://msdn.microsoft.com/en-us/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)   
 [Simge (.pdb) ve Kaynak Dosyaları Belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)





