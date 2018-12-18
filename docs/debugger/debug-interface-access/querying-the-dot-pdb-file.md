---
title: Sorgulama. Pdb dosyası | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a13f98e9d1507c0044057099d61b625e1142929e
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282059"
---
# <a name="querying-the-pdb-file"></a>.Pdb Dosyasını Sorgulama
Program veritabanı dosyası (.pdb uzantısına) türü ve, derleme ve bağlama proje boyunca toplanan sembolik hata ayıklama bilgisini içeren bir ikili dosyadır. Bir PDB dosyası ile C/C++ programı derleme oluşturulduğunda **/zi** veya **/zi** veya [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], veya [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] ile program **/debug** seçeneği. Başvuru için hata ayıklama bilgisi .pdb dosyasına nesne dosyaları içerir. Pdb dosyaları hakkında daha fazla bilgi için bkz. [PDB dosyaları](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yd4f8bd1(v=vs.100)). DIA uygulama çeşitli simgeler, nesneleri ve veri öğeleri bir yürütülebilir görüntü içinde hakkındaki ayrıntıları almak için aşağıdaki genel adımları kullanabilirsiniz.  
  
### <a name="to-query-the-pdb-file"></a>.Pdb dosyasını sorgulama  
  
1.  Oluşturarak bir veri kaynağı alma bir [Idiadatasource](../../debugger/debug-interface-access/idiadatasource.md) arabirimi.  
  
    ```C++  
    CComPtr<IDiaDataSource> pSource;  
    hr = CoCreateInstance( CLSID_DiaSource,  
                           NULL,  
                           CLSCTX_INPROC_SERVER,  
                           __uuidof( IDiaDataSource ),  
                          (void **) &pSource);  
  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    ```  
  
2.  Çağrı [Idiadatasource::loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) veya [Idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) hata ayıklama bilgileri yüklenemedi.  
  
    ```C++  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename, szFilename, sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    ```  
  
3.  Çağrı [Idiadatasource::opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md) açmak için bir [Idiasession](../../debugger/debug-interface-access/idiasession.md) hata ayıklama bilgileri erişim elde etmek için.  
  
    ```C++  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4.  Yöntemi kullanarak `IDiaSession` sorgulamak için veri kaynağındaki simge.  
  
    ```C++  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5.  Kullanım `IDiaEnum*` arabirimleri saymak ve simgeler veya diğer öğeleri taramak için hata ayıklama bilgileri.  
  
    ```C++  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) ) && celt == 1 )  
    {  
         // Do something with each IDiaTable.  
    }  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)