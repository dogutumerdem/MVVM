# Introduction 

This is a MVVM framework. Integrates power of [Reactive Programming](https://github.com/dotnet/reactive) with MVVM model for WPF application. For an effective modelling of MVVM, [Castle Windsor](https://github.com/castleproject/Windsor) used as IoC container.

## Sample and Simple Application

You can find an appcliation sample in the project, *SimpleApp*.

## Overview

You can find `CodeMap.dgml` provides a visual overview for the project.

* `IVisual`, `IControl`, `IWindow`, `IMessageBase`  are interfaces for View.

* `IControlViewModel`, `IWindowViewModel`, are interfaces for ViewModel.

* `ReactiveObject` is the implementation of `INotifyPropertyChanged` interface.

* `BaseViewModel` and `BaseModel` extend `ReactiveObject` abstract class.

* `BaseControlViewModel` and `BaseWindowViewModel` are extending `BaseViewModel`.

* `PagedCollection<T>` is a paged collection implementation using Rx framework.

* `WebFileUploader` and `WebFileDownloader` are file upload/download implementation using Rx framework.

* `RxMessageBus` is message bus implementation using Rx framework, to inter-component messaging. `IMessageBase`  is the message subject interface. Message subjects should implement this empty interface.

* `BackgroundThread` is non-blocking background process manager implementation using Rx framework.

* `Observable<T>` is property wrapper using Rx framework.
    ``` csharp
    public Observable<string> Title { get; set; }

    // Watching change

    public BaseViewModel()
    {
        Title = new Observable<string>();

        Title.Subscribe(x =>
            {
                SecurityCode = x;
            });
    }
    ```

