---
title: Düzenle ve Devam Edin ile kesme modunda Düzenleme | Microsoft Docs
description: Kesme modundayken düzenleme kodunuzu düzenlemek için Düzenle ve Visual Basic'yi nasıl kullanabileceğinize bakın. Kesme moduna girmenin çeşitli yolları vardır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e62c6a7a6e30bac6d054f3e5484498047426d96d
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386806"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Nasıl yapılır: Düzenleme ve Devam Ile Kesme Modunda Düzenleme Uygulama (Visual Basic)
Kodunuzu Kesme modunda düzenlemek ve yürütmeyi durdurmadan ve yeniden başlatmadan devam etmek için Düzenle ve Devam'ı kullanabilirsiniz.

Hata ayıklama sırasında Düzenle ve Devam Edin'i kullanmayla ilgili sınırlamalar için bkz. Desteklenen [Kod Değişiklikleri (C# ve Visual Basic)](../debugger/supported-code-changes-csharp.md).

### <a name="to-edit-code-in-break-mode"></a>Kodu Kesme modunda düzenlemek için

1. Aşağıdakilerden birini yaparak Kesme moduna girin:

    - Kodunuzda bir kesme noktası  ayarlayın, sonra  Hata Ayıklama menüsünden Hata Ayıklamayı Başlat'ı seçin ve uygulamanın kesme noktasıyla birlikte isabetini bekleyin.

         -veya-

    - Hata ayıklamayı başlat ve ardından Hata **Ayıkla menüsünden** Hepsini **Kır'ı** seçin.

         -veya-

    - Bir özel durum oluştuğunda, Özel Durum **Yardımcısı'nda Düzenlemeyi** **Etkinleştir'i seçin.**

2. İstenen ve desteklenen kod değişikliklerini yapın.

     Daha fazla bilgi için [bkz. Desteklenen Kod Değişiklikleri (C# ve Visual Basic)](../debugger/supported-code-changes-csharp.md).

    > [!NOTE]
    > Düzenle ve Devam' tarafından izin verilmiyor bir kod değişikliği yapmaya çalışırken, düzenlemenizin altı mor dalgalı çizgiyle altı çizili olur ve düzenleme Görev Listesi. Geçersiz kod değişikliğini geri almadıkça kod yürütmeye devam etmek mümkün olmayacaktır.

3. Hata **Ayıkla menüsünde Devam'a** **tıklar ve** yürütmeyi sürdürün.

     Kodunuz artık projeye dahil edilmiş uygulanan düzenlemeleriniz ile yürütülür.

## <a name="see-also"></a>Ayrıca bkz.
- [Desteklenen Kod Değişiklikleri (C# ve Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Düzenle ve Devam Et (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
