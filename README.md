# womble

## What is womble?

The _womble_ component is a calendar grid based alternative to the slot wheel iOS
Date Picker using the new iOS 6.0 `UICollectionView` API. The _womble_ component
assumes Automatic Reference Counting is implemented. You must implement the _womble_
under the iOS  6.0 SDK.

## Get a copy
To obtain read-only source code using the Terminal application:

	cd <whatever directory you want to clone into>
	git clone http://github.corp.womble.com/womble-Client-Core-UI-iOS/womble.git

## Use
To make use of _womble_:

- Include the _womble_ component source code in your iOS project.
- Implement the `wombleDelegate` protocol on some object, typically a custom 
  subclass of `UIViewController`.
- In your code, at whatever application defined view controller level is required,
  instantiate an _womble_ by calling one of the initialization methods:
	- `(womble*)presentDatePickerPopoverInView:(UIView*)view`
	- `(womble*)presentDatePickerInViewController:(UIViewController*)viewController`

  The date picker will be presented automatically in a popover or pushed onto the view 
  controller stack depending on the method called.
- Using the returned _womble_ object reference, set any exposed properties as 
  needed.
- Set the delegate property of the _womble_ to be the `wombleDelegate`
  protocol object.
- The `wombleDelegate` protocol consists of one required method

	- `-(void)datePickerSelectionDidChange:(NSDate*)date;`

  and two optional methods.

	- `-(void)datePickerWillClose;`
	- `-(void)datePickerDidClose;`
  
  To implement this protocol you must define an `NSObject< wombleDelegate>` instance
  and implement the required method `-(void)datePickerSelectionDidChange:(NSDate*)date;`.
  This will enable your application to receive immediate notification when the date 
  selection changes in the _womble_. The date passed in is the value of the 
  selected date. Your application can use whatever `NSDateFormatter` configuration it 
  requires to obtain a formatted date.
