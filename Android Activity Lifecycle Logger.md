### **Android Activity Lifecycle Logger**
This program will **log all lifecycle methods** of an Android `Activity` to Logcat.

---

### **Step 1: Create a New Android Project**
1. **Open Android Studio**
2. **Create a New Project** > Select **Empty Activity**
3. **Name** the app (e.g., `LifecycleLoggerApp`), choose **Java**, and click **Finish**.

---

### **Step 2: Modify `MainActivity.java`**
📂 **`java > com.example.lifecyclelogger > MainActivity.java`**
```java
package com.example.lifecyclelogger;

import android.os.Bundle;
import android.util.Log;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    private static final String TAG = "ActivityLifecycle";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Log.d(TAG, "onCreate() called");
    }

    @Override
    protected void onStart() {
        super.onStart();
        Log.d(TAG, "onStart() called");
    }

    @Override
    protected void onResume() {
        super.onResume();
        Log.d(TAG, "onResume() called");
    }

    @Override
    protected void onPause() {
        super.onPause();
        Log.d(TAG, "onPause() called");
    }

    @Override
    protected void onStop() {
        super.onStop();
        Log.d(TAG, "onStop() called");
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        Log.d(TAG, "onDestroy() called");
    }
}
```

---

### **Step 3: Modify `activity_main.xml`**
📂 **`res > layout > activity_main.xml`**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    android:padding="20dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Lifecycle Logger"
        android:textSize="22sp"
        android:textStyle="bold"
        android:padding="10dp"/>
</LinearLayout>
```

---

### **Step 4: Run the App & Check Logs**
#### **How to View Logs in Logcat**
1. **Run the App** (`Shift + F10` or Click ▶ Run).
2. **Open Logcat** (Bottom Panel in Android Studio).
3. **Filter Logs**: Type `ActivityLifecycle` in the search bar.
4. Perform the following actions and observe Logcat:

| Action | Logged Message |
|--------|--------------|
| Launch App | `onCreate()`, `onStart()`, `onResume()` |
| Press Home Button | `onPause()`, `onStop()` |
| Reopen App | `onStart()`, `onResume()` |
| Close App | `onPause()`, `onStop()`, `onDestroy()` |

---

### ✅ **Features Implemented**
✔ Logs all **lifecycle methods** of an `Activity`.  
✔ View logs in **Logcat** for debugging.  
✔ Helps understand **Android Lifecycle Events**.  

🚀 **Run it and check Logcat to see the activity lifecycle in action!** 🎯
