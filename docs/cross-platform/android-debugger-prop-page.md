---
title: Android hata ayıklayıcıyı özellikleri (C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
author: corob
ms.author: mblome
manager: douge
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: be240ed2cea05194d51040fd29a17de9a4472fc9
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232650"
---
# <a name="android-debugger-properties"></a>Android hata ayıklayıcıyı özellikleri

Özellik | Açıklama | Seçenekleri
--- | ---| ---
Hata ayıklayıcı türü | Hata ayıklanacak kod türlerini belirtir. | **Yalnızca yerel**<br>**Yalnızca Java**<br>
Hedef hata ayıklama | Hata ayıklama için kullanılacak öykünücüyü veya cihazı belirtir. Hiçbir öykünücü çalışmıyorsa, 'Android sanal cihazı (AVD) Manager' Lütfen kullanan bir cihazı başlatmak için.
Başlatılacak paket | Konumunu belirtir *.apk* , hataları ayıklanabilir. Uygulamanın hataları ayıklanırken belirli paketin (APK) başlatılmasını belirtmek için bu seçeneği belirleyin.
Başlatma etkinliği | Uygulamayı başlatmak için kullanılacak Android etkinliği, bildirimde kullanılan kimliğin eşleşmesi gerekir. Listeden almak için Uygula'ya basın *AndroidManifest.xml* ve dinamik olarak doldurma.
Ek sembol arama yolları | Hata ayıklama sembolleri için ek arama yolu.
Ek Java kaynağı arama yolları | Java kaynak dosyaları için ek arama yolları. (Yalnızca hata ayıklayıcı türü yalnızca Java olduğunda geçerlidir.)
