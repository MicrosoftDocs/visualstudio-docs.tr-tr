---
title: DisassemblyData | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cb7682129ed077cf7f84f9a72edc5e75c0398ff3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51804559"
---
# <a name="disassemblydata"></a>DisassemblyData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Görüntülenecek bir ayrıştırma yönerge tümleşik geliştirme ortamı (IDE) için açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
typedef struct tagDisassemblyData {   
   DISASSEMBLY_STREAM_FIELDS dwFields;  
   BSTR                      bstrAddress;  
   BSTR                      bstrAddressOffset;  
   BSTR                      bstrCodeBytes;  
   BSTR                      bstrOpcode;  
   BSTR                      bstrOperands;  
   BSTR                      bstrSymbol;  
   UINT64                    uCodeLocationId;  
   TEXT_POSITION             posBeg;  
   TEXT_POSITION             posEnd;  
   BSTR                      bstrDocumentUrl;  
   DWORD                     dwByteOffset;  
   DISASSEMBLY_FLAGS         dwFlags;  
} DisassemblyData;  
```  
  
```csharp  
public struct DisassemblyData {   
   public uint          dwFields;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrCodeBytes;  
   public string        bstrOpcode;  
   public string        bstrOperands;  
   public string        bstrSymbol;  
   public ulong         uCodeLocationId;  
   public TEXT_POSITION posBeg;  
   public TEXT_POSITION posEnd;  
   public string        bstrDocumentUrl;  
   public uint          dwByteOffset;  
   public uint          dwFlags;  
};  
```  
  
## <a name="members"></a>Üyeler  
 `dwFields`  
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) hangi alanların doldurulmuş belirten sabiti.  
  
 `bstrAddress`  
 Bazı başlangıç noktası (genellikle ilişkilendirilmiş işlev başına) uzaklık olarak adresi.  
  
 `bstrCodeBytes`  
 Bu yönerge kodu bayt sayısı.  
  
 `bstrOpcode`  
 Bu yönerge için yönerge kodu.  
  
 `bstrOperands`  
 Bu yönerge için işlenen.  
  
 `bstrSymbol`  
 Sembol adı varsa (ortak sembol, etiket ve benzeri) adresi ile ilişkili.  
  
 `uCodeLocationId`  
 Ayrıştırılmış bu satırı kod konum tanımlayıcısı. Bir satır kod bağlamı adresini başka bir kod bağlamı adresinizden büyükse, ardından ilk ayrıştırılmış kodu konum tanımlayıcısı aynı zamanda ikinci kod konum tanımlayıcısı büyük olacaktır.  
  
 `posBeg`  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) belge ayrıştırma veri başladığı konumu karşılık gelir.  
  
 `posEnd`  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) belgede sona ereceği Ayrıştırılmış kod veri konumuna karşılık gelir.  
  
 `bstrDocumentUrl`  
 Dosya adı olarak gösterilen metin belgeleri `bstrDocumentUrl` alan burada kaynağı bulunabilir, dosya adı ile oturum doldurulmuş biçimini kullanarak `file://file name`.  
  
 Dosya adları ' gösterilemez metin belgeleri `bstrDocumentUrl` belge için benzersiz bir tanımlayıcıdır ve hata ayıklama altyapısı uygulamalıdır [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) yöntemi.  
  
 Bu alan ayrıca sağlama hakkında ek bilgiler içerebilir. Açıklamalar, Ayrıntılar için bkz.  
  
 `dwByteOffset`  
 Yönergedir kod satırını başından itibaren bayt sayısı.  
  
 `dwFlags`  
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) hangi bayrakları etkin olan belirten sabiti.  
  
## <a name="remarks"></a>Açıklamalar  
 Her `DisassemblyData` ayrıştırması bir yönerge yapısını açıklar. Bu yapılar bir dizi öğesinden döndürülen [okuma](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) yöntemi.  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) yapısı yalnızca metin tabanlı belgeler için kullanılır. Bu yönerge için kaynak kodu aralığı bir deyim ya da satır, örneğin oluşturulmuş yalnızca ilk yönerge için doldurulur, `dwByteOffset == 0`.  
  
 Metinsel olmayan belgeler için bir belge bağlamına koddan elde edilebilir ve `bstrDocumentUrl` alan, bir null değer olmalıdır. Varsa `bstrDocumentUrl` alan aynıdır `bstrDocumentUrl` alanındaki önceki `DisassemblyData` dizi öğesi, ardından ayarlayın `bstrDocumentUrl` bir null değer.  
  
 Varsa `dwFlags` alan `DF_DOCUMENT_CHECKSUM` bayrağı ayarlanmış, ek bir sağlama toplamı bilgisi işaret ettiği dizeyi izleyen sonra `bstrDocumentUrl` alan. Özellikle, boş bir dize Sonlandırıcı sonra vardır, sırayla sağlama toplamı bayt sayısını belirten bir 4 baytlık değer takip eder ve sırayla sağlama toplamı bayt tarafından izlenir sağlama algoritması tanımlayan bir GUID izler. Bu konudaki örnek kodlama ve kodunu çözme Bu alanda konusunda bkz [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].  
  
## <a name="example"></a>Örnek  
 `bstrDocumentUrl` Alan, bir dize dışında ek bilgiler içerebilir, varsa `DF_DOCUMENT_CHECKSUM` bayrağı ayarlanır. Oluşturma ve bu kodlu bir dize okuma işlemini basittir [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)]. Bununla birlikte, [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], başka bir konudur. Olanlar merak, aşağıdaki örnekte kodlanmış bir dizeden oluşturmanın yollarından biri gösterilmektedir [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] ve kodlanmış dize olarak kodunu çözmek için tek yönlü [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
namespace MyNamespace  
    class MyClass  
    {  
        string EncodeData(string documentString,  
                          Guid checksumGuid,  
                          byte[] checksumData)  
        {  
            string returnString = documentString;  
  
            if (checksumGuid == null || checksumData == null)  
            {  
                // Nothing more to do. Just return the string.  
                return returnString;  
            }  
  
            returnString += '\0'; // separating null value  
  
            // Add checksum GUID to string.  
            byte[] guidDataArray  = checksumGuid.ToByteArray();  
            int    guidDataLength = guidDataArray.Length;  
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);  
            }  
            // Copy guid data bytes to string as wide characters.  
            // Assumption: sizeof(char) == 2.  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum count (a 32-bit value).  
            Int32 checksumCount = checksumData.Length;  
            Marshal.StructureToPtr(checksumCount, pBuffer, true);  
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum data.  
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);  
            for (int i = 0; i < checksumCount; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, checksumData[i]);  
            }  
            for (int i = 0; i < checksumCount / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
            Marshal.FreeCoTaskMem(pBuffer);  
  
            return returnString;  
        }  
  
        void DecodeData(    string encodedString,  
                        out string documentString,  
                        out Guid   checksumGuid,  
                        out byte[] checksumData)  
       {  
           documentString = String.Empty;  
           checksumGuid = Guid.Empty;  
           checksumData = null;  
  
           IntPtr pBuffer = Marshal.StringToBSTR(encodedString);  
           if (null != pBuffer)  
           {  
               int bufferOffset = 0;  
  
               // Parse string out.  String is assumed to be Unicode.  
               documentString = Marshal.PtrToStringUni(pBuffer);  
               bufferOffset += (documentString.Length + 1) * sizeof(char);  
  
               // Parse Guid out.  
               // Read guid bytes from buffer and store in temporary  
               // buffer that contains only the guid bytes. Then the  
               // Marshal.PtrToStructure() can work properly.  
               byte[] guidDataArray  = checksumGuid.ToByteArray();  
               int    guidDataLength = guidDataArray.Length;  
               IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);  
               for (int i = 0; i < guidDataLength; i++)  
               {  
                   Marshal.WriteByte(pGuidBuffer, i,  
                                     Marshal.ReadByte(pBuffer, bufferOffset + i);  
               }  
               bufferOffset += guidDataLength;  
               checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));  
               Marshal.FreeCoTaskMem(pGuidBuffer);  
  
              // Parse out the number of checksum data bytes (always 32-bit value).  
              int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);  
              bufferOffset += sizeof(Int32);  
  
              // Parse out the checksum data.  
              checksumData = new byte[dataCount];  
              for (int i = 0; i < dataCount; i++)  
              {  
                  checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);  
              }  
           }  
       }  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılar ve birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Okuma](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)

