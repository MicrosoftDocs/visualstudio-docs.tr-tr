---
title: "Nasıl yapılır: hangi DLL'de kilitlendiğini programınızın bulma | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40f27e0bec20e1dd037beaa5f60ea648c0ccb171
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257103"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>Nasıl yapılır: hangi DLL'de kilitlendiğini programınızın bulma (C#, C++, Visual Basic F#)
  
 Uygulamanızı bir sistem DLL'i veya başka birisinin kodu çağrısı sırasında kilitleniyor bulmak kilitlenme oluştuğunda hangi DLL etkindi gerekirse. Kendi programımı dışında bir DLL içindeki bir kilitlenme karşılaşırsanız, konumu şunu kullanarak belirleyebilirsiniz **modülleri** penceresi.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Modüller penceresini kullanarak bir kilitlenme burada bulmak için oluştu  
  
1.  Kilitlenme durumu oluştuğu adresini not edin.

    Hata iletisinde adresi gösterilmez, DLL tanımlamak için alternatif yöntemler kullanmayı gerekebilir. Bir sistem DLL'i şüpheleniyorsanız yapabilecekleriniz [yük sembolleri](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Microsoft sembol sunucularından hata ayıklama sırasında. Aksi takdirde, gerekebilir [bir döküm dosyası oluşturma](../debugger/using-dump-files.md) yığın yerine bilgi olduğu. Çeşitli [Araçları](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) döküm dosyalarını oluşturmak kullanılabilir.
  
2.  Üzerinde **hata ayıklama** menüsünde seçin **Windows**, tıklatıp **modülleri**.  
  
3.  İçinde **modülleri** penceresinde Bul **adresi** sütun. Bunu görmek için kaydırma çubuğunu kullanmanız gerekebilir.  
  
4.  Tıklayın **adresi** DLL'leri adresine göre sıralamak için sütunun üstünde düğme.  
  
5.  Sıralanmış listenin kilitlenme konumu adresi aralığı içeren DLL bulmak için tarayın.  
  
6.  Bakmak **adı** ve **yolu** DLL adı ve yolu görmek için sütun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DLL projelerinde hata ayıklama](../debugger/debugging-dll-projects.md)   
 [Nasıl Yapılır: Modüller Penceresini Kullanma](../debugger/how-to-use-the-modules-window.md)