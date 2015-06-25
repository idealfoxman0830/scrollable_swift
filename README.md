# Scrolling content vertically in iOS with autolayout

This is a small iOS library that helps scrolling screen content vertically, similar to web browser scrolling.

<img src='https://raw.githubusercontent.com/exchangegroup/scrollable-content-ios/master/graphics/scrolling-content-vertically-autolayout-ios.png' width='320' alt='Scrolling content vertically with autolayout in iOS'>


## Setup

There are three ways you can add Scrollable to your Xcode project.

**Add source (iOS 7+)**

Simply add [ScrollableDistrib.swift](https://github.com/exchangegroup/Cosmos/blob/master/Distrib/CosmosDistrib.swift) file into your Xcode project.

**Setup with Carthage (iOS 8+)**

Alternatively, add `github "exchangegroup/Cosmos" ~> 1.0` to your Cartfile and run `carthage update`.

**Setup with CocoaPods (iOS 8+)**

If you are using CocoaPods add this text to your Podfile and run `pod install`.

    use_frameworks!
    pod 'Cosmos', '~> 1.0'

# Usage

1. Add a scroll view to your storyboard with necessary constraints
1. In storyboard, drag content views to the scroll view (labels, images etc.)
1. In storyboard, add autolayout constraints for the content views: top, bottom, leading and trailing.
1. From storyboard, create a `scrollView` outlet for the scroll view in your view controller.
1. In view controller's `viewDidLoad`, call:

```
Scrollable.createContentView(scrollView)
```

## How it works

`Scrollable.createContentView` function creates a **content view** and embeds all scroll view subviews in it.
Then it goes through all scroll view constraints and moves them into the **content view**.

## Troubleshooting

When creating autolayout constraint for content views please use numeric values for the `Constant` field. When I left it empty (`Standard`) it threw an exception:

```
Assertion failure in -[NSLayoutConstraint constant], /SourceCache/Foundation/Foundation-1047.25/Layout.subproj/NSLayoutConstraint.m:601
2014-11-28 11:53:27.816 scrolled-content[2821:60b] *** Terminating app due to uncaught exception 'NSInternalInconsistencyException', reason: '(null)'
```

## Attribution

Image of armadillo is made by [Adrián Rodríguez](http://www.freeimages.com/profile/neferto) and taken from [http://www.freeimages.com/photo/1339784](http://www.freeimages.com/photo/1339784).

## License

Scrollable is released under the [MIT License](LICENSE).
