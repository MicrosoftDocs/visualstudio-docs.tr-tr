---
title: Windows betik arabirimleri | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4c750627-6797-4857-9f5e-e5f54371f83c
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f98e60a82735ae561edf404763e0700f71b3a3d4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905369"
---
# <a name="windows-script-interfaces"></a>Windows Komut Dosyası Arabirimleri

Microsoft Windows betik arabirimleri, bir komut dosyası eklemek için uygulama ve OLE Otomasyon için bir yol sağlar. Windows komut kullanan ana komut dosyası oluşturma kaynakları ve satıcılarından birden fazla betik altyapısını bileşenleri arasında betik yönetmek için kullanabilirsiniz. Betik yürütmesinin — dil, söz dizimi, kalıcı biçimi, yürütme modeli ve benzeri — betik satıcıya bırakılır.

Windows komut dosyası belgeleri, aşağıdaki bölümlere ayrılmıştır:

[Windows Betik Konakları](../winscript/windows-script-hosts.md)

[Windows Betik Motorları](../winscript/windows-script-engines.md)

[Etkin Betik Hata Ayıklamaya Genel Bakış](../winscript/active-script-debugging-overview.md)

[Etkin Betik Profil Oluşturmaya Genel Bakış](../winscript/active-script-profiling-overview.md)

[Windows Betik Arabirimleri Başvurusu](../winscript/reference/windows-script-interfaces-reference.md)

## <a name="windows-script-background"></a>Windows betik arka plan

Windows betik arabirimleri iki kategoriye ayrılır: Windows betik konakları ve Windows kod altyapısı sayısı. Bir konak, bir komut dosyası motoru oluşturur ve altyapısını temel komut dosyalarını çalıştırmak için çağırır. Windows betik konakları örnekleri şunlardır:

- Microsoft Internet Explorer

- Internet yazma araçları

- Kabuk

Windows betik motorları geliştirilebilir, herhangi bir dili veya çalışma zamanı ortamı için de dahil olmak üzere:

- Microsoft Visual Basic Scripting Edition (VBScript)

- Perl

- Lisp

Ana bilgisayar uygulaması kadar esnek hale getirmek için Windows komut dosyası için bir OLE Otomasyon sarmalayıcıdır sağlanır. Bununla birlikte, komut dosyası altyapısı oluşturmak için bu sarmalayıcı nesnesini kullanan bir ana çalışma zamanı ad alanı, Kalıcılık modeli ve Windows komut dosyası doğrudan kullandıysanız, olduğu benzeri denetime derecesini yok.

Windows betik tasarım yalnızca bir geliştirme ortamında (örneğin, tarayıcılar ve Görüntüleyiciler) nonauthoring konakları ve (örneğin, VBScript) komut dosyası motorları basit tutulabilir böylece gerekli arabirim öğeleri yalıtır.

## <a name="windows-script-basic-architecture"></a>Windows betik temel mimarisi

Aşağıdaki resimde, bir Windows Script host ile bir Windows komut dosyası altyapısı arasındaki etkileşim gösterilmektedir.

Konak ve altyapısı arasındaki etkileşim içinde yer alan adımların aşağıdaki listede verilmiştir.

1.  Bir proje oluşturun. Konak, bir proje veya belgeyi yükler. (Bu adım Windows betiği için belirli değil, ancak bütünlük açısından buraya dahil edilir.)

2.  Windows komut dosyası altyapısı oluşturun. Konak çağrıları `CoCreateInstance` yeni bir Windows komut dosyası altyapısı oluşturmak için kullanılacak belirli komut dosyası altyapısı sınıf tanımlayıcısı (CLSID) belirtme. Örneğin, Internet Explorer'ın HTML tarayıcı komut dosyası altyapısının sınıf tanımlayıcısı CLSID aracılığıyla alır HTML öznitelik = \<Nesne > etiketi.

3.  Komut dosyası yükleyin. Betik içeriği kalıcı ise ana komut dosyası altyapısının çağırır `IPersist*::Load` betik depolama, stream veya özellik paketi akışa yöntemi. Aksi takdirde, konak ya da kullandığı `IPersist*::InitNew` veya [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) null betiği oluşturmak için yöntemi. Metin kullanabilirsiniz gibi bir betik tutan bir konak [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) komut dosyası altyapısı çağırdıktan sonra betiğin metnini akışa `IActiveScriptParse::InitNew`.

4.  Adlandırılmış öğeleri ekleyin. Komut dosyası altyapısının ad alanı alınan her üst düzey adlandırılmış öğe için (örneğin, sayfaları ve formları), konak çağırır [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) altyapının ad alanında bir giriş oluşturmak için yöntemi. Bu adım, üst düzey adlandırılmış öğeleri kalıcı durumunu 3. adımda yüklenen komut dosyasının bir parçası olduğunda gerekli değildir. Bir konak kullanmaz `IActiveScript::AddNamedItem` öğeleri (örneğin, HTML sayfasındaki denetimleri) adlı alt düzey eklemek için; bunun yerine, altyapı dolaylı olarak alt düzey öğeleri üst düzey öğeleri ana bilgisayarın kullanarak alır `ITypeInfo` ve `IDispatch` arabirimleri.

5.  Betiği çalıştırın. Konak SCRIPTSTATE_CONNECTED bayrak ayarlayarak betiği çalıştırmaya başlamak altyapı neden [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) yöntemi. Bu çağrı, büyük olasılıkla statik bağlama, takma olayları (aşağıya bakın) ve bir komut dosyası için benzer şekilde bir kod yürütmeden dahil olmak üzere tüm komut dosyası altyapısı oluşturma iş gerçekleştirecek `main()` işlevi.

6.  Öğe bilgi alın. Komut dosyası altyapısı bir üst düzey öğesi ile bir simge ilişkilendirmek için her durumda çağrı [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) yöntemi verilen öğe hakkında bilgi verir.

7.  Olayları bağlayın. Gerçek betiğini başlatmadan önce komut dosyası altyapısı aracılığıyla tüm nesneleri olaylarını bağlandığı `IConnectionPoint` arabirimi.

8.  Özellikleri ve yöntemleri çağırır. Komut dosyası çalıştırılırken, komut dosyası altyapısı yöntemlere ve özelliklere başvuruları adlandırılmış nesneler üzerinde fark etti `IDispatch::Invoke` veya diğer OLE bağlama mekanizmalarını.

## <a name="windows-script-terms"></a>Windows betik koşulları

Bu liste, bu belgede kullanılan betik oluşturma ile ilgili terimlerin tanımları içerir.

|Terim|Tanım|
|----------|----------------|
|Kod nesnesi|Visual Basic'te, bir formun arkasındaki modülü gibi adlandırılmış bir öğesi ile ilişkili olan komut dosyası altyapısı tarafından oluşturulan bir örnek veya adlandırılmış bir öğesi ile ilişkilendirilen bir C++ sınıfı. Tercihen, bu kod nesnesi konak veya başka bir betik olmayan varlık işleyebileceğiniz şekilde OLE Otomasyonu destekleyen OLE Bileşen Nesne Modeli (COM) nesnesidir.|
|Adlandırılmış öğe|Bir OLE COM nesnesi (tercihen destekleyen OLE Otomasyonu) konak betiğe ilginç kabul ettiği. HTML sayfası ve tarayıcıyı bir Web tarayıcısı ve belge ve Microsoft Word iletişim kutuları verilebilir.|
|Komut Dosyası|Komut dosyası altyapısı çalıştıran programı yapan veriler. Bir betik bloklarını, metin parçalarını dahil olmak üzere tüm bitişik bir yürütülebilir veri olabilir `pcode`, hatta makineye özgü yürütülebilir bayt kodları. Bir betiği bir konak komut dosyası altyapısı biri aracılığıyla yükler `IPersist*` arabirimleri aracılığıyla veya [Iactivescriptparse](../winscript/reference/iactivescriptparse.md) arabirimi.|
|Komut dosyası altyapısı|Komut dosyaları işler OLE nesne. Bir komut dosyası altyapısı uygulayan [IActiveScript](../winscript/reference/iactivescript.md) ve isteğe bağlı olarak [Iactivescriptparse](../winscript/reference/iactivescriptparse.md) arabirimleri.|
|Komut dosyası ana bilgisayarı|Uygulama ya da Windows komut dosyası altyapısı sahip program. Konak uygulayan [Iactivescriptsite](../winscript/reference/iactivescriptsite.md) ve isteğe bağlı olarak [Iactivescriptsitewindow](../winscript/reference/iactivescriptsitewindow.md) arabirimleri.|
|Kod oluşturma|Bir nesne üzerinden iliştirilmiş bir betiğin bir bölümü [Iactivescriptparse](../winscript/reference/iactivescriptparse.md) arabirimi. Kod parçacıklarını toplama koleksiyonu betiğidir.|
|Komut dosyası dili|Bir betik yazılı (VBScript, örneğin) ve bu dil semantiği olduğu dili.|