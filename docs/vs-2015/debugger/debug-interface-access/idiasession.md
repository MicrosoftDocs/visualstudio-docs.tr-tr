---
title: Idiasession | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c2baa4b026fd9856625ce25be283c2c969f79a99
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799632"
---
# <a name="idiasession"></a>IDiaSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklama sembolleri için bir sorgu bağlamı sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>Yöntemler  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDiaSession`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Bu sembol deposu sembolleri karşılık gelen bir yürütülebilir dosya için yük adresi alır. Bu, geçildi, aynı değerdir `put_loadAddress` yöntemi.|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Yükleme adresine karşılık gelen yürütülebilir dosyası için sembolleri bu sembol deposu içerisinde ayarlar. **Not:** aldığınızda, bu yöntemi çağırmak önemli bir `IDiaSession` nesne ve başlamadan önce nesnesini kullanarak.|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Genel kapsamdaki bir başvuru alır.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Sembol deposu içerisinde bulunan tüm tablolar için bir numaralandırıcı alır.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Statik konumlardaki tüm adlandırılmış sembol için bir numaralandırıcı alır.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Ad ve simge türüyle eşleşen tüm alt öğelerini belirtilen üst tanımlayıcı alır.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|İçeriyor veya belirtilen bir adres için en yakın olan bir belirtilen simge türü alır.|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|İçeren veya bir belirtilen göreli sanal adres için (RVA) en yakın bir belirtilen simge türü alır.|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|İçeriyor veya belirtilen sanal adres (VA) için en yakın olan bir belirtilen simge türü alır.|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Belirtilen meta veri belirteci içeren simgeyi alır.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|İki simge eşdeğer olup olmadığını denetler.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Bir sembol benzersiz kimliğine göre alır.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|İçeriyor veya belirtilen göreli sanal adres ve uzaklığı için en yakın olan bir belirtilen simge türü alır.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|İçeriyor veya belirtilen sanal adres ve uzaklığı için en yakın olan bir belirtilen simge türü alır.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Derlenecek dosya ve ada göre bir kaynak dosyası alır.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Bir kaynak dosyası, kaynak dosya tanımlayıcısı tarafından alır.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Belirtilen bir derlenecek ve kaynak dosya tanımlayıcısı içinde satır numaralarını alır.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Belirtilen adres içeren belirtilen derlenecek satırları alır.|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Belirtilen göreli sanal adres içeren belirtilen derlenecek satırları alır.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Belirtilen adres aralığında bulunan satırlar için satır numarası bilgisi bulur.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Kaynak dosya ve satır numarası tarafından belirtilen bir derlenecek satırları alır.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Öznitelik sağlayıcıları tarafından sembol deposuna veya diğer bileşenleri derleme işleminin yerleştirilen bir kaynağı alır.|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Hata ayıklama veri akışlarını numaralandırılmış bir dizisini alır.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Bir istemci belirli bir adresi satır içi karelerden tümünün üzerinden yinelemek sağlayan bir sabit listesi alır.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Bir istemci bir belirtilen göreli sanal adres (RVA) satır içi karelerden tümünün üzerinden yinelemek sağlayan bir sabit listesi alır.|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Belirtilen sanal adres (VA) satır içi karelerden tümünün üzerinden yinelemek bir istemci sağlayan bir sabit listesi alır.|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Satır numarası bilgisi tüm işlevlerin satır içine alınmış, doğrudan veya dolaylı olarak, belirtilen üst simgesiyle yinelemek bir istemci sağlayan bir sabit listesi alır.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Satır numarası bilgisi tüm işlevlerin satır içine alınmış, doğrudan veya dolaylı olarak, belirtilen üst simgesiyle yinelemek bir istemci sağlar ve belirtilen adres aralığında bulunan bir sabit listesi alır.|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Satır numarası bilgisi tüm işlevlerin satır içine alınmış, doğrudan veya dolaylı olarak, belirtilen üst simgesiyle yinelemek bir istemci sağlar ve belirtilen göreli sanal adres içinde (RVA) bulunan bir sabit listesi alır.|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Satır numarası bilgisi tüm işlevlerin satır içine alınmış, doğrudan veya dolaylı olarak, belirtilen üst simgesiyle yinelemek bir istemci sağlar ve belirtilen sanal adres (VA) içinde bulunan bir sabit listesi alır.|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Bir istemci doğrudan veya dolaylı olarak, belirtilen kaynak dosya ve satır numarası, satır içi yapılırlar tüm işlevlerin satır numarası bilgisi yinelemek sağlayan bir sabit listesi alır.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Belirtilen adla eşleşen tüm satır içine alınmış işlevlerin satır numarası bilgisi yineleme yapmak bir istemci sağlayan bir sabit listesi alır.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Belirtilen etiket değeri karşılık gelen değişkeni için semboller numaralandırması üst Hızlandırıcı saplama işlevi döndürür.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Bu yöntem karşılık gelen bir etiket değeri verildiğinde, belirtilen üst Hızlandırıcı saplama işlevinde belirtilen göreli sanal adresten bulunan simgeleri bir sabit listesi döndürür.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Belirtilen satır içi işlev adına karşılık gelen satır içi çerçeveler için semboller numaralandırmasını döndürür.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Belirtilen kaynak konum için karşılık gelen satır içi çerçeveler için semboller numaralandırmasını döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çağırmak önemlidir [Idiasession::put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) oluşturduktan sonra yöntemi `IDiaSession` nesne — ve geçirilen değeri `put_loadAddress` yöntemi olmalıdır sıfır olmayan — tüm sanal adres (VA) özellikleri olması için simgeleri erişilebilir. Yük adresi hangi programı hata ayıklaması yapılan yürütülebilir yüklenen öğesinden gelir. Örneğin, Win32 işlevini çağırabilir `GetModuleInformation` yük adresi yürütülebilir dosyası için bir yürütülebilir dosya için belirli alınacak.  
  
## <a name="example"></a>Örnek  
 Bu örnek nasıl alınacağını gösterir `IDiaSession` genel bir başlatma DIA SDK'ın bir parçası olarak arabirimi.  
  
```cpp#  
CComPtr<IDiaDataSource> pSource;  
ComPtr<IDiaSession> psession;  
  
void InitializeDIA(const char *szFilename)  
{  
    HRESULT hr = CoCreateInstance( CLSID_DiaSource,  
                                   NULL,  
                                   CLSCTX_INPROC_SERVER,  
                                   __uuidof( IDiaDataSource ),  
                                  (void **) &pSource);  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename,  
              szFilename,  
              sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    if ( FAILED( pSource->openSession( &psession ) ) )  
    {  
        Fatal( "openSession" );  
    }  
}  
```  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: Dia2.h  
  
 Kitaplık: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arabirimler (arabirim erişimi SDK'SINDA hata ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Genel bakış](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [exe](../../debugger/debug-interface-access/exe.md)   
 [Idiaaddressmap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiadatasource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource::opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [Idiasymbol::findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [.Pdb Dosyasını Sorgulama](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)



