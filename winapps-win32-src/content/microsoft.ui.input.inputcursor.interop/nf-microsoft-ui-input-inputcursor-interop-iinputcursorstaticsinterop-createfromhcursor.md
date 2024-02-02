---
UID: NF:microsoft.ui.input.inputcursor.interop.IInputCursorStaticsInterop.CreateFromHCursor
tech.root: 
title: IInputCursorStaticsInterop::CreateFromHCursor
ms.date: 
targetos: Windows
description: 
prerelease: false
req.assembly: 
req.construct-type: function
req.ddi-compliance: 
req.dll: 
req.header: microsoft.ui.input.inputcursor.interop.h
req.idl: 
req.include-header: 
req.irql: 
req.kmdf-ver: 
req.lib: 
req.max-support: 
req.namespace: 
req.redist: 
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.target-type: 
req.type-library: 
req.umdf-ver: 
req.unicode-ansi: 
topic_type:
 - apiref
api_type:
 - COM
api_location:
 - microsoft.ui.input.inputcursor.interop.h
api_name:
 - IInputCursorStaticsInterop::CreateFromHCursor
f1_keywords:
 - IInputCursorStaticsInterop::CreateFromHCursor
 - microsoft.ui.input.inputcursor.interop/IInputCursorStaticsInterop::CreateFromHCursor
dev_langs:
 - c++
helpviewer_keywords:
 - CreateFromHCursor
---

## -description

Creates an [InputCursor](/windows/windows-app-sdk/api/winrt/microsoft.ui.input.inputcursor) from the provided cursor handle.

## -parameters

### -param cursor

Type: **HCURSOR**

A handle to the cursor.

### -param result

The [InputCursor](/windows/windows-app-sdk/api/winrt/microsoft.ui.input.inputcursor).

If *cursor* specifies a system cursor, an [InputSystemCursor](/windows/windows-app-sdk/api/winrt/microsoft.ui.input.inputsystemcursor) is created. Otherwise, an [InputCustomCursor](/windows/windows-app-sdk/api/winrt/microsoft.ui.input.inputcustomcursor) is created by copying the cursor.

## -returns

Type: **HRESULT**

If the function succeeds it returns **ERROR_SUCCESS**. Otherwise, the function returns an error code.

## -remarks

## -see-also
