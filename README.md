# [TEMPLATE RESEARCH TECHNOLOGY](#template-research-technology) 
## [Agenda](#agenda)
### [Fundamental Android](#fundamental-android)
#### [Syntax Java Core](#syntax-java-core)
##### [If - statement](#if---statement)
###### [Knowledge surround it](#knowledge-surround-it)
###### [Practical](#practical)

>> - [Robolectric](#robolectric)
>> - [Espresso](#espresso)
>> - [References](#references)
    
# Robolectric
>>> - [Project setup](#project-setup) 
# Project setup
    
    testCompile "org.robolectric:robolectric:3.3.2"
    androidTestCompile 'junit:junit:4.12'
   
# Espresso
>>> - [Project setup](#project-setup) 

    - The best solution is to add untrusted server certificates automatically to android studio when using the internet from workplace. Go to Settings -> Tools -> Server Certificates, now check "Accept non-trusted certificates automatically". After this coding can be done offline.
    
    - testCompile 'junit:junit:4.12'
    androidTestCompile('com.android.support.test.espresso:espresso-core:2.2.2', {
        exclude group: 'com.android.support', module: 'support-annotations'
    })
    
    - Example 1:
    public class LoginActivityEspressoTest {

    private String TAG = "LoginActivityTest";

    @Rule
    public ActivityTestRule<LoginActivity> mLoginActivity = new ActivityTestRule<>(LoginActivity.class);

    SessionManager sessionManager;

    @Before
    public void initialize() {
        sessionManager = SessionManager.getInstance(InstrumentationRegistry.getContext());
        sessionManager.setUserName("AAAAA");
    }

    @Test
    public void ensureTextChangesWork() {
        // Type text and then press the button.
        try {
            Thread.sleep(1000);
            Log.i(TAG, "Type text and then press the button");
            onView(withId(R.id.edtUsername)).perform(typeText("AAAAA"), closeSoftKeyboard());
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        try {
            Thread.sleep(1000);
            Log.i(TAG, "Perform click into edtUsername");
            onView(withId(R.id.edtUsername)).perform(click());
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        try {
            Thread.sleep(1000);
            Log.i(TAG, "Check that the text was changed");
            onView(withId(R.id.edtUsername)).check(matches(withText(sessionManager.getUserName())));
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

    }}
   

   
   
# References
- Using Robolectric for Android unit testing on the JVM - Tutorial
http://www.vogella.com/tutorials/Robolectric/article.html

# Espresso
http://www.vogella.com/tutorials/AndroidTestingEspresso/article.html#espresso_gradleconfiguration
https://medium.com/mindorks/android-testing-part-1-espresso-basics-7219b86c862b

