---
title: Başvuru pencereleri sembol bilgileri | Microsoft Docs
description: Visual Studio Profil Oluşturma Araçları program ikili dosyalarında işlev adları gibi sembolik adları çözümlemek için sembol (. pdb) dosyalarını nasıl kullandığını öğrenin.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: af194a324840bc3e8b8e67199c7e213d7dca96c9
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720689"
---
# <a name="how-to-reference-windows-symbol-information"></a>Nasıl yapılır: Başvuru pencereleri sembol bilgileri
Visual Studio Profil Oluşturma Araçları sembol kullanın (.*pdb*) dosyaları, program ikili dosyalarında işlev adları gibi sembolik adları çözümlemek için. Doğru şekilde indirmek ve güncelleştirmek için aşağıdaki adımları izleyebilirsiniz. Yerel bilgisayardaki Windows sürümü için *pdb* dosyaları.

> [!NOTE]
> Bu ayar varolan raporları etkilemez. Yalnızca sembol sunucusu belirttikten sonra oluşturulan raporların sembol bilgisi olacaktır.

 Daha fazla bilgi için bkz [. simge belirtme (.*pdb*) ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-use-the-microsoft-symbol-server"></a>Microsoft symbol Server 'ı kullanmak için

1. C:\symbolcachegibi sembol dosyası bilgilerini içerecek bir klasör oluşturun.

2. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.

     **Seçenekler** iletişim kutusu görüntülenir.

3. **Hata ayıklama** ağacını genişletin ve ardından **semboller**' e tıklayın.

4. **Sembol dosyası (. pdb) konumlarında** **Microsoft sembol sunucuları** ' nı seçin.

5. **Sembol sunucusundan bu dizine önbellek sembolleri**, 1. adımda oluşturulan klasörün yolunu yazın, örneğin:

     **C:\SymbolCache**

     Ayrıca üç nokta düğmesine (**...**) tıklayabilir ve sonra **klasöre gözatamıyorum** iletişim kutusundan bir dizin seçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)
- [Nasıl yapılır: sembol bilgilerini serileştirme](../profiling/how-to-serialize-symbol-information.md)
