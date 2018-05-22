---
title: Guarding Against Reentrancy in Hook Functions
description: While a hook function processes an event, additional events may be triggered, which may cause the hook function to reenter before the processing for the original event is finished.
ms.assetid: '2382e7a4-82df-423a-8479-66e28baf8105'
---

# Guarding Against Reentrancy in Hook Functions

While a hook function processes an event, additional events may be triggered, which may cause the hook function to reenter before the processing for the original event is finished. The problem with reentrancy in hook functions is that events are completed out of sequence unless the hook function handles this situation.

For example, consider a case where a hook function in a screen reader program is processing the [**EVENT\_OBJECT\_VALUECHANGE**](event-constants.md#event-object-valuechange) event for an edit control. If, while processing the first value change event the hook function is reentered to process a subsequent value change event, the second event is completed before the first event. This situation results in the screen reader conveying inaccurate information to the user.

Because event processing is interrupted, additional events might be received any time the hook function calls a function that causes the owning thread's message queue to get checked. This happens when any of the following are called within the hook function:

-   The Windows [**SendMessage**](https://msdn.microsoft.com/library/windows/desktop/ms644950), [**GetMessage**](https://msdn.microsoft.com/library/windows/desktop/ms644936), [**PeekMessage**](https://msdn.microsoft.com/library/windows/desktop/ms644943), [**DialogBox**](https://msdn.microsoft.com/library/windows/desktop/ms645452), or [**MessageBox**](https://msdn.microsoft.com/library/windows/desktop/ms645505) function
-   The Microsoft Active Accessibility functions [**AccessibleObjectFromEvent**](accessibleobjectfromevent.md), [**AccessibleObjectFromWindow**](accessibleobjectfromwindow.md), [**AccessibleObjectFromPoint**](accessibleobjectfrompoint.md)
-   An [**IAccessible**](iaccessible.md) interface or other Component Object Model (COM) property or method that crosses process boundaries

Because hook functions call [**AccessibleObjectFromEvent**](accessibleobjectfromevent.md) and [**IAccessible**](iaccessible.md) properties and methods, it is not possible to prevent reentrancy. The only solution is for client developers to add code in the hook function that detects reentrancy and take appropriate action if the hook function is reentered.

 

 



