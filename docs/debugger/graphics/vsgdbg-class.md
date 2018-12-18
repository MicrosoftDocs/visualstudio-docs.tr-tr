---
title: VsgDbg sınıfı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c48142d3458cf3c85b0391fcf33dc7238d16abb2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474774"
---
# <a name="vsgdbg-class"></a>VsgDbg Sınıfı
Grafik tanılama uygulama bileşeninin programsal denetim için bir arabirimi temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```C++  
class VsgDbg;  
```  
  
## <a name="members"></a>Üyeler  
 `VsgDbg` Sınıfı, aşağıdaki üyeleri destekler.  
  
### <a name="public-constructors"></a>Ortak Oluşturucular  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (Oluşturucu)](vsgdbg-vsgdbg-constructor.md)|Bir örneğini oluşturur `VsgDbg` sınıfı ve isteğe bağlı olarak etkin olarak yakalamak ve grafik bilgilerini kaydetmek için grafik tanılamayı uygulama bileşeninin hazırlar.|  
|[VsgDbg::~VsgDbg (Yok Edici)](vsgdbg-tilde-vsgdbg-destructor.md)|Örneği bozar `VsgDbg` sınıfı.|  
  
### <a name="public-methods"></a>Ortak Yöntemler  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[AddMessage](addmessage.md)|Özel ileti grafik tanılama HUD (Head yukarı görüntüle) ekler.|  
|[BeginCapture](begincapture.md)|İle sona erer yakalama aralığı başlar `EndCapture`.|  
|[CaptureCurrentFrame](capturecurrentframe.md)|Grafik günlük dosyası için geçerli çerçeve kalanı yakalar.|  
|[Kopyalama (Programlı Yakalama)](copy-programmatic-capture.md)|Etkin Grafikler (.vsglog) günlük dosyasının içeriğini yeni bir dosyaya kopyalar.|  
|[EndCapture](endcapture.md)|Başlatıldığı yakalama zaman aralığı sona `BeginCapture`.|  
|[Init](init.md)|Etkin olarak yakalamak ve grafik bilgilerini kaydetmek için grafik tanılamayı uygulama bileşeninin hazırlar.|  
|[ToggleHUD](togglehud.md)|Grafik tanılama HUD katmana açmak veya kapatmak değiştirir.|  
|[UnInit](uninit.md)|Grafik günlük dosyası sonlandırır kapatılır ve uygulama, etkin olarak grafik bilgilerini kaydetme sırasında kullanılan kaynakları serbest bırakır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `VsgDbg` Sınıfı, grafik tanılama özellikleri programlı olarak denetlemek için kullanabileceğiniz bir arabirimi temsil eder. Bazı özellikler bile, aktif olarak yakalama ve grafik bilgilerini kaydetme kullanabilirsiniz; Bu içerir `AddMessage` üye işlevini ve `ToggleHUD` üye işlevi. Bir üye işlevleri başlatmak veya etkin grafik bilgilerini yakalama durdurmak için grafik tanılamayı uygulama bileşeninin hazırlama ya da uygulama etkin olarak yakalama ve grafik bilgilerini bir grafik günlük dosyasına kaydetme sırasında çağrılması gerekir.