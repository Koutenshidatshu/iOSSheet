
## Table of Contents


## UIKit
- [X] UIViewController
  
  UIViewController class is a subclass of UIResponder, and the part of the MVC pattern. A View Controller manages a set of views and helps in making the application’s user interface. It coordinates with model objects and other controller objects. It is known for playing the role for both view objects and controller objects. Each view controller displays its own views for the app content. The views are loaded automatically when the user accesses the view property of view controller in the app. 

     ### ViewController’s main responsibilities:

    - Updating the contents of the views, usually in response to changes to the underlying data.

    - Responding to user interactions with views.

    - Resizing views and managing the layout of the overall interface.

    - Coordinating with other objects—including other view controllers—in your app.

    ### There are two types of view controllers:
    - Content view controllers manage a discrete piece of your app’s content and are the main type of view controller that you create.
   -  Container view controllers collect information from other view controllers (known as child view controllers) and present it in a way that facilitates navigation or presents the content of those view controllers differently.
  
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
    `init(coder:)`While creating the views of your app in a Storyboard, init(coder:) is the method that gets called to instantiate your view controller and bring it to life. During the initial phase of a view controller, you usually allocate the resources that the view controller will need during its lifetime. In this method, you might instantiate dependencies, including subviews that you’ll add to your view programmatically. And note that init(coder:) is called only once during the life of the object, as all init methods are.

    `loadView()` It is only called when the view controller is created and only when done programatically. You can override this method in order to create your views manually. This is the method that creates the view for the view controller. If you are working with storyboards or nib files, then you do not have to anything with this method and you can ignore it. Its implementation in UIViewController loads the interface from the interface file and connects all the outlets and actions for you.

    `viewDidLoad()` Called when the view controller’s content view (the top of its view hierarchy) is created and loaded from a storyboard. The view controller’s outlets are guaranteed to have valid values by the time this method is called. Use this method to perform any additional setup required by your view controller.

    Typically, iOS calls viewDidLoad() only once, when its content view is first created; however, the content view is not necessarily created when the controller is first instantiated. Instead, it is lazily created the first time the system or any code accesses the controller’s view property.

    `viewWillAppear()`Called just before the view controller’s content view is added to the app’s view hierarchy. Use this method to trigger any operations that need to occur before the content view is presented onscreen. Despite the name, just because the system calls this method, it does not guarantee that the content view will become visible. The view may be obscured by other views or hidden. This method simply indicates that the content view is about to be added to the app’s view hierarchy.

    `viewDidAppear()`Called just after the view controller’s content view has been added to the app’s view hierarchy. Use this method to trigger any operations that need to occur as soon as the view is presented onscreen, such as fetching data or showing an animation. Despite the name, just because the system calls this method, it does not guarantee that the content view is visible. The view may be obscured by other views or hidden. This method simply indicates that the content view has been added to the app’s view hierarchy.

    `viewWillDisappear()`Called just before the view controller’s content view is removed from the app’s view hierarchy. Use this method to perform cleanup tasks like committing changes or resigning the first responder status. Despite the name, the system does not call this method just because the content view will be hidden or obscured. This method is only called when the content view is about to be removed from the app’s view hierarchy.

    `viewDidDisappear()`Called just after the view controller’s content view has been removed from the app’s view hierarchy. Use this method to perform additional teardown activities. Despite the name, the system does not call this method just because the content view has become hidden or obscured. This method is only called when the content view has been removed from the app’s view hierarchy.

    `didReceiveMemoryWarning()` Called when the parent application receives a memory warning. On iOS 6.0 it will no longer clear the view by default.

- [X] UINavigationController
    > A navigation controller is responsible for managing the navigation of hierarchical content. The navigation controller manages the current displayed screens using the navigation stack. At the bottom of this stack is the root view controller and at the top is the view controller currently displayed. You use methods to push and pop view controllers on and of the stack.

    ### What is a navigation stack?
    `“A navigation controller object manages its child view controllers using an ordered array, known as the navigation stack. The first view controller in the array is the root view controller and represents the bottom of the stack. The last view controller in the array is the topmost item on the stack, and represents the view controller currently being displayed.”`

- [X] UINib

    A object caches the contents of a nib file in memory.
    Nib files are the quintessential resource type used to create iOS and Mac apps. A nib file is a data archive that essentially contains a set of freeze-dried objects that you want to recreate at runtime. Nib files are used most commonly to store preconfigured windows, views, and other visually oriented objects but they can also store nonvisual objects such as controllers.

    One of the most important objects in a nib file is the File’s Owner object. Unlike interface objects, the File’s Owner object is a placeholder object that is not created when the nib file is loaded. Instead, you create this object in your code and pass it to the nib-loading code. The reason this object is so important is that it is the main link between your application code and the contents of the nib file. More specifically, it is the controller object that is responsible for the contents of the nib file.

    ### About the First Responder

    In a nib file, the First Responder is a placeholder object that represents the first object in your application’s dynamically determined responder chain.

    Each time you ask the NSBundle or NSNib class to load a nib file, the underlying code creates a new copy of the objects in that file


- [X] UITableView
  
    `UITableView` manages the basic appearance of the table, display a single column of vertically scrolling content.

    ### There are two protocols responsibilities in   `UITableView`:
   
   - `Data Source` provides data to the table view. Include thing like number of sections, the number of rows in each sections, title of section headers and footers and table view rows.
   - `Delegate` manage layout and data manipulation. Like height or the identation of cells, insert, delete, and re-ordering for each rows.

    `UITableViewDataSource` has two require protocols. 
    - `tableView(_:numberOfRowsInSection:)` method tells the table view how many elements a section contains.
    - `tableView(_:cellForRowAt:)` method needs to return configured cells for a specific row.

    `UITableViewDataSourcePrefetching` in iOS 10, Apple has introduced prefetching API prefetch data source, that enables table view’s data source to begin loading smoothly before `cellForRowAt` method called. This is useful for download large method obtain from disk / server. That also give some laziness in accesing data models.

    > set the view controller to table view prefetch 
    ```
    tableView.prefetchDataSource = self
    ```
    Initiate asynchronous loading for data required to specific index path.

    ```
    extension ViewController: UITableViewDataSourcePrefetching {
        func tableView(_ tableView: UITableView, prefetchRowsAt indexPaths: [IndexPath]) {
            print("prefetch Rows At \(indexPaths)")
    }
    ```
    Mechanism prefetch is When the user scrolls down, `tableView(_ tableView: UITableView, prefetchRowsAt indexPaths: [IndexPath]) `get’s called and index path holds for the next 10 rows. 


- [X] UICollectionView
  
    in iOS 10 `UICollectionViewDataSourcePrefetching` just like `UITableView`, collection view can implement smooth scrolling performance. 

    ### To implement Prefetch required 3 methods: 
    > collectionView(_:numberOfItemsInSection:)
    > collectionView(_:cellForItemAt:)
    > collectionView(_:prefetchItemsAt:)

    `UICollectionViewDataSourcePrefetching` contain two functions: 
    ```
    func collectionView(_ collectionView: UICollectionView, prefetchItemsAt     indexPaths: [IndexPath]) {
        print("prefetch Rows At \(indexPaths)")
    }
    ```

    ```
    func collectionView(_ collectionView: UICollectionView, cancelPrefetchingForItemsAt indexPaths: [IndexPath]) {
        print("prefetch Rows At \(indexPaths)")
    }
    ```

    `collectionView(_:cancelPrefetchingForItemsAt:)` this method to revert or clean up data source when prefetch for array of cells has been canclled by Collection View. Example when user change direction for scrolling.

- [x] UIStackView
  
    In iOS 9, The Advantage of `UIStackView` basically to simpler way to specify layout, like nested layout. 
    ### Cool things in UIStackView

    > `arrangedStackView` it's kind of hearts of `UIStackView`, it's array of UI views and it's represent the items that are in stack. 

    > `layoutMargins` control the margins around the edges of the stack. But need to change `isRelatedLayoutMargins` set to `true` to configure this method. 

    > `distribution: UIStackViewDistribution` control of arranged subviews along the stack derection of the axis.

    > Changing Content Dynamiclly
    - stack view automatically updates it's layout vased on content changes, like add or remove arranged subviews. 
    - Properties can be changed at run time to allow dynamic changes.
    -  And `isHidden` properly has to special for arranged subviews, that effects to the items arranged subviews. 
  

    ### UIStackView with Auto Layout

    It's work seamlessly, because actually creating auto layout constraints internally.

    `backgroundColor` property has no effect on `UIStackView`, because it's always is a clear color and because `UIStackView`
    doesn't render itself, it's only layout it's sub views.

    `drawRect()` doesn't ever called on it, it will no effect. Just like rounded corner and line corner. 

    `setCustomSpacing()` in iOS 11 can set custom spacing between different views in the stack, this useful when using custom in stackview.


- [X] UIControl

    Features of controls system views as controls are button, switch, slider, page control, date picker, segmented control and stepper. This class inherites from `UIView`.

    ### Target Action
    Control have various states and change visually according to the state. And it generates various events according to the touch type.

    `addTarget(_:action:for: )`
    thi method receives the object that the method is implemented as first paramater. The action paramater is implemented as a selector signature matches any of the signature and cannot be nil. Selector is a concept used in Object c. It's described as a message that can be send to an object or class.
    Example: 
    ```
    @objc func action(_ sender: Any) {

    }
    ```
    ```
    let selector = #selector(action(_:))
    btn.addTarget(self, action: selector, for: .touchUpInside)
    ```

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

  ## Swift

- [X] Callback function to send a completion handler

    This function is useful to tell whatever is calling that function to perform something or give some data. 
    ### Example : 

    ```
    func dataTask(with request: URLRequest,
        completionHandler: @escaping (Data?, URLResponse?, Error?) -> Void)
        -> URLSessionDataTask {
        // make an URL request
        // wait for results
        // check for errors and sometginf
        completionHandler(data, response, error)
        // return the data task
    }
    ```

    In the argument for callback is a closure `(Data?, URLResponse?, Error?)`
    and return void

    ```
    let task = urlSession.dataTask(with: urlRequest, completionHandler: {
        (data, response, error) in
        // this is where the completion execute the data
    })
    task.resume()
    ```

    ### And simpler way to call function

    if a closure in the last argument, can using trailing closure syntax and way simpler. 

    ```
    let task = session.dataTask(with: urlRequest) {
        (data, response, error) in
        // this is where the completion handler execute the data
    }
    task.resume()
    ``` 

    When we call the method and we need to execute the something or need to wait method to process, the way is using complete handler, then the code will called completion handler. Best way using completion handler is for asynchronous call,by the using we fire the the network call and not to wait around for these response, when network call is done, the completion handler quickly excalate to notify. So we can doing something after that. 
    another example in Apple OS SDK:

   `(void)animateWithDuration:(NSTimeInterval)duration 
                 animations:(void (^)(void))animations 
                 completion:(void (^)(BOOL finished))completion;`

    > Animate changes to one or more views using the specified duration and completion handler. Completion A block object to be executed when the animation sequence ends. This block has no return value and takes a single Boolean argument that indicates whether or not the animations actually finished before the completion handler was called. If the duration of the animation is 0, this block is performed at the beginning of the next run loop cycle. This parameter may be NULL.


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
