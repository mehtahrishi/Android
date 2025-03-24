### **How to Create an Android App that Displays an Alert Dialog on Back Button Press**
This guide will help you create an **Android app** where an **alert dialog** appears when the user presses the **Back button**, asking if they want to **exit**.

---

### **Step 1: Create a New Android Project**
- **Open Android Studio**
- Click **New Project** > Select **Empty Activity**
- Click **Next**, name your app, choose **Java** as the language, and click **Finish**.

---

### **Step 2: Modify `activity_main.xml` (UI Design)**
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
        android:text="Hi From Hrishi Mehta Press Back to Exit"
        android:textSize="22sp"
        android:textStyle="bold"
        android:padding="10dp"/>
</LinearLayout>
```

---

### **Step 3: Modify `MainActivity.java` (Handle Back Button Press)**
📂 **`java > com.example.yourapp > MainActivity.java`**
```java
package com.example.yourapp;

import android.content.DialogInterface;
import android.os.Bundle;
import android.view.KeyEvent;
import android.widget.Toast;
import androidx.appcompat.app.AlertDialog;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    // Override Back Button Press
    @Override
    public void onBackPressed() {
        showExitDialog();
    }

    // Method to show Exit Confirmation Dialog
    private void showExitDialog() {
        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setTitle("Exit App");
        builder.setMessage("Are you sure you want to exit?");
        
        // Exit on "Yes"
        builder.setPositiveButton("Yes", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int which) {
                finish();  // Close App
            }
        });

        // Dismiss Dialog on "No"
        builder.setNegativeButton("No", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int which) {
                dialog.dismiss();
            }
        });

        // Show the Alert Dialog
        builder.create().show();
    }
}
```

---

### **Step 4: Run the Application**
1. **Build & Run** (`Shift + F10` or Click ▶ Run)
2. **Press the Back Button** → A **confirmation dialog** will appear.
3. If **"Yes"** is clicked → The app **closes**.  
4. If **"No"** is clicked → The dialog **disappears**, and the user stays in the app.

---

### ✅ **Features Implemented**
✔ **Back Button Press Handling**  
✔ **Alert Dialog with Exit Confirmation**  
✔ **Custom Message & Buttons**  

🚀 **Try running it and let me know if you need any improvements!** 🎯
