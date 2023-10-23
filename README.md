# Android Interview
## GIT
```
      A---B---C topic
     /
D---E---F---G master
```
### Git Rebase
```
              A'--B'--C' topic
             /
D---E---F---G master
```
### Git Cherry pick
```
      A---B---C topic
     /
D---E---F---G master
             \
              A'--B'--C' topic_new
```

###  What is an activity?
- Activity in java is a single screen that represents GU- Graphical   User Interface) with which users can interact in- rder to do  something like dial the phone, view email, etc.

### What is a service in Android?
- Service is an application component that facilitates - anapplication     to run in the background in order to - performlong-running operations    without user interaction. A - servicecan run continuously in the    background even if the - applicationis closed or even after the user    switches to - anotherapplication
### Differentiate Activities from Services:
- Activities
    - They are designed to run in the foreground
    - Used when the user interface is necessary.
    - They are dependent.
- Services
  - These are mainly designed to run in the background. Foreground services are also available.
  - Used when the user interface is not necessary.
  - They act independently.

### What is the use of Bundle in Android?
- Bundles are used to pass the required data between various Android activities. These are like HashMap that can take trivial data types. Below code shows how to transfer a piece of data by using bundle:
```
Bundle b=new Bundle();
b.putString("Email","abc@xyz.com");
i.putExtras(b); // where i is intent
```
### What is an Adapter in Android?
- An adapter in Android acts as a bridge between an AdapterView and the underlying data for that view. The adapter holds the data and sends the data to the adapter view, the view can take the data from the adapter view and shows the data on different views like a spinner, list view, grid view, etc
### What is AAPT?
- AAPT stands for Android Asset Packaging Tool. It is a build tool that gives the ability to developers to view, create, and update ZIP-compatible archives (zip, jar, and apk). It parses, indexes, and compiles the resources into a binary format that is optimized for the platform of Android
  
### What is Android Debug Bridge(ADB)?
- Android Debug Bridge is a command-line tool used to allow and control communication with an emulator instance. It gives the power for developers to execute remote shell commands to run applications on an emulator.
### What is DDMS?
- DDMS(Dalvik Debug Monitor Server) is a debugging tool in the Android platform. It gives the following list of debugging features:
  - Port forwarding services.
  - Thread and heap information.
  - Logcat.
  - Screen capture on the device.
  - Network traffic tracking.
  - Incoming call and SMS spoofing.
  - Location data spoofing.
### What is AIDL? Which data types are supported by AIDL?
- AIDL(Android Interface Definition Language) is a tool that handles the interface requirements between a client and a service for interprocess communication(IPC) to communicate at the same level.

- The process involves dividing an object into primitives that are understood by the Android operating system. Data Types supported by AIDL is as follows:
    - String
    - List
    - Map
    - CharSequence
    - Java data types (int, long, char, and boolean)
### What is the life cycle of Android activity?
- **OnCreate()**: It is called when activity is created. Using this,the views are created and data is collected from bundles.
- **OnStart()**: It is called if the activity is becoming visible tothe user. It may be succeeded by onResume() if the activity comesto the foreground, or onStop() if it becomes hidden.
- **OnResume()**: It is called when the activity will start aninteraction with the user.
- **OnPause()**: This is called when the activity is moving to thebackground but hasn’t been killed yet.
- **OnStop()**: This is called when an activity is no longer visible tothe user.
- **OnDestroy()**: This is called when the activity is finished ordestroyed.
- **OnRestart()**: This is called after the activity has been stopped,prior to it being started again.
### What is Fragment and its lifecycle.
- **CREATED**
    - onCreate()
    - onCreateView()
    - onViewCreated()
    - onViewStateRestored()
- **STARTED**
    - onStart()
- **RESUMED**
    -  onResume()
- **STARTED**
    -  onPause()
- **CREATED**
    -  onStop()
### When only onDestroy is called for an activity without onPause() and onStop()?
-   When we call finish method

### What is onSavedInstanceState() and onRestoreInstanceState() in activity?
- onSavedInstanceState() - This method is used to store data before pausing the activity.
- onRestoreInstanceState() - This method is used to recover the saved state of an activity when the activity is recreated after destruction. So, the onRestoreInstanceState() receive the bundle that contains the instance state information.


### Difference between FragmentPagerAdapter vs FragmentStatePagerAdapter?
- FragmentPagerAdapter: Each fragment visited by the user will be stored in the memory but the view will be destroyed. When the page is revisited, then the view will be created not the instance of the fragment.
- FragmentStatePagerAdapter: Here, the fragment instance will be destroyed when it is not visible to the user, except the saved state of the fragment.

### Explain the dialog boxes supported on Android.
-   AlertDialog
-   DatePickerDialog
-   TimePickerDialog
-   ProgressDialog
### What is AndroidManifest.xml file and why do you need this?
- The AndroidManifest.xml file contains information regarding the application that the Android system must know before the codes can be executed.
- This file is essential in every Android application.
- It is declared in the root directory.
- This file performs several tasks such as:
    - Providing a unique name to the java package.
    - Describing various components of the application such as activity, services, and many more.
    - Defining the classes which will implement these components

### What is an intent?
- An intent is a messaging object that is used to request an action from other components of an application. It can also be used to launch an activity, send SMS, send an email, display a web page, etc.
- It shows notification messages to the user from within an Android-enabled device. It alerts the user of a particular state that occurred. There are two types of intents in Android:
    - Implicit Intent- Used to invoke the system components.
    - Explicit Intent- Used to invoke the activity class.

### Difference between Implicit and Explicit Intent.
- Explicit Intent:
    - An Explicit Intent is where you inform the system about which activity should handle this intent. Here target component is defined directly in the intent.
        ```
        Intent i = new Intent(this, Activitytwo.class); #ActivityTwo is the target component
        i.putExtra("Value1","This is ActivityTwo"); 
        i.putExtra("Value2","This Value two for ActivityTwo"); 
        startactivity(i);
        ```
        
- Implicit Intent:
  - An Implicit Intent permits you to declare the action you want to carry out. Further, the Android system will check which components are registered to handle that specific action based on intent data. Here target component is not defined in the intent.
    ```
    Intent i = new Intent(ACTION_VIEW,Uri.parse("http://www.interview bit.com")); 
    startActivity(i);
    ```
## Services
### Started Services:
### Bound Services:
### Intent Services:
### Foreground Services:

## WorkManager
```
class MyWorker(context: Context, workerParams: WorkerParameters) : Worker(context, workerParams) {
    override fun doWork(): Result {
        return Result.success()
    }
}

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        val myWorkRequest = OneTimeWorkRequestBuilder<MyWorker>().build()
        WorkManager.getInstance(this).enqueue(myWorkRequest)
    }
}

```
### What is context?
- The context in Android is the context of the current state of the application or object. The context comes with services like giving access to databases and preferences, resolving resources, and more.

There are two types of context. They are:
- Activity context
    - 
    This activity context is attached to the lifecycle of an activity.
    The activity context can be used when you are passing the context in the scope of an activity or you need the context whose lifecycle is attached to the context of the activity.
- Application context:
    -
    This application context is attached to the lifecycle of an application.
    The application context should be used where you need a context whose lifecycle is separate from the current context or when you are passing a context beyond the scope of activity.

### What is ANR in Android? What are the measures you can take to avoid ANR?
- ANR(Application is Not Responding) is a dialog box that appears when the application is not responding. This ANR dialogue is displayed whenever the main thread within an application has been unresponsive for a long time under the following conditions:
    - When there is no response to an input event even after 5 seconds.
    - When a broadcast receiver has not completed its execution within 10 seconds.

Following measures can be taken to avoid ANR:
  - An application should perform lengthy database or networking operations in separate threads to avoid ANR.
- For background task-intensive applications, you can lessen pressure from the UI thread by using the IntentService.
### What are broadcast receivers? How is it implemented?
- A broadcast receiver is a mechanism used for listening to system-level events like listening for incoming calls, SMS, etc. by the host application. It is implemented as a subclass of BroadcastReceiver class and each message is broadcasted as an intent object.
```
public class MyReceiver extends BroadcastReceiver 
{
    public void onReceive(context,intent){}
}
```
### What is the difference between Serializable and Parcelable? Which is the best approach in Android?
- While developing applications usually it needs to transfer data from one activity to another. This data needs to be added into a corresponding intent object. Some additional actions are required to make the data suitable for transfer. For doing that the object should be either serializable or parcelable.
    - Serializable:
      - Serializable is a standard Java interface. In this approach, you simply mark a class Serializable by implementing the interface and java will automatically serialize it.
    Reflection is used during the process and many additional objects are created. This leads to plenty of garbage collection and poor performance
    - Parcelable:
      - Parcelable is an Android-specific interface. In this approach, you implement the serialization yourself.
      - Reflection is not used during this process and hence no garbage is created.
      - Parcelable is far more efficient than Serializable since it gets around some problems with the default Java serialization scheme. Also, it is faster because it is optimized for usage on the development of Android, and shows better results.

### What are the differences between Service and Thread?
- Service
  - Service is an application component that facilitates an application to run in the background in order to perform long-running operations without user interaction. 
  - It exposes few functionalities to other applications by calling Context.bindService().
  - When an application is killed, service is not killed.
- Thread
  - A Thread is a concurrent unit of execution.
  - Google has brought in handlers and loopers into threads.
  - When an application is killed, the thread is killed.
### What is the content provider? How it is implemented?
- Content provider is one of the primary building blocks of Android applications, which manages access to a central repository of data. It acts as a standard interface that connects data in one process with code running in another process. So it can be used to share the data between different applications.

- They are responsible for encapsulating the data and providing mechanisms for defining data security. It is implemented as a subclass of ContentProviderclass and must implement a set of APIs that will enable other applications to perform transactions
    ```
    public class MyContentprovider extends ContentProvider 
    {
     public void onCreate(){}
    }
    ```
### What is the significance of the .dex file?
- Android programs are compiled into a .dex file (Dalvik Executable file) by DVM, which are then zipped into a .apk file on the device. .dex files are created by translating compiled applications written in java. .dex is a format that is optimized for effective storage and memory-mappable executions.

### What is the difference between compileSdkVersion and targetSdkVersion?
- compileSdkVersion:
    - The compileSdkVersion is the version of API the application is compiled against. You can use Android API features involved in that version of the API (as well as all previous versions).
    - For example, if you try and use API 15 features but set compileSdkVersion to 14, you will get a compilation error. If you set compileSdkVersion to 15 you can still run the app on an API 14 device as long as your app’s execution paths do not attempt to invoke any APIs specific to API 15.

- targetSdkVersion:
  - The targetSdkVersion indicates that you have tested your app on (presumably up to and including) the version you specify. This is like a certification or sign-off you are giving the Android OS as a hint to how it should handle your application in terms of OS features.
  - For example, setting the targetSdkVersion value to “11” or higher permits the system to apply a new default theme (Holo) to the application when running on Android 3.0 or higher. It also disables screen compatibility mode when running on larger screens (because support for API level 11 implicitly supports larger screens)
### What is JobScheduler?
- The JobSchedular API is used for scheduling different types of jobs against the framework that will be executed in your app’s own process. This allows your application to perform the given task while being considerate of the device’s battery at the cost of timing control.

- The JobScheduler supports batch scheduling of jobs. The Android system can combine jobs for reducing battery consumption. JobManager automatically handles the network unreliability so it makes handling uploads easier.

- Here is some example of a situation where you would use this job scheduler:
  -  Tasks that should be done when the device is connected to a power supply.
   - Tasks that require a Wi-Fi connection or network access.
    - Tasks should run on a regular basis as a batch where the timing is not critical.


### some questions:
 1. API stands for  (Application Programming Interface  )
 2. What is an interface in Android?  (It acts as a bridge between class and the outside world. )
 3. What does Manifest.xml in Android consist of?  (Has all of the information about an application.)
 4. (Android Inc. ) has developed the Android.
 5. What is JNI in Android?  (Java Native Interface)
 6. Android web browser is based on  (Open-source webkit )
 7. After installation on a device, each Android application lives in  (Security sandbox)?


## Scope of coroutine
- Global Scope
- LifeCycle Scope
- ViewModel Scope

# Coroutines
## Coroutine Concepts:
- Scope
- suspending functions
- jobs
- context
- Dispatcher
- error handling

## Coroutine Builders:
- launch{} --> generate job
- async{} --> return deffered

**GlobalScope:**
the scope of the coroutine is the lifecycle of the entire application
```
GlobalScope.launch {
    delay(4000)
    println("word")
}
```

**SimpleCoroutine:**
```
runBlocking {
    repeat(1_000_000) { 
        launch {
            println(".")
        }
    }
}
```

**CoroutineScope:**
```
runBlocking {
    coroutineScope {
        delay(1000L)
        println("")
    }
}
```

## Context
- Dispatcher: which thread the coroutine is run on 
- Job: handle on the coroutines
```
    runBlocking {
        launch(CoroutineName("myCoroutine")) {
            println("This is run from
            ${coroutineContext[CoroutineName.Key]}")
        }
    }
```


## withContext
- Allow us to easily change context
- Easily switch between dispatchers
```
    runBlocking {
        launch(Dispatchers.Default) {
            println("first context")
            withContext(Dispatchers.IO) {
                println("second context")
            }
            println("third context")
        }
    }

    // first context [StandaloneCoroutine{Active}@4f9fcd95, Dispatchers.Default]
    // second context[DispatchedCoroutine{Active}@45e6de7c, Dispatchers.IO]
    // third context[StandaloneCoroutine{Active}@4f9fcd95, Dispatchers.Default]

```

## Suspending function:
- make callbacks seamless
```
fun main() {
    GlobalScope.launch {
        seyHello()
    }
}
suspend fun seyHello() {
    println("Hello")
}
```
## Jobs
- A hanlde on the coroutine
- A.launch() call return a Job
- Live in the hierachy of other Jobs both as parents or childer
- can access lifecycle variables and methods
    - cancel()
    - join()
- if a job is cancelled, all its parents and children will be cancelled too


## Dispatchers:
**A dispatcher determines which thread or thread pool the coroutine runs on**

**Different dispatcher are available depending on the task specificity**
- Main
    - main thread update in ui 
    - main dispatcher needs to be defined in gradle
- Default
    - useful for network communication or reading/writing files
- Unconfined
    - starts the corotine in the inherited dispatcher that called it
```
fun main() {
    runBlocking {
        launch(Dispatchers.Unconfined) {
            println("Unconfined 1 ${Thread.currentThread().name}")
            delay(100L)
            println("Unconfined 2 ${Thread.currentThread().name  }")
        }
        launch(Dispatchers.Default) {
            println("Default")
        }
        launch(Dispatchers.IO) {
            println("IO")
        }
        launch(newSingleThreadContext("My Thread")) {
            println("new Single Thread context")
        }
    }
}

// Unconfined 1 main
// Default
// IO
// new Single Thread context
// Unconfined 2 kotlinx.coroutines.DefaultExecutor
```

- the point is in  **Unconfined** Dispatcher change the current thread to another inherited thread. 


## async
- just like launch, except it return a result
- in the form of a deferred
- Deferred - afutute promise of returned value
- when we need the value, we call await()
    - if the value  is available, it will return immediately
    - if the value is not available, it will pause the thread until it is

```
fun main() {
    runBlocking {
        val first = async { getFirstValue() }
        val second = async { getSecondValue() }


        println("Doing some")
        delay(500L)
        println("Waiting for values")


        val firstValue = first.await()
        val secondValue = second.await()

        println("The total is ${firstValue + secondValue}")
    }
}

suspend fun getFirstValue(): Int {
    delay(1000L)
    val nextInt = Random.nextInt(100)
    println(nextInt)
    return nextInt
}


suspend fun getSecondValue(): Int {
    delay(2000L)
    val nextInt = Random.nextInt(1000)
    println(nextInt)
    return nextInt
}
```

### withContext in Kotlin Coroutines

```
// kotlin function using async
private suspend fun doTaskOne(): String{
    delay(2000)
    return "One"
}

private suspend fun doTaskTwo(): String{
    delay(2000)
    return "Two"
}
```
```
// kotlin function using withContext
fun startLongRunningTaskInParallel(){
  viewModelScope.launch{
    val resultOneDeferred = async { TaskOne() }
    val resultTwoDeferred = async { TaskTwo() }
    val combinedResult = resultOneDeferred.await() + resultTwoDeferred.await()
  }
}
```
```
fun testWithContext{
  var resultOne = "GFG"
  var resultTwo = "Is Best"
  Log.i("withContext", "Before")
  resultOne = withContext(Dispatchers.IO) { function1() }
  resultTwo = withContext(Dispatchers.IO) { function2() }
  Log.i("withContext", "After")
  val resultText = resultOne + resultTwo
  Log.i("withContext", resultText)
}
 
suspend fun function1(): String{
  delay(1000L)
  val message = "function1"
  Log.i("withContext", message)
  return message
}
 
suspend fun function2(): String{
  delay(100L)
  val message = "function2"
  Log.i("withContext", message)
  return message
}
```



## Launch vs Async in Kotlin Coroutines
- Launch Function
    - The launch will not block the main thread, but on the other hand, the execution of the rest part of the code will not wait for the launch result since launch is not a suspend call. Following is a Kotlin Program Using Launch:

```
        fun GFG()
        {
            var resultOne = "Android"
            var resultTwo = "Kotlin"
            Log.i("Launch", "Before")
            launch(Dispatchers.IO) { resultOne = function1() }
            launch(Dispatchers.IO) { resultTwo = function2() }
            Log.i("Launch", "After")
            val resultText = resultOne + resultTwo
            Log.i("Launch", resultText)
        }
        
        suspend fun function1(): String
        {
            delay(1000L)
            val message = "function1"
            Log.i("Launch", message)
            return message
        }
        
        suspend fun function2(): String
        {
            delay(100L)
            val message = "function2"
            Log.i("Launch", message)
            return message
        }
```


## Exception Handling
- launch
- async

for example:
```
val myHandle=CoroutineExceptionHandler{
coroutineContext,throwable->
    // handle exception    
}

launch(myHandler){
    // do some task here
    throw IndexOutOfBoundException()
}


launch(Dispatchers.Default+myHandler){
    // do some task here
    throw IndexOutOfBoundException()
}
```
----------------------------------------------------------------
# Algoithms -  BigO
- Theoretical definition of the compolexity of an algorithm as a function of the size.
- O => Order of magnitude of complexity
- n => A function of the size

## Linear Search . O(n)
## Binary Search . O(log n)
### O(n)
- there is no difference between O(n) and O(2n) or O(10000n) all is going to => o(n)
- that means we drop constant

```
fun printItems(n: Int) {
    for (i in 0..n) {
        println(n)      // O(n)
    }
    for (i in 0..n) {
        println(n)      // O(n)
    }
}
```
- O(2n) --> O(n)


### O(n2)
- theres is no difference between O(n2) and O(n1000) all is going to => O(n2)

### O(n2 + n)
- in this case turns to O(n2)

### O(1)

```
fun addItem(n: Int): Int {
    return n + n + n ....
}
```
### binary search
in this list 1,2,3,4,5,6,7,8
- we can use this method to find number 1
- 1,2,3,4   5,6,7,8
- 1,2    3,4
- 1   2
- 1

we need to split list from middle 
```
fun binarySearch(list: List<Int>, target: Int): Int? {
    var left = 0
    var right = list.size - 1

    while (left <= right) {
        val middle = (left + right) / 2
        when {
            list[middle] == target -> return middle
            list[middle] < target -> left = middle + 1
            else -> right = middle - 1
        }
    }
    return null
}
fun main() {
    val listOf = listOf<Int>(1, 2, 3, 4, 5, 6, 7, 8)
    println(binarySearch(listOf, 5)) ==> // 4 , index of number 5
}

```

### O(a) , O(b) 

```
fun printItems(a: Int, b: Int) {
    for (i in 0..a) {
        println(a)          // O(a)
    }
    for (i in 0..b) {
        println(b)          // O(b)
    }
}
```

it's not O(n+n) = O(2n) = O(n)
its O(a+b)

**inside to gether**
```
fun printItems(a: Int, b: Int) {
    for (i in 0..a) {
        for (i in 0..b) {
            println(a+b)        // O(a*b)
        }
    }
}
```

## BigO in Array

in this list=[11,2,3,24]

**O(1)**
- for adding item:
    - list.add(15) ==> [11,2,3,23,15] ---> O(1)
    - list.remove(15) ==> [11,2,3,23,15] ---> O(1)
  
**O(n)**
- for reIndexing item in lists
    - list.add(0,15) ==> [15,11,2,3,23] 
    - list.remove(15) ==> [15,11,2,3,23]

 its make O(n) , bcs every index going to replce each other
 
 another way to say that, is when we want find by number is O(n)

 but when we want to find number by index is O(1)


 ## Wrap Up

  **O(n2)** ==> loop within a Loop

  **O(n)** ==> Proportional

  **O(log n)** ==> Divide and Conquer

  **O(1)** ==> Constant



  # LinkedList


  read, add and delete is O(n)


# Stack
LIFO : last in first out

```
class Stack(value: Int) {
    private var top: Node
    private var height: Int

    internal inner class Node(var value: Int) {
        var next: Node? = null
    }

    init {
        val newNode = Node(value)
        top = newNode
        height = 1
    }

    fun printStack() {
        var temp: Node? = top
        while (temp != null) {
            println(temp.value)
            temp = temp.next
        }
    }
    fun getTop() {
        println("Top ${top.value}")
    }

    fun getHeight() {
        println("Height $height")
    }
}
```

this is simple sample stack

for pushing item into stack

```
    fun push(value: Int) {

        var temp: Node = Node(value)
        if (height == 0) top = temp
        else {
            temp.next = top;top = temp
        }
        height++
    }
```

for pop stack
```
    fun pop(): Node? {
        if (height == 0) return null
        val temp = top
        top = top.next!!
        temp.next = null
        height--
        return temp
    }
```


# Tree
                                47
                21                              76
        18              27              52              82
    12      20      25      30      49      63      78      91


**Tree is O(log n)** and its so efficient
but someTtimes its going like this:

        47
            76
                82
                    91


in this way its like LinkedList and its **O(n)**

so for lookup(),insert(),remove() tree is **O(log n)**

for comparistion linkedList :

        head            tail
        ||              ||
        47==>76==>82==>92==> NULL


### lookup():
for example lookup 92 : 
- we should start from 47 until 92, so its **O(n)** in linkedList
- but in binarySearchTree is **O(log n)**
- so for like this binarySeach better than linkedList
### remove():
for example remove 92:
- in linkedList we should itearate all the index to find 92 so its **O(n)**
- but in binarySearch its just **O(log n)**
### insert():

        head                tail
        ||                  ||
        47==>76==>82==>92==>78==>null

for insert() is actully faster with a linkedList, and thats bcs we just need to add to the end,

so its **O(1)** but in binary Seach Tree is **O(log n)**

**in this case arrayList act like linkedList**

constructor:
```
class Tree {
    var root: Node? = null

    inner class Node private constructor(var value: Int) {
        var left: Node? = null
        var right: Node? = null
    }
}
```
insert:

```
    fun insert(value: Int): Boolean {
        val newNode = Node(value)
        if (root == null) {
            root = newNode
            return true
        }
        var temp = root
        while (true) {
            if (newNode.value == temp!!.value) return false
            if (newNode.value < temp.value) {
                if (temp.left == null) {
                    temp.left = newNode
                    return true
                }
                temp = temp.left
            } else {
                if (temp.right == null) {
                    temp.right = newNode
                    return true
                }
                temp = temp.right
            }
        }
    }

```


# Kotlin
## Scope Function
    - apply,with,run,let,also

    - apply returns the receiver
    - with  returns a result of the last expression whithin its block. 



# Android Architecture
- MVP:

    - Model: The Model represents the data and business logic of the application. It encapsulates the data sources, such as databases, network requests, or local storage, and handles data manipulation and retrieval. The Model component is responsible for providing the necessary data to the Presenter.

    - View: The View represents the user interface of the application. In Android, it typically consists of Activities, Fragments, or custom Views. The View is responsible for displaying data to the user and capturing user interactions. However, it should not contain any business logic. Instead, it delegates user actions to the Presenter.

    - Presenter: The Presenter acts as a middleman between the Model and the View. It receives user input from the View and interacts with the Model to retrieve or manipulate data. The Presenter then updates the View based on the data received from the Model. It separates the logic of handling user interactions from the UI components, making the application easier to test and maintain.


    # Context Receivers


## Design Pattern
### Builder
    ```
    class Car(builder: Builder) {
    private val color: String
    private val brand: String
    private val model: String
    private val year: Int

    init {
        color = builder.color
        brand = builder.brand
        model = builder.model
        year = builder.year
    }

    class Builder {
        var color: String = ""
        var brand: String = ""
        var model: String = ""
        var year: Int = 0

        fun setColor(color: String): Builder {
            this.color = color
            return this
        }

        fun setBrand(brand: String): Builder {
            this.brand = brand
            return this
        }

        fun setModel(model: String): Builder {
            this.model = model
            return this
        }

        fun setYear(year: Int): Builder {
            this.year = year
            return this
        }

        fun build(): Car {
            return Car(this)
        }
    }
}
val car = Car.Builder()
    .setColor("Red")
    .setBrand("Toyota")
    .setModel("Camry")
    .setYear(2022)
    .build()
    ```
### Factory
```
bstract class Vehicle {
    abstract fun start()
    abstract fun stop()
}

class Car : Vehicle() {
    override fun start() {
        println("Car started.")
    }

    override fun stop() {
        println("Car stopped.")
    }
}

class Bike : Vehicle() {
    override fun start() {
        println("Bike started.")
    }

    override fun stop() {
        println("Bike stopped.")
    }
}

class VehicleFactory {
    fun createVehicle(type: String): Vehicle {
        return when (type) {
            "car" -> Car()
            "bike" -> Bike()
            else -> throw IllegalArgumentException("Invalid vehicle type.")
        }



val factory = VehicleFactory()

val car = factory.createVehicle("car")
car.start() // Output: Car started.
car.stop()  // Output: Car stopped.

val bike = factory.createVehicle("bike")
bike.start() // Output: Bike started.
bike.stop()  // Output: Bike stopped.
```
### Observer
```
interface Observer {
    fun update(data: Any)
}
class Subject {
    private val observers: MutableList<Observer> = mutableListOf()

    fun attach(observer: Observer) {
        observers.add(observer)
    }

    fun detach(observer: Observer) {
        observers.remove(observer)
    }

    fun notifyObservers(data: Any) {
        for (observer in observers) {
            observer.update(data)
        }
    }
}

class ConcreteObserver(private val name: String) : Observer {
    override fun update(data: Any) {
        println("$name received data: $data")
    }
}

fun main() {
    val subject = Subject()

    val observer1 = ConcreteObserver("Observer 1")
    val observer2 = ConcreteObserver("Observer 2")

    subject.attach(observer1)
    subject.attach(observer2)

    subject.notifyObservers("Hello World!")

    subject.detach(observer2)

    subject.notifyObservers("Goodbye!")
}
```
