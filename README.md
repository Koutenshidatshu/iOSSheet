
## Table of Contents


## UIKit
- [X] UIViewController
    > UIViewController class is a subclass of UIResponder, and the part of the MVC pattern. A View Controller manages a set of views and helps in making the application’s user interface. It coordinates with model objects and other controller objects. It is known for playing the role for both view objects and controller objects. Each view controller displays its own views for the app content. The views are loaded automatically when the user accesses the view property of view controller in the app. 

    > A view controller’s main responsibilities include the following:

    - Updating the contents of the views, usually in response to changes to the underlying data.

    - Responding to user interactions with views.

    - Resizing views and managing the layout of the overall interface.

    - Coordinating with other objects—including other view controllers—in your app.

### There are two types of view controllers:
1. Content view controllers manage a discrete piece of your app’s content and are the main type of view controller that you create.

2. Container view controllers collect information from other view controllers (known as child view controllers) and present it in a way that facilitates navigation or presents the content of those view controllers differently.
  
## Lifecycle events order: 
   - init(coder:)
   - (void)loadView
   - (void)viewDidLoad
   - (void)viewWillAppear
   - (void)viewDidAppear
   - (void)didReceiveMemoryWarning 
   - (void)viewWillDisappear 
   - (void)viewDidDisappear


 ### OS calls the UIViewController methods as follows:

`viewDidLoad()` Called when the view controller’s content view (the top of its view hierarchy) is created and loaded from a storyboard. The view controller’s outlets are guaranteed to have valid values by the time this method is called. Use this method to perform any additional setup required by your view controller.

Typically, iOS calls viewDidLoad() only once, when its content view is first created; however, the content view is not necessarily created when the controller is first instantiated. Instead, it is lazily created the first time the system or any code accesses the controller’s view property.

`viewWillAppear()`Called just before the view controller’s content view is added to the app’s view hierarchy. Use this method to trigger any operations that need to occur before the content view is presented onscreen. Despite the name, just because the system calls this method, it does not guarantee that the content view will become visible. The view may be obscured by other views or hidden. This method simply indicates that the content view is about to be added to the app’s view hierarchy.

`viewDidAppear()`Called just after the view controller’s content view has been added to the app’s view hierarchy. Use this method to trigger any operations that need to occur as soon as the view is presented onscreen, such as fetching data or showing an animation. Despite the name, just because the system calls this method, it does not guarantee that the content view is visible. The view may be obscured by other views or hidden. This method simply indicates that the content view has been added to the app’s view hierarchy.

`viewWillDisappear()`Called just before the view controller’s content view is removed from the app’s view hierarchy. Use this method to perform cleanup tasks like committing changes or resigning the first responder status. Despite the name, the system does not call this method just because the content view will be hidden or obscured. This method is only called when the content view is about to be removed from the app’s view hierarchy.

`viewDidDisappear()`Called just after the view controller’s content view has been removed from the app’s view hierarchy. Use this method to perform additional teardown activities. Despite the name, the system does not call this method just because the content view has become hidden or obscured. This method is only called when the content view has been removed from the app’s view hierarchy.

`didReceiveMemoryWarning()` Called when the parent application receives a memory warning. On iOS 6.0 it will no longer clear the view by default.



- [ ] UINavigationController
- [ ] UICollectionView
- [ ] UITableView
- [ ] UIStackView
- [ ] UIControl
- [ ] UIPageControl
- [ ] UISlider
- [ ] UIStepper
- [ ] UISearchTextField
- [ ] UISearchBar
- [ ] UIToolbar
- [ ] UITabBar
- [ ] UISegmentedControl
- [ ] Content Hugging Priority
- [ ] Content Compression Priority
- [ ] Safe Area
- [ ] Margins
- [ ] UIBounds
- [ ] UIFrame
- [ ] UIShadow
- [ ] UIRect
- [ ] UIBezierPath
- [ ] layoutSubViews
- [ ] setNeedsLayout
- [ ] layoutIfNeeded
- [ ] UIEvent
- [ ] UINib

  ## Swift

- [ ] Overloading
- [ ] Variadic Parameters
- [ ] Modifiable Parameters
- [ ] Function in Function
- [ ] Recursion
- [ ] Function as Value
- [ ] Anonymous Functions
- [ ] Define-and-Call
- [ ] Closures
- [ ] Function Returning Function
- [ ] Escaping Closures
- [ ] Curried Functions
- [ ] Selectors
- [ ] Computed Variable
- [ ] Computed Properties
- [ ] Property Wrappers
- [ ] Setter Observers
- [ ] Lazy Initialization
- [ ] Singleton
- [ ] Lazy Initialization of Instance Properties
- [ ] Character and String Index
- [ ] Range
- [ ] Tuple
- [ ] Optional
- [ ] Initializers
- [ ] Properties
- [ ] Methods
- [ ] Subscripts
- [ ] Nested Object Types
- [ ] Enums
- [ ] Raw Values
- [ ] Associated Values
- [ ] Struct as Namespace
- [ ] Value Types and Reference Types
- [ ] Subclass and Superclass
- [ ] Class Initializers
- [ ] Class Deinitializer
- [ ] Class Properties
- [ ] Static/Class Members
- [ ] Polymorphism
- [ ] Casting
- [ ] Bridging to Objective-C
- [ ] Type References
- [ ] From Instance to Type
- [ ] From self to Type
- [ ] Type as Value
- [ ] Summary of Type Terminology
- [ ] Comparing Types
- [ ] Protocols
- [ ] Protocol Type Testing and Casting
- [ ] Declaring a Protocol
- [ ] Protocol Composition
- [ ] Class Protocols
- [ ] Optional Protocol Members
- [ ] Implicitly Required Initializers
- [ ] Mutating Func
- [ ] Expressible by Literal
- [ ] Generic
- [ ] Type Constraints
- [ ] Explicit Specialization
- [ ] Generic Invariance
- [ ] Associated Type Chains
- [ ] Where Clauses
- [ ] Extensions
- [ ] Extending Protocols
- [ ] Extending Generics
