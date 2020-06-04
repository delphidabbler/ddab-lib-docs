# Drop Files Components FAQ

This page has some frequently asked questions about the DelphiDabbler [Drop Files Components](http://www.delphidabbler.com/software/dropfiles). You can also try the components' documentation {TODO: Add link}.

## Contents

1. [How do I handle files dropped on a single component on my form?](#faq-1)
2. [Why don't the components accept drag and drop when using Vista?](#faq-2)
3. [The WinHelp help file doesn't work on Vista / Windows 7. Can you please convert to HTML Help?](#faq-3)
4. [The components don't seem to accept files dropped from Outlook. Is there any way to make that work?](#faq-4)
5. [Can the components filter a list of dropped components by file extension?](#faq-5)
6. [How do I filter a list of dropped files using a wildcard?](#faq-6)
7. [Where do I find drop files component examples?](#faq-7)
8. [Can the components handle file drops on an application minimised to the tray / notification area?](#faq-8)
9. [Can the components handle drag and drop onto frames?](#faq-9)
10. [Can I find out where files were dropped on a control?](#faq-10)

----

## FAQ 1

**How do I handle files dropped on a single component on my form?**

Use a `TPJCtrlDropFiles` component. Drop this on the same form as the control you want to drop files on and set the component's `ManagedControl` to reference the control. Any files dropped on the managed control will now be intercepted by the `TPJCtrlDropFiles` component and will trigger its `OnDropFiles` event, which you should then handle as normal.

## FAQ 2

**Why don't the components accept drag and drop when using Vista?**

For security reasons in Windows Vista and later, drag/drop is disallowed between windows with different security permissions. This means that applications that processes drag and drop may not be able to receive files dragged and dropped from another window if the security permissions are not compatible.

This is a "feature" of the operating system, not a problem with the components.

## FAQ 3

**The WinHelp help file doesn't work on Vista / Windows 7. Can you please convert to HTML Help?**

No, sorry. I've tried Microsoft's conversion utility which is difficult to use and it will take much too long to convert. I just don't have the time. Instead I've created some on-line Drop Files Components documentation {TODO: Link needed}

## FAQ 4

**The components don't seem to accept files dropped from Outlook. Is there any way to make that work?**

No. The components only accept files dragged and dropped from Windows Explorer. To change this would need a complete rewrite.

I suggest you look for code that supports OLE drag and drop.

## FAQ 5

**Can the components filter a list of dropped components by file extension?**

There are two ways to do this.

### Method 1

Handle the component's `OnFileFilter` event.

To accept only files with the '.myext' extension place the following code in the event handler.

```pascal
Accept := ExtractFileExt(FileName) = '.myext';
```

### Method 2

Use a `TPJExtFileFilter` component.

Drop one of these components on the form and assign a reference to it to the Drop Files Component's `Filter` property. Now set the `TPJExtFileFilter` component's `Extension` property to a semi-colon separated list of the extensions you want to accept, for example `'.txt;.htm;.html'`.

The associated drop files component will now accept only files with the specified extensions.

## FAQ 6

**How do I filter a list of dropped files using a wildcard?**

Use a `TPJWildCardFileFilter` component, set its `Wildcard` property to the required wildcard and assign the component to the appropriate Drop Files Component's `Filter` property.

Note that wild cards must conform to the DOS / Windows wild card specification.

## FAQ 7

**Where do I find drop files component examples?**

From v5.0 two demo / example projects have been included with the component download.

## FAQ 8

**Can the components handle file drops on an application minimised to the tray / notification area?**

No.

## FAQ 9

**Can the components handle drag and drop onto frames?**

Yes - use `TPJCtrlDropFiles` and set its `ManagedControl` property to reference the required frame.

## FAQ 10

**Can I find out where files were dropped on a control?**

Yes. All three drop files components expose a `DropPoint` property that gives you the x and y co-ordinates of the position the files were dropped.

For `TPJDropFiles` the position is relative to the client area of the control, for `TPJFormDropFiles` the position is in terms of the client area of the containing form and for `TPJCtrlDropFiles` the co-ordinates are relative to the managed control.
