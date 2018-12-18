---
title: Derleme Olayları İletişim Kutusu (Visual Basic)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- build events, specifying
- pre-build events
- Build Events dialog box
- post-build events
ms.assetid: 3a81a7c7-39f9-47a8-ba5a-b351227f380e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7e81a9308439af6a0dd688440dc6aa193a66eabf
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219360"
---
# <a name="build-events-dialog-box-visual-basic"></a>Derleme Olayları İletişim Kutusu (Visual Basic)

Kullanım **Build Events** yapı yapılandırma yönergeleri belirtmek için iletişim kutusu. Altında herhangi bir ön derleme veya derleme sonrası olayı çalıştığı koşulları belirtebilirsiniz. Daha fazla bilgi için [nasıl yapılır: Specify Build Events (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

**Derleme öncesi olay komut satırı**

Oluşturma başlamadan önce yürütülecek herhangi bir komut belirtir. Uzun komutları yazmak için tıklatın **Düzenle derleme öncesi** görüntülenecek [derleme öncesi olay/derleme sonrası olay komut satırı iletişim kutusu](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Derleme öncesi olayları, projenin güncel olduğundan ve hiçbir derlemenin tetiklenmesinin çalıştırmayın.

**Derleme sonrası olay komut satırı**

Oluşturma bittikten sonra yürütülecek herhangi bir komut belirtir. Uzun komutları yazmak için tıklatın **Düzenle derleme sonrası** görüntülenecek **derleme öncesi olay/derleme sonrası olay komut satırı** iletişim kutusu.

> [!NOTE]
> Ekleme bir `call` .bat dosyaları çalıştıran tüm derleme sonrası komutları önce deyimi. Örneğin, `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat`.

**Derleme sonrası olayı Çalıştır**

Aşağıdaki tabloda gösterildiği gibi çalıştırmak derleme sonrası olay koşulları belirtir.

|Seçenek|Sonuç|
|------------|------------|
|**Her zaman**|Derleme sonrası olay oluşturma işlemi başarılı olup olmadığını bağımsız olarak çalışır.|
|**Başarıyla derlendiğinde**|Derleme başarılı olursa, derleme sonrası olay çalıştırılır. Olay oluşturma işlemi başarılı olduğu sürece, güncel, hatta bir proje için çalışır. Varsayılan ayar budur.|
|**Derleme proje çıktısı zaman güncelleştirir**|Derleme sonrası olay, yalnızca önceki Derleyici çıkış dosyasından derleyicinin çıktı dosyası (.exe veya .dll) farklı olduğu durumlarda çalıştırılır. Bir projenin güncel olması halinde bir derleme sonrası olay çalıştırılmaz.|

## <a name="see-also"></a>Ayrıca Bkz.

- [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Nasıl Yapılır: Derleme Olayları Belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Derleme Öncesi Olay/Derleme Sonrası Olay Komut Satırı İletişim Kutusu](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)