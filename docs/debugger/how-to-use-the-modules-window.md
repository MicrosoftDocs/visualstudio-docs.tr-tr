---
title: DLL'ler ve yürütülebilir dosyaları görüntüleme
titleSuffix: Visual Studio Modules window
ms.custom: seodec18
ms.date: 11/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2702eb38e895f5fa9021fae754ae1e4a9325cf18
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066788"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>DLL'ler ve yürütülebilir dosyalar modüller penceresini görüntüleyin (C#, C++, Visual Basic F#)
 
Visual Studio hata ayıklama sırasında **modülleri** penceresinde listeler ve DLL'ler ve yürütülebilir dosyalar hakkındaki bilgileri gösterir (*.exe* dosyaları), uygulama kullanır. 

> [!NOTE]
> Modüller penceresini SQL veya komut dosyası hata ayıklaması için kullanılabilir değil. 
  
## <a name="use-the-modules-window"></a>Modüller penceresini kullanma

Hata ayıklarken modüller penceresini açmak için seçmeniz **hata ayıklama** > **Windows** > **modülleri**. 
  
Varsayılan olarak, **modülleri** penceresi modülleri yükleme sırası tarafından sıralar. Herhangi bir pencere sütuna göre sıralamak için sütun üst kısmındaki başlık'ı seçin.  
  
## <a name="load-symbols"></a>Sembolleri yükle  

**Sembol durumu** sütununda **modülleri** penceresi hata ayıklama simgeleri yüklü modüllerine sahip gösterir. Durum ise **sembollerin yüklenmesi atlandı**, **bulunamıyor veya açılamıyor PDB dosyası**, veya **yükleme Ekle/Çıkar ayarı tarafından devre dışı bırakıldı**, sembolleri el ile yükleyebilir. Yükleme ve semboller kullanma hakkında daha fazla bilgi için bkz. [belirtin, sembol (.pdb) ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

**Sembolleri el ile yüklemek için:**  

1. İçinde **modülleri** penceresinde, simgelerin modülü henüz yüklenen sağ tıklatın. 
   
   - Seçin **sembol yükleme bilgisi** neden hakkındaki ayrıntılar için Sembol yüklenmedi. 
   
   - Seçin **yük sembolleri** sembolleri el ile yüklemek için.  
   
1. Sembolleri olmayan, seçin **sembol ayarları** açmak için **seçenekleri** iletişim kutusunda belirtin veya sembol yükleme konumları değiştirin. 
   
   Genel Microsoft sembol sunucuları veya diğer sunucularından sembolleri yükle veya bilgisayarınızda bir klasöre sembolleri. Ayrıntılar için bkz [sembol konumlarını belirtin ve yükleme davranışını](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior).   

**Sembol yükleme davranışı ayarları değiştirmek için:**  

1. İçinde **modülleri** penceresinde herhangi bir modülden sağ tıklayın.  
   
1. Seçin **sembol ayarları**.  
  
1. Seçin **tüm sembolleri**, ya da dahil etmek veya hariç tutmak için hangi modülü seçin.  
  
1. Seçin **Tamam**. Değişiklikler bir sonraki hata ayıklama oturumunda etkili olur.  
  
**Sembol yükleme davranışı belirli bir modül için değiştirmek için:**  

1.  İçinde **modülleri** penceresinde modülü sağ tıklatın.  

1.  Sağ tıklama menüsünü seçin veya seçimini **otomatik her zaman yük**. Değişiklikler bir sonraki hata ayıklama oturumunda etkili olur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Yürütmeyi kesme](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))   
 [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)   
 [Sembol (.pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)