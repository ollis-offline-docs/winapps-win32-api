---
UID: NF:microsoft.ui.input.inputpretranslatesource.interop.IInputPreTranslateKeyboardSourceHandler.OnDirectMessage
tech.root: uiinterop
title: IInputPreTranslateKeyboardSourceHandler::OnDirectMessage
ms.date: 02/15/2024
targetos: Windows
description: Handles keyboard input messages for pre-translate processing on element with current focus.
prerelease: false
req.assembly: 
req.construct-type: function
req.ddi-compliance: 
req.dll: 
req.header: microsoft.ui.input.inputpretranslatesource.interop.h
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
 - microsoft.ui.input.inputpretranslatesource.interop.h
api_name:
 - IInputPreTranslateKeyboardSourceHandler::OnDirectMessage
f1_keywords:
 - IInputPreTranslateKeyboardSourceHandler::OnDirectMessage
 - microsoft.ui.input.inputpretranslatesource.interop/IInputPreTranslateKeyboardSourceHandler::OnDirectMessage
dev_langs:
 - c++
helpviewer_keywords:
 - OnDirectMessage
---

# OnDirectMessage function

## -description

Handles keyboard input messages for pre-translate processing on element with current focus.

## -parameters

### -param source [in]

The keyboard input source.

### -param msg [in]

The keyboard input message.

### -param keyboardModifiers [in]

The collection of keyboard modifiers.

These are are a combination of flags that can hold the following values:

FVIRTKEY                0x0001      Message is WM_(SYS)KEYDOWN or WM_(SYS)KEYUP.
FSHIFT                  0x0004      VK_SHIFT is pressed.
FCONTROL                0x0008      VK_CONTROL is pressed (or VK_RCONTROL when the AltGr key is present and pressed).
FALT                    0x0010      VK_MENU is pressed (or VK_LMENU when the AltGr key is present and pressed).

### -param handled [in, out]

True, if message handled. Otherwise, false.

## -returns

This function has no return value.

## -remarks

## -see-also

[OnTreeMessage function](nf-microsoft-ui-input-inputpretranslatesource-interop-iinputpretranslatekeyboardsourcehandler-ontreemessage.md)
