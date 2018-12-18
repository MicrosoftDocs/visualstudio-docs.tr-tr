---
title: 'İzlenecek yol: JavaScript kullanarak SDK oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1be1cf15e1f43af5999d4d65a5342d9c7b46da25
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884075"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>İzlenecek yol: JavaScript kullanarak SDK oluşturma
Bu izlenecek yol, bir basit matematik SDK'sı bir Visual Studio Uzantısı (VSIX) olarak oluşturmak için JavaScript kullanmayı öğretir.  İzlenecek yol, şu bölümlere ayrılmıştır:  
  
- [SimpleMathVSIX uzantı SDK projesi oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)  
  
- [SDK'sını kullanan örnek bir uygulama oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)  
  
  JavaScript için sınıf kitaplığı proje türü yoktur. Bu kılavuzda, örnek *arithmetic.js* doğrudan içinde VSIX projesi dosyası oluşturulur. Uygulamada, öncelikle yapı ve Windows Store uygulaması olarak JavaScript ve CSS dosyaları test öneririz — kullanarak örneğin, **boş uygulama** şablonu — bir VSIX projesinde almadan önce.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolda takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createSimpleMathVSIX"></a> SimpleMathVSIX uzantı SDK projesi oluşturmak için  
  
1.  Menü çubuğunda, **dosya** > **yeni** > **proje**.  
  
2.  Şablon kategoriler listesinde altında **Visual C#** seçin **genişletilebilirlik**ve ardından **VSIX projesi** şablonu.  
  
3.  İçinde **adı** metin kutusunda, belirtin `SimpleMathVSIX` ve **Tamam** düğmesi.  
  
4.  Varsa **Visual Studio Paket Sihirbazı'nı** görüntülenirse, seçin **sonraki** düğmesini **Hoş Geldiniz** sayfasında ve ardından **sayfa 1 / 7**, seçin **Son** düğmesi.  
  
     Ancak **bildirim Tasarımcısı** açar, biz tutacağız Bu izlenecek yol basit doğrudan bildirim dosyasını değiştirerek.  
  
5.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **source.extension.vsixmanifest** dosya ve ardından **kodu görüntüle**. Dosyanın mevcut içeriğini değiştirmek için bu kodu kullanın.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">  
      <Metadata>  
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />  
        <DisplayName>Simple Math</DisplayName>  
        <Description>Does basic arithmetic calculations.</Description>  
      </Metadata>  
      <Installation Scope="Global" AllUsers="true">  
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />  
      </Installation>  
      <Dependencies>  
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />  
      </Dependencies>  
      <Assets>  
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />  
      </Assets>  
    </PackageManifest>  
    ```  
  
6.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **SimpleMathVSIX** proje ve ardından **Ekle** > **yeni öğe**.  
  
7.  İçinde **veri** kategorisi seçin **XML dosyası**, dosya adı `SDKManifest.xml`ve **Ekle** düğmesi.  
  
8.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **SDKManifest.xml** dosya ve ardından **açın** dosyasını görüntüleyecek şekilde **XMLDüzenleyicisi**.  
  
9. Aşağıdaki kodu ekleyin **SDKManifest.xml** dosya.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <FileList  
      DisplayName="Simple Math"  
      MinVSVersion="14.0"  
      AppliesTo="JavaScript+WindowsAppContainer"  
      SupportsMultipleVersions="Error"  
      MoreInfo="https://msdn.microsoft.com/">  
  
      <!-- JS -->  
      <File Content="js\arithmetic.js" />  
    </FileList>  
  
    ```  
  
10. İçinde **Çözüm Gezgini**, kısayol menüsünde **SDKManifest.xml** dosya öğesini **özellikleri**.  
  
11. İçinde **özellikleri** penceresinde **VSIX Ekle** özelliğini **True**.  
  
12. İçinde **Çözüm Gezgini**, kısayol menüsünde **SimpleMathVSIX** projesinin **Ekle** > **yeni klasör**, ve ardından klasörünü adlandırın `Redist`.  
  
13. Bu klasör yapısını oluşturmak için Redist altındaki alt klasörleri ekleyin:  
  
     *\Redist\CommonConfiguration\Neutral\SimpleMath\js\\*  
  
14. Kısayol menüsünde **\js\\**  klasörü seçin **Ekle** > **yeni öğe**.  
  
15. Altında **Visual C# öğeleri**seçin **Web** kategori tıklayın ve ardından **JavaScript dosyası** öğesi. Dosya adı `arithmetic.js`ve ardından **Ekle** düğmesi.  
  
16. Aşağıdaki kodu ekleyin *arithmetic.js*:  
  
    ```csharp  
    (function (global) {  
        "use strict";  
        global.Arithmetic = {  
            add: function (firstNumber, secondNumber) {  
                return firstNumber + secondNumber;  
            },  
  
            subtract: function (firstNumber, secondNumber) {  
                return firstNumber - secondNumber;  
            },  
  
            multiply: function (firstNumber, secondNumber) {  
                return firstNumber * secondNumber;  
            },  
  
            divide: function (firstNumber, secondNumber) {  
                return firstNumber / secondNumber;  
            }  
        };  
    })(this);  
  
    ```  
  
17. İçinde **Çözüm Gezgini**, kısayol menüsünde **arithmetic.js** dosya öğesini **özellikleri**. Bu özellik değişiklikleri yapın:  
  
    -   Ayarlama **VSIX Ekle** özelliğini **True**.  
  
    -   Ayarlama **çıkış dizinine Kopyala** özelliğini **her zaman Kopyala**.  
  
18. İçinde **Çözüm Gezgini**, kısayol menüsünde **SimpleMathVSIX** projesinin **yapı**.  
  
19. Yapı projesi için kısayol menüsündeki başarıyla tamamlandıktan sonra seçin **klasörü dosya Gezgini'nde Aç**. Gidin **\bin\debug\\**, çalıştırıp `SimpleMathVSIX.vsix` yükleyin.  
  
20. Seçin **yükleme** düğmesi ve let yükleme tamamlandı.  
  
21. Visual Studio'yu yeniden başlatın.  
  
##  <a name="createSampleApp"></a> SDK'sını kullanan örnek bir uygulama oluşturmak için  
  
1. Menü çubuğunda, **dosya** > **yeni** > **proje**.  
  
2. Şablon kategoriler listesinde altında **JavaScript**seçin **Windows Store**ve ardından **boş uygulama** şablonu.  
  
3. İçinde **adı** kutusunda, belirtin `ArithmeticUI`. Seçin **Tamam** düğmesi.  
  
4. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ArithmeticUI** proje ve ardından **Ekle** > **başvuru**.  
  
5. Altında **Windows**, seçin **uzantıları**, dikkat **basit matematik** görüntülenir.  
  
6. Seçin **basit matematik** onay kutusunu işaretleyin ve ardından **Tamam** düğmesi.  
  
7. İçinde **Çözüm Gezgini**altında **başvuruları**, dikkat **basit matematik** başvuru görüntülenir. Genişletin ve fark bir **\js\\**  içeren klasör **arithmetic.js**. Açabileceğiniz **arithmetic.js** kaynak kodunuzu yüklendiğini doğrulamak için.  
  
8. İçeriğini değiştirmek için aşağıdaki kodu kullanın *default.htm*.  
  
   ```html  
   <!DOCTYPE html>  
   <html>  
   <head>  
       <meta charset="utf-8" />  
       <title>ArithmeticUI</title>  
  
       <!-- WinJS references -->  
       <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />  
       <script src="//Microsoft.WinJS.1.0/js/base.js"></script>  
       <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>  
  
       <!-- ArithmeticUI references -->  
       <link href="/css/default.css" rel="stylesheet" />  
       <script src="/js/default.js"></script>  
       <script src="/SimpleMath/js/arithmetic.js"></script>  
   </head>  
   <body>  
       <form>  
       <div id="calculator" class="ms-grid">  
           <input name="firstNumber" id="firstNumber" type="number" step="any">  
           <div id="operators">  
               <button class="operator" type="button">+</button>  
               <button class="operator" type="button">-</button>  
               <button class="operator" type="button">*</button>  
               <button class="operator" type="button">/</button>  
           </div>  
           <input id="secondNumber" type="number">  
           <button class="calculate" type="button">=</button>  
           <input id="result" type="number" name="result" disabled="" readonly="">  
       </div>  
       </form>  
   </body>  
   </html>  
   ```  
  
9. İçeriğini değiştirmek için aşağıdaki kodu kullanın *\js\default.js*.  
  
    ```csharp  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var operation = null;  
  
        function calculateResult() {  
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),  
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),  
                result = 0;  
  
            if (isNaN(firstNumber) || isNaN(secondNumber)) {  
                result = 0;  
            }  
            else {  
                switch (operation) {  
                    case "+":  
                        result = Arithmetic.add(firstNumber, secondNumber);  
                        break;  
                    case "-":  
                        result = Arithmetic.subtract(firstNumber, secondNumber);  
                        break;  
                    case "*":  
                        result = Arithmetic.multiply(firstNumber, secondNumber);  
                        break;  
                    case "/":  
                        result = Arithmetic.divide(firstNumber, secondNumber);  
                        break;  
                    default:  
                }  
            }  
            document.querySelector("#result").value = result.toString();  
        }  
  
        app.onactivated = function (args) {  
            document.querySelector("#calculator").addEventListener("click", function (event) {  
                if (event.target.tagName.toLowerCase() === "button") {  
                    switch (event.target.className) {  
                        case "operator":  
                            operation = event.target.innerText;  
                            break;  
                        case "calculate":  
                            calculateResult();  
                            break;  
                        default:  
                            break;  
                    }  
                }  
            });  
        };  
  
        app.start();  
    })();  
    ```  
  
10. Öğesinin içeriğini değiştirin *\css\default.css* Bu kod ile:  
  
    ```xml  
    form {  
        display: -ms-grid;  
        -ms-grid-rows: 1fr auto 1fr;  
        -ms-grid-columns: 1fr auto 1fr;  
        height: 100%;  
        width: 100%;  
    }  
  
    button, input[type=number] {  
        margin-right: 5px;  
        -ms-grid-row-align: center;  
    }  
  
    #calculator {  
        -ms-grid-column: 2;  
        -ms-grid-row: 2;  
        display: -ms-grid;  
        -ms-grid-rows: 1fr;  
        -ms-grid-columns: auto min-content auto auto auto;  
    }  
  
    .ms-grid input {  
        width: 5em;  
    }  
  
    #firstNumber {  
        -ms-grid-column: 1;  
        -ms-grid-row-align: center;  
    }  
  
    #operators {  
        -ms-grid-column: 2;  
        -ms-grid-row-align: center;  
    }  
  
        #operators button.operator {  
            margin-bottom: 5px;  
            height: 40px;  
        }  
  
    #secondNumber {  
        -ms-grid-column: 3;  
    }  
  
    button.calculate {  
        -ms-grid-column: 4;  
        -ms-grid-row-align: center;  
        height: 40px;  
    }  
  
    #result {  
        -ms-grid-column: 5;  
    }  
  
    ```  
  
11. Seçin **F5** anahtarı oluşturun ve uygulamayı çalıştırın.  
  
12. Uygulama kullanıcı Arabirimindeki herhangi iki sayıyı girin, bir işlem seçin ve ardından **=** düğmesi. Doğru sonucu görünür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Bir yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md)
