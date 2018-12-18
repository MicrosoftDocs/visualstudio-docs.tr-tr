---
title: Uzak araçları indirme engelini kaldırma
ms.custom: ''
ms.date: 07/19/2018
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0586b8f0699ec2eca5843d59df1b6ddd7cecbd3
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180717"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>Nasıl yapılır: Windows Server'da uzak Araçlar'ın indirme engelini kaldırma

Varsayılan güvenlik ayarlarını Internet Explorer'da Windows Server bileşenleri gibi uzak araçları indirmek zaman yapabilirsiniz.

* Web siteleri açarak ve kaynağı içeren etki alanını açıkça izin verilmediği sürece web kaynaklara erişimi engeller Internet Explorer Artırılmış Güvenlik Yapılandırması etkin (diğer bir deyişle, güvenilen). Bu ayarı devre dışı olsa da, bir güvenlik riski sunabilir çünkü bunu önermiyoruz.

* Windows Server 2016, bir varsayılan ayarı **Internet Seçenekleri** > **güvenlik** > **Internet**  >   **Özel düzey** > **indirir** ayrıca indirmeler devre dışı bırakır dosya. Doğrudan Windows Server'da uzak araçları indirmek isterseniz, dosya indirme etkinleştirmeniz gerekir.

Windows Server'da araçları indirmek için aşağıdakilerden birini öneririz:

* Çalışan bir Visual Studio gibi farklı bir bilgisayarda Uzak araçları indirmek ve ardından kopyalama *.exe* Windows Server'a dosya.

* Uzaktan hata ayıklayıcıyı çalıştırmak [bir dosya paylaşımından](../debugger/remote-debugging.md#fileshare_msvsmon) Visual Studio makinenizde.

* Doğrudan Windows Server'da uzak araçları indirmek ve Güvenilen siteler eklemek için istemleri kabul edin. Bu çok sayıda istemleri neden olabilir, böylece Modern Web siteleri genellikle çok sayıda üçüncü taraf kaynakları içerir. Ayrıca, yeniden yönlendirilen bağlantıları el ile eklenmesi gerekebilir. Yükleme başlamadan önce bazı Güvenilen siteler eklemek seçebilirsiniz. Git **Internet Seçenekleri > Güvenlik > Güvenilen siteler > siteleri** ve aşağıdaki siteleri ekleyin.

  * VisualStudio.microsoft.com
  * download.VisualStudio.microsoft.com
  * hakkında: boş

  My.visualstudio.com hata ayıklayıcıyı eski sürümleri için oturum açma başarılı olduğundan emin olmak için bu ek siteleri ekleyin:

  * Microsoft.com
  * go.microsoft.com
  * download.microsoft.com
  * My.VisualStudio.com
  * login.microsoftonline.com
  * Login.live.com
  * secure.aadcdn.microsoftonline-p.com
  * MSFT.STS.microsoft.com
  * auth.Gfx.MS
  * app.vssps.visualstudio.com
  * vlscppe.microsoft.com
  * Query.prod.cms.RT.microsoft.com

    Uzak Araçlar'ı indirirken bu etki alanları eklemek seçin ve sonra seçin, **Ekle** istendiğinde.

    ![Engellenen içerik iletişim kutusu](../debugger/media/remotedbg-blocked-content.png)

    Yazılımı indirdiğinizde, çeşitli web sitesi komut dosyaları ve kaynakları yüklemeye izin vermek için bazı ek istekler alın. My.VisualStudio.com üzerinde oturum açma başarılı olduğundan emin olmak için ek etki alanlarını eklemenizi öneririz.