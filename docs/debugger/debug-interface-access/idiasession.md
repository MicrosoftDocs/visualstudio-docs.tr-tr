---
title: Idiasession | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b2791f318a921a25535d5e9a8f17e2c595f1f56
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468339"
---
# <a name="idiasession"></a>IDiaSession
Sorgu bağlamı için hata ayıklama simgeleri sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>Yöntemler  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDiaSession`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Bu sembol deposu sembolleri karşılık gelen yürütülebilir dosyasının yük adresini alır. Bu geçirilmedi değerin aynısıdır `put_loadAddress` yöntemi.|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Yükleme adresine karşılık gelen yürütülebilir dosyası için bu simge deposunda simgeleri ayarlar. **Not:** aldığınızda, bu yöntemi çağırmak önemli bir `IDiaSession` nesne ve başlamadan önce nesnesini kullanarak.|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Genel kapsamlı bir başvuru alır.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Sembol deposunda bulunan tüm tablolar için bir numaralandırıcı alır.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Statik konumlardaki tüm adlandırılmış sembolleri için bir numaralandırıcı alır.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Ad ve simge türüyle eşleşen tüm alt öğeleri belirtilen üst tanımlayıcı alır.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|İçeriyor veya belirtilen bir adres için en yakın olan bir belirtilen simge türü alır.|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|İçeriyor veya belirtilen göreli sanal adresi için (RAV) en yakın olan bir belirtilen simge türü alır.|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|İçeriyor veya belirtilen sanal adres (VA) için en yakın olan bir belirtilen simge türü alır.|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Belirtilen meta veri simgesi içeren simge alır.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|İki simge eşdeğer olup olmadığını denetler.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Bir simge benzersiz tanımlayıcısıyla alır.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|İçeriyor veya belirtilen göreli sanal adres ve uzaklık için en yakın olan bir belirtilen simge türü alır.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|İçeriyor veya belirtilen sanal adres ve uzaklık için en yakın olan bir belirtilen simge türü alır.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Kaynak dosya derlenecek ve ad ile alır.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Bir kaynak dosya kaynak dosya tanımlayıcısı tarafından alır.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Satır numaraları içinde belirtilen derlenecek ve kaynak dosya tanımlayıcı alır.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Belirtilen adres içeren belirtilen derlenecek satırları alır.|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Belirtilen göreli sanal adres içeren belirtilen derlenecek satırları alır.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Belirtilen adres aralığında bulunan satırlar için satır numarası bilgilerini bulur.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Kaynak dosya ve satır numarası tarafından belirtilen derlenecek satırları alır.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Öznitelik sağlayıcıları tarafından sembol deposu veya diğer bileşenleri derleme işleminin yerleştirilen bir kaynağı alır.|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Hata ayıklama veri akışlarını numaralandırılmış bir dizisini alır.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Tüm satır içi çerçeveler belirli bir adresi üzerinde yinelemek bir istemci izin veren bir numaralandırmasını alır.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Tüm satır içi çerçeveler bir adresinde belirtilen göreli sanal (RVA) yinelemek bir istemci izin veren bir numaralandırmasını alır.|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Tüm satır içi çerçeveler belirtilen sanal adresine (VA) yinelemek bir istemci izin veren bir numaralandırmasını alır.|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Satır numarası bilgilerini doğrudan içermesinden, tüm işlevleri veya dolaylı olarak, belirtilen üst simgesiyle yinelemek bir istemci izin veren bir numaralandırmasını alır.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Satır numarası bilgilerini doğrudan içermesinden, tüm işlevleri veya dolaylı olarak, belirtilen üst simgesiyle yinelemek bir istemcinin sağlar ve belirtilen adres aralığında bulunan bir numaralandırmasını alır.|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Satır numarası bilgilerini doğrudan içermesinden, tüm işlevleri veya dolaylı olarak, belirtilen üst simgesiyle yinelemek bir istemcinin sağlar ve belirtilen göreli sanal adres içinde (RVA) bulunan bir numaralandırmasını alır.|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Satır numarası bilgilerini doğrudan içermesinden, tüm işlevleri veya dolaylı olarak, belirtilen üst simgesiyle yinelemek bir istemcinin sağlar ve belirtilen sanal adres (VA) içinde bulunan bir numaralandırmasını alır.|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Satır numarası bilgilerini doğrudan veya dolaylı olarak, belirtilen kaynak dosyası ve satır numarası içermesinden, tüm işlevlerin yinelemek bir istemci izin veren bir numaralandırmasını alır.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Belirtilen bir adla eşleşen tüm satır içi işlevlerin satır numarası bilgilerini yinelemek bir istemci izin veren bir numaralandırmasını alır.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Belirtilen etiket değeri karşılık gelen bir değişken sembolleri numaralandırması üst Hızlandırıcı saplama işlevi döndürür.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Bu yöntem karşılık gelen bir etiket değeri verildiğinde, belirtilen üst Hızlandırıcı saplama işlevinde belirtilen göreli sanal adresinde bulunan sembolleri numaralandırması döndürür.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Belirtilen satır içi işlev adına karşılık gelen satır içi çerçeveler simgelerini numaralandırması döndürür.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Belirtilen kaynak konumuna karşılık gelen satır içi çerçeveler simgelerini numaralandırması döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrı önemlidir [Idiasession::put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) oluşturduktan sonra yöntemi `IDiaSession` nesne — ve geçirilen değerini `put_loadAddress` yöntemi sıfır olmalıdır — olması simgelerin tüm sanal adres (VA) özellikleri erişilebilir. Ayıklanacak yürütülebilir hangi program yüklü yük adresi gelir. Örneğin, Win32 işlevi çağırabilirsiniz `GetModuleInformation` yük adresi yürütülebilir dosyası için bir tanıtıcı yürütülebilir dosyaya verilen almak için.  
  
## <a name="example"></a>Örnek  
 Bu örnek nasıl alınacağını gösterir `IDiaSession` arabirimi genel başlatma DIA SDK'ın bir parçası olarak.  
  
```C++  
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
 Başlık: Dia2.h  
  
 Kitaplığı: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arabirimler (arabirim erişimi SDK'SINDA hata ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Genel bakış](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)   
 [Idiaaddressmap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiadatasource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource::opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [Idiasymbol::findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [.Pdb Dosyasını Sorgulama](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)