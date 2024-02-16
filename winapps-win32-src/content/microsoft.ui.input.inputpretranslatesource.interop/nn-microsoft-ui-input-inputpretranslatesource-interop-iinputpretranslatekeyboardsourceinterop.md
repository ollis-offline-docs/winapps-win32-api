---
UID: NN:microsoft.ui.input.inputpretranslatesource.interop.IInputPreTranslateKeyboardSourceInterop
tech.root: 
title: IInputPreTranslateKeyboardSourceInterop
ms.date: 
targetos: Windows
description: 
prerelease: false
req.assembly: 
req.construct-type: iface
req.ddi-compliance: 
req.header: microsoft.ui.input.inputpretranslatesource.interop.h
req.idl: 
req.include-header: 
req.max-support: 
req.namespace: 
req.redist: 
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.target-type: 
req.unicode-ansi: 
topic_type:
 - apiref
api_type:
 - COM
api_location:
 - microsoft.ui.input.inputpretranslatesource.interop.h
api_name:
 - IInputPreTranslateKeyboardSourceInterop
f1_keywords:
 - IInputPreTranslateKeyboardSourceInterop
 - microsoft.ui.input.inputpretranslatesource.interop/IInputPreTranslateKeyboardSourceInterop
dev_langs:
 - c++
helpviewer_keywords:
 - IInputPreTranslateKeyboardSourceInterop
---

# IInputPreTranslateKeyboardSourceInterop interface

## -description

Enables keyboard input interoperability between XAML and a native window.

## -remarks

## -examples

The following example shows a traditional Win32 accelerator table inside the PreTranslateMessage processing.

```cpp
class MyHandler : COM<IInputPreTranslateKeyboardSourceHandler>
{
public:
    HRESULT Create(
        IInputPreTranslateKeyboardSource * source,
        HWND acceleratorHwnd,
        HACCEL acceleratorTable)
    {
        // Register for accelerator processing. The scope of processing is determined 
        // by the ContentNode that the InputPreTranslateKeyboardSource is servicing.
        ComPtr<IInputPreTranslateKeyboardSourceInterop> interop;
        FAIL_FAST_IF_FAILED(source->QueryInterface(IID_PPV_ARGS(&interop)));

        FAIL_FAST_IF_FAILED(interop->SetHandler(this));
        m_preTranslateSource = source;

        // Remember the accelerator table and its target HWND.  This could be changed 
        // to load the accelerators for this node or enable changing tables at runtime.
        m_acceleratorHwnd = acceleratorHwnd;
        m_acceleratorTable = acceleratorTable;

        return S_OK;
    }

    ~MyHandler()
    {
        if (m_preTranslateSource != nullptr)
        {
            m_preTranslateSource->SetHandler(nullptr);
            m_preTranslateSource = nullptr;
        }

        m_acceleratorHwnd = nullptr;
        m_acceleratorTable = nullptr;
    }

    IFACEMETHOD(OnDirectMessage)(
        _In_ IInputPreTranslateKeyboardSource * /*source*/,
        _Inout_ MSG * msg,
        _Inout_ BOOL * handled
        ) override
    {
        // PASS 1: Attempt to handle the accelerator when the underlying ContentNode explicitly 
        // has focus. This allows this InputObject to "win", even if other ContentNodes in the 
        // tree would also have handled this accelerator.  If "handled == TRUE" then 
        // traversal stops and no OnTreeMessage handlers will be called.

        *handled = ::TranslateAccelerator(m_acceleratorHwnd, m_acceleratorTable, msg) != 0;

        return S_OK;
    }

    IFACEMETHOD(OnTreeMessage)(
        _In_ IInputPreTranslateKeyboardSource * /*source*/,
        _Inout_ MSG * msg,
        _Out_ BOOL * handled
        ) override
    {
        // PASS 2: Attempt to handle the accelerator when the underlying ContentNode does not
        // necessarily have focus and the general tree traversal is occurring. In this situation,
        // the specific ContentNode message with focus did not handled during Pass 1 with
        // OnDirectMessage, so we are calling various OnTreeMessage in order to handle during
        // Pass 2.

        *handled = ::TranslateAccelerator(m_acceleratorHwnd, m_acceleratorTable, msg) != 0;

        return S_OK;
    }

private:
    ComPtr<IInputPreTranslateKeyboardSource> m_preTranslateSource;
    HWND m_acceleratorHwnd = nullptr;  // HWND to send WM_COMMAND and WM_SYSCOMMAND messages
    HACCEL m_acceleratorTable = nullptr;  // Current accelerator table for this node
```

## -see-also
