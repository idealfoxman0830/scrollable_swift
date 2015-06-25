# Scrolling content vertically in iOS with Auto Layout

This is a small iOS library that helps scrolling screen content vertically, similar to web browser scrolling.

<img src='https://raw.githubusercontent.com/exchangegroup/scrollable-content-ios/master/graphics/scrolling-content-vertically-autolayout-ios.png' width='320' alt='Scrolling content vertically with autolayout in iOS'>


## Setup

There are three ways you can add Scrollable to your Xcode project.

**Add source (iOS 7+)**

Simply add [ScrollableDistrib.swift](https://github.com/exchangegroup/Scrollable/blob/master/Distrib/ScrollableDistrib.swift) file into your Xcode project.

**Setup with Carthage (iOS 8+)**

Alternatively, add `github "exchangegroup/Scrollable" ~> 1.0` to your Cartfile and run `carthage update`.

**Setup with CocoaPods (iOS 8+)**

If you are using CocoaPods add this text to your Podfile and run `pod install`.

    use_frameworks!
    pod 'Scrollable', '~> 1.0'

## Usage


1. Add `import Scrollable` to your code if you used Carthage or CocoaPods setup methods.
1. Add a scroll view to your storyboard with necessary constraints.
1. In storyboard, drag content views **to the scroll view** (your labels, images etc.).
1. Add Auto Layout constraints for all the content views. The trick is to make sure **all four sides of the scroll view** have layout constraints to the content views. This will make the scroll view content size expand according to the size of the content views.


<img src='https://raw.githubusercontent.com/exchangegroup/Scrollable/master/graphics/content_views_with_constraints.png' width='566' alt='Content views layout'>

#### Layout the scroll view content

1. From storyboard, create a `scrollView` outlet for the scroll view in your view controller.
1. Finally, in view controller's `viewDidLoad`, call:

```
Scrollable.createContentView(scrollView)
```

## How it works

`Scrollable.createContentView` function creates a **content view** and embeds all scroll view subviews in it.
Then it goes through all scroll view constraints and moves them into the **content view**.

## Troubleshooting

When creating Auto Layout constraint for content views please use numeric values for the `Constant` field. When I left it empty (`Standard`) it threw an exception:

```
Assertion failure in -[NSLayoutConstraint constant], /SourceCache/Foundation/Foundation-1047.25/Layout.subproj/NSLayoutConstraint.m:601
2014-11-28 11:53:27.816 scrolled-content[2821:60b] *** Terminating app due to uncaught exception 'NSInternalInconsistencyException', reason: '(null)'
```

## Attribution

Image of armadillo is made by [Adrián Rodríguez](http://www.freeimages.com/profile/neferto) and taken from [http://www.freeimages.com/photo/1339784](http://www.freeimages.com/photo/1339784).

## License

Scrollable is released under the [MIT License](LICENSE).
