---
title: Sorgulama. Pdb dosyası | Microsoft Docs
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
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f82180427155a364ad4240eeede0503e99857f80
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793269"
---
# <a name="querying-the-pdb-file"></a>.Pdb Dosyasını Sorgulama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Program veritabanı dosyası (.pdb uzantısına) türü ve, derleme ve bağlama proje boyunca toplanan sembolik hata ayıklama bilgisini içeren bir ikili dosyadır. Bir PDB dosyası ile C/C++ programı derleme oluşturulduğunda **/zi** veya **/zi** veya [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)], veya [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] ile program **/debug** seçeneği. Başvuru için hata ayıklama bilgisi .pdb dosyasına nesne dosyaları içerir. Pdb dosyaları hakkında daha fazla bilgi için bkz. [PDB dosyaları](http://msdn.microsoft.com/en-us/1761c84e-8c2c-4632-9649-b5f99964ed3f). DIA uygulama çeşitli simgeler, nesneleri ve veri öğeleri bir yürütülebilir görüntü içinde hakkındaki ayrıntıları almak için aşağıdaki genel adımları kullanabilirsiniz.  
  
### <a name="to-query-the-pdb-file"></a>.Pdb dosyasını sorgulama  
  
1.  Oluşturarak bir veri kaynağı alma bir [Idiadatasource](../../debugger/debug-interface-access/idiadatasource.md) arabirimi.  
  
    ```cpp#  
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
  
    ```cpp#  
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
  
    ```cpp#  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4.  Yöntemi kullanarak `IDiaSession` sorgulamak için veri kaynağındaki simge.  
  
    ```cpp#  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5.  Kullanım `IDiaEnum*` arabirimleri saymak ve simgeler veya diğer öğeleri taramak için hata ayıklama bilgileri.  
  
    ```cpp#  
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



