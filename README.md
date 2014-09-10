<img src="https://dl.dropboxusercontent.com/u/148921/assets/logo.svg" width="100" />

Adds animated GIF support to UIKit. For the Japanese prefecture, click [here](https://goo.gl/maps/CCeAc).

#### Why?

Because Apple's `+animatedImage*` sucks, and the few third party implementations that
got it right (see [Credits](#credits)) still require you to use a `UIImageView` subclass.

#### How?

Gifu is a `UIImage` subclass and `UIImageView` extension written in Swift.
It uses `CADisplayLink` to animate the view and only keeps a limited number of
frames in-memory, which exponentially minimizes memory usage for large GIF files (+300
frames).

The figure below summarizes how this works in practice. Given an image
containing 10 frames, Gifu will load the current frame (red), pre-load the next two frames in this example (orange),
and nullify all the other frames to free up memory (gray):

<img src="https://raw.githubusercontent.com/kaishin/gifu/master/figure.gif" width="300" />

#### Usage

Use git submodules or drag-and-drop the files in your Xcode project. I can't
believe I'm saying this in 2014.

Once done, you can call `setAnimatableImage(named:)` or
`setAnimatableImage(data:)` on your `UIImageView` (or its subclass):

```swift
let imageView = UIImageView(...)

imageView.setAnimatableImage(named: "computer-kid.gif")
// or
imageView.setAnimatableImage(data: NSData(...))
```

You can start/stop the animation using `UIImageView`'s `startAnimating()` and
`stopAnimating()`.

You can find a demo [here](https://github.com/kaishin/gifu/tree/demo) (requires Xcode 6 Beta-7).

<img src="https://raw.githubusercontent.com/kaishin/gifu/demo/demo.gif" width="300" />

#### Compatibility

- iOS 7+

#### Roadmap

The usual suspects:

- Add documentation.
- Write some basic tests.

Needless to say, you are welcome to contribute.

#### Credits

- The animation technique described above was originally spotted on
[OLImageView](https://github.com/ondalabs/OLImageView), then improved in [YLGIFImage](https://github.com/liyong03/YLGIFImage).

- The font used in the logo is [Azuki](http://www.myfonts.com/fonts/bluevinyl/azuki/)

- Kudos to my colleague [Tony DiPasquale](https://github.com/tonyd256) for helping out with the factory methods.

- The characters used in the icon and example image in the demo are from [Samurai Champloo](https://en.wikipedia.org/wiki/Samurai_Champloo). The name and characters are property of their respective owners.

#### License

See LICENSE.
