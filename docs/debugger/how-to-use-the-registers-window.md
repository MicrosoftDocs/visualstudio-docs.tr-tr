---
title: Görünüm hata ayıklayıcıda değerleri kaydetme | Microsoft Docs
ms.custom: seodec18
ms.date: 11/19/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31d9b9a9243bdf5bd39ebddf90ffa0ea32b23072
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058447"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Görüntüleme değerleri yazmaçlar penceresi içinde kaydetmek (C#, C++, Visual Basic F#)

**Kaydeder** penceresi görüntülendiğinde, Visual Studio hata ayıklama sırasında içeriklerini kaydedin. Yazmaçları kavramları üst düzey bir giriş için ve **kaydeder** penceresinde görmek [hata ayıklama temelleri: yazmaçlar penceresi](../debugger/debugging-basics-registers-window.md).

> [!NOTE]
> Betik veya SQL uygulamalar için kayıt bilgileri kullanılamıyor.

Uygulamanızda kodu yürütür olarak hata ayıklama sırasında değişiklik değerleri kaydedin. Değişen değerler kısa bir süre önce görünür kırmızıyla **kaydeder** penceresi.

Dağınıklığı, azaltmak için **kaydeder** penceresi kayıtları platform ve işlemci göre değişiklik gösteren gruplar halinde düzenler türü. Görüntüleyebilir ya da yazmaç gruplarını gizleyebilirsiniz. Daha fazla bilgi için [nasıl yapılır: yazmaç gruplarını görüntüleme ve gizleme](../debugger/how-to-display-and-hide-register-groups.md).

YAZMAÇ değerlerini düzenleyebilirsiniz. Daha fazla bilgi için [nasıl yapılır: yazmaç değerini düzenleme](../debugger/how-to-edit-a-register-value.md).

**Yazmaçlar penceresi açmak için**

1. Adres seviyesinde, seçerek hata ayıklamayı **adres seviyesinde hata ayıklamayı** içinde **Araçları** (veya **hata ayıklama**) > **seçenekleri**  >  **Hata ayıklama**.

1. Hata ayıklama kesme noktası veya çalışıyor olsa da seçin **hata ayıklama** > **Windows** > **kaydeder**, veya basın **Alt** + **5**.

>[!NOTE]
>İletişim kutuları ve menü komutları, Visual Studio sürümü veya ayarlarınızı bağlı olarak farklı olabilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** Visual Studio **Araçları** menüsü. Daha fazla bilgi için [ayarlarına](../ide/environment-settings.md#reset-settings).

### <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama temelleri: yazmaçlar penceresi](../debugger/debugging-basics-registers-window.md)
- [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)
