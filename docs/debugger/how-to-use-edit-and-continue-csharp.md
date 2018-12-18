---
title: 'Nasıl yapılır: Düzenle ve kullanma (C#) devam | Microsoft Docs'
ms.custom: ''
ms.date: 10/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 41e97f488344e3d34ce326a3d35880d94da4ad9a
ms.sourcegitcommit: c5e72875206b8c5737c29d5b1ec7b86eec747303
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49382811"
---
# <a name="how-to-use-edit-and-continue-c"></a>Nasıl Yapılır: Düzenle ve Devam Et'i Kullanma (C#)
Düzenle ve devam et ile değişiklikler yapabilir ve bu, durdurmak ve hata ayıklama oturumunu yeniden başlatmak zorunda kalmadan hata ayıklama sırasında kodunuzda kesme modunda değişiklikleri uygulayın.  

Düzenle ve devam et için kesme modunda, kod değişiklik yaptığınızda C# otomatik olarak gerçekleşir ardından kullanarak hata ayıklamaya devam **devam**, **adım**, veya **sonraki deyimi Ayarla**, veya hata ayıklayıcı penceresindeki bir işlevi değerlendirin.  

Daha fazla bilgi için [Düzenle ve devam et (Visual C#)](../debugger/edit-and-continue-visual-csharp.md).

>[!NOTE]
>Düzenle ve desteklenmeyen en iyi duruma getirilmiş için karma, devam et veya SQL Server ortak dil çalışma zamanı (CLR) tümleştirme kodunda. Diğer desteklenmeyen senaryolar hakkında daha fazla bilgi için bkz: [desteklenen kod değişiklikleri (C# ve Visual Basic)](../debugger/supported-code-changes-csharp.md). Düzenle ve bu senaryoları biri ile devam etmek çalışırsanız, Düzenle ve devam et desteklenmediğini belirten bir ileti kutusu görünür.  
  
**Düzenle ve Devam Et'i devre dışı bırakmak veya etkinleştirmek için:**  
   
1. Hata ayıklama oturumunda kullanıyorsanız, hata ayıklamayı Durdur (**hata ayıklama** > **hata ayıklamayı Durdur** veya **Shift**+**F5**) .
   
1. İçinde **Araçları** > **seçenekleri** (veya **hata ayıklama** > **seçenekleri**) > **hataayıklama**  >  **Genel**seçin veya temizleyin **etkinleştirme Düzenle ve devam et** onay kutusu.  
  
Başlattığınızda veya hata ayıklama oturumunu yeniden ayarı etkinleşir.  

**Düzenle ve devam et kullanmak için:**  
   
1. , Kesme modunda hata ayıklarken sizin kaynak kodunuza bir değişiklik yapın.  
   
1. Gelen **hata ayıklama** menüsünde tıklatın **devam**, **adım**, veya **sonraki deyimi Ayarla**, veya hata ayıklayıcı penceresindeki bir işlevi değerlendirin.  
   
   Hata ayıklama, yeni, derlenmiş kod iler devam eder. 

Kod değişikliklerini bazı türleri, Düzenle ve devam et tarafından desteklenmez. Daha fazla bilgi için [desteklenen kod değişiklikleri (C# ve Visual Basic)](../debugger/supported-code-changes-csharp.md).   
