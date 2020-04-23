# Menu

>Fully customizable macOS drop-down menu. It includes **30** settings you can play with.

![](screenshot1.png)

## Requirements

* Xcode 11+
* macOS 10.12+
* Swift 5.0 and higher

## Installation

Since this is a Swift Package, the installation process is pretty stright forward.

### Manual way
Update your `Package.swift` dependencies:

```
dependencies: [
    .package(url: "https://github.com/iSapozhnik/Menu", from: "1.0.8")
]
```

### Via Xcode:
1. Go to `File -> Swift Packages -> Add Package Dependency`. 
2. Put GitHub URL `https://github.com/iSapozhnik/Menu` and click `Next`
3. Select the latest version
4. Click `Finish`

## What can be customized? Everything!
```swift
public protocol Configuration {
    var titleBottomSpace: CGFloat                           { get }
    var titleFont: NSFont?                                  { get }
    var titleColor: NSColor                                 { get }
    var backgroundColor: NSColor                            { get }
    var cornerRadius: CGFloat                               { get }
    var hasShadow: Bool                                     { get }
    var appearsBelowSender: Bool                            { get }
    var animationDuration: TimeInterval                     { get }
    var contentEdgeInsets: NSEdgeInsets                     { get }
    var maximumContentHeight: CGFloat?                      { get }
    var separatorColor: NSColor                             { get }
    var separatorThickness: CGFloat                         { get }
    var separatorHorizontalPadding: Padding.Horizontal      { get }
    var separatorVerticlaPadding: Padding.Vertical          { get }
    var rememberSelection: Bool                             { get }
    var textAlignment: Alignment                            { get }
    var iconAlignment: Alignment                            { get }
    var menuItemFont: NSFont?                               { get }
    var menuItemHeight: CGFloat                             { get }
    var menuItemHoverBackgroundColor: NSColor               { get }
    var menuItemTextColor: NSColor                          { get }
    var menuItemHoverTextColor: NSColor                     { get }
    var menuItemCheckmarkColor: NSColor                     { get }
    var menuItemHoverCheckmarkColor: NSColor                { get }
    var menuItemCheckmarkHeight: CGFloat                    { get }
    var menuItemCheckmarkThikness: CGFloat                  { get }
    var menuItemImageHeight: CGFloat?                       { get }
    var menuItemImageTintColor: NSColor?                    { get }
    var menuItemHoverImageTintColor: NSColor?               { get }
    var menuItemHoverAnimationDuration: TimeInterval        { get }
}
```
## How to use

```swift
import Cocoa
import Menu

class ViewController: NSViewController {
    private let myMenu = Menu(with: "Select a search engine:")

    @IBOutlet var showMenuButton: NSButton!

    override func viewDidLoad() {
        super.viewDidLoad()

        let bing = MenuItem("Bing search", image: Icn.bing.image, action: { [weak self] in
            self?.showMenuButton.title = "Bing"
        })
        let item = MenuItem("DuckDuckGo search", image: Icn.duck.image, action: { [weak self] in
            self?.showMenuButton.title = "DuckDuckGo"
        })
        let google = MenuItem("Google search", image: Icn.google.image, action: { [weak self] in
            self?.showMenuButton.title = "Google"
        })
        let longText = MenuItem("Some very-very-very long text with no icon", action: { [weak self] in
            self?.showMenuButton.title = "Some very long text"
        })
        let emojiItem = MenuItem("Emojis are here 😎🚀", action: { [weak self] in
            self?.showMenuButton.title = "Emojis are here 😎🚀"
        })
        let exit = MenuItem("Exit", image: Icn.exit.image, action: {
            NSApplication.shared.terminate(nil)
        })
        let separator = MenuItem.separator()
        let menuItems = [
            bing,
            item,
            google,
            separator,
            longText,
            emojiItem,
            separator,
            exit
        ]

        myMenu.addItems(menuItems)
    }

    @IBAction func didClickedButton(_ sender: NSButton) {
        myMenu.show(from: sender)
    }
}
```

## Examples

In this section I've collected some examples of what can be i,plemented do using **Menu** control. On the left side some random example from Dribbble and on the right side my implementation.

| Dribbble      | Menu          | Code          |
| ------------- |:-------------:|:-------------:|
| [link](https://dribbble.com/shots/4233782-Snooze-notifications-in-Twist) | |
| ![](examples/twist.png)     | ![](examples/menu_twist.png) | |
| [link](https://dribbble.com/shots/7055473-Dropdowns) | | |
| ![](examples/example_0.png) | ![](examples/menu_0.png) | [code](examples/example.md) |

## Credits

Created and maintained by [**@iSapozhnik**](https://twitter.com/iSapozhnik).

## License

Released under the MIT License. See `LICENSE` for details.

>**Copyright &copy; 2020-present Sapozhnik Ivan.**

<!--
https://dribbble.com/shots/4953294-Daily-UI-Challenge-04-Dropdown-Menu

-->

<!--
https://dribbble.com/shots/7055473-Dropdowns
```
class Config: MenuConfiguration {
    override var cornerRadius: CGFloat {
        return 15.0
    }

    override var backgroundColor: NSColor {
        return NSColor(red: 63/255, green: 59/255, blue: 59/255, alpha: 1.0)
    }

    override var menuItemHoverBackgroundColor: NSColor {
        return NSColor(red: 86/255, green: 81/255, blue: 81/255, alpha: 1.0)
    }

    override var menuItemHoverCornerRadius: CGFloat {
        return 10
    }

    override var contentEdgeInsets: NSEdgeInsets {
        return NSEdgeInsets(top: 8, left: 16, bottom: 8, right: 16)
    }

    override var menuItemHeight: CGFloat {
        return 40.0
    }

    override var menuItemHoverEdgeInsets: NSEdgeInsets {
        return NSEdgeInsets(top: 0, left: 8, bottom: 0, right: 8)
    }
}
```-->

