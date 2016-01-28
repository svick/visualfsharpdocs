# Async.Start Method (F#)

Starts the asynchronous computation in the thread pool. Do not await its result.

**Namespace/Module Path:** Microsoft.FSharp.Control

**Assembly:** FSharp.Core (in FSharp.Core.dll)


## CAPS_SYNTAX_MD

```
// Signature:
static member Start : Async<unit> * ?CancellationToken -> unit

// Usage:
Async.Start (computation)
Async.Start (computation, cancellationToken = cancellationToken)
```

#### CAPS_PARAMETERS_MD
*computation*
Type: [Async](http://msdn.microsoft.com/en-us/library/e0b28ea2-dea5-4021-b2b9-d7d4761babde)**&lt;**[unit](http://msdn.microsoft.com/en-us/library/00b837c2-6c8a-483a-87d3-0479c64037a7)**&gt;**


The computation to run asynchronously.


*cancellationToken*
Type: [CancellationToken](http://msdn.microsoft.com/en-us/library/31a3eafe-b61b-46c4-927d-bc9a3ae357c2)


The cancellation token to be associated with the computation. If one is not supplied, the default cancellation token is used.




## CAPS_REMARKS_MD
If no cancellation token is provided then the default cancellation token is used.

**The following code example shows how to start an asynchronous computation on the thread pool.**
```

    open System.Windows.Forms

    let bufferData = Array.zeroCreate<byte> 100000000

    let async1 =
         async {
           use outputFile = System.IO.File.Create("longoutput.dat")
           do! outputFile.AsyncWrite(bufferData) 
         }
      

    let form = new Form(Text = "Test Form")
    let button = new Button(Text = "Start")
    form.Controls.Add(button)
    button.Click.Add(fun args -> Async.Start(async1))
    Application.Run(form)
```

## Platforms
Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2


## Version Information
**F# Core Library Versions**

Supported in: 2.0, 4.0, Portable




## See Also
[Control.Async Class &#40;F&#35;&#41;](Control.Async+Class+%28F%23%29.md)

[Microsoft.FSharp.Control Namespace &#40;F&#35;&#41;](Microsoft.FSharp.Control+Namespace+%28F%23%29.md)
