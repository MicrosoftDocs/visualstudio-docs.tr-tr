---
title: 'Nasıl yapılır: başvuru pencereleri sembol bilgileri | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ace6b0eaf71b4bfb992d0ff0ccdb09351eac2c19
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844176"
---
# <a name="how-to-reference-windows-symbol-information"></a>Nasıl yapılır: başvuru Windows sembol bilgileri
Profil oluşturma Visual Studio Araçları simgesini kullanın (. *pdb*) gibi simgesel adları çözümlemek için dosyaları işlev program ikili adları. Otomatik olarak karşıdan yükle ve doğru güncelleştirmek için aşağıdaki adımları izleyebilirsiniz. *pdb* dosyaları yerel bilgisayarda Windows sürümü için.  
  
> [!NOTE]
>  Bu ayar, varolan raporları etkilemez. Yalnızca simge sunucusunu belirttikten sonra oluşturulan raporlar sembol bilgileri gerekir.  
  
 Daha fazla bilgi için bkz: [belirt simgesi (. *pdb*) ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
### <a name="to-use-the-microsoft-symbol-server"></a>Microsoft Simge sunucusunu kullanmak için  
  
1.  C:\SymbolCache gibi simge dosyası bilgileri içeren bir klasör oluşturun.  
  
2.  Üzerinde **Araçları** menüsünde tıklatın **seçenekleri**.  
  
     **Seçenekleri** iletişim kutusu görüntülenir.  
  
3.  Genişletme **hata ayıklama** ağacı ve ardından **simgeleri**.  
  
4.  İçinde **simge (.pdb) dosya konumları**seçin **Microsoft simge sunucuları**  
  
5.  İçinde **önbelleğe bu dizin simge sunucusundan simgeleri**, adım 1 ' de örneğin oluşturulduğu klasörünün yolunu yazın:  
  
     **C:\SymbolCache**  
  
     Üç nokta düğmesini tıklatarak (**...** ) ve ardından bir dizinden **klasöre Gözat** iletişim kutusu.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [Nasıl yapılır: Sembol bilgilerini seri hale getirme](../profiling/how-to-serialize-symbol-information.md)