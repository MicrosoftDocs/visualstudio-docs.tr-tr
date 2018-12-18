---
title: Idiatable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b9b792876e281f73f4df0246734403812a72aea
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056416"
---
# <a name="idiatable"></a>IDiaTable
DIA veri kaynağı tablosu numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDiaTable`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Alır [IEnumVARIANT arabirimi](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) bu Sıralayıcı sürümü.|  
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Tablonun adını alır.|  
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Tablosundaki öğelerin sayısını alır.|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Belirli giriş dizini için bir başvuru alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirimi uygulayan `IEnumUnknown` Microsoft.VisualStudio.OLE.Interop ad alanı numaralandırma yöntemleri. `IEnumUnknown` Numaralandırma arabirimidir İçindekiler üzerinde yineleme için çok daha verimli [Idiatable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) ve [Idiatable::Item](../../debugger/debug-interface-access/idiatable-item.md) yöntemleri.  
  
 Yorumu `IUnknown` arabirimi tarafından döndürülen `IDiaTable::Item` yöntemi veya `Next` yöntemi (Microsoft.VisualStudio.OLE.Interop ad alanında) tablo türüne bağlıdır. Örneğin, varsa `IDiaTable` arabirimi temsil eder, eklenen kaynakların bir listesinde `IUnknown` arabirimi seçmeleri için [Idiaınjectedsource](../../debugger/debug-interface-access/idiainjectedsource.md) arabirimi.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirim çağırarak elde [Idiaenumtables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md) veya [Idiaenumtables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md) yöntemleri.  
  
 Aşağıdaki arabirimleri ile uygulanan `IDiaTable` arabirimi (diğer bir deyişle, sorgu `IDiaTable` aşağıdaki arabirimlerinden biri, arabirimin):  
  
-   [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
-   [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
-   [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
-   [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
-   [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
-   [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
-   [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## <a name="example"></a>Örnek  
 İlk işlev `ShowTableNames`, oturumda tüm tabloların adlarını görüntüler. İkinci işlev `GetTable`, belirtilen arabirimini uygulayan bir tablo için tabloların tümü arar. Üçüncü işlevi `UseTable`, nasıl kullanılacağını gösterir `GetTable` işlevi.  
  
> [!NOTE]
>  `CDiaBSTR` kaydırılan bir sınıf bir `BSTR` ve örnek oluşturma kapsam dışına çıktığında dize boşaltma otomatik olarak yönetir.  
  
```C++  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) )  
            && celt == 1 )  
    {  
        CDiaBSTR bstrTableName;  
        if ( pTable->get_name( &bstrTableName ) != 0 )  
        {  
            Fatal( "get_name" );  
        }  
        printf( "Found table: %ws\n", bstrTableName );  
    }  
  
// Searches the list of all tables for a table that supports  
// the specified interface.  Use this function to obtain an  
// enumeration interface.  
HRESULT GetTable(IDiaSession* pSession,  
                 REFIID       iid,  
                 void**       ppUnk)  
{  
    CComPtr<IDiaEnumTables> pEnumTables;  
    HRESULT hResult;  
  
    if (FAILED(pSession->getEnumTables(&pEnumTables)))  
        Fatal("getEnumTables");  
  
    CComPtr<IDiaTable> pTable;  
    ULONG celt = 0;  
    while (SUCCEEDED(hResult = pEnumTables->Next(1, &pTable, &celt)) &&  
           celt == 1)  
    {  
        if (pTable->QueryInterface(iid, (void**)ppUnk) == S_OK)  
        {  
            return S_OK;  
        }  
        pTable = NULL;  
    }  
  
    if (FAILED(hResult))  
        Fatal("EnumTables->Next");  
  
    return E_FAIL;  
}  
  
// This function shows how to use the GetTable function.  
void UseTable(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pEnumSegments;  
    if (SUCCEEDED(GetTable(pSession, __uuidof(IDiaEnumSegments), &pEnumSegments)))  
    {  
        // Do something with pEnumSegments.  
    }  
}  
```  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: Dia2.h  
  
 Kitaplığı: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arabirimler (arabirim erişimi SDK'SINDA hata ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiaenumtables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [Idiaenumtables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)